
add_executable(xdgTestHelper
  main.swift)
target_link_libraries(xdgTestHelper PRIVATE
  Foundation
  FoundationNetworking
  FoundationXML)
# TODO(compnerd) properly propogate `BUILD_RPATH` to the target using CMake
if(NOT CMAKE_SYSTEM_NAME STREQUAL Windows AND NOT CMAKE_SYSTEM_NAME STREQUAL Darwin)
  target_link_options(xdgTestHelper PRIVATE
    "SHELL:-Xlinker -rpath -Xlinker $<TARGET_FILE_DIR:swiftDispatch> -Xlinker -rpath -Xlinker $<TARGET_FILE_DIR:Foundation>")
endif()
