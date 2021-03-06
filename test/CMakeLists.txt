find_package(Catch2 REQUIRED)

include(Catch)

add_executable(test_target 
    remap_test.cpp 
    to_matrix_channeled_test.cpp 
    to_matrix_test.cpp
    rm_cvref_test.cpp 
    pixel_to_vector_test.cpp 
    vector_to_pixel_test.cpp 
    from_matrix_test.cpp 
    as_matrix_test.cpp
    as_matrix_channeled_test.cpp
    true_channel_type_test.cpp
    pad_test.cpp
    channelwise_reduce_test.cpp)
target_link_libraries(test_target PRIVATE Catch2::Catch2 blazing-gil)
target_compile_options(test_target PRIVATE
$<$<CXX_COMPILER_ID:MSVC>:/W4 /WX>
$<$<NOT:$<CXX_COMPILER_ID:MSVC>>:-Wall -Wextra -pedantic -Werror>
)
catch_discover_tests(test_target)
