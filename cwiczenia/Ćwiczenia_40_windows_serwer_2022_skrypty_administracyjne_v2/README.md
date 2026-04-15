# Ćwiczenia 40 -- tworzenie skryptów administracyjnych

---

## 🐧 Uruchamianie skryptu Bash — INF.02

### 1. Shebang

Na początku każdego skryptu Bash umieszczamy:

```bash
#!/bin/bash
```

👉 oznacza to:

- użycie interpretera Bash
- system wie, jak uruchomić plik jako skrypt

---

### 2. Nadanie uprawnień do uruchamiania

```bash
chmod +x skrypt.sh
```

👉 `+x` oznacza:

- plik staje się wykonywalny (executable)

---

### 3. Uruchamianie skryptu

#### ✔ Sposób 1 — standardowy (egzaminacyjny)

```bash
./skrypt.sh
```

👉 wymaga wcześniej `chmod +x`

---

#### ✔ Sposób 2 — bez nadawania uprawnień

```bash
bash skrypt.sh
```

👉 nie wymaga `chmod +x`

---

### 4. Uruchamianie z parametrami

```bash
./skrypt.sh uczen egzamin
```

lub

```bash
bash skrypt.sh uczen egzamin
```

---

### 5. Przykładowy szablon skryptu

```bash
#!/bin/bash

echo "Start skryptu"

echo "Pierwszy parametr: $1"
echo "Drugi parametr: $2"
```

---

## 1. Bash (Linux)

- Wyświetlenie komunikatu „Hello World”  

```Bash
#!/bin/bash
echo "Hello World"
```

- Archiwizacja pliku z użyciem tar i gzip  

```bash
#!/bin/bash
tar cvfz archiwum.tar.gz plik.txt
```

- Archiwizacja katalogu użytkownika  

```bash
#!/bin/bash
tar cvfj backup_katalogu.tar.bz2 /home/user
```

- Wykonanie kopii zapasowej plików logów systemowych  

```bash
#!/bin/bash
sudo cp /var/log/syslog /home/user/syslog_backup.log
```

- Wykonanie kopii zapasowej pliku konfiguracyjnego (.conf)  

```bash
#!/bin/bash
cp /etc/apache2/apache2.conf apache2.conf.bak
```

- Utworzenie nowego użytkownika w systemie  

```bash
#!/bin/bash
sudo useradd jan
sudo passwd jan
```

- Utworzenie nowej grupy w systemie  

```bash
#!/bin/bash
sudo groupadd programisci
```

- Dodanie użytkownika do istniejącej grupy  

```bash
#!/bin/bash
sudo usermod -aG programisci jan
```

- Usunięcie użytkownika z systemu  

```bash
#!/bin/bash
sudo userdel jan
```

- Utworzenie pięciu użytkowników na podstawie parametrów  

```bash
#!/bin/bash

KONTO=$1

for i in {1..5}
do
    useradd -m ${KONTO}${i}
done
```

- Utworzenie grupy systemowej i przypisanie do niej użytkowników  

```bash
#!/bin/bash

GRUPA="informatyk"
sudo groupadd -r $GRUPA

for i in {1..5}
do
    sudo useradd -m uczen$i -g $GRUPA
done
```

- Utworzenie katalogów domowych w niestandardowej lokalizacji  

```bash
#!/bin/bash

KATALOG=$1

for i in {1..5}
do
    useradd -m -d /home/$KATALOG/uczen$i uczen$i
done
```

- Wykonanie backupu katalogu użytkownika z datą w nazwie  

```bash
#!/bin/bash

DATA=$(date +%F)
tar -czvf backup_$DATA.tar.gz /home/user
```

- Nadanie uprawnień do plików i katalogów  

```bash
#!/bin/bash

chmod 755 skrypt.sh
chown root:admin skrypt.sh
```

- Automatyzacja zadań administracyjnych w Bash  

```bash
#!/bin/bash

echo "Start administracji systemem"

apt update -y
apt autoremove -y

echo "Gotowe"
```

