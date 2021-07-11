# Copyright (c) 2017 Erwin Rol <erwin@erwinrol.com>
# Copyright (c) 2020 STMicroelectronics
#
# SPDX-License-Identifier: Apache-2.0

zephyr_library_sources(GD32E10x_Firmware_Library_V1.0.3/Firmware/CMSIS/GD/GD32E10x/Source/system_gd32e10x.c)
zephyr_library_sources_ifdef(CONFIG_USE_GD32_HAL_ADC GD32E10x_Firmware_Library_V1.0.3/Firmware/GD32E10x_standard_peripheral/Source/gd32e10x_adc.c)
zephyr_library_sources_ifdef(CONFIG_USE_GD32_HAL_GPIO GD32E10x_Firmware_Library_V1.0.3/Firmware/GD32E10x_standard_peripheral/Source/gd32e10x_gpio.c)
zephyr_library_sources_ifdef(CONFIG_USE_GD32_HAL_UART GD32E10x_Firmware_Library_V1.0.3/Firmware/GD32E10x_standard_peripheral/Source/gd32e10x_usart.c)
zephyr_library_sources_ifdef(CONFIG_USE_GD32_HAL_RCU GD32E10x_Firmware_Library_V1.0.3/Firmware/GD32E10x_standard_peripheral/Source/gd32e10x_rcu.c)
