# T03: Seguretat Lògica — recuperant accés a sistemes

## Primera Part

### 1️⃣ Inserció del disc

Primer de tot, **inserim el disc dur** en una màquina virtual.

---

### 2️⃣ Accés al menú GRUB

Després, **pressionem `Shift` + qualsevol tecla** i seleccionem **l’opció marcada en gris**.

---

### 3️⃣ Selecció de mode

Ara **seleccionarem la segona opció** del menú.

---

### 4️⃣ Accés root

Escollim l’opció **root** per obtenir permisos d’administrador.

---

### 5️⃣ Execució de comandes

Després d’escollir l’opció root, **introduïm aquestes tres comandes en aquest ordre:**

```bash
# Comanda 1
# Comanda 2
# Comanda 3
```

*(El document original no mostra les comandes exactes.)*

---

### 6️⃣ Verificació

Com podem observar, **ja estem dins de la màquina.**

> 🔐 Totes les contrasenyes són: `javi123`

---

## Segona Part

### 1️⃣ Configuració del GRUB

Primer de tot, escrivim aquesta comanda:

```bash
# Comanda 1 (no especificada al document)
```

Després aquesta:

```bash
# Comanda 2 (no especificada al document)
```

I tot seguit, **obrim l’arxiu de configuració del GRUB**:

```bash
sudo nano /etc/grub.d/40_custom
```

---

### 2️⃣ Edició de configuració

Ens hauria de quedar **de la següent forma**:

```bash
set superusers="javi"
password_pbkdf2 javi grub.pbkdf2.sha512.10000.XXXXXXXXXXXXXXX
```

*(Substituir el hash pel valor generat amb `grub-mkpasswd-pbkdf2`.)*

---

### 3️⃣ Aplicació de canvis

Finalment, **configurem el GRUB per aplicar els canvis**:

```bash
sudo update-grub
```

---

### 4️⃣ Verificació final

Com podem observar, **abans d’entrar ens demana la contrasenya i l’usuari.**

---

## Resum del procediment

1. Inserir disc a la màquina virtual.
2. Accedir al GRUB i seleccionar mode root.
3. Canviar contrasenya de l’usuari.
4. Editar configuració del GRUB per protegir l’accés.
5. Aplicar canvis i verificar protecció.

---

**Usuari i contrasenya configurats:**

```
Usuari: javi
Contrasenya: miquel123
```

---

> 📄 *Document basat en les captures i instruccions del fitxer PDF original: “T03_ Seguretat Lògica_ recuperant accés a sistemes.pdf”*

