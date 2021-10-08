#####################################################################################################################
################################################ Archlinux Install ##################################################
################################################# MBR-BIOS-Install Written By Aref R Ahmed ##########################
################################################## wanak3000@gmail.com Date:10/7/2020 ###############################
# Steps By Step Archlinux MBR-BIOS-Install:-
# Test the internet connection use ethernet cable connection the recommended method:-
#######################################################################################
# ping google.com
# timedatectl set-ntp true
# timedate status
# list the name of hard drive:-
##################################
# fdisk -l 
# Use cfdisk or fdisk to make sda1(ext4-boot-500M), ada2(swap-same size of pc ram) sda3(ext4-root):-
#####################################################################################################
# Format the sda1 and sda3 partitions to ext4 filesystem NO NEED to format sda2(swap):-
#########################################################################################
# Making ext4 file system:- 
########################
# mkfs.etx4 /dev/sda1
# mkfs.ext4 /dev/ada3
# Make swap partition in sda2:-
###############################
# mkswap /dev/sda2
# swapon /dev/sda2
# Mounting the partition sda3(root)first then sda1(boot)second:-
###############################################################
# mount /dev/sda3 /mnt
# Making boot directory in the mnt directory:-
#############################################
# mkdir /mnt/boot
# Mounting sda1(boot)to mnt directory:-
#########################################
# mount /dev/sda1 /mnt/boot
# Editing Mirrorlist:-
#######################
# nano /etc/pacman.d/mirrorlist 
# Installing the linux-kernel:-
###############################
# pacstrap /mnt base linux linux-firmware
# genfstab -U /mnt >> /mnt/etc/fstab
# arch-chroot /mnt
# ln -sf /usr/share/zoneinfo/America/New_York /etc/localtime
# hwclock --systohc
# Editing locale.gen file:-
##########################
# nano /etc/locale.gen
# Do uncomment the line en_us.UTF-8 by deleteing the # in the begining of this line only:-
#############################################################################################
# Generate locale.gen file:-
###########################
# locale-gen
#Install nano,vim and sudo:-
############################
# pacman -S nano vim sudo
# Setup US language-Keyboard:-
############################
# nano/etc/locale.conf 
# Type the following:-
#######################
# LANG=en_us.UTF-
# Press Cntrol+o to save then Press Cntro+x to exit:-
# Creating hostname file:-
#########################
# nano /etc/hostname   
# Type Any host name You Like in the hostname file,Example I typed arefvbox:- 
# Press Cntrol+o to save then Press Cntro+x to exit:-
#######################################################
# Creating hosts file:-
#####################
# nano /etc/hosts     
# Type exactly the following in the hosts file:-
#################################################
# 127.0.0.1  localhost
# ::1        localhost
# 127.0.1.1 arefvbox.localdomain arefvbox
# Press Cntrol+o to save then Press Cntro+x to exit:-
#######################################################
# Create root password:-
#########################
# passwd
# Type the password twice to confirm:-
######################################
# Adding standard user example I used is aref:- 
###############################################
# useradd -m aref  
# We adding the user aref to the following groups by typing the following command:-
#######################################################################################
# usermod -aG wheel,audio,video,lp,optical,storage aref
# Enable sudo for the standard user-aref:-
############################################
# Using nano instead visudo by typing the following command:-
##############################################################
# EDITOR=nano visudo  
# uncomment the line # % wheel=ALL(All) ALL by deleting # in the begining of this line only then do the following:-
###################################################################################################################
# Press Cntrol+o to save then Press Cntro+x to exit:-
#####################################################
# Install grub and configure grub-install(BIOS-MBR):-
#####################################################
# pacman -S grub
# grub-install /dev/sda
# grub-mkconfig -o /boot/grub/grub.cfg
# installing network:-
######################
# pacman -S networkmanager wpa_supplicant wireless_tools iw netctl
# pacman -S dialog
# systemctl NetworkManager
# exit
# umount -l /mnt
# reboot
# After log in successfully as standard user:-
# Install xorg:-
#################
# sudo pacman -S xorg
# To Know Your Display Card Manufacture type the following command:-
#####################################################################
# lspci   
# Install Intel-Display-Driver:-
##################################
# sudo pacman -S xf86-video-intel
# Install AMD-Display-Driver:-
#################################
# sudo pacman -S xf86-video-amdgpu
# Install Nvidia-Display-Driver:-
####################################
# sudo pacman -S xf86-video-nouveau
# Install ATI-display-driver:-
################################
# sudo pacman xf86-video-ati
# Install Unveral-Display-Diver(vesa):-
##########################################
# sudo pacman -S xf86-video-vesa
# Installing the lxde-desktop and the lxdm-disply-manager:-
############################################################
# sudo pacman -S lxde 
# Enable the lxdm-display-manager at startup-vey-important-step:-
################################################################
# sudo systemctl enable lxdm
# Restart the system:-
#######################
# reboot

##################### Thanks Aref R Ahmed E-Mail wanak3000@gmail.com ### Facebook:-Aref Ahmed ####################
##################### Written By Aref R Ahmed Date 10/7/2020,Wanak-Corp ##########################################
##################### Note any line in this Archwiki has NO hash(####),line under it then it is command ##########
##################### Any command in this Archwiki MUST Execuited in the terminal please follow the directions ###
##################### Must be run in the bash terminal as root user ##############################################   
##################################################################################################################
