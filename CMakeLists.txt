# Copyright (c) Microsoft Corporation
#
# All rights reserved.
#
# MIT License
#
# Permission is hereby granted, free of charge, to any person obtaining a copy of
# this software and associated documentation files (the "Software"), to deal in
# the Software without restriction, including without limitation the rights to
# use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
# of the Software, and to permit persons to whom the Software is furnished to do
# so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED *AS IS*, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.

cmake_minimum_required(VERSION 3.20)

project(Clp LANGUAGES C CXX VERSION 1.17.7)

set(CMAKE_CXX_STANDARD 20)

include(GNUInstallDirs)
include(CMakePackageConfigHelpers)

set(CLP_INSTALL_INCLUDE_DIR ${CMAKE_INSTALL_INCLUDEDIR}/Coin)
set(CLP_INSTALL_CMAKE_DIR ${CMAKE_INSTALL_LIBDIR}/cmake/${PROJECT_NAME})

find_package(CoinUtils REQUIRED)
find_package(Osi REQUIRED)

set(CLP_SOURCES
  src/ClpNonLinearCost.cpp
  src/ClpModel.cpp
  src/AbcPrimalColumnSteepest.cpp
  src/AbcWarmStart.cpp
  src/ClpConstraintLinear.cpp
  src/ClpPEDualRowSteepest.cpp
  src/AbcSimplexFactorization.cpp
  src/ClpCholeskyDense.cpp
  src/ClpSimplexNonlinear.cpp
  src/AbcMatrix.cpp
  src/ClpSolve.cpp
  src/ClpParam.cpp
  src/ClpPESimplex.cpp
  src/ClpCholeskyTaucs.cpp
  src/ClpDualRowPivot.cpp
  src/ClpNetworkBasis.cpp
  src/ClpDualRowDantzig.cpp
  src/ClpCholeskyPardiso.cpp
  src/ClpPlusMinusOneMatrix.cpp
  src/ClpCholeskyBase.cpp
  src/CoinAbcBaseFactorization3.cpp
  src/CoinAbcFactorization3.cpp
  src/AbcSimplexPrimal.cpp
  src/ClpSolver.cpp
  src/ClpGubDynamicMatrix.cpp
  src/ClpPrimalColumnSteepest.cpp
  src/ClpMain.cpp
  src/CoinAbcFactorization2.cpp
  src/CoinAbcBaseFactorization2.cpp
  src/AbcDualRowPivot.cpp
  src/CoinAbcDenseFactorization.cpp
  src/CbcOrClpParam.cpp
  src/CoinAbcFactorization1.cpp
  src/CoinAbcBaseFactorization1.cpp
  src/ClpInterior.cpp
  src/CoinAbcFactorization5.cpp
  src/AbcSimplexParallel.cpp
  src/CoinAbcBaseFactorization5.cpp
  src/ClpPredictorCorrector.cpp
  src/AbcPrimalColumnPivot.cpp
  src/CoinAbcBaseFactorization4.cpp
  src/CoinAbcFactorization4.cpp
  src/ClpPrimalColumnDantzig.cpp
  src/ClpMatrixBase.cpp
  src/ClpObjective.cpp
  src/ClpDynamicMatrix.cpp
  src/ClpCholeskyWssmpKKT.cpp
  src/CoinAbcSmallFactorization2.cpp
  src/ClpFactorization.cpp
  src/CoinAbcSmallFactorization3.cpp
  src/ClpPEDualRowDantzig.cpp
  src/ClpDualRowSteepest.cpp
  src/ClpPdcoBase.cpp
  src/AbcNonLinearCost.cpp
  src/ClpPdco.cpp
  src/CoinAbcSmallFactorization1.cpp
  src/ClpHelperFunctions.cpp
  src/ClpCholeskyUfl.cpp
  src/CoinAbcSmallFactorization4.cpp
  src/CoinAbcSmallFactorization5.cpp
  src/ClpLinearObjective.cpp
  src/ClpPresolve.cpp
  src/ClpQuadraticObjective.cpp
  src/ClpParameters.cpp
  src/ClpLsqr.cpp
  src/AbcPrimalColumnDantzig.cpp
  src/ClpNetworkMatrix.cpp
  src/Clp_C_Interface.cpp
  src/ClpParamUtils.cpp
  src/CoinAbcOrderedFactorization5.cpp
  src/ClpPrimalColumnPivot.cpp
  src/ClpCholeskyWssmp.cpp
  src/CoinAbcHelperFunctions.cpp
  src/CoinAbcOrderedFactorization4.cpp
  src/ClpPackedMatrix.cpp
  src/ClpMessage.cpp
  src/ClpDynamicExampleMatrix.cpp
  src/ClpDummyMatrix.cpp
  src/ClpOutput.cpp
  src/ClpSimplexPrimal.cpp
  src/ClpConstraintQuadratic.cpp
  src/ClpEventHandler.cpp
  src/AbcDualRowDantzig.cpp
  src/ClpCholeskyMumps.cpp
  src/ClpSimplexOther.cpp
  src/AbcDualRowSteepest.cpp
  src/ClpSimplexDual.cpp
  src/AbcSimplexDual.cpp
  src/ClpSimplex.cpp
  src/CoinAbcOrderedFactorization3.cpp
  src/ClpPEPrimalColumnDantzig.cpp
  src/CoinAbcOrderedFactorization2.cpp
  src/ClpConstraint.cpp
  src/ClpNode.cpp
  src/ClpGubMatrix.cpp
  src/CoinAbcOrderedFactorization1.cpp
  src/ClpPEPrimalColumnSteepest.cpp
  src/AbcSimplex.cpp
  src/Idiot.cpp
  src/IdiSolve.cpp
  src/MyEventHandler.cpp
  src/MyMessageHandler.cpp
  src/unitTest.cpp
  src/OsiClp/OsiClpSolverInterface.cpp
)

