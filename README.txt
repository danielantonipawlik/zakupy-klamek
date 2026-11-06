ZAKUPOWIEC — KLAMKI Z CHIN
Statyczna aplikacja HTML/CSS/JS. Bez kont i backendu.

Uruchomienie lokalne:
python3 -m http.server 8769 --bind 127.0.0.1 --directory /workspace/zakupy-klamek
Otwórz http://127.0.0.1:8769/ na tej samej maszynie.

Publikacja:
Opublikuj index.html, style.css, app.js, sw.js i manifest.json w tym samym katalogu dowolnego hostingu HTTPS. Nie wymaga budowania ani zależności npm.
Service Worker zapewnia cache offline po pierwszej instalacji na HTTPS lub localhost. Po zmianach plików podnieś wersję CACHE w sw.js.

Dane:
Wszystkie sprawy, dostawcy, kalkulacje, statusy dokumentów i RFQ są zapisane wyłącznie w localStorage tej przeglądarki pod adresem strony. Nie ma synchronizacji ani kopii w chmurze. Pobieraj JSON. Zmiana adresu wymaga importu JSON. Brak szyfrowania localStorage. Nie wpisuj haseł ani danych płatniczych.

Kalkulator:
Wszystkie koszty w PLN netto, cena za wskazaną jednostkę. Cło domyślnie puste, VAT 23%. Wartość celna: towar + transport Chiny + fracht do UE + ubezpieczenie do UE + ręczna korekta. Agent powinien ustalić korektę m.in. z tytułu form. VAT: (wartość celna + cło + dodatkowe koszty w podstawie VAT) × wpisana stawka. Koszty dodatkowe VAT powinny być już ujęte w kosztach zakupu, nie są ponownie dodawane do kosztu netto. Nie dubluj transportu zawartego w cenie FCA/FOB/CIF. Próbki, formy i inspekcja są ujęte w koszcie partii, lecz nie automatycznie w wartości celnej. Cło i klasyfikacja wymagają urzędowej weryfikacji przed odprawą.

Testy:
node --check app.js i sw.js — OK.
Testy DOM (jsdom, bez przeglądarki) — OK: tworzenie i zapis sprawy, dwóch dostawców i porównanie, rachunek landed cost, ostrzeżenie pustego cła, checklista, RFQ, walidacja importu, etapy, szukanie, mapa, źródła, escaping HTML.
Nie przeprowadzono wizualnego testu w przeglądarce ani rzeczywistego testu offline Service Workera.

Publikacja — stan 6 listopada 2026, Europe/Warsaw:
Nie wdrożono publicznie. gh nie jest zalogowany. Brak zainstalowanych i skonfigurowanych CLI Netlify/Surge/Wrangler/Vercel. Przetestowano oficjalny anonimowy Cloudflare Quick Tunnel; przydzielił URL, lecz połączenie z edge nie zostało ustanowione: TLS handshake EOF i błąd DNS. Proces tunelu zatrzymano, nie ma działającego adresu HTTPS. Lokalny HTTP odpowiada 200. Nie utworzono konta, nie odczytywano poświadczeń, nie kontaktowano dostawców.

Aktualizacja: przycisk „Wczytaj testowe zamówienie” oraz adres ?demo=1.
Kalkulator: kurs waluty (NBP), fracht USD, wybór oferty → PLN.
RFQ: bez ceny docelowej i uwag wewnętrznych; pole „Uwagi dla dostawcy (EN)”.
