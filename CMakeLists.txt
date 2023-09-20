#
# project: fips-nanobind
#
cmake_minimum_required(VERSION 3.27)

find_package(Python 3.8  REQUIRED COMPONENTS Interpreter Development.Module)

if (NOT FIPS_IMPORT)
# include the fips main cmake file
get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
include("${FIPS_ROOT_DIR}/cmake/fips.cmake")

    project(fips-nanobind) 
    fips_setup()
endif()
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

fips_begin_lib(nanobind)
    target_include_directories(nanobind PUBLIC ${Python_INCLUDE_DIRS} nanobind/include)
    target_include_directories(nanobind PRIVATE nanobind/ext/robin_map/include)
    fips_files(
        nanobind/include/nanobind/make_iterator.h
        nanobind/include/nanobind/nanobind.h
        nanobind/include/nanobind/nb_accessor.h
        nanobind/include/nanobind/nb_attr.h
        nanobind/include/nanobind/nb_call.h
        nanobind/include/nanobind/nb_cast.h
        nanobind/include/nanobind/nb_class.h
        nanobind/include/nanobind/nb_defs.h
        nanobind/include/nanobind/nb_descr.h
        nanobind/include/nanobind/nb_enums.h
        nanobind/include/nanobind/nb_error.h
        nanobind/include/nanobind/nb_func.h
        nanobind/include/nanobind/nb_lib.h
        nanobind/include/nanobind/nb_misc.h
        nanobind/include/nanobind/nb_python.h
        nanobind/include/nanobind/nb_traits.h
        nanobind/include/nanobind/nb_tuple.h
        nanobind/include/nanobind/nb_types.h
        nanobind/include/nanobind/ndarray.h
        nanobind/include/nanobind/trampoline.h
        nanobind/include/nanobind/operators.h
        nanobind/include/nanobind/stl/array.h
        nanobind/include/nanobind/stl/bind_map.h
        nanobind/include/nanobind/stl/bind_vector.h
        nanobind/include/nanobind/stl/detail
        nanobind/include/nanobind/stl/detail/nb_array.h
        nanobind/include/nanobind/stl/detail/nb_dict.h
        nanobind/include/nanobind/stl/detail/nb_list.h
        nanobind/include/nanobind/stl/detail/nb_set.h
        nanobind/include/nanobind/stl/detail/traits.h
        nanobind/include/nanobind/stl/filesystem.h
        nanobind/include/nanobind/stl/function.h
        nanobind/include/nanobind/stl/list.h
        nanobind/include/nanobind/stl/map.h
        nanobind/include/nanobind/stl/optional.h
        nanobind/include/nanobind/stl/pair.h
        nanobind/include/nanobind/stl/set.h
        nanobind/include/nanobind/stl/shared_ptr.h
        nanobind/include/nanobind/stl/string.h
        nanobind/include/nanobind/stl/string_view.h
        nanobind/include/nanobind/stl/tuple.h
        nanobind/include/nanobind/stl/unique_ptr.h
        nanobind/include/nanobind/stl/unordered_map.h
        nanobind/include/nanobind/stl/unordered_set.h
        nanobind/include/nanobind/stl/variant.h
        nanobind/include/nanobind/stl/vector.h
        nanobind/include/nanobind/eigen/dense.h
        nanobind/include/nanobind/eigen/sparse.h

        nanobind/src/buffer.h
        nanobind/src/nb_internals.h
        nanobind/src/nb_internals.cpp
        nanobind/src/nb_func.cpp
        nanobind/src/nb_type.cpp
        nanobind/src/nb_enum.cpp
        nanobind/src/nb_ndarray.cpp
        nanobind/src/nb_static_property.cpp
        nanobind/src/common.cpp
        nanobind/src/error.cpp
        nanobind/src/trampoline.cpp
        nanobind/src/implicit.cpp
    )
fips_end_lib()


