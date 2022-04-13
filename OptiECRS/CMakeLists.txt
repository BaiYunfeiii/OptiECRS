cmake_minimum_required(VERSION 3.9)

project(OptiECRS VERSION 1.0.0 DESCRIPTION "OptiECRS")

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

file(GLOB_RECURSE EDV_INCLUDE_FILES "galois/*.h" "matrix/*.h" "procedures/*.h")

add_library(OptiECRS STATIC
        galois/galois.cpp
        matrix/extendedcauchymatrix.cpp
        procedures/optimizebranchandbound.cpp
        procedures/optimizeconsecutive.cpp
        procedures/optimizedirection.cpp
        procedures/optimizedirectionalcost.cpp
        procedures/optimizemixedinteger.cpp
        procedures/optimizemixedintegeralt.cpp
        procedures/randomheuristic.cpp
        )

set_target_properties(OptiECRS PROPERTIES VERSION ${PROJECT_VERSION})
set_target_properties(OptiECRS PROPERTIES SOVERSION 1)
set_target_properties(${PROJECT_NAME}
        PROPERTIES
        PUBLIC_HEADER OptiECRS.h)

include(GNUInstallDirs)
install(TARGETS OptiECRS
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}/OptiECRS
        PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/OptiECRS)