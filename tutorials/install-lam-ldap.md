<div align="center">

  <img src="/img/logo_ubuntu.png" alt="Logo Ubuntu" width="100"/>

# 🐧 Ubuntu LDAP Tutorials
### Instal·lació de LAM (LDAP Account Manager) en un servidor Ubuntu

Aquest tutorial explica com instal·lar i configurar **LDAP Account Manager (LAM)** en un servidor Ubuntu amb LDAP ja actiu.

</div>

---

## 📚 Objectius

- Instal·lar LAM en un servidor Ubuntu amb LDAP
- Configurar LAM per connectar-se al servidor LDAP existent
- Accedir a LAM via navegador web per gestionar usuaris i grups

---

## 📝 1️⃣ Actualitzar el sistema

És recomanable començar actualitzant els paquets del sistema:

```bash
sudo apt update && sudo apt upgrade -y
```

## 📥 2️⃣ Instal·lar LDAP Account Manager (LAM)

Instal·lem LAM des dels repositoris oficials d’Ubuntu:

```bash
sudo apt install ldap-account-manager -y
```

## 🔧 3️⃣ Configurar LAM per connectar al teu LDAP

```bash
http://<ip_servidor_ldap_lam>/lam
```
**Accedim a la configuració del LAM**

<img src="/img/config_lam.png" alt="Configuració inicial LAM" width="500"/>
 
⚠️ Substitueix  **<ip_servidor_ldap_lam>** per l'adreça ip de **xarxa NAT**  o **anfitrió** des de el teu client o anfitrió.

---

**Editem el perfil del servidor**

<img src="/img/lam_profile.png" alt="Configuració del perfil" width="250"/>

**Introduim la contrasenya per defecte**

<img src="/img/lam_login.png" alt="Introduir usuari i contrasenya" width="350"/>

```bash
lam
```
⚠️ La contrasenya per defecte del perfil lam és: **lam**

---

**Anem a l'apartat Server Settings**

<img src="/img/lam_settings.png" alt="Server settings" width="800"/>

```bash
Per exemple: cn=admin,dc=mydomain,dc=test
```
⚠️ Substituirem **dc=mydomain** i **dc=test**, per les dades del domini configurades en el ldap.

---

**Ara anem a l'apartat Tools Settings i configurem el domini**

<img src="/img/lam_tools.png" alt="Tools set i gutings" width="700"/>

```bash
Per exemple: dc=mydomain,dc=test
```
⚠️ Substituirem **dc=mydomain** i **dc=test**, per les dades del domini configurades en el ldap.

---
**Dins Account Types anem a l'apartat Active account types**

<img src="/img/lam_account_types.png" alt="Account Types" width="250"/>
<img src="/img/lam_act_account.png" alt="Account" width="700"/>

⚠️ Substituirem **uo=users** i **uo=groups**, amb el nom que vulguem per guardar els usuaris i grups.

---

**Guardem els canvis**

<img src="/img/save.png" alt="Logo Ubuntu" width="200"/>

⚠️ Anem al final de la pestanya **General settings** o **Account Types** i guardem la configuració.

---

**Accedim al LDAP**

<img src="/img/ldap_login.png" alt="Logo Ubuntu" width="400"/>

⚠️ La contrasenya serà la configurada al fer la instal·lació del nostre LDAP server.

---

