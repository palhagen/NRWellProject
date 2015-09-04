cmake_minimum_required (VERSION 2.8)

project (NR_iotools)

include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}/../..
	)

add_library( ${PROJECT_NAME}
fileio.cpp
fileio.hpp
logkit.cpp
logkit.hpp
stringtools.cpp
stringtools.hpp
tabularfile.cpp
tabularfile.hpp
)
