SET(SPATIAL_DOMAINS_SOURCES
Conditions.cpp
GeomFactors.cpp
Geometry0D.cpp
Geometry1D.cpp
Geometry2D.cpp
Geometry3D.cpp
Geometry.cpp
HexGeom.cpp
InterfaceComponent.cpp
MeshComponents.cpp
MeshGraph.cpp
MeshGraph1D.cpp
MeshGraph2D.cpp
MeshGraph3D.cpp
pchSpatialDomains.cpp
PrismGeom.cpp
PyrGeom.cpp
QuadGeom.cpp
SegGeom.cpp
PointGeom.cpp
TetGeom.cpp
TriGeom.cpp
)

SET(SPATIAL_DOMAINS_HEADERS
Conditions.h
Curve.hpp
GeomFactors.h
Geometry0D.h
Geometry1D.h
Geometry2D.h
Geometry3D.h
Geometry.h
HexGeom.h
InterfaceComponent.h
MeshComponents.h
MeshGraph1D.h
MeshGraph2D.h
MeshGraph3D.h
MeshGraph.h
pchSpatialDomains.h
PrismGeom.h
PyrGeom.h
QuadGeom.h
SegGeom.h
PointGeom.h
SpatialDomainsDeclspec.h
TetGeom.h
TriGeom.h
SpatialDomains.hpp
)

SET(TINYXML_SOURCES
${TINYXML_SRC_DIR}/tinyxml.cpp
${TINYXML_SRC_DIR}/tinyxmlparser.cpp 
${TINYXML_SRC_DIR}/tinyxmlerror.cpp 
${TINYXML_SRC_DIR}/tinystr.cpp
)

SET(TINYXML_HEADERS
${TINYXML_INCLUDE_DIR}/tinystr.h
${TINYXML_INCLUDE_DIR}/tinyxml.h
)


ADD_DEFINITIONS(-DSPATIAL_DOMAINS_EXPORTS)

ADD_NEKTAR_LIBRARY(SpatialDomains lib ${NEKTAR_LIBRARY_TYPE} ${SPATIAL_DOMAINS_SOURCES} ${SPATIAL_DOMAINS_HEADERS})
TARGET_LINK_LIBRARIES(SpatialDomains
        optimized LibUtilities debug LibUtilities-g
        optimized StdRegions  debug StdRegions-g
        optimized ${TINYXML_LIB} debug ${TINYXML_LIB}
        ${Boost_THREAD_LIBRARY}
		${Boost_DATE_TIME_LIBRARY}
		${Boost_IOSTREAMS_LIBRARY}
		${Boost_ZLIB_LIBRARY}
	)

SET_LAPACK_LINK_LIBRARIES(SpatialDomains)

INSTALL(DIRECTORY ./ DESTINATION ${NEKTAR_INCLUDE_DIR}/SpatialDomains COMPONENT dev FILES_MATCHING PATTERN "*.h" PATTERN "*.hpp")

ADD_NEKTAR_LIBRARY(tinyxml lib STATIC ${TINYXML_SOURCES} ${TINYXML_HEADERS})

