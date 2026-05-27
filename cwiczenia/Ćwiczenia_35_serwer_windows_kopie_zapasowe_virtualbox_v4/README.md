# Ćwiczenia 35 -- kopie zapasowe - windows server 2019 Standard

1. Zaloguj się na swoje konto administrator.

1. Uruchom menedżer serwera → Zarządzaj -\> dodaj role, funkcje.

1. W kreatorze w pozycji funkcje zaznacz: **kopia zapasowa systemu
    windows server**

   ![image1](media/image1.png)

1. Utworzyć profil mobilny w jednostce organizacyjnej o nazwie
    **kopie**.

   ![image2](media/image2.png)

1. Zalogować się na to konto na stacji.
1. Na stacji utworzyć katalog „archiwum" i udostępnić go.

   ![image3](media/image3.png)

1. Na serwerze: Narzędzia -\> Kopia zapasowa systemu
    Windows Server -\> jednorazowa kopia zapasowa (prawa strona akcje)

   ![image4](media/image4.png)

1. Inne opcje-\> dalej -\> niestandardowa -\> dalej -\> dodaj elementy
    -\> wybrać jeden lub dwa niewielkie katalogi -\> dalej -\> zdalny
    folder udostępniony -\> podać lokalizacje
    [\\\\nazwa](../../../../../../../%5C%5Cnazwa)
    \_lub_ip_stacji\\nazwa_udziału → dalej → Kopia zapasowa

   ![image5](media/image5.png)

   ![image6](media/image6.png)

   ![image7](media/image7.png)

1. Zweryfikuj na serwerze poprawność wykonania kopii:

   ![image8](media/image8.png)

1. Zapisz plik z listą zarchiwizowanych katalogów i plików na pulpicie.
1. Zweryfikuj na stacji poprawność wykonanej kopii. Powinien powstać
    katalog WindowsImageBackup z podkatalogami. ( około 100MB)

   ![image9](media/image9.png)

1. Spróbuj odtworzyć zawartość kopii.

   ![image10](media/image10.png)

   ![image11](media/image11.png)

1. Przygotuj powyższą kopię według harmonogramu 1:00 i 11:00 godz. (
    dobierz godzinę ćwiczeń)

   ![image12](media/image12.png)

   ![image13](media/image13.png)

   ![image14](media/image14.png)

   ![image15](media/image15.png)

1. Sprawdzenie wykonania kopii za pomocą harmonogramu.

   ![image16](media/image16.png)

   ![image17](media/image17.png)

1. Wykonaj sprawdzenie kopii stanu systemu. (**kilka giga nie
    wykonujemy!!!**)

   ![image18](media/image18.png)

   ![image19](media/image19.png)

1. Wykonaj kopię z wykluczeniem wszystkich plików z rozszerzeniem txt.

1. KONIEC.🔚
