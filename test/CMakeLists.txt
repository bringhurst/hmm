add_executable(tests tests.cpp)
target_link_libraries(tests PRIVATE hmm::libhmm Catch2::Catch2WithMain)
