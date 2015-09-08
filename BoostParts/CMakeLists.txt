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

# bcp boost/filesystem.hpp d:/gitroot-magnesj/NRWellProject/BoostParts

# WARNING: When doing this from fresh boost sources, note that
# in the file /boost/config/user.hpp the BOOST_ALL_NO_LIB
# define has been uncommented. Otherwise, we will get linker 
# errors on MSVC because of boost auto-linking.

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
