# Work Environment Setup Using PiKVM 🛜

📅 Last Updated: 08/18/2025 

## PiKVM Setup

* **PiKVM Configuration** using **supporter's personal laptop** through **AnyDesk**

    📖 <a href="PiKVM_Setup_Guide.pdf" download>*PiKVM_Setup_Guide.pdf*</a>

    * Connect to KVM using SSH
        ```
        ssh root@[IP Address]
        ```
    * Get root permission
        ```
        su root
        ```
    * Update KVM
        ```
        pikvm-update
        ```
        ⚠️ *There might be an issue with PiKVM update, you can be helped from* https://docs.pikvm.org/_update_os/

    * Editing configuration for KVM
        ```
        rw #enable read-write mode
        ```
        ```
        kvmd-edidconf --import-preset v4plus.no-1920x1200 --set-mfc-id ACR --set-product-id 1381 --set-serial 23150474 --set-monitor-name R246W --set-monitor-serial T8NEE0038522 --apply
        ```

    * Override PiKVM Config
        ```
        sudo nano /etc/kvmd/override.yaml
        ```

        Add configuration context to *override.yaml* file.
        ```
        kvmd:
            msd:
                type: disabled
        otg:
            manufacturer: Logitech
            product: USB Receiver
            vendor_id: 0x046D
            product_id: 0xC52B
            serial: 
        ```
    
    * Install tailscale vpn
        ```
        pacman -S tailscale-pikvm
        systemctl enable --now tailscaled
        tailscale up
        ```


## Terminal@Me

* VM Workstation Setup ( Windows OS, Tailscale-VPN )
* Sign in PiKVM & Company Laptop through IP Address from Tailscale