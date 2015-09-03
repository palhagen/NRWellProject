cmake_minimum_required (VERSION 2.8)

project (NR_well)

include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}/../..
	)

add_library( ${PROJECT_NAME}
	laswell.cpp
	norsarwell.cpp
	rmswell.cpp
	well.cpp
	welloperations.cpp
)
