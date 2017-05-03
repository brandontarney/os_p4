# os_p4
Operating Systems 605.412 Project 4: Modify Minix FS
- Modify Ctime in Minix File System to reflect when the time a file is created

## Assignment Details:
- Assignment: **JHU Operating Systems 605.412 Project 4**
- Author: **Brandon Tarney**
- Date: **4/30/17**
- Contact: **brandon.tarney@gmail.com**
- Login: **root**
- Passwd: **os412**


## About the code
1. **IDE:** VIM ftw
1. **Important code:** 
 1. Proj dir: /root/os/os_p3/
 1. driver_homework/homework/homework.c
1. **How-to run:**
 1. Use executables in driver_test/
 1. driver_test/run_all   (runs a basic set of functionality)
1. **Input:** N/A
1. **Output:** printf statements
1. **Unit tests:** N/A
1. Program was created in personal VirtualBox Minix v3.3 VM, see [the github repo for a copy](https://github.com/1amBulletproof/OS_P4)



Notes from Office Hours
- There are 3 times maintained in inodes in MINIX:
    - Ctime last change of the inode information (example: permissions) 
        - Think about where you would find the time when the file was created...
        - CLUE: upon creation all 3 file times are set....
        - CLUE: simply prevent any other modification of CTIME after this...
    - Atime (access time) - open file and read it
    - MTime (modify time) - last time of file modification

- TODO: look in MFS/VFS & look where information in inodes is being manipulated

