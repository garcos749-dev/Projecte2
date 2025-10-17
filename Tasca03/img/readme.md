# T03: Seguretat Lògica — recuperant accés a sistemes

## Breu descripció

Després de la primera feina exitosa, us arriba un encàrrec urgent que obliga a que us hi poseu per donar-li solució.

Com a fase prèvia rebreu una formació sobre la seguretat lògica que us permetrà tenir els coneixements necessaris per afrontar la tasca.

Han arribat a la consultora un equip provinent d’un client que demana que els hi solucionem el problema. Tenen un portàtil amb **Zorin OS** (un Linux amb entorn gràfic) que usava habitualment un directiu. El problema és que ha oblidat la contrasenya i és necessari poder recuperar l’accés perquè hi ha documentació molt important que cal recuperar. Per evitar que una acció catastròfica pugui danyar l’equip original, ens han clonat el disc en un disc virtual perquè hi treballeu.

## Objectius

1. Crear una màquina virtual i connectar-hi el disc virtual clonat.
2. Accedir a la màquina virtual i trobar el nom d'usuari existent.
3. Assignar una contrasenya nova a l'usuari i verificar l'accés.
4. Investigar i aplicar mesures per fortificar l'accés al GRUB mitjançant contrasenya.
5. Documentar tot el procediment (amb imatges) i pujar-lo al repositori.

## Pas a pas (resum)

* **Preparació**: preparar la màquina virtual (VirtualBox / VMware / QEMU) i connectar el disc virtual rebut.
* **Accés al sistema**: arrencar la VM i entrar al mode de recuperació o editar GRUB per obtenir shell d'administrador.
* **Identificació d'usuari**: llistar els usuaris del sistema (`ls /home`, `getent passwd`, etc.).
* **Canvi de contrasenya**: usar `passwd <usuari>` o editar `/etc/shadow` si cal, i verificar l'accés iniciant sessió.
* **Fortificació del GRUB**: investigar i configurar una contrasenya al GRUB (per exemple `grub-mkpasswd-pbkdf2` i editar `/etc/grub.d/40_custom` o `/etc/grub.d/01_users` depenent de la versió), i regenerar la configuració de GRUB (`update-grub` o `grub2-mkconfig`).
* **Proves**: comprovar que l'arrencada normal funciona i que l'edició de línies de GRUB requereix autenticació.
* **Documentació**: capturar imatges de cada pas (pantalles de GRUB, terminal, comandes i sortides) i inserir-les al document final.

## Procediment individual (detallat)

1. **Vulneració de l’accés al GRUB**

   * Arranqueu la màquina virtual amb el disc clonat.
   * A la pantalla del GRUB, seleccioneu l'entrada i premeu `e` per editar la línia d'arrencada (si està permitit).
   * Modifiqueu la línia del kernel per afegir `init=/bin/bash` o `rw init=/bin/bash` per obtenir un shell amb permisos de root.
   * Arranqueu amb `Ctrl+X` o la combinació indicada i accediu al shell de root.

2. **Identificació de l’usuari del sistema**

   * Un cop al shell, podeu llistar usuaris amb:

     ```bash
     ls /home
     getent passwd | awk -F: '$3 >= 1000 {print $1}'
     ```
   * Apunteu el nom d'usuari identificat.

3. **Modificació de la contrasenya i verificació**

   * Canvieu la contrasenya de l'usuari:

     ```bash
     passwd <nom_usuari>
     ```
   * Reinicieu la màquina i proveu d'iniciar sessió amb la nova contrasenya.

4. **Investigació per fortificar l’accés al GRUB**

   * Objectiu: impedir que un atacant pugui editar entrades de GRUB o arrencar amb un init alternatiu sense autenticació.
   * Mètodes comuns:

     * Crear una contrasenya per a GRUB amb `grub-mkpasswd-pbkdf2`.
     * Afegir usuari(s) i hash al fitxer de configuració de GRUB (`/etc/grub.d/40_custom` o fitxers específics de la distribució) i afegir restriccions (per exemple `set superusers="admin"` i `password_pbkdf2 admin <hash>`).
     * Regenerar la configuració de GRUB amb `update-grub` o `grub2-mkconfig -o /boot/grub/grub.cfg`.
   * Altres mesures addicionals:

     * Habilitar xifrat de disc complet (LUKS) perquè el contingut del disc no sigui accessible sense la contrasenya d'arrencada.
     * Establir contrasenya de la BIOS/UEFI per evitar arrencar des d'un dispositiu extern.
     * Desactivar arrencada des d'USB/CD i protegir la configuració del firmware amb contrasenya.

## Configuració de la màquina virtual per fortificar GRUB (recomanacions)

* No compartir fitxers amb la màquina host ni habilitar carpetes compartides automàtiques.
* Configurar el firmware de la VM (UEFI/BIOS virtual) amb contrasenya si l'entorn ho permet.
* Assegurar que la imatge clonada estigui xifrada o que la política del client exigeixi xifrat a la màquina real.
* Documentar i provar el procediment de restauració en cas de pèrdua d'accés legítima (perquè la fortificació també pot bloquejar l'administrador si no es gestiona adequadament).

## Material de suport

* Disc virtual (subministrat pel client).
* Apunts RA1AA4 Seguretat Lògica.
* Article: *Recuperant Password en Linux* — WayToIT.
  [https://waytoit.wordpress.com/2013/06/06/recuperando-password-en-ubuntu/](https://waytoit.wordpress.com/2013/06/06/recuperando-password-en-ubuntu/)

## Evidència i imatges

> **Nota:** Cal incloure captures de pantalla a cada pas quan feu el document final. Exemple d'imatges a afegir:
>
> * Pantalla del GRUB abans i després de la protecció.
> * Sortida del terminal amb comandes `ls /home`, `getent passwd` i `passwd`.
> * Sortida de `grub-mkpasswd-pbkdf2` amb el hash generat (no compartir la contrasenya en text pla).

## Referències / Fonts

* WayToIT — Recuperando Password en Ubuntu. [https://waytoit.wordpress.com/2013/06/06/recuperando-password-en-ubuntu/](https://waytoit.wordpress.com/2013/06/06/recuperando-password-en-ubuntu/)
* Documentació oficial de GRUB (consultar la versió de GRUB instal·lada per a la sintaxi exacta).
* Guies de xifrat de disc (LUKS) i bones pràctiques de seguretat d'ARRANCADA segura (Secure Boot).

---

*Fi del document. Pugeu aquest fitxer amb les imatges al vostre repositori quan estigui complet.*

