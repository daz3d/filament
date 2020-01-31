#######################################################################
# Copyright (C) 2018-2020 DAZ 3D, Inc. All Rights Reserved.
#
# Pull in custom sim to add to build
#######################################################################

set(DZ_SHIM_SRC_DIR "" CACHE PATH "path to shim source code" )

if(EXISTS ${DZ_SHIM_SRC_DIR})
	get_filename_component(DZ_FILAMENT_ROOT_DIR "${CMAKE_CURRENT_LIST_DIR}/../" ABSOLUTE)
	add_subdirectory( ${DZ_SHIM_SRC_DIR} dzfilamentapi)
endif()