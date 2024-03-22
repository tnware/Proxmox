<div align="center">
  <a href="#">
    <img src="https://raw.githubusercontent.com/tnware/Proxmox/main/misc/images/logo.png" height="100px" />
  </a>
</div>
<h2 align="center">Contributing to Proxmox VE Helper Scripts</h2>

We are thrilled to have you consider contributing to Proxmox VE Helper Scripts. Our project thrives on the contributions of our community, and we’re excited to include your improvements.

Here’s what you need to know about contributing to our repository:


- **Pull Requests Welcome**: We're open to all contributions. When you submit a pull request to the [**main** branch](https://github.com/tnware/Proxmox/tree/main), know that we appreciate your effort and interest in improving this project. We aim to review your contributions thoughtfully and provide feedback. While we strive to maintain a high standard, we're more focused on the value of your contribution, rather than looking for reasons to turn you away.


- **Constructive Feedback**: We believe in building each other up. If there are any adjustments needed or if a pull request doesn’t get accepted, it’s all part of the process. We encourage you to view feedback as a learning opportunity. Our goal is to work together to make the project better, and we value your input and effort.


- **Collaboration and Respect**: Your ideas and contributions make a difference. Even if there's a decision you might not agree with, we ask for your understanding and cooperation. Every decision is made with the project’s best interests in mind. Let’s maintain a positive and respectful environment, where we all work together towards enhancing Proxmox VE Helper Scripts.


# How to Contribute

Here are the steps and guidelines to follow when adding new scripts or contributing in other ways to our project.

## Script Addition Guidelines

When contributing a new script, please follow these directions:

### Where to Place Your Script

- **Container (ct) Scripts**: Place your container script in the `ct/` directory.  For an "Example" application, name your script `ct/example.sh`.
- **Install Scripts**: Your installation script belongs in the `install/` directory, following the `script-install.sh` naming pattern. For an "Example" application, name your script `install/example-install.sh`.

### Naming Your Script

- Ensure the application name within your script precisely matches the script's filename. If the name is not consistent across all referenced areas, the app will fail to install. 

## Integration with the Platform

Adding your script doesn't require any alterations to the core files:

- `build.func`: Integrates user settings with collected information and works seamlessly with new scripts.
- `create_lxc.sh`: Constructs the LXC container and needs no modifications for new install scripts.
- `install.func`: Installs the application and is designed to cooperate with your script, provided naming conventions are met.

## Showing documentation on the main page

Adding your contribution to the main page for the project should be straightforward and easy to accomplish.

A new frontend UI for this purpose will be coming down the pipeline.


## Steps for Contribution

1. **Fork the Repository**: Begin by forking the project to your GitHub account.
2. **Introduce Your Script**: Follow the outlined guidelines to add your script to the relevant locations.
3. **Verify Naming Accuracy**: Confirm the script's filename aligns with the application name within it.
4. **Test Your Contribution**: Ensure your script functions correctly within our project environment.
5. **Propose a Pull Request**: Submit a PR from your fork to the main project, with a comprehensive description of your contribution.

## Additional Considerations

- Familiarize yourself with the project's scripts for an understanding of the formatting and coding standards.
- For queries or clarifications regarding contributions, don't hesitate to contact the project maintainers.

Your contributions are highly valued, and we're here to assist throughout your contribution journey. Thank you for your involvement in enhancing this remarkable project!
