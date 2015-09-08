########################################################
#  
#  This is a CMake configuration file.
#  To use it you need CMake which can be 
#  downloaded from here: 
#    http://www.cmake.org/cmake/resources/software.html
#
#########################################################

# The interesting parts of Boost have been extracted using 
# the BCP tool:
#   http://www.boost.org/doc/libs/1_45_0/tools/bcp/doc/html/index.html
#

# Build instructions for BCP
# Taken from http://stackoverflow.com/questions/440585/building-boost-bcp
#
# 1. Open a Visual Studio 2010 command prompt
# 2. Go to the tools\jam\src folder in Boost and type: build.bat
# 3. It should produce a subfolder bin.ntx86 that contains bjam.exe. Copy bjam.exe to the Boost main folder.
# 4. Go into the tools\bcp folder and type: ..\..\bjam.exe --toolset=msvc
# 5. Copy bcp.exe to the Boost main folder.
# 6. In the file /boost/config/user.hpp uncomment the BOOST_ALL_NO_LIB
#    define.Otherwise, we will get linker errors on MSVC because of boost auto-linking.

# Usage of BCP to extract needed parts of boost for NRlib
# bcp boost/filesystem.hpp d:/gitroot-magnesj/NRWellProject/BoostParts


cmake_minimum_required( VERSION 2.8 ) 

project( BoostParts )

set( SOURCES  
    libs/filesystem/v2/src/v2_operations.cpp
    libs/filesystem/v2/src/v2_path.cpp
    libs/filesystem/v2/src/v2_portability.cpp

    libs/system/src/error_code.cpp
) 
    
    
#############################################################################

include_directories( ${CMAKE_CURRENT_SOURCE_DIR} )
            
add_library( BoostParts ${SOURCES} ) 
 
#############################################################################
 
# Special compiler and linker flags for MSVC
if( MSVC )
    add_definitions( /DUNICODE /D_UNICODE /Zc:wchar_t-  )
    
    set( CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /Oi /GL" ) 
    set_target_properties( ${PROJECT_NAME} PROPERTIES STATIC_LIBRARY_FLAGS "/LTCG" )
endif()
