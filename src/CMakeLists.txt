add_library(libhmm libhmm.cpp)
add_library(hmm::libhmm ALIAS libhmm)

set_target_properties(
  libhmm
  PROPERTIES OUTPUT_NAME hmm
)

target_compile_features(libhmm PUBLIC cxx_std_20)

target_include_directories(libhmm
  PUBLIC
    $<INSTALL_INTERFACE:include>
    $<BUILD_INTERFACE:${CMAKE_SOURCE_DIR}/include>
  PRIVATE
    ${CMAKE_SOURCE_DIR}/include
)

include(GNUInstallDirs)
install(TARGETS libhmm
  EXPORT hmm-targets
  LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
  ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
  RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
  INCLUDES DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
)

install(
  DIRECTORY ${PROJECT_SOURCE_DIR}/include/
  DESTINATION ${CMAKE_INSTALL_INCLUDEDIR} 
)

install(
  EXPORT hmm-targets
  FILE hmm-config.cmake
  NAMESPACE hmm::
  DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/hmm
)
