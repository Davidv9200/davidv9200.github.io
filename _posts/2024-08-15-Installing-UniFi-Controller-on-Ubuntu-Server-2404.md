---
layout: post
title: "Installing UniFi Controller on Ubuntu Server 24.04"
date: 2024-08-15 11:00:00 -0000
categories: software networking
tags: tutorial config
image:
 path: /assets/img/headers/Unifi-Controller-Install-Ubuntu-server.webp
---

## Prerequisites

    1. **Ubuntu Server 24.04** installed and running.
    2. **Root** or **Sudo** privileges.

## Step 1: Update System Packages
First, update your system packages to ensure you have the latest updates:

   ```bash
    sudo apt update
    sudo apt upgrade -y
    ```

## Step 2: Install Required Dependencies

    Install the required dependencies:

   ```bash
    sudo apt install -y wget gnupg
    ```

    ## Step 3: Add the UniFi Repository

    1. **Import the GPG key:**

       ```bash
        wget -qO - https://dl.ui.com/unifi/unifi-repo.gpg | sudo apt-key add -
        ```

    2. **Add the UniFi repository:**

       ```bash
        echo "deb http://www.ui.com/download/unifi/debian stable ubiquiti" | sudo tee /etc/apt/sources.list.d/unifi.list
        ```

    ## Step 4: Install UniFi Controller

    1. **Update package lists:**

       ```bash
        sudo apt update
        ```

    2. **Install the UniFi Controller:**

       ```bash
        sudo apt install -y unifi
        ```

    ## Step 5: Start and Enable the UniFi Service

    Ensure the UniFi Controller service is started and enabled to start on boot:

   ```bash
    sudo systemctl start unifi
    sudo systemctl enable unifi
    ```

    ## Step 6: Access the UniFi Controller

    Open your web browser and navigate to:

    ```
    https://<your_server_ip>:8443
    ```

    Replace `<your_server_ip>` with your actual server IP address.

    ## Step 7: Configure UniFi Controller

    Follow the on-screen instructions to complete the initial setup and configuration of the UniFi Controller.

    ## Optional: Configure Firewall

    If you are using UFW (Uncomplicated Firewall), you may need to allow port 8443:

   ```bash
    sudo ufw allow 8443/tcp
    ```
## Troubleshooting

    - Check the status of the UniFi Controller service if you encounter issues:

       ```bash
        sudo systemctl status unifi
        ```

    - View logs for debugging:

       ```bash
        sudo journalctl -u unifi
        ```

## Conclusion
You should now have the UniFi Controller up and running on your Ubuntu Server 24.04. Enjoy managing your UniFi network devices!
