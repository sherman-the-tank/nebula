nebula_add_library(
    codec_test_obj OBJECT
    ResultSchemaProvider.cpp
    SchemaWriter.cpp
)

set(CODEC_TEST_LIBS
    $<TARGET_OBJECTS:codec_obj>
    $<TARGET_OBJECTS:codec_test_obj>
    $<TARGET_OBJECTS:common_meta_thrift_obj>
    $<TARGET_OBJECTS:common_common_thrift_obj>
    $<TARGET_OBJECTS:common_datatypes_obj>
    $<TARGET_OBJECTS:common_thrift_obj>
    $<TARGET_OBJECTS:common_base_obj>
    $<TARGET_OBJECTS:common_network_obj>
    $<TARGET_OBJECTS:common_fs_obj>
    $<TARGET_OBJECTS:common_thread_obj>
)


nebula_add_test(
    NAME row_reader_v1_test
    SOURCES RowReaderV1Test.cpp
    OBJECTS ${CODEC_TEST_LIBS}
    LIBRARIES ${THRIFT_LIBRARIES} wangle gtest
)

#nebula_add_executable(
#    NAME row_reader_bm
#    SOURCES RowReaderBenchmark.cpp
#    OBJECTS ${CODEC_TEST_LIBS}
#    LIBRARIES ${THRIFT_LIBRARIES} follybenchmark wangle boost_regex
#)
#
#nebula_add_test(
#    NAME nebula_codec_test
#    SOURCES NebulaCodecTest.cpp
#    OBJECTS ${CODEC_TEST_LIBS}
#    LIBRARIES ${THRIFT_LIBRARIES} wangle gtest
#)