set(CLP_HEADERS
  src/ClpParamUtils.hpp
  src/ClpCholeskyWssmp.hpp
  src/CoinAbcHelperFunctions.hpp
  src/ClpPrimalColumnPivot.hpp
  src/ClpPackedMatrix.hpp
  src/ClpDynamicExampleMatrix.hpp
  src/ClpMessage.hpp
  src/CoinAbcCommonFactorization.hpp
  src/ClpDummyMatrix.hpp
  src/ClpOutput.hpp
  src/ClpEventHandler.hpp
  src/ClpConstraintQuadratic.hpp
  src/ClpSimplexPrimal.hpp
  src/ClpCholeskyMumps.hpp
  src/AbcDualRowDantzig.hpp
  src/AbcDualRowSteepest.hpp
  src/ClpSimplexDual.hpp
  src/AbcSimplexDual.hpp
  src/ClpSimplexOther.hpp
  src/ClpPEPrimalColumnDantzig.hpp
  src/ClpSimplex.hpp
  src/ClpConstraint.hpp
  src/ClpNode.hpp
  src/ClpGubMatrix.hpp
  src/AbcSimplex.hpp
  src/ClpPEPrimalColumnSteepest.hpp
  src/ClpDynamicMatrix.hpp
  src/ClpFactorization.hpp
  src/ClpCholeskyWssmpKKT.hpp
  src/ClpPEDualRowDantzig.hpp
  src/CoinAbcCommon.hpp
  src/ClpDualRowSteepest.hpp
  src/AbcNonLinearCost.hpp
  src/CoinAbcBaseFactorization.hpp
  src/ClpPdcoBase.hpp
  src/ClpPdco.hpp
  src/AbcCommon.hpp
  src/ClpHelperFunctions.hpp
  src/ClpCholeskyUfl.hpp
  src/ClpLinearObjective.hpp
  src/ClpPresolve.hpp
  src/ClpParameters.hpp
  src/ClpQuadraticObjective.hpp
  src/ClpLsqr.hpp
  src/ClpNetworkMatrix.hpp
  src/AbcPrimalColumnDantzig.hpp
  src/AbcSimplexPrimal.hpp
  src/ClpGubDynamicMatrix.hpp
  src/ClpSolver.hpp
  src/ClpPrimalColumnSteepest.hpp
  src/ClpConfig.h
  src/AbcDualRowPivot.hpp
  src/ClpInterior.hpp
  src/CoinAbcDenseFactorization.hpp
  src/CbcOrClpParam.hpp
  src/ClpPredictorCorrector.hpp
  src/AbcPrimalColumnPivot.hpp
  src/ClpObjective.hpp
  src/ClpMatrixBase.hpp
  src/ClpPrimalColumnDantzig.hpp
  src/CoinAbcFactorization.hpp
  src/ClpNonLinearCost.hpp
  src/ClpModel.hpp
  src/ClpConstraintLinear.hpp
  src/ClpPEDualRowSteepest.hpp
  src/AbcPrimalColumnSteepest.hpp
  src/AbcWarmStart.hpp
  src/AbcSimplexFactorization.hpp
  src/ClpCholeskyDense.hpp
  src/ClpSimplexNonlinear.hpp
  src/AbcMatrix.hpp
  src/ClpSolve.hpp
  src/ClpParam.hpp
  src/ClpPESimplex.hpp
  src/ClpModelParameters.hpp
  src/ClpCholeskyTaucs.hpp
  src/ClpDualRowPivot.hpp
  src/Clp_C_Interface.h
  src/ClpPrimalQuadraticDantzig.hpp
  src/ClpNetworkBasis.hpp
  src/ClpCholeskyPardiso.hpp
  src/ClpPlusMinusOneMatrix.hpp
  src/ClpDualRowDantzig.hpp
  src/ClpCholeskyBase.hpp
  src/Idiot.hpp
  src/MyEventHandler.hpp
  src/MyMessageHandler.hpp
  src/config_clp_default.h
  src/config_default.h
  src/configall_system.h
  src/configall_system_msc.h
  src/OsiClp/OsiClpConfig.h
  src/OsiClp/OsiClpSolverInterface.hpp
)

