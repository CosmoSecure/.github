![CosmoSecure](../assets/CosmoSecure.png)
<!-- 
![GitHub Downloads (all assets, all releases)](https://img.shields.io/github/downloads/CosmoSecure/CosmoSecure/total?style=plastic)
-->
![GitHub License](https://img.shields.io/github/license/CosmoSecure/.github?style=social)
![Platform Compatibility](https://img.shields.io/badge/Platforms-Windows%20%7C%20Linux-green)

# CosmoSecure

CosmoSecure is an open-source, cross-platform password manager implementing **Zero-Knowledge Proof (ZKP) architecture** with **client-side encryption**.  
Built with Rust, Tauri, and React, it ensures the server never knows your master password through encrypted canary verification, providing genuine zero-knowledge security with complete user control over sensitive data.

---

## Application Goals

CosmoSecure addresses a fundamental question:

**How can a secure desktop password manager be built with client-side encryption and complete user control over sensitive data?**

The application aims to:

- Implement **Zero-Knowledge Proof** architecture where the server cannot verify master passwords
- Provide client-side encryption with encrypted canary verification
- Maintain complete user control over master passwords through ZKP authentication
- Offer transparent, auditable security implementations
- Balance robust cryptographic security with intuitive user experience
- Currently supports cloud storage with local storage planned for future releases

---

## Security Architecture and Trust Model

CosmoSecure implements a local-first security model with clearly defined trust boundaries.

### Core Security Features

- **Zero-Knowledge Proof (ZKP)**: Server stores only encrypted canary values, never password hashes - authentication happens entirely client-side through canary decryption
- **Client-Side Verification**: Master password correctness is verified by decrypting an encrypted canary string locally, not by server comparison
- **PBKDF2 Key Derivation**: 100,000 iterations with random salts protect against brute-force attacks
- **AES-GCM Encryption**: Industry-standard 256-bit authenticated encryption protects all password data
- **SHA-256 for Password Encryption**: Master password hashed only for encrypting stored passwords, never for authentication
- **Minimal Attack Surface**: Built with Rust for memory safety and Tauri for sandboxed execution
- **Content Protection**: Window content protection prevents screen capture and recording

### Threat Model

**CosmoSecure protects against:**
- Unauthorized access to encrypted password databases
- Accidental plaintext password storage
- Network-based attacks on password data
- Cross-site scripting and injection attacks
- Screen capture and screenshot attempts (Windows content protection)

### Storage Architecture

- **Cloud Storage**: Currently implemented - encrypted password data, encrypted canary values, and hashed passwords stored in MongoDB (master password itself is never stored)
- **Local Storage**: Planned for future releases to enable fully offline password management
- **Zero-Knowledge Design**: Server never receives or stores the actual master password - only encrypted canary values for verification

---

## Platform Support

### Windows
- Windows 10
- Windows 11

### Linux
- Ubuntu 20.04 LTS / 22.04 LTS  
- Debian 11
- Kali Linux (2023)
- RHEL 9 / 10

---

## Technical Architecture

### Frontend Stack
- **React 18** with TypeScript for modern UI development
- **Tailwind CSS** for responsive, theme-aware styling
- **Framer Motion** for smooth animations and transitions
- **Material-UI** components for consistent design language

### Backend & Security
- **Rust** for memory-safe systems programming
- **Tauri v2** for secure desktop application framework
- **CryptoJS** for client-side encryption operations
- **MongoDB** integration for cloud storage

### Key Features
- Cross-platform desktop application (Windows, Linux)
- **Zero-Knowledge Proof** master password verification using encrypted canary approach
- Real-time password strength analysis and breach monitoring
- Secure password generation with customizable parameters
- Client-side encryption with PBKDF2 key derivation (100k iterations)
- Dark/light theme support with system integration
- Encrypted session management and data persistence

---

## Development & Contribution

CosmoSecure is an open-source project welcoming community contributions.

### Prerequisites
- [Node.js](https://nodejs.org/) (v16 or higher)
- [Rust](https://www.rust-lang.org/tools/install) 
- [Tauri v2.0](https://v2.tauri.app/)

### Getting Started
```bash
# Clone repository
git clone https://github.com/akash2061/CosmoSecure.git
cd CosmoSecure

# Install dependencies  
npm install

# Development mode
npm run tauri dev

# Build for production
npm run tauri build
```

### Contributing Guidelines
- All security-related changes require thorough review and testing
- Code must follow Rust and TypeScript best practices
- Cryptographic implementations should include comprehensive documentation
- UI/UX changes should maintain accessibility and security standards
- Include appropriate tests for new functionality

### Security Reports
Security vulnerabilities should be reported via GitHub Issues with the `security` label.  
Critical security issues will be prioritized and addressed promptly.

Please report security vulnerabilities [here](https://github.com/CosmoSecure/.github/security/advisories/new)

---

## License

CosmoSecure is licensed under the **Apache License 2.0**.  
See the [LICENSE](LICENSE) file for complete details.

---

## Contact

- **Maintainer**: [akash2061](https://github.com/akash2061)
- **Email**: [aakash.soni8781@gmail.com](mailto:aakash.soni8781@gmail.com)
- **Issues**: [GitHub Issues](https://github.com/CosmoSecure/CosmoSecure/issues)

---

## What This Project Demonstrates

- **Zero-Knowledge Proof implementation** using encrypted canary verification
- Secure cryptographic workflows with PBKDF2 + AES-GCM in Rust
- Client-side authentication where the server cannot verify passwords
- Cross-platform desktop security using Tauri framework
- Modern React-based UI with security-first design principles
- Transparent security model with clearly defined trust boundaries

---

<p align="center">
    <a href="https://www.buymeacoffee.com/akash2061"><img width="200" src="https://github.com/akash2061/akash2061/blob/main/icons/bmc-button.png" /></a>
</p>

---

## Thank You!

Thank you for using **CosmoSecure**! We hope it helps you manage your passwords securely and efficiently. Stay tuned for new features, and don't hesitate to share your feedback!
