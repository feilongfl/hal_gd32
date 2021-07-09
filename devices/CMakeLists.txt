# Makefile - GD32Cube SDK
#
# Copyright (c) 2016 Linaro Limited
#
# SPDX-License-Identifier: Apache-2.0

#add_library(GD32CUBE INTERFACE)
zephyr_library()

string(TOUPPER ${CONFIG_SOC} _GD32CUBE_CPU)
string(REPLACE "X" "x" GD32CUBE_CPU ${_GD32CUBE_CPU})

# GD32Cub uses the CPU name to expose SOC-specific attributes of a specific
# peripheral.
# It also requires USE_HAL_DRIVER to be define in order to benefit from
# GD32Cube HAL and LL APIs
zephyr_compile_definitions(
  -D${GD32CUBE_CPU}
  -DUSE_HAL_DRIVER
  -DUSE_FULL_LL_DRIVER
  )

set(gd_socs
    gd32e1x
  )

if(CONFIG_CPU_CORTEX_M4)
  zephyr_compile_definitions( -DCORE_CM4 )
elseif(CONFIG_CPU_CORTEX_M7)
  zephyr_compile_definitions( -DCORE_CM7 )
endif()

if(CONFIG_CLOCK_GD32_HSE_CLOCK)
  zephyr_compile_definitions( -DHSE_VALUE=${CONFIG_CLOCK_GD32_HSE_CLOCK} )
endif()

foreach(gd_soc ${gd_socs})
  string(TOUPPER ${gd_soc} soc_to_upper)
  if(CONFIG_SOC_SERIES_${soc_to_upper})
    zephyr_include_directories(
      ${gd_soc}x/GD32E10x_Firmware_Library_V1.0.3/Firmware/CMSIS/
      ${gd_soc}x/GD32E10x_Firmware_Library_V1.0.3/Firmware/CMSIS/GD/GD32E10x/Include
      ${gd_soc}x/GD32E10x_Firmware_Library_V1.0.3/Firmware/GD32E10x_standard_peripheral/Include
	  )

    add_subdirectory(${gd_soc}x)

  endif()
endforeach()

if(CONFIG_USE_GD32_ASSERT)
	zephyr_compile_definitions( -DUSE_FULL_ASSERT )
endif()