- 💾 Montowanie pendrive + listing /etc → plik → kopiowanie

```bash
#!/bin/bash

# 1. Ścieżka do pendrive (urządzenie – może się zmieniać!)
USB_DEV="/dev/sdb1"

# 2. Punkt montowania
MOUNT_DIR="/mnt/pendrive"

# 3. Tworzenie punktu montowania
mkdir -p $MOUNT_DIR

# 4. Montowanie pendrive
mount $USB_DEV $MOUNT_DIR

# 5. Tworzenie listy plików z /etc
ls /etc | grep "^c" > letter_c.txt

# 6. Kopiowanie pliku na pendrive
cp letter_c.txt $MOUNT_DIR/

# 7. Informacja
echo "Zakończono: plik skopiowany na pendrive"

# 8. (opcjonalnie) odmontowanie
umount $MOUNT_DIR
```

---

## 2. Windows 11 (*.cmd)

- Wyświetlenie komunikatu „Hello World”  

```bash
@echo off
echo Hello World
pause
```

- Utworzenie katalogu na dane użytkownika  

```bash
@echo off
mkdir C:\Users\DaneUzytkownika
pause
```

- Skopiowanie pliku do katalogu zapasowego  

```bash
@echo off
mkdir C:\Backup
copy C:\plik.txt C:\Backup\
pause
```

- Wykonanie kopii zapasowej plików logów systemowych  

```bash
@echo off
copy C:\Windows\System32\winevt\Logs\*.evtx C:\Backup\
pause
```

- Utworzenie archiwum plików  

```bash
@echo off
powershell Compress-Archive -Path C:\Dane\* -DestinationPath C:\Backup\dane.zip
pause
```

- Utworzenie lokalnego konta użytkownika  

```bash
@echo off
net user jan Haslo123 /add
pause
```

- Utworzenie lokalnej grupy użytkowników  

```bash
@echo off
net localgroup Programisci /add
pause
```

- Dodanie użytkownika do grupy lokalnej  

```bash
@echo off
net localgroup Programisci jan /add
pause
```

- Usunięcie użytkownika z systemu  

```bash
@echo off
net user jan /delete
pause
```

- Automatyczne tworzenie wielu użytkowników (pętla)  

```bash
@echo off

for /L %%i in (1,1,5) do (
    net user uczen%%i Haslo123 /add
)
pause
```

- Odczyt informacji o użytkowniku  

```bash
@echo off
net user jan
pause
```

- Zmiana hasła użytkownika  

```bash
@echo off
net user jan NoweHaslo123
pause
```

- Zarządzanie katalogami użytkowników  

```bash
@echo off
mkdir C:\Users\jan
mkdir C:\Users\anna
mkdir C:\Users\piotr
pause
```

- Nadawanie uprawnień do plików i katalogów  

```bash
@echo off
icacls C:\Dane /grant jan:F
pause
```

- Automatyzacja zadań w plikach .cmd  

```bash
@echo off
echo Aktualizacja systemu...
echo Czyszczenie plików tymczasowych...
del /q/f/s %TEMP%\*
echo Gotowe
pause
```

---

## 3. Windows Server 2022 (VBScript / Active Directory)

- Wyświetlenie komunikatu „Hello World”  

```Bash
WScript.Echo "Hello World"
```

- Przyłączenie stacji do domeny  

 wskazówka:
 <https://technet.microsoft.com/pl-pl/library/cc788049(v=ws.10).aspx>

```Bash
netdom join STACJA /domain:zsmeie.abcd /ou:OU=Computers,DC=zsmeie,DC=abcd /userd:zsmeie\Administrator /passwordd:ZAQ!2wsx
```

 lub dla power shella, rekomendowane:

```Bash
Add-Computer -DomainName zsmeie.abcd -Credential (Get-Credential)
```

- Tworzenie jednostki organizacyjnej (OU)  

