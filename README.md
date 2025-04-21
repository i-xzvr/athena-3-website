# ATHENA 3.0

Advanced Technological Hybrid for Enhanced Neural Autonomy (ATHENA) 3.0 is an open-source, self-learning AI platform with Mission, Command, and Planning (MCP) capabilities. The platform integrates AI distillation, multi-modal AI, real-time adaptability, and quantum-resilient design.

## Quick Start Guide

### Prerequisites

- **CPU**: 4+ cores, 2.5 GHz or higher
- **GPU**: NVIDIA GeForce GTX 1660 or better (CUDA 11.0+ compatible)
- **RAM**: 16GB+ DDR4
- **Storage**: 256GB+ SSD (NVMe preferred)
- **OS**: Ubuntu 22.04 LTS (recommended)
- **Docker**: 24.0.0+ and Docker Compose 2.20.0+
- **NVIDIA Container Toolkit**: For GPU support

### Installation

#### Docker Installation (Recommended)

1. **Install Docker and Docker Compose**:
   ```bash
   sudo apt update
   sudo apt install docker.io docker-compose
   sudo systemctl enable --now docker
   sudo usermod -aG docker $USER
   ```

2. **Install NVIDIA Container Toolkit** (for GPU support):
   ```bash
   distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
   curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
   curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
   sudo apt update
   sudo apt install -y nvidia-container-toolkit
   sudo systemctl restart docker
   ```

3. **Clone the Repository**:
   ```bash
   git clone https://github.com/i-xzvr/athena.git
   cd athena
   ```

4. **Configure Environment**:
   ```bash
   cp .env.example .env
   # Edit .env file with your configuration
   ```

5. **Start ATHENA Services**:
   ```bash
   docker-compose up -d
   ```

6. **Access ATHENA**:
   - Web Interface: http://localhost:8080
   - API: http://localhost:8080/api/v1

### Basic Usage

#### Creating a Mission

```bash
# Using the API
curl -X POST http://localhost:8080/api/v1/mission \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -d '{
    "mission_name": "Example Mission",
    "mission_description": "This is an example mission",
    "objectives": [
      {
        "objective_id": "obj1",
        "type": "navigation",
        "parameters": [
          {"name": "x", "value": "1.0"},
          {"name": "y", "value": "2.0"},
          {"name": "theta", "value": "0.0"}
        ]
      }
    ]
  }'
```

#### Executing a Mission

```bash
# Using the API
curl -X POST http://localhost:8080/api/v1/mission/YOUR_MISSION_ID/execute \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -d '{
    "parameters": []
  }'
```

#### Monitoring Status

```bash
# Using the API
curl -X GET http://localhost:8080/api/v1/mission/YOUR_MISSION_ID \
  -H "Authorization: Bearer YOUR_TOKEN"
```

## Key Features

- **Mission, Command, and Planning (MCP)**: Advanced mission planning, command processing, and resource allocation
- **AI Distillation**: Compress large models into efficient, deployable systems
- **Multi-Modal AI**: Process and understand vision, speech, text, and sensor data
- **Self-Learning**: Improve through reinforcement learning and continual adaptation
- **Quantum-Resistant Security**: Future-proof security with post-quantum cryptography
- **ROS2 Integration**: Seamless integration with robotic systems
- **Containerized Deployment**: Easy deployment with Docker and Kubernetes

## Repository Structure

```
athena/
├── athena/                  # Main Python package
│   ├── __init__.py
│   ├── main.py              # Entry point
│   ├── mcp/                 # MCP module
│   ├── distillation/        # AI Distillation module
│   ├── multimodal/          # Multi-Modal AI module
│   ├── self_learning/       # Self-Learning module
│   ├── security/            # Quantum Security module
│   ├── api/                 # API server
│   ├── web/                 # Web interface
│   ├── ros2/                # ROS2 integration
│   ├── utils/               # Utility functions
│   └── cli/                 # Command-line interface
├── config/                  # Configuration files
├── data/                    # Data directory
├── models/                  # Model storage
├── docker/                  # Docker configuration
├── kubernetes/              # Kubernetes manifests
├── scripts/                 # Utility scripts
├── tests/                   # Test suite
├── docs/                    # Documentation
├── examples/                # Example code and notebooks
├── requirements.txt         # Python dependencies
├── setup.py                 # Package setup
├── docker-compose.yml       # Docker Compose configuration
└── README.md                # Project README
```

## Documentation

For comprehensive documentation, see:

- [User and Developer Guide](./documentation/user_developer_guide.md)
- [ROS2 Integration](./integration_procedures/ros2_integration.md)
- [Docker Deployment](./integration_procedures/docker_deployment.md)
- [Hardware Requirements](./implementation_details/hardware_requirements.md)
- [Configuration Files](./implementation_details/configuration_files.md)

## Contributing

We welcome contributions to ATHENA 3.0! See [CONTRIBUTING.md](./documentation/contributing.md) for guidelines.

## License

ATHENA 3.0 is released under the MIT License. See [LICENSE](LICENSE) for details.

## Acknowledgments

ATHENA 3.0 builds upon numerous open-source projects and research in AI, robotics, and autonomous systems. We thank all contributors to these foundational technologies.
