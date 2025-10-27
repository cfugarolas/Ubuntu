<div align="center"> 
  
  <img src="/img/logo_ubuntu.png" alt="Logo Ubuntu" width="100"/>

# 🐧 Ubuntu Tutorials
### Instal·lació i configuració bàsica d’OpenLDAP a Ubuntu

Petit tutorial per aprendre a instal·lar, configurar i verificar un servidor LDAP en Ubuntu.

</div>

---

## 📚 Instal·lació d’OpenLDAP en Ubuntu

Aquest tutorial explica com instal·lar i configurar un servidor LDAP en Ubuntu.
Veurem:

- Instal·lació de paquets necessaris.
- Configuració inicial.
- Comprovar el funcionament del servei.

## 🧩 Objectiu

- Instal·lar OpenLDAP i el paquet d’utilitats.
- Configurar les dades bàsiques del directori LDAP.
- Verificar que el servei funciona correctament.

## 🔍 1. Actualitzar el sistema

Sempre comencem actualitzant els repositoris i paquets, podeu mirar el tutorial d'actualització
[📖 Actualitzar completament el sistema Ubuntu](../tutorials/actualitzacions-sistema.md)

## 📦 2. Instal·lar OpenLDAP i eines

Instal·lem el servidor i les utilitats administratives:

```bash
sudo apt install slapd ldap-utils -y
```
Durant la instal·lació et demanarà una contrasenya per l’admin LDAP.

**🔐 Recorda-la! La necessitaràs per gestionar el directori.**

## ⚙️ 3. Configuració posterior a la instal·lació

Per reconfigurar els paràmetres inicials:

```bash
sudo dpkg-reconfigure slapd
```
| Pregunta             | Recomanació       |
| -------------------- | ----------------- |
| Ometre configuració? | **No**            |
| Nom de domini (DNS)  | exemple.local     |
| Nom d’organització   | exemple           |
| Base de dades        | MDB (per defecte) |
| Esborrar BD antiga?  | No                |


