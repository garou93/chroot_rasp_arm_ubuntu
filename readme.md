################Outils/notions rencontrées
virtualisation/emulation
RISC/CISC
cross-compilation
architecture x86 vs ARM
GNU/Linux & chaine de compilation GCC

assembleur
uClibc
BusyBox
Buildroot
chroot
KVM et de QEMU

################OBJECTIFS: creer un GNU/Linux embarqué(microlinux ..) from scratch(puis), en s'aidant d'un kit de génération
- utiliser une chaine de compilation raspberry
- creer un env chroot et installer à l'intérieur une chaine de compilation
- emuler une image de Raspbian (emulation native, avec kernel modifié)
- librairies et outils nécessaires
################steps

Chroot un ARM système est un moyen simple d'avoir un accès à un système sans avoir de matériel spécifique, donc nous permettre de construire des paquets pour les appareils ARM. 
Cela peut être une alternative au "cross-compiling" où nous sommes limités à mettre en relation (linking) uniquement avec les librairies du compilateur.
 * copier le binaire `qemu-arm-static` dans le chroot
 * enregistrer `qemu-arm-static` comme ARM interpréteur dans le kernel
 * monter, bind tous les paquest nécessaires
 * Dans le chroot, un petit test avec 'uname'
 
 On peut mm passer au debogage GDB:
 # In a terminal
$ qemu-arm-static -g 10101 ./project
$ sudo apt-get install gdb-multiarch

--> configuration clavier raspi
--> configuration shh
--> recompilation noyau
 
* compilation avec buildroot: configuration pour raspi

==> on teste notre image avec QEMU

Et, voila voila: On  généré une image légère de GNU/LInux hébergeant nos services, encore un petit jeu de configuration réseau:wifi par expl (maintenant on arrive à notre vrai objetif, piouf!)

 (projet en evolution/construction)
 Done!

