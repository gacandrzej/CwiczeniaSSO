# Ćwiczenia 33 -- tworzenie skryptów administracyjnych -- Windows 2022

# 📘 Ćwiczenia — Skrypty administracyjne

---

## 1. Bash (Linux)

- Wyświetlenie komunikatu „Hello World”  
- Archiwizacja pliku z użyciem tar i gzip  
- Archiwizacja katalogu użytkownika  
- Wykonanie kopii zapasowej plików logów systemowych  
- Wykonanie kopii zapasowej pliku konfiguracyjnego (.conf)  
- Utworzenie nowego użytkownika w systemie  
- Utworzenie nowej grupy w systemie  
- Dodanie użytkownika do istniejącej grupy  
- Usunięcie użytkownika z systemu  
- Utworzenie pięciu użytkowników na podstawie parametrów  
- Utworzenie grupy systemowej i przypisanie do niej użytkowników  
- Utworzenie katalogów domowych w niestandardowej lokalizacji  
- Wykonanie backupu katalogu użytkownika z datą w nazwie  
- Nadanie uprawnień do plików i katalogów  
- Automatyzacja zadań administracyjnych w Bash  

---

## 2. Windows 11 (*.cmd)

- Wyświetlenie komunikatu „Hello World”  
- Utworzenie katalogu na dane użytkownika  
- Skopiowanie pliku do katalogu zapasowego  
- Wykonanie kopii zapasowej plików logów systemowych  
- Utworzenie archiwum plików  
- Utworzenie lokalnego konta użytkownika  
- Utworzenie lokalnej grupy użytkowników  
- Dodanie użytkownika do grupy lokalnej  
- Usunięcie użytkownika z systemu  
- Automatyczne tworzenie wielu użytkowników (pętla)  
- Odczyt informacji o użytkowniku  
- Zmiana hasła użytkownika  
- Zarządzanie katalogami użytkowników  
- Nadawanie uprawnień do plików i katalogów  
- Automatyzacja zadań w plikach .cmd  

---

## 3. Windows Server 2022 (VBScript / Active Directory)

- Wyświetlenie komunikatu „Hello World”  
- Przyłączenie stacji do domeny  
- Tworzenie jednostki organizacyjnej (OU)  
- Tworzenie konta użytkownika w Active Directory  
- Ustawianie atrybutów użytkownika  
- Konfiguracja profilu użytkownika  
- Ustawienie hasła użytkownika  
- Włączenie konta użytkownika  
- Odczyt atrybutów konta  
- Tworzenie wielu użytkowników z pliku CSV  
- Wykorzystanie argumentów w skryptach VBScript  
- Automatyzacja tworzenia kont w AD  
- Zarządzanie jednostkami organizacyjnymi  
- Weryfikacja operacji w Active Directory  
- Automatyzacja administracji domeną  

---

1. Napisz skrypt (rozszerzenie vbs), który:
<!-- -->
a)  Wyświetli „hello world" , wsk. Wscript.Echo „"

```Bash
WScript.Echo "Hello World"
```

b)  przyłączający stację do domeny,

 wskazówka:
 <https://technet.microsoft.com/pl-pl/library/cc788049(v=ws.10).aspx>

```Bash
netdom join STACJA /domain:zsmeie.abcd /ou:OU=Computers,DC=zsmeie,DC=abcd /userd:zsmeie\Administrator /passwordd:ZAQ!2wsx
```

 lub dla power shella, rekomendowane:

```Bash
Add-Computer -DomainName zsmeie.abcd -Credential (Get-Credential)
```

c)  Tworzący jednostkę organizacyjną w Active Directory,

```Bash
Set objDomain = GetObject("LDAP://ou=gr1,ou=3k,dc=zsmeie,dc=abcd")
Set objOU = objDomain.Create("organizationalUnit", "ou=2026")
objOU.SetInfo
```

d)  tworzący konto w Active Directory,

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

e)  odczytujący atrybuty wybranego konta
    w ktorej jednostce organizacyjnej znajduje się konto

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

f)  tworzący jednocześnie 5 kont w OU:

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