add_library(${PROJECT_NAME} ${CLP_SOURCES})

# Alias pour usage identique en sous-projet et via find_package()
add_library(Coin::Clp ALIAS ${PROJECT_NAME})

target_compile_options(${PROJECT_NAME}
  PRIVATE
    $<$<CXX_COMPILER_ID:MSVC>:
      /bigobj /MP /wd4996 /wd4819 /wd4251 /wd4267 /wd4244 /wd4275>
    $<$<CXX_COMPILER_ID:AppleClang>:
      -Wno-inconsistent-missing-override
      -Wno-unused-command-line-argument
      -Wno-unused-result
      -Wno-exceptions>
)

if(APPLE)
    set(CMAKE_OSX_DEPLOYMENT_TARGET "10.9"
        CACHE STRING "Minimum OS X deployment version")
endif()

# PIC : obligatoire pour .so, inoffensif pour .a
set_target_properties(${PROJECT_NAME} PROPERTIES
  POSITION_INDEPENDENT_CODE ON
  VERSION   "${PROJECT_VERSION}"
  SOVERSION "${PROJECT_VERSION_MAJOR}"
)

target_include_directories(${PROJECT_NAME}
                           PUBLIC
                           $<INSTALL_INTERFACE:${CLP_INSTALL_INCLUDE_DIR}>
                           $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src/>
                           $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src/OsiClp>)

include(CheckIncludeFileCXX)
check_include_file_cxx("cmath"  HAVE_CMATH)
check_include_file_cxx("cfloat" HAVE_CFLOAT)
if(NOT HAVE_CMATH OR NOT HAVE_CFLOAT)
  message(FATAL_ERROR "Missing required headers: cmath or cfloat.")
endif()

target_compile_definitions(${PROJECT_NAME}
  PRIVATE
    HAVE_CMATH
    HAVE_CFLOAT
    $<$<CXX_COMPILER_ID:MSVC>:_CRT_SECURE_NO_WARNINGS>
)

target_link_libraries(${PROJECT_NAME} PUBLIC Coin::CoinUtils Coin::Osi)

install(
  TARGETS   ${PROJECT_NAME}
  EXPORT    ClpTargets
  ARCHIVE   DESTINATION "${CMAKE_INSTALL_LIBDIR}"  COMPONENT library
  LIBRARY   DESTINATION "${CMAKE_INSTALL_LIBDIR}"  COMPONENT library
  RUNTIME   DESTINATION "${CMAKE_INSTALL_BINDIR}"  COMPONENT library
)

install(
  FILES       ${CLP_HEADERS}
  DESTINATION "${CLP_INSTALL_INCLUDEDIR}"
  COMPONENT   headers
)

configure_package_config_file(
  "${CMAKE_CURRENT_SOURCE_DIR}/Config.cmake.in"
  "${CMAKE_CURRENT_BINARY_DIR}/ClpConfig.cmake"
  INSTALL_DESTINATION "${CLP_INSTALL_CMAKEDIR}"
  PATH_VARS
    CLP_INSTALL_INCLUDEDIR
    CMAKE_INSTALL_LIBDIR
)

write_basic_package_version_file(
  "${CMAKE_CURRENT_BINARY_DIR}/ClpConfigVersion.cmake"
  VERSION       "${PROJECT_VERSION}"
  COMPATIBILITY SameMajorVersion
)

install(
  FILES
    "${CMAKE_CURRENT_BINARY_DIR}/ClpConfig.cmake"
    "${CMAKE_CURRENT_BINARY_DIR}/ClpConfigVersion.cmake"
  DESTINATION "${CLP_INSTALL_CMAKEDIR}"
)

install(
  EXPORT      ClpTargets
  NAMESPACE   Coin::
  DESTINATION "${CLP_INSTALL_CMAKEDIR}"
)
