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

## 📥 2️⃣ Instal·lar LDAP Account Manager (LAM)

Instal·lem LAM des dels repositoris oficials d’Ubuntu:

```bash
sudo apt install ldap-account-manager -y
```

## 🔧 3️⃣ Configurar LAM per connectar al teu LDAP
