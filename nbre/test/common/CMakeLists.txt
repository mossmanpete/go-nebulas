add_executable(test_common main.cpp
  gtest_util.cpp
  gtest_util_json.cpp
  gtest_math.cpp
  #gtest_util_conf.cpp
  )

add_executable(test_timer_loop test_timer_loop.cpp)


target_link_libraries(test_common nbre_rt gtest)
target_link_libraries(test_timer_loop nbre_rt)

gtest_discover_tests(test_common)

add_test(NAME test_common
  COMMAND test_common)
set_tests_properties(
  test_common PROPERTIES
  ENVIRONMENT "LD_LIBRARY_PATH=${PROJECT_SOURCE_DIR}/lib/lib"
  )

add_subdirectory(ipc)


