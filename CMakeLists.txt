cmake_minimum_required(VERSION 3.2)
project(opcua-modeling-tutorial-server)

# open62541 must be installed.
# If in custom path, then use -DCMAKE_PREFIX_PATH=/home/user/install
find_package(open62541 1.1 REQUIRED COMPONENTS FullNamespace)

# Output directory for Nodeset Compiler
set(GENERATE_OUTPUT_DIR "${CMAKE_BINARY_DIR}/src_generated/")

file(MAKE_DIRECTORY "${GENERATE_OUTPUT_DIR}")
include_directories("${GENERATE_OUTPUT_DIR}")

ua_generate_nodeset_and_datatypes(
        NAME "foo_flt"
        TARGET_PREFIX "${PROJECT_NAME}"
        FILE_CSV "${PROJECT_SOURCE_DIR}/model/Published/FooFlt/FooFltModel.csv"
        FILE_BSD "${PROJECT_SOURCE_DIR}/model/Published/FooFlt/FooFlt.Types.bsd"
        OUTPUT_DIR "${GENERATE_OUTPUT_DIR}"
	# This namespace index must match the order in which you are adding the nodeset in the source code
        NAMESPACE_MAP "2:https://new.foo.com/zebra-compression/flattening-and-subspacefolding/UA/"
        FILE_NS "${PROJECT_SOURCE_DIR}/model/Published/FooFlt/FooFlt.NodeSet2.xml"
        INTERNAL
)

# Previous macro automatically sets some variables which hold the generated source code files using the provided NAME
add_executable(opcua-modeling-tutorial-server
               ${UA_NODESET_FOO_FLT_SOURCES}
               ${UA_TYPES_FOO_FLT_SOURCES}
               main.c
               )

# Make sure the nodeset compiler is execute before compiling the main file
add_dependencies(opcua-modeling-tutorial-server
                 ${PROJECT_NAME}-ns-foo_flt
                 )

target_link_libraries(opcua-modeling-tutorial-server open62541::open62541)
