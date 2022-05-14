set(BINARY ${CMAKE_PROJECT_NAME}_tst)

file(GLOB_RECURSE TEST_SOURCES LIST_DIRECTORIES false *.h *.cpp)

set(SOURCES ${TEST_SOURCES})

add_executable(${BINARY} ${TEST_SOURCES})

add_test(NAME ${BINARY} COMMAND ${BINARY})

# Your-external "mylib", add GLOBAL if the imported library is located in directories above the current.
add_library( libsample SHARED IMPORTED GLOBAL)
# You can define two import-locations: one for debug and one for release.
set_target_properties( libsample PROPERTIES IMPORTED_LOCATION ${CMAKE_SOURCE_DIR}/include/libsample2.so )

# target_link_libraries(${BINARY} PUBLIC ${CMAKE_PROJECT_NAME}_lib gtest)
target_link_libraries(${BINARY} libsample gtest)