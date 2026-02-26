# Ćwiczenia 51 -- GP0, wdrażanie oprogramowania + pulpit zdalny

1.  Zaloguj się na konto administrator.
2.  W AD utwórz nową jednostkę organizacyjną o nazwie **addapp**.
3.  Dołącz stację do domeny.
4.  Po dołączeniu stacji, przenieś komputer w AD do jednostki organizacyjnej addapp.
5.  Przenieś konto, na które logujesz się na stacji do jednostki
    organizacyjnej addapp.

 ![](media/image1.png)

6.  Na dysku udostępnij folder o nazwie apps (udostępnianie
    zaawansowane) jako ukryty,  
 obie zakładki: udostępnianie i zabezpieczenia.

 - administratorzy domeny - pełna kontrola,

 - użytkownicy uwierzytelnieni -- odczyt,

 - wszyscy -zmiana(change).

 ![](media/image2.png)

7.  Na stacji wybierz: Ten komputer - \> Mapuj dysk sieciowy (
    [\\\\10.9.8.1\\apps\$](../../../../../../apps$) ) pod literę R:
8.  Ściągnąć instalkę teams ze strony:

    https://learn.microsoft.com/en-us/microsoftteams/msi-deployment  

    https://go.microsoft.com/fwlink/?linkid=2243204&clcid=0x409

    https://go.microsoft.com/fwlink/?linkid=2196106

9.  Pobrane pliki installerów zapisz na zmapowanym dysku R.
10. Utwórz skrypt bat o zawartości:
```bash
    .\teamsbootstrapper.exe -p -o "\unc\path\to\teams.msix
```
10. Skrypt dodać w 
```text
Computer configuration -> Policies -> Windows settings -> Scripts -> Startup.
```
i przycisk add

11. Ściągnąć instalkę putty:
    https://the.earth.li/~sgtatham/putty/latest/w64/putty-64bit-0.83-installer.msi
11. Ściągnąć plik dla 7-zip:
    https://7-zip.org/a/7z2600-x64.msi
12. Również zapisz plik msi na zmapowanym dysku R.
12. Możesz zaktualizować te pliki na nośnikach pendrive. 
12. Otwórz przystawkę GPO Zarządzanie zasadami grupy.

 ![](media/image3.png)

13. Dla jednostki **addapp** utwórz nowy obiekt zasad grup.
14. Podać nazwę instalacja oprogramowania. OK.
15. Po utworzeniu obiektu wybierz Edytuj.

 ![](media/image4.png)

16. W nowo otwartym oknie:  
```text
Konfiguracja komputera -> Zasady -> Ustawienia oprogramowania ->Instalacja oprogramowania.
```

17. Następnie prawym klawiszem myszki i z rozwiniętego menu
    kontekstowego wybieramy:
```text
Nowy -> Pakiet.
```
18. Nazwa pliku, podajemy
    [\\\\nazwa_servera\\apps](../../../../../../apps) i wybieramy plik
    teams \...msi .

 ![](media/image5.png)

19. Rozmieszczenie oprogramowania: przypisany.

 ![](media/image6.png)

20. Analogicznie dla drugiego pakietu msi.

 ![](media/image7.png)

21. Finalnie:

 ![](media/image8.png)

22. Wybierz:
```text
Szablony administracyjne -> System -> Wyświetlaj bardzo szczegółowe komunikaty o stanie. Włącz.
```

![](media/image9.png)

23. Zamykamy okno edycji zasad.

24. Zapisz raport na pulpicie z utworzonych
    zasad. Prawy klawisz myszy po prawej stronie na Settings.

![](media/image10.png)

25. Na stacji w cmd wpisujemy polecenie: gpupdate /force
 Serwer:

 ![](media/image11.png)

 Stacja:

 ![](media/image12.png)

26. Po restarcie stacji sprawdzić czy oprogramowanie zostało
    zainstalowane.

 ![](media/image13.png)

27. Sprawdzenie oprogramowania:

![](media/image14.png)

28. Sprawdź poleceniem 
```bash
 gpresult /r
```
oraz 
```bash
 gpresult /h raport.html
```

29. Odłącz stację od domeny.
29. Przenieś komputer w AD z jednostki organizacyjnej **addapp** do
    kontenera Computers.

30. Zatrzymaj udostępnianie katalogu apps, następnie usuń ten folder.
31. Usunąć raport z pulpitu. 
32. Opróżnij kosz.
32. W przystawce _`GPO Group Policy Management`_ usunąć obiekt „instalacja
    oprogramowania".

---

33. Dodatkowe ćwiczenie -- **pulpit zdalny**.
34. Konfiguracja pulpitu zdalnego: 
```text
Server Manager -> Local Server -> Remote Desktop
```
, klikamy na disabled

![](media/image15.png)

35. Na stacji windows. Po kliknięciu Podłącz podać hasło i odpowiedzieć
    twierdzącą w nowym oknie.

![](media/image16.png)

 ![](media/image17.png)

36. Wyłączyć pulpit zdalny.
37. KONIEC.🔚
