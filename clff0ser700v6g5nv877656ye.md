---
title: "How to Triple Boot (Windows & Ubuntu & Kali) !!"
datePublished: Sun Mar 19 2023 06:31:39 GMT+0000 (Coordinated Universal Time)
cuid: clff0ser700v6g5nv877656ye
slug: how-to-triple-boot-windows-ubuntu-kali
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1677768660772/2750b14a-8ac2-46da-bafe-d39a6615da3e.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1677768684681/99129637-454c-4a4e-ae74-ab68e2b3dadd.png
tags: linux, kali-linux, wemakedevs, mayankaggarwal, mayank

---

Triple booting Windows, Ubuntu, and Kali Linux on your computer can be a great way to take advantage of the strengths of each operating system. Windows is widely used for its ease of use and compatibility with many applications, while Ubuntu is popular among developers and those who value open-source software. Kali Linux is a popular penetration testing and ethical hacking distribution that is used by security professionals. In this blog, we will guide you through the steps to set up a triple boot system with Windows, Ubuntu, and Kali Linux.

Before you begin, make sure to back up any important data on your computer, as the installation process involves partitioning your hard drive, which can result in data loss if not done correctly.

Make sure your computer supports UEFI and that you have a UEFI bootable installation media for Windows. You can download a UEFI-compatible Windows ISO file from the Microsoft website and create a bootable USB drive using a tool like Rufus.

### **Step 1: Boot from the UEFI installation media**

Insert the UEFI bootable USB drive into your computer and restart it. Press the key to enter the boot menu (usually F12 or Del) and select the USB drive as the boot device.

### **Step 2: Choose the UEFI installation option**

When the Windows Setup screen appears, select the language, time and currency format, and keyboard or input method you want to use. Click Next and then click Install Now. On the next screen, select the option to install Windows in UEFI mode.

### **Step 3: Create a partition for Windows**

Follow the prompts to accept the license terms and choose the type of installation you want (Custom or Upgrade). If you choose Custom, you will be prompted to select the partition where you want to install Windows. Click on the unallocated space on your hard drive and click New to create a partition for Windows. Make sure to select the partition type as GPT (GUID Partition Table). Make sure to have min 30 GB of free space because we need to install Ubuntu and kali on our system.

### **Step 4: Complete the installation**

Follow the remaining prompts to set up your username, password, and other settings. Once the installation is complete, restart your computer. You should now be able to boot into Windows in UEFI mode.

Now you need to check that your PC is booted in UEFI Mode successfully.

So, Press windows+r and type msinfo32, and press enter.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677763243314/109f08da-c11b-4a0a-91de-cc34ee19e214.png?auto=compress,format&format=webp align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677763381537/253a1c00-eee6-4283-9e1e-60aaa22d423f.png?auto=compress,format&format=webp align="left")

---

### **Installing Ubuntu!!**

### **Step 1: Prepare a bootable USB drive**

The first step is to create a bootable USB drive containing the Ubuntu installation files. You can download the Ubuntu ISO file from the official website and use a tool like Rufus or Etcher to create a bootable USB drive.

To Download Ubuntu [**visit here**](https://ubuntu.com/download/desktop).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677763563971/f2e216ed-c180-43e4-8545-1b3589ea52e4.png?auto=compress,format&format=webp align="left")

To Download Rufus [**visit here**](https://rufus.ie/en/).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677763607487/a5250bc6-1729-4106-af2a-1efccf7a8655.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677763938464/bd0b83d0-6cf1-48bf-8af4-336b0cce6cc7.png?auto=compress,format&format=webp align="center")

### **Step 2: Create a partition for Ubuntu**

The next step is to create a partition on your hard drive for Ubuntu. To do this, open the Disk Management tool in Windows by pressing the Windows key + X and selecting Disk Management from the menu. Right-click on the partition you want to shrink and select Shrink Volume. Specify the amount of space you want to allocate to Ubuntu and click Shrink. We need an unallocated partitioning of more than 10 GB for installing Ubuntu. Create a temporary partition for kali of a minimum of 10 GB in size and allocate it for now.

### **Step 3: Boot from the USB drive**

Insert the USB drive into your computer and restart it. Press the key to enter the boot menu (usually F12 or Del) and select the USB drive as the boot device.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677763765633/ae476f09-e609-43f4-afe2-ca9114e320ad.png?auto=compress,format&format=webp align="center")

### **Step 4: Install Ubuntu**

The Ubuntu installer will now start. Select your language and click Install Ubuntu. Follow the prompts to select your time zone, keyboard layout, and network settings. When you reach the Installation type screen, select the option to Install Ubuntu alongside Windows. Choose install Ubuntu alongside bootloader and click Install Now.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677763786460/7d915228-3198-44d7-8ab7-8eb01a20f133.png?auto=compress,format&format=webp align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677763816768/789cbc3c-806e-4a25-9cac-2dec382b41db.png?auto=compress,format&format=webp align="center")

