# CTest

This repository demonstrates the usage of ctest with cmake.

## CMake

Please refer to [leetcode project](https://github.com/BruceChanJianLe/leetcode) for a more holistic example.
```cmake
# 1 two sum test
add_executable(1two_sum_test ./1two_sum_test.cpp)
target_link_libraries(1two_sum_test gtest_main)
target_include_directories(1two_sum_test PRIVATE ../include)

# 2 add two numbers test
add_executable(2add_two_numbers_test ./2add_two_numbers_test.cpp)
target_link_libraries(2add_two_numbers_test gtest_main)
target_include_directories(2add_two_numbers_test PRIVATE ../include)

# Add tests
include(GoogleTest)
add_test(NAME 1two_sum_test COMMAND 1two_sum_test)
add_test(NAME 2add_two_numbers_test COMMAND 2add_two_numbers_test)
```

Selectively run google unit test. For example, you would like to run `2add_two_numbers_test`.
The folder structure is as below.

```bash
.
├── build
├── CMakeLists.txt
├── include
├── Session.vim
├── Testing
└── tests
```

Command to run. `--test-dir` flag to point to the executable director.
`-V` for verbose, the more Vs the more verbose.
`-R` for regular expression matching.

```bash
ctest --test-dir build -VV -R 2
```

## Reference
- [link](https://opensource.com/article/22/1/unit-testing-googletest-ctest)
