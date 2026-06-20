<div align="center">

  <img src="../ui/icons/app.svg" alt="Onion Tunnel Manager" width="112" height="112">

  # Onion Tunnel Manager

  **Publish and reach private services through Tor onion services with a focused desktop interface.**

  Powered by Arti and Chisel.

</div>

Onion Tunnel Manager starts, configures, and monitors the processes needed to carry Chisel tunnels over Tor. It can publish a local Chisel server as an onion service, connect a Chisel client to that service through Arti's local SOCKS proxy, or do both from the same application.

The result is a small, self-contained control surface for private TCP and UDP forwarding without manually maintaining Arti configuration files or long Chisel command lines.

## Highlights

- **Server and client modes** in one native desktop application
- **Arti-managed onion services** with automatic address discovery
- **Forward and reverse Chisel tunnels** over TCP or UDP
- **Reusable profiles** with isolated settings and Tor state
- **Authentication and fingerprint options** for hardened Chisel connections
- **Live process logs** with copy support and sensitive authentication values redacted from displayed commands
- **Binary capability checks** before a session starts
- **Automatic process cleanup** when a session stops or the application exits
- **Dark, cream, and forest themes** with remembered window state
- **Single-instance operation** on Windows and Linux

## How It Works

```text
Public side                         Tor network                         Private side

Local service <-- Chisel server <-- Arti onion service  .onion  Arti SOCKS --> Chisel client --> Local port
```

On the server, Arti publishes an onion service that forwards to a Chisel server bound to localhost. On the client, Arti provides a local SOCKS proxy and Chisel uses it to reach the server's `.onion` address. Onion Tunnel Manager generates the required Arti configuration, builds the Chisel commands, and supervises both processes.

## Get Onion Tunnel Manager

Download the latest package for your platform from the repository's **Releases** page, extract it, and launch Onion Tunnel Manager.

Packages are available for:

- Windows 64-bit
- Linux 64-bit

Arti and Chisel are included with the application package. Onion Tunnel Manager detects them automatically; alternate binaries can be selected from the **Binaries** section when needed.

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

- Onion Tunnel Manager is a process manager and configuration interface; the network security properties come from Tor, Arti, and Chisel.
- A tunnel exposes whatever endpoint you configure. Bind services to loopback unless remote access is intentional.
- Use Chisel authentication and verify the server fingerprint where appropriate.
- Review the **Server Log** and **Client Log** tabs when diagnosing connectivity, but inspect logs before sharing them.
- Keep Onion Tunnel Manager, Arti, and Chisel updated and obtain binaries from trusted sources.

## Powered By

- [Arti](https://arti.torproject.org/) for Tor connectivity and onion services
- [Chisel](https://github.com/jpillora/chisel) for application tunnels

## Trademark Notice

Tor is a trademark of The Tor Project, Inc. Onion Tunnel Manager is an independent project and is not endorsed by, sponsored by, or affiliated with The Tor Project.

<div align="center">

  Made by [LeftStack](https://github.com/leftstack)

</div>
