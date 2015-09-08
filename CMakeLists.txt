cmake_minimum_required (VERSION 2.8)

project (NR-Project)

#SET (BOOST_ROOT "d:/boost_1_59_0/")

#set(Boost_INCLUDE_DIR "d:/local/boost_1_44_0/")
#set(Boost_LIBRARY_DIR "d:/local/boost_1_44_0/lib64/")
#FIND_PACKAGE( Boost 1.40 COMPONENTS filesystem REQUIRED )
#INCLUDE_DIRECTORIES( ${Boost_INCLUDE_DIR} )
#LINK_DIRECTORIES( ${Boost_LIBRARY_DIR} )


ADD_SUBDIRECTORY(BoostParts)

include_directories(
	${BoostParts_SOURCE_DIR}
	)


add_subdirectory (nrlib/well)
add_subdirectory (nrlib/iotools)

add_subdirectory(well_UnitTests )

