cmake_minimum_required (VERSION 3.23)

project ("ChatServer")

add_subdirectory(dependency/boost EXCLUDE_FROM_ALL)

# Server
add_executable (ChatServer "server/main.cpp" )
target_link_libraries(ChatServer Boost::asio)

# Client
add_executable (ChatClient "client/main.cpp")
target_link_libraries(ChatClient Boost::asio Boost::thread)

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET ChatServer PROPERTY CXX_STANDARD 20)
endif()