```Bash
Set objDomain = GetObject("LDAP://ou=gr1,ou=3k,dc=zsmeie,dc=abcd")
Set objOU = objDomain.Create("organizationalUnit", "ou=2026")
objOU.SetInfo
```

- Tworzenie konta użytkownika w Active Directory  

```Bash
'w jakiej OU tworzymy konto
Set jedorg = GetObject("LDAP://ou=gr1,ou=3k,dc=zsmeie,dc=abcd")

'tworzenie konta
Set usr = jedorg.Create("User","cn=xKowalskiJ")

'podstawowe dane
usr.Put "givenName", "Jan"
usr.Put "sn", "xKowalski"
usr.Put "displayName", "xKowalski Jan"
usr.Put "userPrincipalName", "xKowalskiJ@zsmeie.abcd"
usr.Put "sAMAccountName", "xKowalskiJ"
usr.Put "mail", "xKowalskiJ@zsmeie.abcd"
usr.Put "mailNickname", "xKowalskiJ"
usr.Put "description", "przez skrypt"

'profil użytkownika
usr.Put "profilePath", "\\k5\profile$\%username%"
usr.Put "HomeDirectory", "\\k5\profile$\%username%"
usr.Put "HomeDrive", "h:"

'zapis
usr.SetInfo

'aktywacja konta i hasło
usr.SetPassword "password"
usr.AccountDisabled = False
usr.SetInfo
```

- Ustawianie atrybutów użytkownika  

```Bash
Const crlf = vbCrLf

Set usr = GetObject("LDAP://cn=xKowalskiJ,ou=gr1,ou=3k,dc=zsmeie,dc=abcd")

WScript.Echo "User Principal Name: " & usr.userPrincipalName & crlf & _
"SAM Account Name: " & usr.sAMAccountName & crlf & _
"givenName: " & usr.givenName & crlf & _
"Profile Path: " & usr.ProfilePath & crlf & _
"displayName: " & usr.displayName & crlf & _
"Home Directory: " & usr.HomeDirectory & crlf & _
"Home Drive: " & usr.HomeDrive & crlf & _
"Created: " & usr.whenCreated & crlf & _
"Changed: " & usr.whenChanged
```

- Konfiguracja profilu użytkownika

```bash
usr.Put "profilePath", "\\k5\profile$\%username%"
usr.Put "HomeDirectory", "\\k5\profile$\%username%"
usr.Put "HomeDrive", "H:"
usr.SetInfo
```

- Ustawienie/zmiana hasła użytkownika  

```bash
usr.SetPassword "NoweHaslo123"
usr.SetInfo
```

- Włączenie konta użytkownika

```bash
' WŁĄCZENIE
usr.AccountDisabled = False
usr.SetInfo

' BLOKOWANIE
usr.AccountDisabled = True
usr.SetInfo
```

- odblokowanie konta

```bash
usr.AccountDisabled = False  'odblokowanie
usr.SetInfo
```

- Odczyt atrybutów konta  

```bash
Const crlf = vbCrLf

Set usr = GetObject("LDAP://cn=xKowalskiJ,ou=gr1,ou=3k,dc=zsmeie,dc=abcd")

WScript.Echo _
"UPN: " & usr.userPrincipalName & crlf & _
"SAM: " & usr.sAMAccountName & crlf & _
"Imię: " & usr.givenName & crlf & _
"Nazwisko: " & usr.sn & crlf & _
"Display: " & usr.displayName & crlf & _
"Profil: " & usr.profilePath & crlf & _
"Home: " & usr.HomeDirectory & crlf & _
"Drive: " & usr.HomeDrive & crlf & _
"Created: " & usr.whenCreated & crlf & _
"Changed: " & usr.whenChanged
```

- Wykorzystanie argumentów w skryptach VBScript  

```bash
Set args = WScript.Arguments

If args.Count = 3 Then
    Set usr = GetObject("LDAP://ou=gr1,ou=3k,dc=zsmeie,dc=abcd")

    Set newUser = usr.Create("User", "cn=" & args(0))
    newUser.Put "givenName", args(1)
    newUser.Put "sn", args(2)

    newUser.SetInfo
End If
```

