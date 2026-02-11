# Marketing Mix Modeling – wpływ kanałów akwizycji na sprzedaż

## Opis zadania

Celem projektu jest analiza wpływu poszczególnych kanałów marketingowych na sprzedaż w sklepie internetowym. Sklep reklamuje się za pośrednictwem wielu kanałów akwizycji, takich jak m.in. telewizja, reklamy outdoorowe oraz kanały internetowe (Google Ads, Meta Ads, TikTok Ads itd.).

Ze względu na brak możliwości jednoznacznego przypisania pojedynczego zakupu do konkretnego kanału (brak jawnej atrybucji użytkownika), klasyczne modele atrybucji (np. last-click) nie znajdują tu zastosowania. Zamiast tego analiza opiera się na zagregowanych danych historycznych i podejściu typu **Marketing Mix Modeling (MMM)**.

---

## Cele analizy

Główne pytania biznesowe, na które odpowiada projekt:

1. **Jakiego przyrostu przychodów można się spodziewać, gdy wydatki reklamowe na danym kanale wzrosną o X%?**
2. **Które kanały akwizycji są najbardziej, a które najmniej rentowne z punktu widzenia generowanej sprzedaży?**

Dodatkowo celem jest identyfikacja innych przydatnych biznesowo wniosków oraz zaproponowanie możliwych kierunków dalszej analizy.

---

## Dane

Analiza opiera się na danych historycznych zagregowanych w podziale na:
- **tydzień**
- **geolokalizację** (np. kraj lub województwo)

Dane zawierają m.in.:

- wydatki reklamowe na poszczególne kanały marketingowe
- łączną sprzedaż
- liczbę impresji / wyświetleń reklam  
  - dla części kanałów (np. Google Ads, Meta Ads) dostępne są dokładne dane  
  - dla TV i części reklam outdoorowych dostępne są jedynie szacunkowe wartości  
  - dla jednego z kanałów outdoorowych brak informacji o impresjach
- ruch organiczny (wejścia bezpośrednie oraz z wyszukiwarek, z wyłączeniem reklam)
- dodatkowe atrybuty opisujące rynek:
  - wielkość rynku
  - populację w danej geolokalizacji
- informacje o akcjach promocyjnych prowadzonych w danym tygodniu i lokalizacji

Źródłem danych jest hurtownia **Google BigQuery**.

---

## Podejście analityczne

Ze względu na charakter danych oraz brak bezpośredniej atrybucji użytkownika, zastosowano podejście **Marketing Mix Modeling**, oparte na modelach regresyjnych i danych zagregowanych.

Główne elementy podejścia:
- agregacja danych w układzie tydzień × geolokalizacja
- uwzględnienie opóźnionego wpływu reklamy (carryover / adstock)
- modelowanie malejących przychodów krańcowych (saturacja kanałów)
- kontrola czynników zewnętrznych, takich jak:
  - sezonowość
  - promocje
  - wielkość rynku i populacja

BigQuery wykorzystywany jest jako warstwa pozyskania, natomiast cała analiza statystyczna i modelowanie realizowane są w języku **Python**.

---

## Technologie

- **SQL / Google BigQuery** – pozyskanie i agregacja danych
- **Python**  
  - pandas, numpy – przetwarzanie danych  
  - matplotlib / seaborn – wizualizacja  
  - statsmodels / scikit-learn – modelowanie statystyczne
- **Jupyter Notebook** – eksploracja danych i analiza
- **GitHub** – wersjonowanie kodu i prezentacja projektu

---

## Wyniki i wnioski

Szczegółowe wyniki analizy, interpretacja współczynników modelu oraz rekomendacje biznesowe znajdują się w pliku `wnioski.pdf`. Projekt kończy się wskazaniem:
- elastyczności sprzedaży względem wydatków reklamowych
- względnej rentowności poszczególnych kanałów

---

## Ograniczenia i dalsze kroki

- brak pełnych danych o impresjach dla wszystkich kanałów
- zagregowany charakter danych (brak danych użytkownikowych)
- możliwa współliniowość między kanałami

Potencjalne kierunki dalszej analizy:
- model bayesowski MMM
- modele hierarchiczne uwzględniające różnice regionalne