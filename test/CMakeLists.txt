#[[
MIT License

Copyright © 2021 Bo Rydberg

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
]]

add_library(catch_main STATIC catch_main.cpp)
target_link_libraries(catch_main PRIVATE project_options)

add_executable(tests tests.cpp)
target_link_libraries(tests PRIVATE project_warnings project_options catch_main)

# Add a file containing a set of constexpr tests
add_executable(constexpr_tests constexpr_tests.cpp)
target_link_libraries(constexpr_tests PRIVATE project_options project_warnings catch_main)

# things go wrong with the constexpr testing
add_executable(relaxed_constexpr_tests constexpr_tests.cpp)
target_link_libraries(relaxed_constexpr_tests PRIVATE project_options project_warnings catch_main)
