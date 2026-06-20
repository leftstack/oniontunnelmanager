<div align="center">

  # Onion Tunnel Manager

  **Publish and reach private services through Tor onion services with a focused desktop interface.**

  Powered by Arti & Chisel.

</div>

Onion Tunnel Manager configures & manages the processes needed to carry Chisel tunnels over Tor. It can publish a local Chisel server as an onion service or connect a Chisel client to that service through Arti's local SOCKS proxy. It can do both from the same application.

The result is a small, self-contained control surface for private TCP & UDP forwarding without manually maintaining Arti configuration files or long Chisel command lines.

## Highlights

- **Server & client modes** in one native desktop application
- **Arti-managed onion services** with automatic address discovery
- **Forward & reverse Chisel tunnels** over TCP or UDP
- **Reusable profiles** with isolated settings and Tor state
- **Authentication and fingerprint options** for hardened Chisel connections
- **Live process logs** with copy support and sensitive authentication values redacted from displayed commands
- **Binary capability checks** before a session starts
- **Automatic process cleanup** when a session stops or the application exits
- **Dark, cream, & forest UI themes**

## How It Works

```text
Public side                         Tor network                         Private side

Local service <-- Chisel server <-- Arti onion service  .onion  Arti SOCKS --> Chisel client --> Local port
```

For server operation, Arti publishes an onion service that forwards to a Chisel server bound to localhost. For client operation, Arti provides a local SOCKS proxy & Chisel uses it to reach the server's `.onion` address. Onion Tunnel Manager generates the required Arti configuration, builds the Chisel commands, and supervises both processes.

## Get Onion Tunnel Manager

Download the latest package for your platform from the repository's **Releases** page, extract it, and launch Onion Tunnel Manager.

Packages are available for:

- Windows 64-bit
- Linux 64-bit

The latest copies of Arti & Chisel are included with the application package. Onion Tunnel Manager detects them automatically, though alternate binaries can be selected from the **Binaries** if you want to use your own built binaries.

## Create a Server

1. Open the **Server** tab and verify the Arti and Chisel binaries.
2. Choose the onion-service nickname and public port.
3. Configure the local Chisel port and any authentication options.
4. Enable reverse tunnels or SOCKS5 support when your use case requires them.
5. Select **Start Server** and wait for the onion address to appear.
6. Copy the generated `.onion` address to the client through a trusted channel.

## Connect a Client

1. Open the **Client** tab and enter the server's `.onion` address and port.
2. Add one or more forward or reverse tunnel rules.
3. Add matching authentication or server fingerprint settings when configured on the server.
4. Select **Start Client**.
5. Use the configured local port while Onion Tunnel Manager keeps Arti and Chisel running.

## Profiles and Data

Profiles make it easy to keep separate endpoints, tunnel rules, credentials, and Tor state. The default profile is created on first launch, and additional profiles can be added, selected, and removed from the profile manager.

Application data is stored in the `profiles` directory beside Onion Tunnel Manager. Treat this directory as sensitive: it may contain authentication settings and the private key material that preserves an onion service's address. Back it up securely if the address must remain stable.

## Security Notes

- Onion Tunnel Manager is a process manager and configuration interface; the network security properties come from Arti & Chisel.
- A tunnel exposes whatever endpoint you configure. Bind services to loopback unless remote access is intentional.
- Use Chisel authentication & verify the server fingerprint where appropriate.
- Review the **Server Log** & **Client Log** tabs when diagnosing connectivity, but inspect logs before sharing them.
- Keep Onion Tunnel Manager, Arti, and Chisel updated & obtain binaries from trusted sources.

## Powered By

- [Arti](https://arti.torproject.org/) for Tor connectivity & onion services
- [Chisel](https://github.com/jpillora/chisel) for application tunnels

## Trademark Notice

Tor is a trademark of The Tor Project, Inc. Onion Tunnel Manager is an independent project and is not endorsed by or affiliated with The Tor Project.

---
*Note: This repository contains binary releases only.*
