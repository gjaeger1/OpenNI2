cmake_minimum_required(VERSION 3.0.0)
project(libopenni2 VERSION 0.1 LANGUAGES CXX)

find_package(PkgConfig REQUIRED)


#####
# library definition
#####
set(LIBOPENNI2_HEADER )
set(LIBOPENNI2_CFLAGS )
set(LIBOPENNI2_INCLUDE_DIR include)

#add_library(libopenni2 INTERFACE)
#target_include_directories(libopenni2 INTERFACE include/)
install(DIRECTORY Include DESTINATION include/OpenNI2)
install(FILES Bin/x64-Release/libOpenNI2.so DESTINATION lib)
install(FILES Bin/x64-Release/OpenNI2/Drivers/libOniFile.so DESTINATION lib)
install(FILES Bin/x64-Release/OpenNI2/Drivers/libDummyDevice.so DESTINATION lib)
install(FILES Bin/x64-Release/OpenNI2/Drivers/libPS1080.so DESTINATION lib)
install(FILES Bin/x64-Release/OpenNI2/Drivers/libPSLink.so DESTINATION lib)

set(LIBOPENNI2_DEST_DIR "${CMAKE_INSTALL_PREFIX}")
set(LIBOPENNI2_VERSION ${PROJECT_VERSION})
set(LIBOPENNI2_DEPS "-lOpenNI2 -lOniFile -lDummyDevice -lPS1080 -lPSLink")

CONFIGURE_FILE("libopenni2.pc.in" "libopenni2.pc" @ONLY)
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/libopenni2.pc DESTINATION share/pkgconfig)

