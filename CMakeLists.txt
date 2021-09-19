cmake_minimum_required(VERSION 3.20)
project(vulkan_learning)

set(CMAKE_CXX_STANDARD 23)

file(GLOB SOURCE_FILES
        main.cpp
)

message("VULKAN_SDK ${VULKAN_SDK}")

set( GLFW_BUILD_DOCS OFF CACHE BOOL  "GLFW lib only" )
set( GLFW_INSTALL OFF CACHE BOOL  "GLFW lib only" )

add_subdirectory(vendor/glfw)

add_executable(${PROJECT_NAME} ${SOURCE_FILES})

target_include_directories(${PROJECT_NAME}
        PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/vendor/glfw/include
        /Users/mdiahovets/VulkanSDK/1.2.189.0/macOS/include

        PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}/src
        )

target_link_libraries(${PROJECT_NAME} glfw /Users/mdiahovets/VulkanSDK/1.2.189.0/macOS/lib/libvulkan.1.dylib)