cmake_minimum_required (VERSION 2.8)
project (lex_yacc_howto)

find_package(BISON)
find_package(FLEX)

FLEX_TARGET(Example1Scanner example1.l ${CMAKE_CURRENT_BINARY_DIR}/example1.yy.c)
add_executable(example1 ${FLEX_Example1Scanner_OUTPUTS})
target_link_libraries(example1 fl)

FLEX_TARGET(Example2Scanner example2.l ${CMAKE_CURRENT_BINARY_DIR}/example2.yy.c)
add_executable(example2 ${FLEX_Example2Scanner_OUTPUTS})
target_link_libraries(example2 fl)

FLEX_TARGET(Example3Scanner example3.l ${CMAKE_CURRENT_BINARY_DIR}/example3.yy.c)
add_executable(example3 ${FLEX_Example3Scanner_OUTPUTS})
target_link_libraries(example3 fl)
