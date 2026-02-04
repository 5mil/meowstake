Meowstake Linux Full Node Environment
=====================================

Overview
--------
This document defines a Linux-based environment tailored for Meowstake that provides:

- A push-button full node setup for Meowstake.
- A GUI-enabled Linux desktop with the Meowstake Qt wallet integrated.
- A bundled cgminer fork configured to support multiple ASIC devices and CPU/GPU mining.

This environment is intended to be used for production full nodes and mining deployments.

Components
----------

1. Base OS
   - Recommended base: Ubuntu LTS (64-bit) with full desktop environment.
   - Must include: build-essential, Qt5, Berkeley DB, OpenSSL, Boost.

2. Meowstake Core
   - meowstaked (daemon)
   - Meowstake-qt (GUI wallet)

3. Mining Stack
   - cgminer fork with:
     - ASIC drivers enabled
     - CPU/GPU fallback enabled
     - unified configuration templates

4. Push-Button Node Setup
   - A single script should:
     - install dependencies
     - build Meowstake core
     - configure the node
     - launch meowstaked + Meowstake-qt

Repository Layout Proposal
--------------------------

Add a new top-level folder:

```
linux-node/
  setup.sh
  cgminer/
  wallet/
  README.md
```

- `setup.sh`: installs dependencies and builds binaries.
- `cgminer/`: the cgminer fork (as a submodule or embedded snapshot).
- `wallet/`: preconfigured desktop entry and launcher.
- `README.md`: instructions for node deployment.

Launch Preparation Checklist
-----------------------------

- Ensure ports are finalized in `src/init.cpp` and `src/bitcoinrpc.cpp`.
- Confirm genesis block and checkpoints in `src/main.cpp` and `src/checkpoints.cpp`.
- Confirm network magic bytes in `src/main.cpp` for production network.
- Validate MAX_MONEY and emission schedule.

Notes
-----
The environment definition will be expanded with exact scripts once the target
Linux distribution and cgminer fork details are finalized.
