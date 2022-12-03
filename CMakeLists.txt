# CMakeList.txt : CMake project for FourInRow, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.8)
project ("FourInRow")

# Compiler configurations
#set(CMAKE_CXX_FLAGS_DEBUG "/MTd /Zi /Ob0 /Od /RTC1")
#set(CMAKE_CXX_FLAGS_RELEASE "/MT /O2 /Ob2 /DNDEBUG")

find_package(gRPC CONFIG REQUIRED)
find_package(Protobuf CONFIG REQUIRED)


# Add source to this project's executable.
add_executable (FourInRow "FourInRow.cpp" "FourInRow.h")


target_link_libraries(FourInRow PRIVATE gRPC::gpr gRPC::grpc gRPC::grpc++ gRPC::grpc++_alts)
target_link_libraries(FourInRow PRIVATE re2::re2 c-ares::cares)
target_link_libraries(FourInRow PRIVATE protobuf::libprotoc protobuf::libprotobuf protobuf::libprotobuf-lite)

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET FourInRow PROPERTY CXX_STANDARD 20)
endif()

# TODO: Add tests and install targets if needed.

