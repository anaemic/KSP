# KSP
Kerbal Space Program PKGBUILDs for Arch Linux

Based on work by felixonmars @ https://github.com/felixonmars/aur3-mirror/tree/master/kerbalspaceprogram
updated to v1.2.2 by anaemic

CURRENTLY NOT WORKING WELL, IN TESTING

Install Instructions:

1) git clone https://github.com/anaemic/KSP
2) cd KSP
3) Download the kerbal space program installer .zip for linux from the official website
4) Move it into your newly created KSP folder
5) makepkg
6) sudo pacman -U kerbalspaceprogram-1.2.2-1-x86_64.pkg.tar 

extras:
you may or may not need to also install the ttf-ms-fonts package from the AUR https://aur.archlinux.org/packages/ttf-ms-fonts/
