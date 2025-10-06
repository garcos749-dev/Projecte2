#Solució 


# 🔋 Estudi i tria d’un SAI per a TecnoGestió S.L.

## 1️⃣ Introducció

L’empresa **TecnoGestió S.L.**, dedicada a la **gestió documental i assessorament informàtic**, té un petit despatx amb:

- 4 ordinadors de sobretaula  
- Una impressora-fotocopiadora multifunció (similar a les de l’escola)  
- Un router d’accés a Internet  

Davant les constants incidències amb el **subministrament elèctric** a la zona, la direcció ha decidit **adquirir un SAI** per garantir la continuïtat del servei i protegir els equips.

---

## 2️⃣ Inventari d’equips

| Equip | Quantitat | Consum (W) per unitat | Consum total (W) |
|--------|------------|------------------------|------------------|
| Ordinadors de sobretaula | 4 | 90 | 360 |
| Monitors 23,8" | 4 | 23 | 92 |
| Router | 1 | 10 | 10 |
| **Total** | | | **462 W** |

🖨️ **Nota:** No es connecta la **impressora multifunció làser** al SAI, ja que té **consums punta molt elevats**.

---

## 3️⃣ Càlculs de potència

### Pas 1: Potència eficaç (W)
\[
P = 4 \times 90 + 4 \times 23 + 10 = 462\text{ W}
\]

### Pas 2: Potència aparent (VA)
S’aplica el factor de potència (**FP = 0,7**):
\[
S = \frac{462}{0,7} = 660\text{ VA}
\]

### Pas 3: Aplicació del marge de seguretat (+20%)
Es divideix entre 0,8:
\[
SAI_{necessari} = \frac{660}{0,8} = 825\text{ VA}
\]

✅ **Resultat:** Es necessita un SAI **d’almenys 825 VA**.  
Comercialment, això equival a un **SAI de 1000 VA o superior**.  
Es recomana un model de **1500 VA** per tenir més marge i autonomia.

---

## 4️⃣ Autonomia requerida

🎯 **Objectiu:** ≥ 10 minuts

Un SAI de **1500 VA** amb una càrrega de **500 W** sol oferir **entre 12 i 20 minuts d’autonomia**, suficient per **guardar la feina i apagar correctament els equips**.

---

## 5️⃣ Models comparats

| Model | Potència (VA/W) | Autonomia (50% càrrega) | Pros | Contres |
|--------|------------------|--------------------------|------|----------|
| **APC Smart-UPS C SMC1500I** | 1500 VA / 900 W | ~24 min | Molt fiable, bona autonomia | Potència útil més baixa |
| **Eaton 5SC1500i** | 1500 VA / 1050 W | ~13 min | Més W útils, bona marca | Autonomia inferior |
| **CyberPower PR1500ELCDRT2U** | 1500 VA / 1350 W | ~11 min | Molta potència útil | Format rack, autonomia justa |

---

## 6️⃣ Selecció final

Es proposa el **model APC Smart-UPS C SMC1500I** per les següents raons:

- Supera el càlcul mínim requerit (825 VA)  
- Ofereix **autonomia superior als 10 minuts** fins i tot amb càrrega plena  
- Té **format torre**, ideal per a un despatx petit  

💡 **Alternativa:**  
L’**Eaton 5SC1500i** és una bona opció si es preveu **creixement d’equips** i es **prioritza la potència** per sobre de l’autonomia.

---

## 7️⃣ Conclusions

- **Càrrega estimada:** 462 W → **825 VA amb marge**  
- **Model recomanat:** APC Smart-UPS C SMC1500I (1500 VA / 900 W)  
- **Beneficis:**  
  - Continuïtat del servei  
  - Protecció dels equips  
  - Temps suficient per tancar correctament els sistemes

---

📚 **Material de suport:** Apunts *RA1AA3 – El SAI*

![Foto activitat](img/imatge01.png)

[Tornar a enunciat](README.md)
