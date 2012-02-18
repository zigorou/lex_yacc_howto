cmake_minimum_required (VERSION 2.6)
project (lex_yacc_howto)

find_package(FLEX)
FLEX_TARGET(Scanner example1.l ${CMAKE_CURRENT_BINARY_DIR}/lex.yy.cc)
add_executable(example1 ${FLEX_Scanner_OUTPUTS})
