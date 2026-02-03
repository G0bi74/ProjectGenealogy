# Project Genealogy

## 📋 O projekcie

Projekt Genealogy to aplikacja napisana w języku Java, która służy do zarządzania i wizualizacji drzew genealogicznych rodzin. Projekt został stworzony jako **zadanie edukacyjne mające na celu rozwinięcie umiejętności programowania** oraz praktyczne zastosowanie zaawansowanych koncepcji programowania obiektowego.

## 🎯 Cele edukacyjne

Ten projekt był realizowany w ramach nauki programowania i miał na celu:
- Rozwijanie umiejętności programowania w języku Java
- Praktyczne zastosowanie programowania obiektowego
- Naukę obsługi plików (CSV, pliki binarne)
- Implementację walidacji danych i obsługi wyjątków
- Wykorzystanie wyrażeń lambda i strumieni (Java Streams API)
- Integrację z zewnętrznymi narzędziami (PlantUML)
- Praktyczne zastosowanie wzorców projektowych

## ✨ Funkcjonalności

### 1. Wczytywanie danych genealogicznych
- Import danych z pliku CSV zawierającego informacje o osobach (imię, nazwisko, daty urodzenia i śmierci, rodzice)
- Walidacja poprawności danych podczas wczytywania

### 2. Walidacja danych
Aplikacja sprawdza poprawność danych i wykrywa:
- **Ujemny czas życia** - sytuacje, gdy data śmierci jest wcześniejsza niż data urodzenia
- **Niejednoznaczność osób** - duplikaty osób o tych samych imionach i nazwiskach
- **Niedozwolony wiek rodzicielski** - przypadki, gdy rodzic był zbyt młody (< 15 lat) lub zmarł przed urodzeniem dziecka
- **Niezdefiniowanych rodziców** - odniesienia do osób, które nie istnieją w bazie danych

### 3. Operacje na danych
- Filtrowanie osób po nazwisku
- Sortowanie osób według daty urodzenia
- Sortowanie osób według długości życia (malejąco)
- Wyszukiwanie najstarszej żyjącej osoby

### 4. Wizualizacja drzewa genealogicznego
- Generowanie diagramów UML przy użyciu PlantUML
- Eksport drzewa genealogicznego do formatu graficznego
- Możliwość kolorowania obiektów na podstawie warunków (np. osoby żyjące)
- Wiele wersji algorytmów generowania diagramów z różnymi możliwościami dostosowania

### 5. Serializacja
- Zapisywanie danych do plików binarnych
- Wczytywanie danych z plików binarnych

## 📁 Struktura projektu

```
ProjectGenealogy/
├── src/
│   ├── Main.java                        # Główna klasa uruchamiająca aplikację
│   ├── Person.java                      # Klasa reprezentująca osobę
│   ├── PersonWithParentsNames.java      # Pomocnicza klasa do parsowania CSV
│   ├── PlantUMLRunner.java              # Klasa do generowania diagramów UML
│   ├── AmbiguousPersonException.java    # Wyjątek dla niejednoznacznych osób
│   ├── NegativeLifespanException.java   # Wyjątek dla ujemnego czasu życia
│   ├── ParentingAgeException.java       # Wyjątek dla niewłaściwego wieku rodzicielskiego
│   └── UndefinedParentException.java    # Wyjątek dla niezdefiniowanych rodziców
├── family.csv                            # Przykładowe dane rodziny
├── out_uml/                              # Folder z wygenerowanymi diagramami UML
├── out/                                  # Folder z plikami skompilowanymi
└── README.md                             # Ten plik
```

## 🚀 Jak uruchomić

### Wymagania
- Java JDK 8 lub nowszy
- PlantUML (opcjonalnie, do generowania diagramów)

### Uruchomienie
1. Skompiluj projekt:
```bash
javac src/*.java -d out
```

2. Uruchom aplikację:
```bash
java -cp out Main
```

## 📊 Format pliku CSV

Plik `family.csv` powinien mieć następującą strukturę:
```csv
imię i nazwisko,data urodzenia,data śmierci,rodzic,rodzic
Marek Kowalski,15.05.1899,25.06.1957,,
Ewa Kowalska,03.11.1901,05.03.1990,,
Anna Dąbrowska,07.02.1930,22.12.1991,Ewa Kowalska,Marek Kowalski
```

- Daty w formacie: `dd.MM.yyyy`
- Puste pole śmierci oznacza osobę żyjącą
- Można podać 0, 1 lub 2 rodziców

## 🛠️ Użyte technologie i koncepcje

- **Java** - główny język programowania
- **Java Collections Framework** - ArrayList, List, Set, Map
- **Java Streams API** - przetwarzanie kolekcji, filtrowanie, sortowanie
- **Lambda expressions** - wyrażenia lambda i referencje do metod
- **Function, Predicate, Consumer** - interfejsy funkcyjne
- **Exception handling** - własne klasy wyjątków
- **File I/O** - BufferedReader, FileReader, ObjectOutputStream
- **PlantUML** - generowanie diagramów UML
- **LocalDate** - obsługa dat

## 📝 Przykłady użycia

### Filtrowanie po nazwisku
```java
List<Person> filtered = Person.filterByName(people, "Kowalski");
```

### Sortowanie według daty urodzenia
```java
List<Person> sorted = Person.sortByBirth(people);
```

### Wyszukiwanie najstarszej żyjącej osoby
```java
Person oldest = Person.findOldestPersonAlive(people);
```

### Generowanie drzewa genealogicznego
```java
PlantUMLRunner.generate(Person.toPlantUMLTreeV1(people), "out_uml", "family");
```

## 👨‍💻 Autor

Projekt stworzony jako zadanie edukacyjne w celu rozwijania umiejętności programowania w języku Java.

## 📄 Licencja

Projekt edukacyjny - wolny do użytku w celach edukacyjnych i nauki programowania
