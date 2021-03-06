SET(LOCAL_REGIONS_SOURCES
Expansion.cpp
Expansion0D.cpp
Expansion1D.cpp
Expansion2D.cpp
Expansion3D.cpp
QuadExp.cpp
HexExp.cpp
MatrixKey.cpp
NodalTetExp.cpp
NodalTriExp.cpp
PointExp.cpp
PrismExp.cpp
PyrExp.cpp
SegExp.cpp
TetExp.cpp
TriExp.cpp
)

SET(LOCAL_REGIONS_HEADERS
Expansion.h
Expansion0D.h
Expansion1D.h
Expansion2D.h
Expansion3D.h
HexExp.h
LinSys.hpp
#LocalRegions.h
LocalRegions.hpp
LocalRegionsDeclspec.h
MatrixKey.h
NodalTetExp.h
NodalTriExp.h
PointExp.h
PrismExp.h
PyrExp.h
QuadExp.h
SegExp.h
TetExp.h
TriExp.h
)


ADD_DEFINITIONS(-DLOCAL_REGIONS_EXPORTS)

ADD_NEKTAR_LIBRARY(LocalRegions lib ${NEKTAR_LIBRARY_TYPE} ${LOCAL_REGIONS_SOURCES} ${LOCAL_REGIONS_HEADERS})
TARGET_LINK_LIBRARIES(LocalRegions
        optimized LibUtilities   debug LibUtilities-g
        optimized SpatialDomains debug SpatialDomains-g
        optimized StdRegions     debug StdRegions-g
        optimized ${TINYXML_LIB} debug ${TINYXML_LIB}
        ${Boost_THREAD_LIBRARY}
        ${Boost_IOSTREAMS_LIBRARY}
        ${Boost_DATE_TIME_LIBRARY}
        ${Boost_PROGRAM_OPTIONS_LIBRARY}
        ${Boost_SYSTEM_LIBRARY}
        ${ZLIB_LIBRARY}
	)
SET_LAPACK_LINK_LIBRARIES(LocalRegions)

INSTALL(DIRECTORY ./ DESTINATION ${NEKTAR_INCLUDE_DIR}/LocalRegions COMPONENT dev FILES_MATCHING PATTERN "*.h" PATTERN "*.hpp")
