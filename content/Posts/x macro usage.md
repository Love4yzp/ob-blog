---
title: C 语言 X-Macros 重用技巧
date: 2024-01-06 23:39:36
tags:
  - C/CPP
permalink: x-macro-usage
aliases: x-macro
---

[X-Macros](https://en.wikipedia.org/wiki/X_macro) 是通过宏定义的方式预设来实现动态编程的效果，我主要是用于在创建一些数组时能够像 Python 中的字典一样，能够直接对应好位置 (下标)。

在 ESP32 中，Mission Pack 和 SenseCAP Indicator[^source] 中的 Embedded C 编程项目中都采用过。

[^source]: <https://github.com/Seeed-Solution/SenseCAP_Indicator_ESP32/blob/main/examples/indicator_lorawan/main/sensor/indicator_sensor.h>

预处理的宏定义枚举，对应着列表对应的设备信息：

```c
// indicator_sensor.h
// 添加传感器类型
#define SENSOR_TYPE_LIST           \
    X(SENSOR_CO2, "CO2")           \
    X(SENSOR_TVOC, "TVOC")         \
    X(SENSOR_HUMIDITY, "Humidity") \
    X(SENSOR_TEMP, "Temperature")  \
    // 可以继续添加其他传感器类型

// 定义传感器类型
#define X(type, str) type,
typedef enum { // 宏定义枚举
    SENSOR_TYPE_LIST
        ENUM_SENSOR_ALL
} SensorType;
#undef X

extern const char *SensorTypeStrings[];

// indicator_sensor.c
#define X(type, str)       str,
const char *SensorTypeStrings[] = {
    SENSOR_TYPE_LIST};
#undef X

char *getSensorName(const SensorType type)
{
    return SensorTypeStrings[type];
}
```

通过 `SENSOR_CO2` 就可以得到 "CO2" ，`O(1)` 的时间复杂度。

```c
char* name_co2 = SensorTypeStrings[SENSOR_CO2];
```

### 有什么好处？

```c
#define PORTA_MQTT_DEVICE_LIST                                           \
    X(Tracker1, "Tracker1", "/device_sensor_data"                        \
                            "/" OrgID "/" DeviceEUI_Tracker1 "/#")       \
    X(Tracker2, "Tracker2", "/device_sensor_data"                        \
                            "/" OrgID "/" DeviceEUI_Tracker2 "/#")       \
    X(Tracker3, "Tracker3", "/device_sensor_data"                        \
                            "/" OrgID "/" DeviceEUI_Tracker3 "/#")       \
    X(Tracker4, "Tracker4", "/device_sensor_data"                        \
                            "/" OrgID "/" DeviceEUI_Tracker4 "/#")       \
    X(Wio_Tracker, "WioTrack", "/device_sensor_data"                     \
                               "/" OrgID "/" DeviceEUI_Wio_Tracker "/#") \
    X(S2103, "S2103", "/device_sensor_data"                              \
                      "/" OrgID "/" DeviceEUI_S2103 "/#")                \
    X(S2105, "S2105", "/device_sensor_data"                              \
                      "/" OrgID "/" DeviceEUI_S2105 "/#")

#define MAX_TRACKER_NUM    4
#define X(id, name, topic) id,
typedef enum DEVICES_ENUM {
    PORTA_MQTT_DEVICE_LIST
        DEVICES_MAX
} DEVICES_ENUM;


extern const char *DEVICES_EUI[];
extern const char *DEVICES_STR[];
extern const char *TOPICS_ALL[];
#undef X
```

当你有大量、固定的信息，且是绑定到一起，需要同时初始化，作用就来了。
