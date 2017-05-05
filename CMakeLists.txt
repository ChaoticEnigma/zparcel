## ZParcel CMakeLists.txt
CMAKE_MINIMUM_REQUIRED(VERSION 3.0)

PROJECT(ZParcel)
ADD_SUBDIRECTORY(libchaos)

### =================== SOURCES =================== ###

SET(ZParcel_SOURCES
    main.h
    main.cpp
    zparcel.h
    zparcel.cpp
)

### =================== BUILD =================== ###

ADD_EXECUTABLE(zparcel ${ZParcel_SOURCES})
LibChaos_Configure_Target(zparcel)

### =================== TESTS =================== ###

ADD_TEST(NAME "Create Parcel" CONFIGURATIONS zparcel COMMAND $<TARGET_FILE:zparcel> test.parcel create)
ADD_TEST(NAME "List Parcel" CONFIGURATIONS zparcel COMMAND $<TARGET_FILE:zparcel> test.parcel list)
ADD_TEST(NAME "Test Parcel" CONFIGURATIONS zparcel COMMAND $<TARGET_FILE:zparcel> test.parcel test)
