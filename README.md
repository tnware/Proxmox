![Proxmox VE Helper-Scripts Logo](./misc/images/logo-81x112.png)

# Proxmox VE Helper-Scripts

[Website](#) | [Contribute](./.github/CONTRIBUTING.md) | [Guides](./USER_SUBMITTED_GUIDES.md) | [Changelog](./CHANGELOG.md) | [Support](#)

---

These scripts empower users to effortlessly create Linux containers or virtual machines, offering options for both straightforward and intricate configurations. The simplified setup sticks to default settings, while the detailed setup allows for customization.

A dialog box presents choices to the user. Following selection, the script compiles and verifies input to finalize the configuration for the container or virtual machine.

- All LXC instances created using this repository come pre-installed with Midnight Commander, which is a command-line tool (`mc`) that offers a user-friendly file and directory management interface for the terminal environment.

- 🚨 **The scripts in the repository will no longer provide support for Proxmox VE 7 starting from July 2024 (scripts will not execute on PVE7). Subsequent <a href='https://forum.proxmox.com/threads/proxmox-ve-support-lifecycle.35755/' target='_blank' rel='noopener noreferrer'>Proxmox VE - Support Lifecycle</a>**

> Exercise caution and meticulously assess scripts and automation tasks from external sources. [Discover more](./CODE-AUDIT.md)

_Proxmox® is a registered trademark of Proxmox Server Solutions GmbH._

## License

The primary license for this project is the GNU Affero General Public License v3.0 (AGPL-3.0). It applies to all parts of the project that are not explicitly identified as being under a different license.

### AGPL-3.0 Licensed Components

Unless stated otherwise, all components of this project, including additional Proxmox VE Helper-Scripts not found in the original repository, are licensed under the AGPL-3.0. You can find the full AGPL-3.0 license text in the [AGPL-LICENSE](AGPL-LICENSE.md) file in this repository.

### Components Licensed Under the MIT License

Certain libraries or modules within this project are under the MIT License. These components are either used as-is or have been modified to fit the needs of this project. These are identified below.

1. [tteck/Proxmox](https://github.com/tteck/Proxmox): under the MIT License. Refer to the respective `LICENSE` or `README` file for this project for more information.

The MIT License is permissive and allows for these components to be integrated into AGPL-licensed projects. The original copyright notice and the license text must be included with any substantial portions of the MIT-licensed software.

`SPDX-License-Identifier: AGPL-3.0-only AND MIT`
