# Makefile - STM32Cube SDK
#
# Copyright (c) 2020 Linaro Limited
#
# SPDX-License-Identifier: Apache-2.0

# message(FATAL_ERROR "FeiLong: ${CONFIG_HAS_GD32CUBE}")
add_subdirectory_ifdef(CONFIG_HAS_GD32CUBE devices)
# add_subdirectory_ifdef(CONFIG_HAS_GD32LIB lib)
