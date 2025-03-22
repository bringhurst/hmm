add_executable(hmm hmm.cpp)
target_link_libraries(hmm PRIVATE hmm::libhmm)

# Install the the default binary directory
include(GNUInstallDirs)
install(
  TARGETS hmm
  RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)
