---
title: "C programming reference doc"
date: "2023-11-11"
# description: "Implementation of command design pattern in python"
tags: ["C"]
categories: ["posts"]
# series: ["Swedish"]
aliases: ["c-programming"]
# ShowToc: true
# TocOpen: true
ShowBreadCrumbs: true
draft: false
---

***Convert void data-type (byte array) to uint8_t type***

```C
static uint8_t notify_func(const void *data)
{
	uint8_t value =  ((uint8_t *)data)[7];
	return value;
}
```

***Structure data-type as function arguments***

```C
static uint8_t notify_func(struct bt_gatt_subscribe_params *params)
{
    printk("value_handle : %d", params->value_handle)
}
```

***Declare enumes as types***

```C
typedef enum {
    STRING,
    NUMBERS,
    COMPLEX,
    DATATYPE_COUNT,
    INVALID_SENSOR
} sensor_datatype_t;
```

***String initialisation to char pointer***

```C

const char *p_mac_addr = "0C:8C:DC:41:E1:EF";

static void print_mac_addr(void)
{
    printk("p_mac_addr : %s\n", p_mac_addr)
}
```

***String as function return values***

```C
char* get_sensor_mac_addr(void){
    return p_mac_addr;
}
```

***Parse unsigned int from byte array pointer***

```C
uint32_t get_uint_32(const uint8_t *array, size_t start_index) {
    uint32_t value = 0;
    value |= array[start_index];
    value |= array[start_index + 1] << 8;
    value |= array[start_index + 2] << 16;
    value |= array[start_index + 3] << 24;
    return value;
}
```

***Parse signed int from byte array pointer***

```C
int32_t get_int_32(const uint8_t *array, size_t start_index) {
    int32_t value = 0;
    value |= array[start_index];
    value |= array[start_index + 1] << 8;
    value |= array[start_index + 2] << 16;
    value |= array[start_index + 3] << 24;
    return value;
}
```

***Declaring function data-types and callback pattern***

```C
// calculation.h
#pragma once

typedef void (*calculation_result_cb_t)(float a, float b, float result);

int init_calculation(calculation_result_cb_t result_callback);
int calculate_sum(float a, float b);
```

```C
// calculation.c
#include "stdio.h"
#include "calculation.h"

static calculation_result_cb_t calc_result_cb = NULL;

int init_calculation(calculation_result_cb_t result_callback) {
    calc_result_cb = result_callback;
    return 0;
}

int calculate_sum(float a, float b) {
    if (calc_result_cb != NULL) {
        calc_result_cb(a, b, a + b);
    }
    return 0;
}
```
```C
// main.c
#include <stdio.h>
#include "calculations/calculation.h"


static void result_cb(float a, float b, float result) {
    printf("%.2f + %.2f = %.2f\n", a, b, result);
}

int main() {
    printf("Callback functions!\n");
    init_calculation(result_cb);

    if (calculate_sum(10, 20)) {
        printf("error\n");
    }
    return 0;
}
```
