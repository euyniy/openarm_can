# OpenArm CAN Library

A C++ library for CAN communication with OpenArm robotic hardware, supporting Damiao motors over CAN/CAN-FD interfaces.
This library is a part of [OpenArm SDK](https://github.com/enactic/openarm_sdk).

## Quick Start

### Prerequisites

- Linux with SocketCAN support
- CAN interface hardware
- CMake 3.22+
- C++17 compiler

### 1. Setup CAN Interface

Configure your CAN interface using the provided script:

```bash
# CAN 2.0 (default)
setup/configure_socketcan.sh can0

# CAN-FD with 5Mbps data rate
setup/configure_socketcan.sh can0 -fd
```

### 2. C++ Library

**Build & Install:**

```bash
cd openarm_can
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build
sudo cmake --install build
```

**Usage:**

```cpp
#include <openarm/can/socket/openarm.hpp>

openarm::can::socket::OpenArm arm("can0", true);  // CAN-FD enabled
arm.init_arm_motors({MotorType::DM4310}, {0x01}, {0x11});
arm.enable_all();
```

### 3. Python (🚧 EXPERIMENTAL - TEMPORARY 🚧)

> ⚠️ **WARNING: UNSTABLE API** ⚠️
> Python bindings are currently a direct low level **temporary port**, and will change **DRASTICALLY**.
> The interface is may break between versions.Use at your own risk! Discussions on the interface are welcomed.

**Build & Install:**

```bash
cd python

# Create and activate virtual environment (recommended)
python -m venv venv
source venv/bin/activate

./build.sh
```

**Usage:**

```python
# WARNING: This API is unstable and will change!
import openarm_can as oa

arm = oa.OpenArm("can0", True)  # CAN-FD enabled
arm.init_arm_motors([oa.MotorType.DM4310], [0x01], [0x11])
arm.enable_all()
```

### Examples

- **C++**: `examples/demo.cpp` - Complete arm control demo
- **Python**: `python/examples/example.py` - Basic Python usage

## Related links

- 📚 Read the [documentation](https://docs.openarm.dev/software/sdk/openarm-can/)
- 💬 Join the community on [Discord](https://discord.gg/FsZaZ4z3We)
- 📬 Contact us through <openarm@enactic.ai>

## License

Licensed under the Apache License 2.0. See `LICENSE.txt` for details.

Copyright 2025 Enactic, Inc.

## Code of Conduct

All participation in the OpenArm project is governed by our [Code of Conduct](CODE_OF_CONDUCT.md).
