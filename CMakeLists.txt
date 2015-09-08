cmake_minimum_required (VERSION 2.8)

project (NR-Project)

add_subdirectory(BoostParts)

include_directories(
	${BoostParts_SOURCE_DIR}
	)


add_subdirectory (nrlib/well)
add_subdirectory (nrlib/iotools)

add_subdirectory(well_UnitTests )

