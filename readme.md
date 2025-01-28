# Lernsituation: Analyse von MBA-Entscheidungsdaten mit Pandas  

---

## **Lernziele**  
- CSV-Daten mit Pandas laden und grundlegende Inspektionen durchführen.  
- Selektiven Datenzugriff mit `iloc` und `loc` beherrschen.  
- Bedingte Filterung (**Boolean Indexing**) anwenden.  
- Daten gruppieren und aggregieren.  
- Transformationen mit `map`, `apply` und `applymap` durchführen.  
- String-Operationen für Textdaten nutzen.  
- Praktische Analysen mit realitätsnahen Fragestellungen umsetzen.  

---

## **Einführung**  
Der Datensatz enthält Informationen von Bachelor-Absolvent*innen, die sich für oder gegen einen MBA entscheiden. Analysiert werden demografische, akademische und berufliche Faktoren sowie Karriereziele.  


---

## **Aufgaben**  

---

### **1. Daten laden und explorieren**  
**Aufgaben:**  
1. Lade die Datei `mba_decisions.csv` in einen DataFrame.  
2. Zeige die **ersten 3 Zeilen** und die **letzten 2 Zeilen** an.  
3. Gib die **Anzahl der Zeilen/Spalten** und die **Datentypen** aller Spalten aus. 
4. Zeige eine Übersicht aller Spalten mit `.info()` an 

**Hilfestellungen:**  
- Verwende `pd.read_csv()` zum Einlesen.  
- Nutze `.head(3)` und `.tail(2)` für die ersten/letzten Zeilen.  
- Die Dimensionen erhältst du über `.shape`, Datentypen mit `.dtypes`.  

---

### **2. Deskriptive Statistiken und Fehlende Werte**  
**Aufgaben:**  
1. Berechne den **Median** des `Undergraduate GPA` und das **Maximum** des `GRE/GMAT Score`.  
2. Zähle, wie viele Personen **keine Management-Erfahrung** haben (`Has Management Experience`).  
3. Überprüfe, ob die Spalte `GRE/GMAT Score` **fehlende Werte** enthält.  

**Hilfestellungen:**  
- Nutze `.median()` und `.max()` für Berechnungen.  
- Filtere mit `df[SERIES == VALUE]` und zähle die Zeilen mit `.shape[0]`.  
- Fehlende Werte: `SERIES.isna().sum()`.  

---

### **3. Selektiver Datenzugriff mit `iloc` und `loc`**  
**Aufgaben:**  
1. Extrahiere die Zeilen **5 bis 15** und die Spalten **Alter, GPA und Gehalt** mit `iloc`.  
2. Wähle alle Personen aus, die **über 100.000 USD** verdienen, und zeige nur ihre **Jobtitel** und **MBA-Finanzierung** an.  

**Hilfestellungen:**  

* iloc nutzt Index-Positionen: `df.iloc[0:10, 0:5]` für Zeilen 0–9 und Spalten 0–4.

* loc filtert mit Bedingungen:
  Beispiel: `df.loc[df['Gender'] == 'Female', ['Age', 'Undergraduate Major']]`


---
### 4. Boolean Indexing für komplexe Filter

1. Filtere Personen mit **GPA ≥ 3.5** und **Networking Importance ≥ 8**.

2. Finde alle, die sich für einen **Online-MBA** entscheiden und **Entrepreneurial Interest ≥ 7** haben.


---
### 5. Gruppieren und Aggregieren

1. Berechne die durchschnittliche Gehaltserhöhung (**Post-MBA vs. Pre-MBA**) pro MBA Funding Source.

2. Ermittle den höchsten **GRE/GMAT** Score pro Undergraduate Major.

**Hilfestellungen:**

* Gruppiere mit `groupby('MBA Funding Source')` und berechne .`mean()`.

* Für den höchsten Score: groupby und dann `.max()`.

---
### 6. Daten transformieren mit map und apply


1. Wandle Has Management Experience in binäre Werte (1 für "Ja", 0 für "Nein") um.

2.  Erhöhe das Expected Post-MBA Salary um 5% für alle mit Undergraduate Major = "Business".

**Hilfestellungen:**

* map mit einem Dictionary:
  `SERIES.map({'Yes': 1, 'No': 0})`
* apply mit Lambda-Funktion:
  `SERIES.apply(lambda x: x * 1.05)`

---
### 7. String-Operationen für Textanalyse
1. Zähle, wie oft "Entrepreneurship" in Reason for MBA vorkommt.
2. Extrahiere den ersten Buchstaben aus Undergraduate Major (z. B. "E" für "Engineering").

**Hilfestellungen:**

* Nutze str.contains() für die Suche


---
### 8. Praxisnahe Analyse

1. Vergleiche das durchschnittliche erwartete Gehalt zwischen Personen mit und ohne Management-Erfahrung.

2. Ermittle die TOP 3 Gründe für einen MBA (Reason for MBA).

**Hilfestellungen:**

* Nutze .value_counts().head(3) für die häufigsten Gründe.