- Automatyzacja tworzenia kont w AD  

```bash
Set jedorg = GetObject("LDAP://ou=gr1,ou=3k,dc=zsmeie,dc=abcd")

Set usr = jedorg.Create("User","cn=xKowalskiJ")

usr.Put "givenName", "Jan"
usr.Put "sn", "Kowalski"

usr.SetPassword "Haslo123"
usr.AccountDisabled = False

usr.SetInfo
```

- Zarządzanie jednostkami organizacyjnymi  

```bash
Set dom = GetObject("LDAP://ou=gr1,ou=3k,dc=zsmeie,dc=abcd")
Set ou = dom.Create("organizationalUnit", "ou=2024")
ou.SetInfo
```

- Weryfikacja operacji w Active Directory  

```bash
On Error Resume Next

Set usr = GetObject("LDAP://cn=test,ou=gr1,ou=3k,dc=zsmeie,dc=abcd")

If Err.Number <> 0 Then
    WScript.Echo "Użytkownik nie istnieje"
Else
    WScript.Echo "Użytkownik istnieje"
End If
```

- Automatyzacja administracji domeną  

```bash
WScript.Echo "Start automatyzacji AD..."

' tutaj operacje:
' - OU
' - user
' - grupy
' - atrybuty

WScript.Echo "Zakończono"
```

- usuwanie jednostki org. z AD

```bash
Set objOU = GetObject("LDAP://ou=2025,ou=gr1,ou=3k,dc=zsmeie,dc=abcd")
objOU.DeleteObject 0
```

- usuwanie użytkownika z Ad

```bash
Set objUser = GetObject("LDAP://cn=xKowalskiJ,ou=gr1,ou=3k,dc=zsmeie,dc=abcd")
objUser.DeleteObject
```

- Dodanie użytkownika do grupy AD

```bash
Set grp = GetObject("LDAP://cn=Uczniowie,ou=gr1,ou=3k,dc=zsmeie,dc=abcd")
grp.Add "LDAP://cn=xKowalskiJ,ou=gr1,ou=3k,dc=zsmeie,dc=abcd"
grp.SetInfo
```

- sprawdzenie czy konto istniej

```bash
On Error Resume Next

Set usr = GetObject("LDAP://cn=test,ou=gr1,ou=3k,dc=zsmeie,dc=abcd")

If Err.Number <> 0 Then
    WScript.Echo "Użytkownik nie istnieje"
Else
    WScript.Echo "Użytkownik istnieje"
End If
```

- wypisanie listy użytkowników w OU

```bash
Set ou = GetObject("LDAP://ou=gr1,ou=3k,dc=zsmeie,dc=abcd")

For Each obj In ou
    WScript.Echo obj.Name
Next
```

- Tworzenie wielu użytkowników z pliku CSV  

wskazówka: potrzebne są 3 pliki:

plik konta.csv:

```csv
1,Jan,Kowalski
2,Anna,Nowak
3,Piotr,Zielinski
4,Kasia,Wisniewska
5,Adam,Kaczmarek
```

skrypt dla for,

```Bash
for /F \"tokens=2,3,4 delims=, \" %%i in (konta.csv) do zakladanie_konta_w_AD.vbs %%i %%j %%k
```

Skrypt zakladanie_konta_w_AD.vbs:

```Bash
Set jedorg = GetObject(\"LDAP://ou=3K,dc=szkolenie,dc=wer\")
set argumenty = WScript.Arguments
if (argumenty.Count() = 3) then
set usr=jedorg.Create(\"User\",\"cn=\" & argumenty.item(0))
usr.Put \"givenName\", argumenty.item(1)
usr.Put \"sn\", argumenty.item(2)
3.  Sprawdź działanie napisanych skryptów.
Wskazówki: włączenie konta + ustawienie hasła:
usr.SetPassword \"password\"
usr.AccountDisabled = false
usr.SetInfo
```
