[English](README.md) | [Vídeo en Español](https://www.youtube.com/watch?v=99qtaJU2E2k)

# OpenVPN Server Auto Setup Script

OpenVPN server installer for Ubuntu, Debian, AlmaLinux, Rocky Linux, CentOS, Fedora, openSUSE, Amazon Linux 2 and Raspberry Pi OS.

This script will let you set up your own VPN server in just a few minutes, even if you haven't used OpenVPN before. [OpenVPN](https://openvpn.net/community-resources/reference-manual-for-openvpn-2-6/) is an open-source, robust and highly flexible VPN protocol.

## Features

- Fully automated OpenVPN server setup, no user input needed
- Supports interactive install using custom options
- Generates VPN profiles to auto-configure Windows, macOS, iOS and Android devices
- Supports managing OpenVPN users and certificates
- Optimizes `sysctl` settings for improved VPN performance

## Installation

First, download the script on your Linux server\*:

```bash
wget -O openvpn.sh https://get.vpnsetup.net/ovpn
```

**Option 1:** Auto install OpenVPN using default options.

```bash
sudo bash openvpn.sh --auto
```

<details>
<summary>
See the script in action (terminal recording).
</summary>

**Note:** This recording is for demo purposes only.

<p align="center"><img src="docs/images/demo1.svg"></p>
</details>

For servers with an external firewall (e.g. [EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html)/[GCE](https://cloud.google.com/firewall/docs/firewalls)), open UDP port 1194 for the VPN.

**Option 2:** Interactive install using custom options.

```bash
sudo bash openvpn.sh
```

You can customize the following options: VPN server's DNS name, protocol (TCP/UDP) and port, DNS server for VPN clients and name of the first client.

For servers with an external firewall, open your selected TCP or UDP port for the VPN.

<details>
<summary>
Click here if you are unable to download.
</summary>

You may also use `curl` to download:

```bash
curl -fL -o openvpn.sh https://get.vpnsetup.net/ovpn
```

Then follow the instructions above to install.

Alternative setup URLs:

```bash
https://github.com/hwdsl2/openvpn-install/raw/master/openvpn-install.sh
https://gitlab.com/hwdsl2/openvpn-install/-/raw/master/openvpn-install.sh
```

If you are unable to download, open [openvpn-install.sh](openvpn-install.sh), then click the `Raw` button on the right. Press `Ctrl/Cmd+A` to select all, `Ctrl/Cmd+C` to copy, then paste into your favorite editor.
</details>
<details>
<summary>
Advanced: Auto install using custom options.
</summary>

Advanced users can auto install OpenVPN using custom options, by providing a Bash "here document" as input to the setup script. This method can also be used to provide input to manage users after install.

First, install OpenVPN interactively using custom options, and write down all your inputs to the script.

```bash
sudo bash openvpn.sh
```

If you need to remove OpenVPN, run the script again and select the appropriate option.

Next, create the custom install command using your inputs. Example:

```bash
sudo bash openvpn.sh <<ANSWERS
n
1
1194
2
client
y
ANSWERS
```

**Note:** The install options may change in future versions of the script.
</details>

\* A cloud server, virtual private server (VPS) or dedicated server.

## Next steps

After setup, you can run the script again to manage users or uninstall OpenVPN.

Get your computer or device to use the VPN. Please refer to:

**[Configure OpenVPN Clients](docs/clients.md)**

**Read [:book: VPN book](https://ko-fi.com/post/Support-this-project-and-get-access-to-supporter-o-O5O7FVF8J) to access [extra content](https://ko-fi.com/post/Support-this-project-and-get-access-to-supporter-o-O5O7FVF8J).**

Enjoy your very own VPN! :sparkles::tada::rocket::sparkles:

## Credits

This script is based on the great work of [Nyr and contributors](https://github.com/Nyr/openvpn-install), with enhancements and changes for compatibility with the [Setup IPsec VPN](https://github.com/hwdsl2/setup-ipsec-vpn) project.

<details>
<summary>
List of enhancements over Nyr/openvpn-install.
</summary>

- Improved compatibility with Setup IPsec VPN
- Improved script reliability, user input and output
- Supports auto install using default options
- Supports using a DNS name as server address
- Added support for openSUSE Linux
- Added support for Amazon Linux 2
- Supports exporting configuration for an existing VPN client
- Supports listing existing VPN clients
- Supports custom DNS server(s) for VPN clients
- Optimizes `sysctl` settings for improved VPN performance
- Improved creation of client config files when using `sudo`

...and more!
</details>

## License

MIT
