cmake_minimum_required (VERSION 3.0)
project( radiusplugin )

set (CMAKE_CXX_STANDARD 11)

file(GLOB OBJECTS
        RadiusClass/RadiusAttribute.cpp
        RadiusClass/RadiusPacket.cpp
        RadiusClass/RadiusConfig.cpp
        RadiusClass/RadiusServer.cpp
        RadiusClass/RadiusVendorSpecificAttribute.cpp
        AccountingProcess.cpp
        Exception.cpp
        PluginContext.cpp
        UserAuth.cpp
        AcctScheduler.cpp
        IpcSocket.cpp
        radiusplugin.cpp
        User.cpp
        AuthenticationProcess.cpp
        main.cpp
        UserAcct.cpp
        UserPlugin.cpp
        Config.cpp)



add_library(plugin SHARED ${OBJECTS})
target_link_libraries(plugin gcrypt pthread)
set_target_properties(plugin PROPERTIES PREFIX "" SUFFIX ".so")


add_executable(test-plugin ${OBJECTS})
target_link_libraries(test-plugin gcrypt pthread)