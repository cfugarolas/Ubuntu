<div align="center"> 
  
  <img src="/img/logo_ubuntu.png" alt="Logo Ubuntu" width="100"/>

# 🐧 Ubuntu Tutorials
### Creació d’Unitats Organitzatives amb arxius .ldif

Tutorial per aprendre a crear i importar objectes al directori LDAP utilitzant fitxers `.ldif`.

</div>

---

# 📘 Introducció

En aquest tutorial aprendrem:

- Què és un fitxer `.ldif`
- Com crear un fitxer `.ldif` des de zero
- Com definir dues Unitats Organitzatives (OUs): **users** i **groups**
- Com importar aquest fitxer al nostre servidor LDAP
- Com verificar que la importació ha funcionat

Aquest és un procés fonamental per preparar l’estructura bàsica d’un directori LDAP.

---

# 📂 Què és un fitxer `.ldif`?

Un fitxer `.ldif` (*LDAP Data Interchange Format*) és un arxiu de text que conté definicions d’objectes LDAP.

S’utilitza per:

- Crear objectes al directori
- Modificar-los
- Importar o exportar dades

Cada entrada `.ldif` representa un objecte i sempre inclou:

- Un **DN** (Distinguished Name)
- Classes d’objecte (*objectClass*)
- Atributs de l’objecte

---

# 🗂️ Creació de les Unitats Organitzatives *users* i *groups*

## 1️⃣ Crear el fitxer `.ldif`

Obrirem un nou fitxer anomenat **OUs.ldif**:

```bash
sudo nano OUs.ldif
```

## 2️⃣ Afegir el contingut LDIF

Copia i enganxa el següent contingut al teu fitxer `.ldif`:

```bash
dn: ou=users,dc=elmeudomini,dc=test
ou: users
objectClass: top
objectClass: organizationalUnit

dn: ou=groups,dc=elmeudomini,dc=test
ou: groups
objectClass: top
objectClass: organizationalUnit
```
## 🔍 Explicació del contingut

### 📁 OU: *users* i  OU: *groups*
- **dn:** identifica l’objecte dins el directori  
- **ou:** nom de la unitat organitzativa  
- **objectClass:** indica que és una OU
---

## 📥 3️⃣ Importar el fitxer `.ldif` al servidor LDAP

Un cop guardat el fitxer, importa les noves OUs amb:

```bash
ldapadd -D "cn=admin,elmeudomini,dc=test" -W -f OUs.ldif
```

## 📌 Significat de la comanda

- **ldapadd** → afegeix noves entrades LDAP  
- **-D** → DN de l’administrador  
- **-W** → demana contrasenya de manera segura  
- **-f** → indica el fitxer a importar  

### ✔️ Sortida esperada

```text
adding new entry "ou=users,dc=elmeudomini,dc=test"
adding new entry "ou=groups,dc=elmeudomini,dc=test"
```
Això confirma que les OUs han estat creades amb èxit.

---

## 🔎 4️⃣ Verificar que les OUs s’han creat correctament

Consulta tot el directori amb:

```bash
sudo slapcat
```
O bé busca només les noves OUs:

```bash
ldapsearch -x -b "dc=elmeudomini,dc=test" "(ou=*)"
```
---

## 🎉 Conclusió

En aquest tutorial hem après:

- ✔️ Què és un fitxer .ldif
- ✔️ Com crear dues Unitats Organitzatives
- ✔️ Com importar-les al directori LDAP
- ✔️ Com verificar que s’han importat correctament

Amb això ja tens la base per continuar ampliant el teu LDAP amb usuaris, grups i més estructures.
