# Setting up Linux for WSL

Date: March 10, 2024

My machine: Windows 11 (Home), AMD motherboard

1. Download Ubuntu Desktop
2. Enable virtualization from BIOS 
    1. [AMD](https://ourcodeworld.com/articles/read/1283/how-to-enable-amd-virtualization-on-the-aorus-x570-motherboard)
3. Hyper-v for windows home
    
    [https://www.xda-developers.com/how-to-install-hyper-v-windows-11-home/](https://www.xda-developers.com/how-to-install-hyper-v-windows-11-home/)
    
    - Create hv.bat file in `windows/system32` file with notepad running as admin
        
        [hv.txt](Setting%20up%20Linux%20for%20WSL%20a7c3b0a70750461e97703a0fa20ef216/hv.txt)
        
        - important to save hv.txt and then save as hv.bat
        - run as administrator
4. For all linux projects: Use the Linux file system root directory: `\\wsl$\<DistroName>\home\<UserName>\Project`
