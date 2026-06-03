# 🏡 Analiza i modelowanie cen mieszkań w Polsce

📊 **Projekt analityczny w języku R**, mający na celu zbadanie wpływu wskaźników makroekonomicznych i demograficznych na ceny transakcyjne mieszkań (PLN/m²) w polskich powiatach oraz zbudowanie skutecznego modelu predykcyjnego.

---

## 👥 Autorzy
* **Sylwester Sowula**
* **Bartosz Opioła**
* **Emanuel Sagan**

📅 **Data projektu:** Kwiecień 2026

---

## 🎯 Cel projektu
Głównym celem analizy jest identyfikacja kluczowych czynników wpływających na rynek nieruchomości w Polsce oraz stworzenie modelu ekonometrycznego zdolnego do przewidywania cen za metr kwadratowy. Projekt sprawdza, w jakim stopniu zamożność regionu, demografia i poziom urbanizacji tłumaczą zróżnicowanie cen mieszkań.

## 🗂 Zbiór danych
Dane obejmują statystyki dla polskich powiatów. Główną zmienną objaśnianą jest `cena_m2`. Do potencjalnych zmiennych objaśniających (predyktorów) należą:
* `wynagrodzenie` - Średnie wynagrodzenie brutto
* `bezrobocie` - Stopa bezrobocia (%)
* `ludnosc` / `gestosc` - Liczba mieszkańców i gęstość zaludnienia
* `urbanizacja` - Wskaźnik urbanizacji (%)
* `pozwolenia_na_1000` - Liczba pozwoleń na budowę na 1000 mieszkańców
* `podmioty_gosp` - Gęstość podmiotów gospodarczych
* `studenci_na_1000` - Liczba studentów na 1000 mieszkańców
* `saldo_migracji_na_1000` - Saldo migracji w przeliczeniu na 1000 mieszkańców

## ⚙️ Metodologia
Projekt został przeprowadzony zgodnie z najlepszymi praktykami analizy danych:
1. **Eksploracyjna Analiza Danych (EDA):** Analiza rozkładów (skośność, kurtoza), badanie obserwacji odstających (outlierów) oraz macierzy korelacji.
2. **Podział danych:** Zbiór został podzielony na część treningową (70%) i testową (30%).
3. **Dobór zmiennych:** Zastosowano i porównano dwie metody selekcji cech:
   * **Krokowa selekcja AIC** (Akaike Information Criterion)
   * **Metoda Hellwiga** (maksymalizacja pojemności informacyjnej)
4. **Transformacja:** W celu eliminacji problemu heteroskedastyczności zlogarytmowano zmienną objaśnianą `log(cena_m2)`.
5. **Diagnostyka modeli:** Wykorzystano testy statystyczne: Shapiro-Wilka (normalność), Breuscha-Pagana (homoskedastyczność), RESET, test Durbina-Watsona oraz test serii.

## 📈 Kluczowe Wyniki
Ostatecznym wyborem okazał się **Model krokowy (AIC) na zmiennej zlogarytmizowanej**, który weryfikowano na zbiorze testowym. 

* **MAE (Średni błąd bezwzględny):** ~826 PLN
* **MAPE (Średni absolutny błąd procentowy):** ~15.82%
* **Najważniejsze zmienne:** Zidentyfikowano, że gęstość podmiotów gospodarczych, liczba pozwoleń na budowę, liczba ludności i wskaźniki akademickie mają najsilniejszy wpływ na cenę.

**Wnioski biznesowe:** Model radzi sobie bardzo dobrze z typowymi powiatami (ceny 4000 - 7000 PLN/m²). Wykazuje jednak tendencję do niedoszacowywania cen w najdroższych, elitarnych lokalizacjach (np. Warszawa, Sopot, powiat tatrzański), co sugeruje, że rynki te rządzą się własnymi, spekulacyjnymi prawami.

## 🛠 Technologie i pakiety R
Projekt został w całości napisany w języku **R**. Główne wykorzystane biblioteki:
* `dplyr` / `tidyr` - manipulacja danymi
* `ggplot2` - zaawansowana wizualizacja
* `MASS` - implementacja algorytmu stepAIC
* `lmtest` / `car` / `tseries` - diagnostyka modeli ekonometrycznych (testy statystyczne)

## 🚀 Jak uruchomić projekt?
1. Sklonuj repozytorium.
2. Upewnij się, że w folderze roboczym znajduje się plik z danymi (plik `.csv`).
3. Zainstaluj wymagane pakiety w R: `install.packages(c("ggplot2", "MASS", "lmtest", "car", "tseries"))`.
4. Uruchom główny skrypt lub plik R Markdown, aby wygenerować raport.
