cmake_minimum_required(VERSION 3.20)
project(zmk-config-corne NONE)

# Set ZMK paths
set(ZMK_ROOT "${CMAKE_CURRENT_SOURCE_DIR}/zmk")
set(ZMK_APP "${ZMK_ROOT}/app")

# Add include directories for IntelliSense
include_directories(
    # ZMK C headers
    ${ZMK_APP}/include
    ${ZMK_APP}/include/zmk
    ${ZMK_APP}/include/dt-bindings
    ${ZMK_APP}/include/drivers

    # DeviceTree files
    ${ZMK_APP}/dts
    ${ZMK_APP}/boards

    # Config directory
    ${CMAKE_CURRENT_SOURCE_DIR}/config
)

# Add compile definitions for ZMK macros
add_compile_definitions(
    DT_HAS_ZMK=1
)

# Create a dummy target to help CLion understand the project structure
# This allows CLion to index the files without actually building anything
add_custom_target(zmk-config-dummy
    SOURCES
        ${CMAKE_CURRENT_SOURCE_DIR}/config/corne.keymap
)