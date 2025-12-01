<div align="center">

<img src="/img/logo_ubuntu.png" alt="Logo Ubuntu" width="100"/>

# 🐧 Ubuntu Tutorials  
### Compartició de fitxers Linux: NFS

Tutorial per aprendre a **instal·lar i configurar els servei NFS (Network File System)**, aplicant totes les configuracions necessaries.

---

</div>

# 🔄 Compartició de fitxers Linux: NFS

Tutorial per aprendre a **instal·lar i configurar els servei NFS (Network File System)**, aplicant totes les configuracions necessaries.

---

## 🧩 Objectiu

- Instal·lació del servei. 
- Creació recurs compartit.  
- Configurar NFS.  
- Accés des del client.

---

## 📥 1️⃣ Instal·lació del servei

La primera activitat ser`instal·lar el servidor NFS i totes les dependències.

```bash
sudo apt install nfs-kernel-server
```

## ⚙️ 2️⃣Creació recurs compartit

Primer de tot crearem una carpeta compartida dins el directori /srv,

```bash
sudo mkdir compartida
```

li treurem la propietat a qualsevol usuari i grup

```bash
sudo chown nobody:nogroup /srv/compartida
```

i donem tots els permisos 1(executat)+2(escriure)+4(lectura)

```bash
sudo chmod -R 777 /srv/compartida
```

## 🔧 3️⃣ Configurar LAM per connectar al teu LDAP
