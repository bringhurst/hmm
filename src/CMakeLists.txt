add_library(libhmm libhmm.cpp)
add_library(hmm::libhmm ALIAS libhmm)

set_target_properties(
  libhmm
  PROPERTIES OUTPUT_NAME hmm
)

target_compile_features(libhmm PUBLIC cxx_std_20)

target_include_directories(
  libhmm
  PRIVATE include
  PUBLIC ${CMAKE_SOURCE_DIR}/include
)
