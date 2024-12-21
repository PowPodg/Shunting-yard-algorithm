#test
include(FetchContent)

FetchContent_Declare(
  googletest
  GIT_REPOSITORY https://github.com/google/googletest.git
  GIT_TAG        release-1.11.0
)
FetchContent_MakeAvailable(googletest)
add_library(GTest::GTest INTERFACE IMPORTED)
target_link_libraries(GTest::GTest INTERFACE gtest_main)

add_executable(algoritm_test alg_test.cpp "../ShuntingYard.h" "../ShuntingYard.cpp")

target_link_libraries(algoritm_test
 PRIVATE
  GTest::GTest
  )

add_test(all_gtest algoritm_test)