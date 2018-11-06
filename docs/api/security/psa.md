## Mbed PSA

### Terms and Abbreviations

| Term         | Meaning                             |
|--------------|-------------------------------------|
| PSA          | Platform Security Architecture      |
| SPM          | Secure Partition Manager            |
| SPE          | Secure Processing Environment       |
| NSPE         | Non-Secure Processing Environment   |
| IPC          | Inter Process Communication         |
| RoT          | Root Of Trust                       |


### Overview
Mbed PSA provides essential root of trust services and infrastructure for developing robust IoT applications.

When Mbed OS is running on PSA Security Model compliant target, Mbed PSA helps to protect cryptographic assets, credentials, and critical code sections by providing an isolation between a Secure Processing Environment (SPE) and a Non-Secure Processing Environment (NSPE). The isolation is managed by the Secure Partition Manager (SPM) which utilizes unique hardware features available on the target. The SPM provides standardized IPC APIs which abstract the fact that partitions could be living inside a virtualized environment (v8M, TEE on Cortex-A), or inside another chip.

Mbed PSA bridges the differences between PSA platforms and Non-PSA platforms for application developers, allowing them to use the same standard PSA APIs on both platform types.
Mbed PSA provides PSA API compliance for developing robust IoT applications and 
allows to choose platform type at later phase according to final application threat model.

### Platform types
Mbed PSA supports the following platform types:
- Non PSA platform: These are single core ARMv7-M targets.
On these targets Mbed PSA provides the same PSA services exposing PSA APIs as it would on PSA targets.
PSA emulation layer allows seamless software portability to more security oriented targets.
- Asymmetric Multiprocessing (AMP) systems: Multi core ARMv7-M targets (for example, PSoC6 featuring CM4 and CM0+ cores).
On these targets one of the cores is dedicated to PSA usage only and implements SPE.
Mbed PSA provides PSA APIs proxy implementation on non-secure core, which redirects execution to the SPE.
- ARMv8-M: New generation of ARM processors featuring TrustZone-M architecture.
PSA support for this platforms is in final stages of development and will be added to the list of Mbed PSA supported platforms shortly.

### Mbed PSA Services

Mbed PSA provides the following services:
- PSA RoT internal storage
- PSA Crypto APIs
