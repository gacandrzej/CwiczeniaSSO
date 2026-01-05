Ćwiczenia 35 -- kopie zapasowe - windows server 2019 Standard
1.  Zaloguj się na swoje konto administrator.
2.  Uruchom menedżer serwera → Zarządzaj -\> dodaj role, funkcje.
3.  W kreatorze w pozycji funkcje zaznacz: **kopia zapasowa systemu
    windows server**
> ![](media/image1.png)
4.  Utworzyć profil mobilny w jednostce organizacyjnej o nazwie
    **kopie**.
> ![](media/image2.png)
5.  Zalogować się na to konto na stacji.
6.  Na stacji utworzyć katalog „archiwum" i udostępnić go.
> ![](media/image3.png)
7.  ![](media/image4.png)
    Na serwerze: Narzędzia -\> Kopia zapasowa systemu
    Windows Server -\> jednorazowa kopia zapasowa (prawa strona akcje)
8.  Inne opcje-\> dalej -\> niestandardowa -\> dalej -\> dodaj elementy
    -\> wybrać jeden lub dwa niewielkie katalogi -\> dalej -\> zdalny
    folder udostępniony -\> podać lokalizacje
    [\\\\nazwa](../../../../../../../%5C%5Cnazwa)
    \_lub_ip_stacji\\nazwa_udziału → dalej → Kopia zapasowa
> ![](media/image5.png)
>
> ![](media/image6.png)
>
> ![](media/image7.png)
9.  Zweryfikuj na serwerze poprawność wykonania kopii:
> ![](media/image8.png)
10. Zapisz plik z listą zarchiwizowanych katalogów i plików na pulpicie.
11. Zweryfikuj na stacji poprawność wykonanej kopii. Powinien powstać
    katalog WindowsImageBackup z podkatalogami. ( około 100MB)
> ![](media/image9.png)
12. Spróbuj odtworzyć zawartość kopii.
> ![](media/image10.png)
>
> ![](media/image11.png)
13. Przygotuj powyższą kopię według harmonogramu 1:00 i 11:00 godz. (
    dobierz godzinę ćwiczeń)
> ![](media/image12.png)
>
> ![](media/image13.png)
>
> ![](media/image14.png)
>
> ![](media/image15.png)
14. Sprawdzenie wykonania kopii za pomocą harmonogramu.
> ![](media/image16.png)
>
> ![](media/image17.png)
15. Wykonaj sprawdzenie kopii stanu systemu. (**kilka giga nie
    wykonujemy!!!**)
> ![](media/image18.png)
>
> ![](media/image19.png)
16. Wykonaj kopię z wykluczeniem wszystkich plików z rozszerzeniem txt.
17. KONIEC.
