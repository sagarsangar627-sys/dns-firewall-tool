# DNS & Firewall Security Tool

A comprehensive C/C++ network security tool combining DNS filtering and firewall capabilities for advanced network protection.

## Features

- **DNS Security**
  - DNS query filtering and blocking
  - Malicious domain detection
  - DNS resolver integration
  - Query logging and analytics
  - DNS cache management

- **Firewall Protection**
  - Packet-level filtering
  - Port-based access control
  - Protocol inspection
  - Connection state tracking
  - Rule-based traffic management

## Project Structure

```
dns-firewall-tool/
├── CMakeLists.txt              # Build configuration
├── README.md                   # Project documentation
├── LICENSE                     # License file
├── docs/                       # Documentation
│   ├── architecture.md         # System architecture
│   ├── dns-module.md          # DNS module documentation
│   ├── firewall-module.md     # Firewall module documentation
│   └── api.md                 # API reference
├── src/                        # Source code
│   ├── main.cpp               # Main entry point
│   ├── dns/                   # DNS module
│   │   ├── dns_server.h
│   │   ├── dns_server.cpp
│   │   ├── dns_filter.h
│   │   ├── dns_filter.cpp
│   │   ├── dns_cache.h
│   │   └── dns_cache.cpp
│   ├── firewall/              # Firewall module
│   │   ├── firewall.h
│   │   ├── firewall.cpp
│   │   ├── packet_filter.h
│   │   ├── packet_filter.cpp
│   │   ├── rules_engine.h
│   │   └── rules_engine.cpp
│   ├── common/                # Common utilities
│   │   ├── logger.h
│   │   ├── logger.cpp
│   │   ├── config.h
│   │   ├── config.cpp
│   │   ├── utils.h
│   │   └── utils.cpp
│   └── network/               # Network utilities
│       ├── socket.h
│       ├── socket.cpp
│       ├── packet.h
│       └── packet.cpp
├── tests/                     # Unit tests
│   ├── test_dns.cpp
│   ├── test_firewall.cpp
│   └── test_utils.cpp
├── config/                    # Configuration files
│   ├── dns_rules.conf
│   ├── firewall_rules.conf
│   └── app_config.yaml
└── scripts/                   # Build and deployment scripts
    ├── build.sh
    ├── install.sh
    └── run_tests.sh
```

## Requirements

- C++14 or higher
- CMake 3.10+
- Linux/Unix environment (primary support)
- libpcap (for packet capture)
- libyaml (for configuration)

## Installation

### Prerequisites

```bash
# Ubuntu/Debian
sudo apt-get install libpcap-dev libyaml-dev cmake build-essential

# macOS
brew install libpcap libyaml cmake
```

### Build

```bash
mkdir build
cd build
cmake ..
make
```

### Installation

```bash
sudo make install
```

## Usage

### Basic DNS Filtering

```bash
sudo ./dns-firewall-tool --dns --config config/dns_rules.conf
```

### Firewall Rules

```bash
sudo ./dns-firewall-tool --firewall --config config/firewall_rules.conf
```

### Combined Mode

```bash
sudo ./dns-firewall-tool --dns --firewall --config config/app_config.yaml
```

## Configuration

### DNS Configuration Example

```yaml
dns:
  port: 53
  interface: 0.0.0.0
  upstream_resolver: 8.8.8.8:53
  blocked_domains:
    - malicious.com
    - ads.example.com
  cache_size: 1000
  cache_ttl: 3600
```

### Firewall Configuration Example

```yaml
firewall:
  enabled: true
  default_policy: DROP
  rules:
    - name: "Allow SSH"
      protocol: TCP
      port: 22
      action: ACCEPT
    - name: "Block Port 80"
      protocol: TCP
      port: 80
      action: DROP
```

## Architecture

The tool is built with a modular architecture:

- **DNS Module**: Handles DNS queries, filtering, and caching
- **Firewall Module**: Manages packet filtering and access control
- **Common Module**: Provides logging, configuration, and utilities
- **Network Module**: Low-level network operations

## API Reference

See [docs/api.md](docs/api.md) for detailed API documentation.

## Testing

```bash
./scripts/run_tests.sh
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Security Notice

This tool requires elevated privileges (root/sudo) to operate on network interfaces. Use responsibly and only on networks you own or have permission to monitor.

## Support

For issues, questions, or contributions, please open an issue or contact the maintainers.

## Roadmap

- [ ] IPv6 support
- [ ] Machine learning-based anomaly detection
- [ ] Web UI dashboard
- [ ] Distributed filtering
- [ ] Performance optimization
- [ ] Windows support