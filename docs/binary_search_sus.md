<a target="_blank" href="https://colab.research.google.com/github/Jacques-Mock-Schindler/Studienleistung6/blob/main/docs/binary_search_sus.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

## Vorbereitungen

Als Vorbereitung für die Aufgaben in diesem Arbeitsblatt wird in der
folgenden Zelle die erforderliche Python Library `random` geladen.


```python
import random
```

# Binary Search

In diesem Notzibuch sollen zwei Suchalgorithmen einander gegenüber
gestellt werden.

## Lineare Suche

Gegeben sei eine Python Liste mit 16 Werten in beliebiger Reihenfolge.
Gesucht ist ein Verfahren, mit dem überprüft werden kann, ob ein
beliebiger Wert in dieser Python Liste vorkommt und wenn ja, mit welchem
Index. 

Die einfachste Lösung für dieses Problem ist es, ein Element nach dem
anderen auf seine Übereinstimmung mit dem gesuchten Wert zu überprüfen.
Wird das Element gefunden, wird der Index zurückgegeben; wird das
Element nicht gefunden -1.  
Das hier beschriebene Vorgehen heisst lineare Suche.  

In der Folge soll mit der hier gegebenen Python Liste `sequenz`
gearbeitet werden.  


```python
sequenz = [17, 35, 42, 24, 21, 36, 75, 34, 12, 35, 23, 69, 34, 28, 
           86, 98]
```

### Aufgabe zur Implementierung der linearen Suche

Implementieren Sie in der folgenden Zelle die lineare Suche als Funktion
in Python.  
Testen Sie Ihre Implementation mit den Werten 1, 17, 98 und 100 an der
Python Liste `sequenz`.


```python
def linear_search(seq, x):
    # TODO: implementieren Sie die Funktion
    pass
```


```python
# Zu testende Werte
print(linear_search(sequenz, 1))
print(linear_search(sequenz, 17))
print(linear_search(sequenz, 98))
print(linear_search(sequenz, 100))
```

### Aufgabe 1 zur Effizienz der linearen Suche

Mit den folgenden Aufgaben soll aufgezeigt werden, wie es um die
Effizienz der linearen Suche steht.

Die Python Liste `sequenz` beinhaltet 16 zufällig gewählte natürliche
Zahlen von 1 bis 100.  
Wählen Sie 100 mal zufällig eine Zahl aus `sequenz` aus und 
suchen Sie mit Hilfe einer Schlaufe in `sequenz` nach diesen zufällig
gewählten Zahlen.   
Wie viele Vergleiche müssen Sie im Durchschnitt über diese 100
Suchdurchläufe vornehmen?


```python
# TODO: nutzen Sie die Python Library, um die Testwerte zu generieren
# und führen Sie die Tests in dieser Zelle durch
```

### Aufgabe 2 zur Effizienz der linearen Suche

Wählen Sie zufällig 100 natürliche Zahlen aus den Zahlen von 1 bis 100
(ziehen mit Zurücklegen) und 
suchen Sie mit Hilfe einer Schlaufe in `sequenz` nach diesen zufällig
gewählten Zahlen.   
Wie viele Vergleiche müssen Sie jetzt im Durchschnitt über diese 100
Suchdruchläufe vornehmen?


```python
# TODO: nutzen Sie die Python Library, um die Testwerte zu generieren
# und führen Sie die Tests in dieser Zelle durch
```

## Binäre Suche

Eine erste Verbesserung der Effizienz der Suche ergibt sich, wenn die zu
durchsuchende Sequenz in aufsteigender Reihenfolge sortiert ist. In der
folgenden Zelle wird eine sortierte Kopie `sequenz_sortiert` von
`sequenz` erstellt.


```python
sequenz_sortiert = sequenz.copy()
sequenz_sortiert.sort()
```

### Aufgabe

Wie kann mit möglichst wenigen Vergleichen überprüft werden, ob ein Wert
im Bereich der Python Liste `sequenz_sortiert` liegt?  
Überprüfen Sie Ihre Implementation mit den Werten 10, 12, 98 und 100.


```python
def in_range(seq, x):
    # TODO: implementieren Sie den Test
    pass
```


```python
# Werte für die Überprüfung Ihrer Implementation
print(in_range(sequenz_sortiert, 10))
print(in_range(sequenz_sortiert, 12))
print(in_range(sequenz_sortiert, 98))
print(in_range(sequenz_sortiert, 100))
```

### Aufgabe

Entwerfen Sie basierend auf dem Konzept von *divide and conquer* einen
Algorithmus für die Suche in einer geordneten Sequenz in dem Sie das
Grundproblem in kleinere Teilprobleme zerlegen. Denken Sie dabei daran,
allfällige Zufallslösungen nicht zu verschwenden.

Hier ist Platz für Ihren Entwurf. Eine mögliche Darstellung des
Entwurfes kann ein Flussdiagramm sein. Ein solches kann von Hand
gezeichnet werden und als Bild hier eingefügt werden.

### Aufgabe

Mathematisch formal kann die binäre Suche folgendermassen dargestellt werden:

$$
\footnotesize
\text{BinarySearch}(A, x, \text{low}, \text{high}) = 
\left\{
    \begin{array}{lll}
        -1, & \text{high} < \text{low} & \text{Basisfall 1}\\
        \text{mid}, & A[\text{mid}] = x & \text{Basisfall 2}\\
        \text{BinarySearch}(A, x, \text{low}, \text{mid} - 1), 
        & x < A[\text{mid}] & \text{Rekursionsfall links}\\
        \text{BinarySearch}(A, x, \text{mid} + 1, \text{high}), 
        & x > A[\text{mid}] & \text{Rekursionsfall rechts} \\
    \end{array}
\right.
$$

Wobei $A$ eine sortierte Python Liste (dynamisches Array), $x$ der gesuchte Wert, $low$ der
Anfangsindex und $high$ der Endindex des Suchbereichs ist. Der Index
$mid$ wird als $\lfloor (\text{low} + \text{high}) / 2 \rfloor$
berechnet.

Implementieren Sie die binäre Suche als Funktion in Python so, wie sie mathematisch formal
dargestellt worden ist.  
Überprüfen Sie auch diese Implementation mit den Werten 10, 12, 98 und 100.


```python
def binary_search(seq, x, lo=0, hi=None):
    # TODO: implementieren Sie die binäre Suche
    pass
```


```python
# Werte zur Überprüfung Ihrer Implementierung
print(binary_search(sequenz_sortiert, 10))
print(binary_search(sequenz_sortiert, 12))
print(binary_search(sequenz_sortiert, 98))
print(binary_search(sequenz_sortiert, 100))
```

### Aufgabe

Wie viele Vergleiche erfordert die binäre Suche in der Python Liste
`sequenz_sortiert` für die Werte 10, 12, 98 und 100?

Um besser Zählen zu können, können die einzelnen Schritte beim
Durchlaufen der Funktion `binary_search()` als Tabelle dargestellt
werden.



Erstellen Sie hier die Tabellen für die vier Werte. Sie können die
Tabellen auch von Hand zeichnen und hier ein Bild einfügen.

### Aufgabe

In welcher Beziehung steht die Zahl 5 zur Zahl 16? Eine Hilfe ergibt
sich möglicherweise aus der Information, dass bei einer Sequenz mit 8
Elementen im Maximum 4 Vergleiche und bei einer solchen mit 32 Elementen
6 Vergleiche erforderlich sind.



Hier ist Platz für Ihre Antwort

### Zusammenfassung binäre Suche

Hier hat es Platz für Ihre Zusammenfassung der Schlussbesprechung.
