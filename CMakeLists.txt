cmake_minimum_required (VERSION 2.8)
project (lex_yacc_howto)

include_directories(${CMAKE_CURRENT_BINARY_DIR})
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

BISON_TARGET(Example4Parser example4.y ${CMAKE_CURRENT_BINARY_DIR}/example4.tab.c)
FLEX_TARGET(Example4Scanner example4.l ${CMAKE_CURRENT_BINARY_DIR}/example4.yy.c)
ADD_FLEX_BISON_DEPENDENCY(Example4Scanner Example4Parser)
add_executable(example4 
  ${BISON_Example4Parser_OUTPUTS} 
  ${FLEX_Example4Scanner_OUTPUTS}
)

