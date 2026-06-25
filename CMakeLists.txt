cmake_minimum_required(VERSION 3.10)
project(dns-firewall-tool VERSION 1.0.0 LANGUAGES CXX)

# Set C++ standard
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra -Werror")

# Find required packages
find_package(PkgConfig REQUIRED)
pkg_check_modules(PCAP REQUIRED libpcap)
pkg_check_modules(YAML REQUIRED yaml-0.1)

# Include directories
include_directories(${PCAP_INCLUDE_DIRS})
include_directories(${YAML_INCLUDE_DIRS})
include_directories(${CMAKE_SOURCE_DIR}/src)

# Source files
set(SOURCES
    src/main.cpp
    src/dns/dns_server.cpp
    src/dns/dns_filter.cpp
    src/dns/dns_cache.cpp
    src/firewall/firewall.cpp
    src/firewall/packet_filter.cpp
    src/firewall/rules_engine.cpp
    src/common/logger.cpp
    src/common/config.cpp
    src/common/utils.cpp
    src/network/socket.cpp
    src/network/packet.cpp
)

# Create executable
add_executable(dns-firewall-tool ${SOURCES})

# Link libraries
target_link_libraries(dns-firewall-tool
    ${PCAP_LIBRARIES}
    ${YAML_LIBRARIES}
    pthread
)

# Installation
install(TARGETS dns-firewall-tool DESTINATION /usr/local/bin)
install(DIRECTORY config/ DESTINATION /etc/dns-firewall-tool)
install(DIRECTORY docs/ DESTINATION /usr/share/doc/dns-firewall-tool)

# Testing
enable_testing()
add_executable(test_dns tests/test_dns.cpp src/dns/dns_filter.cpp src/common/logger.cpp src/common/utils.cpp)
add_executable(test_firewall tests/test_firewall.cpp src/firewall/rules_engine.cpp src/common/logger.cpp src/common/utils.cpp)

add_test(NAME DNS_Tests COMMAND test_dns)
add_test(NAME Firewall_Tests COMMAND test_firewall)