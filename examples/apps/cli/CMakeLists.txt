#
#  Copyright (c) 2019, The OpenThread Authors.
#  All rights reserved.
#
#  Redistribution and use in source and binary forms, with or without
#  modification, are permitted provided that the following conditions are met:
#  1. Redistributions of source code must retain the above copyright
#     notice, this list of conditions and the following disclaimer.
#  2. Redistributions in binary form must reproduce the above copyright
#     notice, this list of conditions and the following disclaimer in the
#     documentation and/or other materials provided with the distribution.
#  3. Neither the name of the copyright holder nor the
#     names of its contributors may be used to endorse or promote products
#     derived from this software without specific prior written permission.
#
#  THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
#  AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
#  IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
#  ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE
#  LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR
#  CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF
#  SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
#  INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN
#  CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)
#  ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
#  POSSIBILITY OF SUCH DAMAGE.
#

set(COMMON_INCLUDES
    ${OT_PUBLIC_INCLUDES}
    ${TI_PUBLIC_INCLUDES}
    ${PROJECT_SOURCE_DIR}/src
    ${PROJECT_SOURCE_DIR}/openthread/examples/platforms
    ${PROJECT_SOURCE_DIR}/openthread/src/core

    # JJM include paths for ICall module
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/drivers/dpl
    ${TI_SIMPLELINK_SDK_DIR}/source
    ${TI_SIMPLELINK_SDK_DIR}/source/ti
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/controller/cc26xx/inc
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/inc
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/rom
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/common/cc26xx
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/icall/inc
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/hal/src/target/_common
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/common/cc26xx/npi/stack/
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/hal/src/inc
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/heapmgr
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/profiles/dev_info
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/profiles/simple_profile
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/icall/src/inc
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/npi/src/
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/osal/src/inc
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/services/src/saddr
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/services/src/sdata
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/common/nv
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/common/cc26xx
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/icall/src
    ${TI_SIMPLELINK_SDK_DIR}/kernel/tirtos7/packages
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/devices/cc13x4_cc26x4
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/posix/gcc

    ${TI_SIMPLELINK_SDK_DIR}/kernel/freertos
    ${TI_SIMPLELINK_SDK_DIR}/kernel

    # Needed for bget.h
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack/common/cc26xx/freertos
)

set(COMMON_SOURCES
    cli_uart.cpp
    main.c
    #bleAppTask.c
    #bleStackMenu.c
    app_main.c
    app_data.c
    app_pairing.c
    app_peripheral.c
    app_dev_info.c
    app_simple_gatt.c
    osal_icall_ble.c
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack/common/cc26xx/freertos/bget.c
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack/common/cc26xx/freertos/TI_heap_wrapper.c
    #${TI_SIMPLELINK_SDK_DIR}/source/ti/dmm/apps/common/ble_remote_display/stack/osal_icall_ble.c
    ${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/rom/agama_r1/rom_init.c
    #${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/common/cc26xx/util.c
    #${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/common/cc26xx/menu/two_btn_menu.c
    #${TI_SIMPLELINK_SDK_DIR}/source/ti/display/Display.c
    #${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack_flash/common/cc26xx/board_key.c
    ${TI_SIMPLELINK_SDK_DIR}/kernel/nortos/dpl/SystemP_nortos.c
    #${TI_SIMPLELINK_SDK_DIR}/source/ti/ble5stack/common/cc26xx/freertos/bget.c
)

set(USR_COMPILE_DEFINITIONS
    "USE_DMM"
    "SYSCFG"
    "CC13X4"
    "CC13XX"
    "POWER_SAVING"
    "TBM_ACTIVE_ITEMS_ONLY"
    "STACK_LIBRARY"
    "EXTENDED_STACK_SETTINGS=EXTENDED_STACK_SETTINGS_DEFAULT"
    "NPI_USE_UART"
    "ICALL_EVENTS"
    "ICALL_JT"
    "ICALL_LITE"
    "ICALL_STACK0_ADDR"
    "USE_ICALL"
    "ICALL_MAX_NUM_ENTITIES=6"
    "ICALL_MAX_NUM_TASKS=3"
    "OSAL_CBTIMER_NUM_TASKS=1"
    "ONE_BLE_LIB_SIZE_OPTIMIZATION"

    # the following are from ti_build_config.opt
    "HOST_CONFIG=PERIPHERAL_CFG"
    "USE_AE"
    "GAP_BOND_MGR"
    "HCI_TL_NONE"
    "FREERTOS"

    # from basic_ble_LP_EM_CC1354P10_1_freertos_ticlang
    "ICALL_NO_APP_EVENTS"
    "UARTLOG_ENABLE"
    "uartlog_FILE=0"
    "DeviceFamily_CC13X4"
    "FLASH_ONLY_BUILD"
    "NVOCMP_NWSAMEITEM=1"
    "EM_CC1354P10_1_LP"
    "NVOCMP_POSIX_MUTEX"
)

set(APPEND CMAKE_C_FLAGS -std=c99)

target_compile_options(openthread-cc13xx_cc26xx
    PUBLIC
        -O0
)

if(TI_SIMPLELINK_KERNEL STREQUAL "freertos")
    list(APPEND COMMON_SOURCES freertos_main.c)

elseif(TI_SIMPLELINK_KERNEL STREQUAL "tirtos7")
    list(APPEND COMMON_SOURCES tirtos_main.c)

else()
    message(FATAL_ERROR "Unsuported TI_SIMPLELINK_KERNEL: ${TI_SIMPLELINK_KERNEL}")
endif()

#if(OT_FTD)
#    include(ftd.cmake)
#endif()

if(OT_MTD)
    include(mtd.cmake)
endif()

#if(OT_RCP)
#    include(radio.cmake)
#endif()
