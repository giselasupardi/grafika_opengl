# CMake entry point
cmake_minimum_required (VERSION 3.0)
project (Tutorials)

find_package(OpenGL REQUIRED)



if( CMAKE_BINARY_DIR STREQUAL CMAKE_SOURCE_DIR )
    message( FATAL_ERROR "Please select another Build Directory ! (and give it a clever name, like bin_Visual2012_64bits/)" )
endif()
if( CMAKE_SOURCE_DIR MATCHES " " )
	message( "Your Source Directory contains spaces. If you experience problems when compiling, this can be the cause." )
endif()
if( CMAKE_BINARY_DIR MATCHES " " )
	message( "Your Build Directory contains spaces. If you experience problems when compiling, this can be the cause." )
endif()



# Compile external dependencies 
add_subdirectory (external)

# On Visual 2005 and above, this module can set the debug working directory
cmake_policy(SET CMP0026 OLD)
list(APPEND CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/external/rpavlik-cmake-modules-fe2273")
include(CreateLaunchers)
include(MSVCMultipleProcessCompile) # /MP

if(INCLUDE_DISTRIB)
	add_subdirectory(distrib)
endif(INCLUDE_DISTRIB)

include_directories(
	external/AntTweakBar-1.16/include/
	external/glfw-3.1.2/include/
	external/glm-0.9.7.1/
	external/glew-1.13.0/include/
	external/assimp-3.0.1270/include/
	external/bullet-2.81-rev2613/src/
	external/glut/include/
	.
)

set(ALL_LIBS
	${OPENGL_LIBRARY}
	glfw
	GLEW_1130
	-lGL
	-lGLU
	-lglut
	-lIL
)

add_definitions(
	-DTW_STATIC
	-DTW_NO_LIB_PRAGMA
	-DTW_NO_DIRECT3D
	-DGLEW_STATIC
	-D_CRT_SECURE_NO_WARNINGS
)

# Tugas minggu 2
## Tugas 1
add_executable(tugas_2_1
	minggu_2/tugas1/tugas_1.cpp
)
target_link_libraries(tugas_2_1
	${ALL_LIBS}
)
# Xcode and Visual working directories
set_target_properties(tugas_2_1 PROPERTIES XCODE_ATTRIBUTE_CONFIGURATION_BUILD_DIR "${CMAKE_CURRENT_SOURCE_DIR}/minggu_2/tugas1")
create_target_launcher(tugas_2_1 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/minggu_2/tugas1")
create_default_target_launcher(tugas_2_1 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/minggu_2/tugas1")

## Tugas 2
add_executable(tugas_2_2
	minggu_2/tugas2/tugas_2.cpp
	common/shader.cpp
	common/shader.hpp
	
	minggu_2/tugas2/CarFragmentShader.fragmentshader
	minggu_2/tugas2/CarVertexShader.vertexshader
	minggu_2/tugas2/CrossFragmentShader.fragmentshader
	minggu_2/tugas2/CrossVertexShader.vertexshader
	minggu_2/tugas2/WheelFragmentShader.fragmentshader
	minggu_2/tugas2/WheelVertexShader.vertexshader
	minggu_2/tugas2/WindowFragmentShader.fragmentshader
	minggu_2/tugas2/WindowVertexShader.vertexshader
)
target_link_libraries(tugas_2_2
	${ALL_LIBS}
)
# Xcode and Visual working directories
set_target_properties(tugas_2_2 PROPERTIES XCODE_ATTRIBUTE_CONFIGURATION_BUILD_DIR "${CMAKE_CURRENT_SOURCE_DIR}/minggu_2/tugas2")
create_target_launcher(tugas_2_2 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/minggu_2/tugas2")
create_default_target_launcher(tugas_2_2 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/minggu_2/tugas2")

# Tugas minggu 3
## Tugas 1
add_executable(tugas_3_1
	minggu_3/tugas1/tugas_1.cpp
)
target_link_libraries(tugas_3_1
	${ALL_LIBS}
)
# Xcode and Visual working directories
set_target_properties(tugas_3_1 PROPERTIES XCODE_ATTRIBUTE_CONFIGURATION_BUILD_DIR "${CMAKE_CURRENT_SOURCE_DIR}/minggu_3/tugas1")
create_target_launcher(tugas_3_1 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/minggu_3/tugas1")
create_default_target_launcher(tugas_3_1 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/minggu_3/tugas1")

# Tugas minggu 4
## Tugas 1
add_executable(tugas_4_1
	minggu_4/tugas1/tugas_1.cpp
	common/shader.cpp
	common/shader.hpp
	common/texture.cpp
	common/texture.hpp
	common/control4.cpp
	common/control4.hpp
)
target_link_libraries(tugas_4_1
	${ALL_LIBS}
)
# Xcode and Visual working directories
set_target_properties(tugas_4_1 PROPERTIES XCODE_ATTRIBUTE_CONFIGURATION_BUILD_DIR "${CMAKE_CURRENT_SOURCE_DIR}/minggu_4/tugas1")
create_target_launcher(tugas_4_1 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/minggu_4/tugas1")
create_default_target_launcher(tugas_4_1 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/minggu_4/tugas1")

# Tugas minggu 5
## Tugas 1
add_executable(tugas_5_1
	minggu_5/tugas1/tugas_1.cpp
	common/shader.cpp
	common/shader.hpp
	common/texture.cpp
	common/texture.hpp
	common/control4.cpp
	common/control4.hpp
)
target_link_libraries(tugas_5_1
	${ALL_LIBS}
)
# Xcode and Visual working directories
set_target_properties(tugas_5_1 PROPERTIES XCODE_ATTRIBUTE_CONFIGURATION_BUILD_DIR "${CMAKE_CURRENT_SOURCE_DIR}/minggu_5/tugas1")
create_target_launcher(tugas_5_1 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/minggu_5/tugas1")
create_default_target_launcher(tugas_5_1 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/minggu_5/tugas1")

# Tugas minggu 6
## Tugas 1
add_executable(tugas_6_1
	minggu_6/tugas1/tugas_1.cpp
	common/shader.cpp
	common/shader.hpp
	common/texture.cpp
	common/texture.hpp
	common/control4.cpp
	common/control4.hpp
)
target_link_libraries(tugas_6_1
	${ALL_LIBS}
)
# Xcode and Visual working directories
set_target_properties(tugas_6_1 PROPERTIES XCODE_ATTRIBUTE_CONFIGURATION_BUILD_DIR "${CMAKE_CURRENT_SOURCE_DIR}/minggu_6/tugas1")
create_target_launcher(tugas_6_1 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/minggu_6/tugas1")
create_default_target_launcher(tugas_6_1 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/minggu_6/tugas1")

SOURCE_GROUP(common REGULAR_EXPRESSION ".*/common/.*" )
SOURCE_GROUP(shaders REGULAR_EXPRESSION ".*/.*shader$" )

if (NOT ${CMAKE_GENERATOR} MATCHES "Xcode" )
# Our Code
add_custom_command(
   TARGET tugas_2_1 POST_BUILD
   COMMAND ${CMAKE_COMMAND} -E copy "${CMAKE_CURRENT_BINARY_DIR}/${CMAKE_CFG_INTDIR}/tugas_2_1${CMAKE_EXECUTABLE_SUFFIX}" "${CMAKE_CURRENT_SOURCE_DIR}/minggu_2/tugas1/"
)
add_custom_command(
   TARGET tugas_2_2 POST_BUILD
   COMMAND ${CMAKE_COMMAND} -E copy "${CMAKE_CURRENT_BINARY_DIR}/${CMAKE_CFG_INTDIR}/tugas_2_2${CMAKE_EXECUTABLE_SUFFIX}" "${CMAKE_CURRENT_SOURCE_DIR}/minggu_2/tugas2/"
)
add_custom_command(
   TARGET tugas_3_1 POST_BUILD
   COMMAND ${CMAKE_COMMAND} -E copy "${CMAKE_CURRENT_BINARY_DIR}/${CMAKE_CFG_INTDIR}/tugas_3_1${CMAKE_EXECUTABLE_SUFFIX}" "${CMAKE_CURRENT_SOURCE_DIR}/minggu_3/tugas1/"
)
add_custom_command(
   TARGET tugas_4_1 POST_BUILD
   COMMAND ${CMAKE_COMMAND} -E copy "${CMAKE_CURRENT_BINARY_DIR}/${CMAKE_CFG_INTDIR}/tugas_4_1${CMAKE_EXECUTABLE_SUFFIX}" "${CMAKE_CURRENT_SOURCE_DIR}/minggu_4/tugas1/"
)
add_custom_command(
   TARGET tugas_5_1 POST_BUILD
   COMMAND ${CMAKE_COMMAND} -E copy "${CMAKE_CURRENT_BINARY_DIR}/${CMAKE_CFG_INTDIR}/tugas_5_1${CMAKE_EXECUTABLE_SUFFIX}" "${CMAKE_CURRENT_SOURCE_DIR}/minggu_5/tugas1/"
)
add_custom_command(
   TARGET tugas_6_1 POST_BUILD
   COMMAND ${CMAKE_COMMAND} -E copy "${CMAKE_CURRENT_BINARY_DIR}/${CMAKE_CFG_INTDIR}/tugas_6_1${CMAKE_EXECUTABLE_SUFFIX}" "${CMAKE_CURRENT_SOURCE_DIR}/minggu_6/tugas1/"
)
#

elseif (${CMAKE_GENERATOR} MATCHES "Xcode" )

endif (NOT ${CMAKE_GENERATOR} MATCHES "Xcode" )