Make sure to checkmark install third-party software.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677764102890/a41b4026-976d-4e55-95e9-45834a99d9be.png?auto=compress,format&format=webp align="center")

### **Step 5: Complete the installation**

Follow the remaining prompts to set up your username, password, and other settings. Once the installation is complete, restart your computer. You should now see a GRUB menu giving you the option to boot into either Ubuntu or Windows.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677767758754/00bd3071-a274-4c7e-82a9-9c684daab848.png align="center")

Congratulations, you have successfully set up a dual boot system with Windows and Ubuntu!

### Installing Kali!

### **Step 1: Prepare a bootable USB drive**

The first step is to create a bootable USB drive containing the Kali installation files. You can download the Kali ISO file from the official website and use a tool like Rufus or Etcher to create a bootable USB drive. Make Sure to disable your antivirus before creating an installation media.

To Download Kali [**visit here**](https://www.kali.org/get-kali/#kali-installer-images).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677766609483/6a58c6ee-c68d-470a-b753-5e948aabc8d4.png align="center")

To Download Rufus [**visit here**](https://rufus.ie/en/).

![Making a Kali Bootable USB Drive on Windows | Kali Linux Documentation](https://www.kali.org/docs/usb/live-usb-install-with-windows/Rufus1.png align="center")

### **Step 2: Create a partition for Kali**

The next step is to create a partition on your hard drive for Kali. To do this, open the Disk Management tool in Windows by pressing the Windows key + X and selecting Disk Management from the menu. Right-click on the partition you allocated temporarily for Kali and just unallocate it.

### **Step 3: Boot from the USB drive**

Insert the Kali Linux bootable USB drive into your computer and restart it. Press the key to enter the boot menu (usually F12 or Del) and select the USB drive as the boot device.

### **Step 4: Install Kali**

The Kali Linux installer will now start. Follow the prompts to select your language, time zone, keyboard layout, and network settings. Choose the partition you created earlier for Kali Linux and click Continue. Follow the prompts to complete the installation.

Follow Steps Given Below:

1. To start your installation, boot with your chosen installation medium. You should be greeted with the Kali Linux Boot screen. Choose either **Graphical install** or **Install** (Text-Mode). In this example, we chose the Graphical install.
    
2. ![](https://www.kali.org/docs/installation/hard-disk-install/boot-installer.png align="center")
    
    Enter the Host Name as Kali or any hostname you want to enter.
    
3. ![](https://www.kali.org/docs/installation/hard-disk-install/setup-hostname-1.png align="left")
    
    You may optionally provide a default domain name for this system to use (values may be pulled in from DHCP or if there is an existing operating system pre-existing).
    
4. ![](https://www.kali.org/docs/installation/hard-disk-install/setup-hostname-2.png align="left")
    
    Next, create the user account for the system (Full name, username, and a strong password).
    
5. ![](https://www.kali.org/docs/installation/hard-disk-install/setup-user-1.png align="left")
    
    ![](https://www.kali.org/docs/installation/hard-disk-install/setup-user-2.png align="left")
    
    ![](https://www.kali.org/docs/installation/hard-disk-install/setup-user-3.png align="left")
    
    Just proceed by pressing next to enter the needed information. now select Use largest continuous partition in order to use our space that was unallocated.
    
6. ![How to Install Kali Linux Alongside With Windows - Eldernode Blog](https://blog.eldernode.com/wp-content/uploads/2022/04/setup-partition-Guided-use-the-largest-continuous-free-space-1.png align="left")
    
    ![](https://www.kali.org/docs/installation/hard-disk-install/setup-partition-3.png align="left")
    
    You just need to select the same options As selected in the images.
    
    ![](https://www.kali.org/docs/installation/hard-disk-install/setup-partition-5.png align="left")
    
    ![](https://www.kali.org/docs/installation/hard-disk-install/setup-default-metapackages.png align="left")
    

### **Step 5: Complete the installation**

Once the installation is complete, restart your computer. You should now see a GRUB menu giving you the option to boot into Windows, Ubuntu, or Kali Linux.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1677767965295/c813def2-717a-493d-bf2b-2f1b71ec2d1b.png align="center")

Congratulations, you have successfully set up a triple boot system with Windows, Ubuntu, and Kali Linux

### **Conclusion**

In conclusion, triple booting Windows, Ubuntu, and Kali Linux can be a great way to get the best of all three operating systems. By following these simple steps, you can easily install Ubuntu and Kali Linux alongside Windows and enjoy the benefits of all three. Just remember to back up your data before you begin and be careful when partitioning your hard drive.

> ***Make Sure to Like and Follow my Bog.***
> 
> ***Get to Know about me better*** [***here***](https://mayankaggarwal.live/)***.***