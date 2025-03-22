add_library(libhmm libhmm.cpp)
add_library(hmm::libhmm ALIAS libhmm)

set_target_properties(
  libhmm
  PROPERTIES OUTPUT_NAME hmm
)

target_compile_features(libhmm PUBLIC cxx_std_20)

target_include_directories(
  PUBLIC
    $<INSTALL_INTERFACE:include>
    $<BUILD_INTERFACE:${CMAKE_SOURCE_DIR/include}
  PRIVATE
    ${CMAKE_SOURCE_DIR}/include
)
