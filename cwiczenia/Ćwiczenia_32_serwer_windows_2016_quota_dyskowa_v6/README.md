Ćwiczenia 32 -- Quota dyskowa
1.  Zaloguj się na swoje konto administrator.
2.  Uruchom menedżer serwera i dodaj role. Dodaj pozycję dla: menadżer
    zasobów serwera plików.
> ![](media/image1.png)
3.  Po instalacji uruchomić przystawkę: Narzędzia administracyjne →
    *Menadżer zasobów serwera plików(Tools-\>File Server Resource
    Manager)*
> ![](media/image2.png)
4.  Utworzyć nowe konto o nazwie **twoje_imię_quota** dla którego należy
    ustawić folder macierzysty (ścieżka
> UNC) na udostępniony, ukryty zasób sieciowy
> [c:\\przydziały_dyskowe](../../../../../E:/c:/przydziały_dyskowe) oraz
> zamapować pod literę dysku Q.
>
> ![](media/image3.png)
5.  Zalogować się na konto **twoje_imię_quota** i sprawdzić poprawność
    zamapowania dysku.
> ![](media/image4.png)
6.  Utwórz drugie konto tak jak w punktach poprzednich.
7.  Najpierw utwórz swój szablon np. 3k
> ![](media/image5.png)
8.  W przystawcę *Menadżer zasobów serwera plików,* z lewej strony
    wybrać:
![](media/image6.png)
 Zarządzanie przydziałami→ Przydziały.
Następnie wybrać akcję: Utwórz przydział.
9.  Ścieżkę przydziału ustaw na katalog użytkownika z profilami czyli
    [c:\\przydziały_dyskowe](../../../../../E:/c:/przydziały_dyskowe)\\.
> Najpierw utwórz swój szablon np. 3k
>
> Zaznacz: Automatycznie zastosuj szablon i utwórz przydziały dla
> istniejących i nowych podfolderów. Ustaw:
a)  ![](media/image7.png)
    limit na 25MB
b)  sztywny
c)  próg ostrzeżeń na 35%
d)  wyślij ostrzeżenie do dziennika zdarzeń
e)  generuj raporty: duże pliki, pliki według właściciela, użycie
    przydziału
f)  wyślij raport do użytkownika, który przekroczył próg
<!-- -->
10. Odśwież widok przydziałów w przystawce na serwerze.
![](media/image8.png)
11. Będąc zalogowanym na koncie twoje_imię_quota
> ![](media/image9.png)
>
> spowoduj pojawienie się komunikatu o ostrzeżeniu.
>
> ![](media/image10.png)
12. Sprawdź dzienniki zdarzeń.
> ![](media/image11.png)
13. Będąc zalogowanym na koncie twoje_imię_quota spowoduj pojawienie się
    komunikatu o przekroczeniu limitu przydziału dysku.
14. Sprawdź dzienniki zdarzeń oraz raporty.
> ![](media/image12.png)
15. Sprawdź czy utworzyły się raporty
    %systemdrive%\\StorageReports\\Incident. Przejrzyj je.
![](media/image13.png)
16. Dla pierwszego konta zmień przydział na 50MB, a drugiego próg
    ostrzeżeń na 60%.
> ![](media/image14.png)
17. Powtórz poprzednie punkty, ale dla **przydziału elastycznego**,
    zmień próg ostrzeżeń na 75%.
18. Napisz skrypt, który wyświetli aktualne przydziały w systemie.
19. Napisz skrypt i sprawdź jego działanie, który ustawi limit na 100MB
    dla wybranego konta.
