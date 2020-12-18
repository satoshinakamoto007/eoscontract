add_contract(bob.token bob.token ${CMAKE_CURRENT_SOURCE_DIR}/src/eosio.token.cpp)

target_include_directories(bob.token
   PUBLIC
   ${CMAKE_CURRENT_SOURCE_DIR}/include)

set_target_properties(bob.token
   PROPERTIES
   RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}")

configure_file( ${CMAKE_CURRENT_SOURCE_DIR}/ricardian/eosio.token.contracts.md.in ${CMAKE_CURRENT_BINARY_DIR}/ricardian/eosio.token.contracts.md @ONLY )

target_compile_options( bob.token PUBLIC -R${CMAKE_CURRENT_SOURCE_DIR}/ricardian -R${CMAKE_CURRENT_BINARY_DIR}/ricardian )
