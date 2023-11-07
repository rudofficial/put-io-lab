# System aukcyjny

## Wprowadzenie

Specyfikacja wymagań funkcjonalnych w ramach informatyzacji procesu sprzedaży produktów w oparciu o mechanizm aukcyjny. 

## Procesy biznesowe

<a id="bc1"></a>
### BC1: Sprzedaż aukcyjna 

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Opis:** Proces biznesowy opisujący sprzedaż za pomocą mechanizmu aukcyjnego. |

**Scenariusz główny:**
1. [Sprzedający](#ac1) wystawia produkt na aukcję. ([UC1](#uc1))
2. [Kupujący](#ac2) oferuje kwotę za produkt wyższą od aktualnie najwyższej oferty. ([BR1](#br1)) ([UC2](#uc2))
3. [Kupujący](#ac2) wygrywa aukcję ([BR2](#br2))
4. [Kupujący](#ac2) przekazuje należność [Sprzedającemu](#ac1). ([UC3](#uc3))
5. [Sprzedający](#ac1) przekazuje produkt [Kupującemu](#ac2). ([UC4](#uc4))

**Scenariusze alternatywne:** 

2.A. Oferta Kupującego została przebita, a [Kupujący](#ac2) pragnie przebić aktualnie najwyższą ofertę.
* 2.A.1. Przejdź do kroku 2.

3.A. Czas aukcji upłynął i [Kupujący](#ac2) przegrał aukcję. ([BR2](#br2))
* 3.A.1. Koniec przypadku użycia.

---

## Aktorzy

<a id="ac1"></a>
### AC1: Sprzedający

Osoba oferująca towar na aukcji.

<a id="ac2"></a>
### AC2: Kupujący

Osoba chcąca zakupić produkt na aukcji.


## Przypadki użycia poziomu użytkownika

### Aktorzy i ich cele

[Sprzedający](#ac1):
* [UC1](#uc1): Wystawienie produktu na aukcję
* [UC4](#uc4): Przekazanie produktu

[Kupujący](#ac2)
* [BR1](#br1): Złożenie oferty
* [BR2](#br2): Wygranie aukcji
* [UC2](#uc2): Złożenie oferty
* [UC3](#uc3): Przekazanie należności
* [UC4](#uc4): Przekazanie produktu

---
<a id="uc1"></a>
### UC1: Wystawienie produktu na aukcję

**Aktorzy:** [Sprzedający](#ac1)

**Scenariusz główny:**
1. [Sprzedający](#ac1) zgłasza do systemu chęć wystawienia produktu na aukcję.
2. System prosi o podanie danych produktu i ceny wywoławczej.
3. [Sprzedający](#ac1) podaje dane produktu oraz cenę wywoławczą.
4. System weryfikuje poprawność danych.
5. System informuje o pomyślnym wystawieniu produktu na aukcję.

**Scenariusze alternatywne:** 

4.A. Podano niepoprawne lub niekompletne dane produktu.
* 4.A.1. System informuje o błędnie podanych danych.
* 4.A.2. Przejdź do kroku 2.

---

<a id="uc2"></a>
### UC2: Złożenie oferty na aukcji

**Aktorzy:**  [Kupujący](#ac2)

**Scenariusz główny:**
1. [Kupujący](#ac2) zgłasza do systemu chęć kupna produktu na aukcji
2. System prosi o podanie danych i kwotę, którą chce przeznaczyć na produkt.
3. [Kupujący](#ac2) podaje swoje dane oraz kwotę.
4. System weryfikuje poprawność danych.
5. System informuje o pomyślnym złożeniu oferty na aukcji.

**Scenariusze alternatywne:** 

4.A. Podano zbyt niską kwotę za produkt.
* 4.A.1. System informuje, że kwota jest niezgodna z [BR1](#br1).
* 4.A.2 Przejdź do kroku 2.

4.B Podano nieprawidłowe dane osobowe.
* 4.B.1 System informuje o wprowadzeniu nieprawidłowych danych.
* 4.B.2 Przejdź do kroku 2.

---

<a id="uc3"></a>
### UC3: Przekazanie należności

**Aktorzy:** [Kupujący](#ac2)

**Scenariusz główny:**
1. [Kupujący](#ac2) zgłasza do systemu chęć dokonania zapłaty za aukcję.
2. System prosi [Kupującego](#ac2) o podanie danych.
3. [Kupujący](#ac2) wprowadza swoje dane.
4. System weryfikuje poprawność danych i upewnia się, że [Kupujący](#ac2) wygrał aukcję.
5. System podaje [Kupującemu](#ac2) dane [Sprzedającego](#ac1) oraz kwotę, którą musi wpłacić do depozytu.
6. [Kupujący](#ac2) wysyła kwotę za przedmiot.
7. System potwierdza przesłanie pieniędzy.

**Scenariusze alternatywne:** 

4.A. Podano niepoprawne lub niekompletne dane osobiste
* 4.A.1. System informuje o błędnie podanych danych.
* 4.A.2. Przejdź do kroku 2.

4.B [Kupujący](#ac2) nie wygrał aukcji
* 4.B.1 System informuje o przegraniu aukcji.
* 4.B.2 Zakończ działanie.

7.A Po określonym czasie pieniądze nie zostały przesłane
* 7.B.1 System informuje [Kupującego](#ac2) o nie przesłaniu pieniędzy.
* 7.B.2 Przejdź do kroku 6.

---

<a id="uc4"></a>
### UC4: Przekazanie produktu

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Scenariusz główny:**
1. System informuje [Sprzedającego](#ac1) o przekazaniu pieniędzy za produkt.
2. System przekazuje [Sprzedającemu](#ac1) dane [Kupującego](#ac2).
3. [Sprzedający](#ac1) wysyła produkt [Kupującemu](#ac2).
4. System informuje [Kupującego](#ac2) o wysłaniu produktu.
5. [Kupujący](#ac2) potwierdza odbiór produktu.
6. System przesyła pieniądze z depozytu do [Sprzedającego](#ac1).

**Scenariusze alternatywne:** 

1.A Pieniądze za produkt nie zostały przesłane
* 1.A.1 System informuje o niezapłaceniu za produkt.
* 1.A.2 System informuje [Kupującego](#ac2), że należy wysłać pieniądze.
* 1.A.3 Przejdź do [UC3](#uc3).

4.A Produkt nie został wysłany
* 4.A.1 System informuje o niewysłaniu produktu.
* 4.A.2 System informuje [Sprzedającego](#ac1), że należy wysłać paczkę
* 4.A.3 Przejdź do kroku 2.

4.B Po określonym czasie produkt nie został wysłany
* 4.B.1 System informuje [Kupującego](#ac2) o tym, że [Sprzedający](#ac1) wciąż nie wysłał paczki.
* 4.B.2 System zwraca pieniądze [Kupującemu](#ac2).
* 4.B.3 Koniec przypadku użycia.

5.A Produkt nie spełnia wymogów aukcji
* 5.A.1 [Kupujący](#ac2) informuje o nie spełnienu wymogów przedmiotu kupionego.
* 5.A.2 System zwraca pieniądze [Kupującemu](#ac2).
* 5.A.3 [Kupujący](#ac2) zwraca paczkę [Sprzedającemu](#ac1).
* 5.A.4 Koniec przypadku użycia.

5.B Produkt nie dotarł do celu
* 5.B.1 [Kupujący](#ac2) informuje system, że paczka do niego nie dotarła.
* 5.B.2 System kontaktuje się z firmą kurierską i stara się rozwiązać problem.
* 5.B.3 Koniec przypadku użycia.

---

## Obiewkty biznesowe (inaczje obiekty dziedzinowe lub informatycjne)

### BO1: Aukcja

Aukcja jest formą zawierania transakcji kupna-sprzedaży, w której Sprzedający określa cenę wywoławczą produktu, natomiast Kupujący mogą oferować własną ofertę zakupu każdorazowo proponując kwotę wyższą od aktualnie oferowanej kwoty. Aukcja kończy się po upływie określonego czasu. Jeśli złożona została co najmniej jedna oferta zakupy produkt nabywa ten Kupujący, który zaproponował najwyższą kwotę. 

### BO2: Produkt

Fizyczny lub cyfrowy obiekt, który ma zostać sprzedany w ramach aukcji.

## Reguły biznesowe

<a id="br1"></a>
### BR1: Złożenie oferty

Złożenie oferty wymaga zaproponowania kwoty wyższej niż aktualnie oferowana o minimum 1,00 PLN.


<a id="br2"></a>
### BR2: Rozstrzygnięcie aukcji

Aukcję wygrywa ten z [Kupujący](#ac2)ch, który w momencie jej zakończenia (upłynięcia czasu) złożył najwyższą ofertę.

## Macierz CRUDL


| Przypadek użycia                                  | Aukcja | Produkt | ... |
| ------------------------------------------------- | ------ | ------- | --- |
| UC1: Wystawienia produktu na aukcję               |    C   |    C    | ... |
| UC2: Złożenie oferty na aukcji                                               |  U, R   |  U, R    | ... |
| UC3: Przekazanie należności |
| UC4: Przekazanie produktu | | D
