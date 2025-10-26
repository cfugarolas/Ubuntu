<div align="center">

<img src="/img/logo_ubuntu.png" alt="Logo Ubuntu" width="100"/>

# 🐧 Ubuntu Tutorials  
### Actualitzar completament el sistema Ubuntu

Petit tutorial per aprendre a **actualitzar i mantenir el teu sistema Ubuntu al dia**, aplicant totes les actualitzacions disponibles de paquets i del sistema operatiu.

---

</div>

# 🔄 Actualitzar totes les actualitzacions del sistema a Ubuntu

Aquest tutorial mostra com **comprovar, descarregar i instal·lar totes les actualitzacions** disponibles a Ubuntu utilitzant la línia d’ordres.

És recomanable fer aquestes tasques regularment per mantenir el sistema segur, estable i amb les últimes millores.

---

## 🧩 Objectiu

- Comprovar la connexió a Internet.  
- Actualitzar la base de dades dels paquets.  
- Instal·lar les actualitzacions disponibles.  
- Netejar els paquets antics o innecessaris.

---

## 🔍 1. Comprovar l'estat actual del sistema i la connexió

Abans de fer cap canvi, assegurem-nos que tenim **connexió a Internet** i **privilegis d’administrador**.

Primer, comprovem la informació bàsica del sistema:

```bash
hostname
lsb_release -a
```
Ara, fem una petita prova de connexió amb ping:

```bash
ping -c 4 8.8.8.8
```

💡 Explicació:

ping comprova la connectivitat amb un servidor (en aquest cas, el DNS de Google).

L’opció -c 4 envia només 4 paquets.

Si reps respostes com 64 bytes from 8.8.8.8, la connexió a Internet funciona correctament.
Si no, revisa la teva configuració de xarxa abans de continuar.

## ⚙️ 2. Actualitzar la llista de paquets

Primer, refresquem la llista dels paquets disponibles des dels repositoris configurats:

```bash
sudo apt update
```

💡 Consell:
Aquest comandament no instal·la res, només actualitza la informació dels paquets disponibles.

## ⚙️ 3. Actualitzar tots els paquets instal·lats

Per instal·lar totes les actualitzacions disponibles, executa:

```bash
sudo apt upgrade -y
```

🔸 Explicació:

apt upgrade actualitza els paquets existents a la seva última versió.

L’opció -y accepta automàticament totes les confirmacions.
