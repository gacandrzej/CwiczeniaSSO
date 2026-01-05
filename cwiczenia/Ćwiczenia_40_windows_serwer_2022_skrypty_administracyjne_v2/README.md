Ćwiczenia 33 -- tworzenie skryptów administracyjnych -- Windows 2022
1.  Zaloguj się na swoje konto administrator.
2.  Napisz skrypt (rozszerzenie vbs), który:
<!-- -->
a)  Wyświetli „hello world" , wsk. Wscript.Echo „"
b)  przyłączający stację do domeny,
> wskazówka:
> <https://technet.microsoft.com/pl-pl/library/cc788049(v=ws.10).aspx>
>
> np.: netdom join STACJA /domain:zsmeie.abcd
> /ou:OU=Computers,DC=zsmeie,DC=abcd
>
> /userd:zsmeie\\Administrator /passwordd:ZAQ!2wsx
>
> lub dla power shella:
>
> Add-Computer -DomainName zsmeie.abcd -Credential (Get-Credential)
c)  Tworzący jednostkę organizacyjną w Active Directory,
> wskazówka: \'w ktorej jednostce organizacyjnej zakladamy jednostkę
> org.( 3k/gr1)
>
> Set objDomain = GetObject(\"LDAP://ou=gr1, ou=3k,dc=zsmeie,dc=abcd\")
>
> Set objOU = objDomain.Create(\"organizationalUnit\", \"ou=2024\")
>
> objOU.SetInfo
d)  tworzący konto w Active Directory,
> wskazówka:
>
> \'w ktorej jednostce organizacyjnej zakladamy konto
>
> Set jedorg = GetObject(\"LDAP://ou=gr1,ou=3k,dc=zsmeie,dc=abcd\")
>
> \'zakladanie nowego konta
>
> set usr=jedorg.Create(\"User\",\"cn=xKowalskiJ\")
>
> \' nadanie wlasciwosci (pierwsza zakladka)
>
> usr.Put \"givenName\", \"Jan\"
>
> usr.Put \"sn\", \"xKowalski\"
>
> usr.Put \"displayName\", \"xKowalski Jan\"
>
> usr.Put \"userPrincipalName\", \"xKowalskiJ@zsmeie.abcd\"
>
> usr.Put \"sAMAccountName\", \"xKowalskiJ\"
>
> usr.Put \"mail\", \"xKowalskiJ@zsmeie.abcd\"
>
> usr.Put \"mailNickname\", \"xKowalskiJ\"
>
> usr.Put \"description\", \"przez skrypt\"
>
> \'ustawienie polozenia profilu i katalogu Moje dokumenty
>
> \'zakladka Profil
>
> usr.Put \"profilePath\", \"\\\\k5\\profile\$\\%username%\"
>
> usr.Put \"HomeDirectory\", \"\\\\k5\\profile\$\\%username%\"
>
> usr.Put \"HomeDrive\" , \"h:\"
>
> \'zapis informacji
>
> usr.SetInfo
e)  odczytujący atrybuty wybranego konta
> \'w ktorej jednostce organizacyjnej znajduje się konto
>
> Set usr = GetObject(\"LDAP://cn=nazwa konta,ou=gr1,
> ou=3k,dc=zsmeie,dc=abcd\")
>
> WScript.Echo \"User Principal Name: \" & usr.userPrincipalName \_
>
> & crlf & \"SAM Account Name: \" & usr.sAMAccountName \_
>
> & crlf & \"givenName: \" & usr.givenName \_
>
> & crlf & \"Profile Path: \" & usr.ProfilePath \_
>
> & crlf & \"displayName: \" & usr.displayName \_
>
> & crlf & \"Home Directory: \" & usr.HomeDirectory \_
>
> & crlf & \"Home Drive: \" & usr.HomeDrive \_
>
> & crlf & \"Created:\" & usr.whenCreated \_
>
> & crlf & \"Changed:\" & usr.whenChanged
f)  tworzący jednocześnie 5 kont w OU:
wskazówka: potrzebne są 3 pliki: skrypt dla for, plik konta.csv, oraz
zakladanie_konta_w_AD.vbs
for /F \"tokens=2,3,4 delims=, \" %%i in (konta.csv) do
zakladanie_konta_w_AD.vbs %%i %%j %%k
Set jedorg = GetObject(\"LDAP://ou=3K,dc=szkolenie,dc=wer\")
set argumenty = WScript.Arguments
if (argumenty.Count() = 3) then
set usr=jedorg.Create(\"User\",\"cn=\" & argumenty.item(0))
usr.Put \"givenName\", argumenty.item(1)
usr.Put \"sn\", argumenty.item(2)
3.  Sprawdź działanie napisanych skryptów.
Wskazówki: włączenie konta + ustawienie hasła:
usr.SetPassword \"password\"
> usr.AccountDisabled = false
usr.SetInfo
