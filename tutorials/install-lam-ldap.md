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

![Configuració inicial LAM](/img/config_lam.png)

⚠️ Substitueix  **<ip_servidor_ldap_lam>** per l'adreça ip de **xarxa NAT**  o **anfitrió** des de el teu client o anfitrió.

**Editem el perfil del servidor**

![Configuració del perfil](/img/lam_profile.png)

**Introduim la contrasenya per defecte**

![Introduir usuari i contrasenya](/img/lam_login.png)

```bash
lam
```
⚠️ La contrasenya per defecte de l'usuari lam és: **lam**

**Anem a les opcions generals a l'apartat Server Settings**

![Server settings](/img/lam_settings.png)

```bash
Per exemple: cn=admin,dc=mydomain,dc=test
```
⚠️ Substituirem **dc=mydomain** i **dc=test**, per les dades del domini configurades en el ldap.

**Ara anem a l'apartat Tools Settings i configurem el domini**

![Tools settings](/img/lam_tools.png)

```bash
Per exemple: dc=mydomain,dc=test
```
⚠️ Substituirem **dc=mydomain** i **dc=test**, per les dades del domini configurades en el ldap.
