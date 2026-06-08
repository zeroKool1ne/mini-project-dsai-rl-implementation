# Präsentation: Reinforcement Learning — Grid World
**10 Minuten | DNL**

---

## 1. Problem Introduction — 2 Minuten

**Was habe ich gewählt?**
> Grid World — ein Agent navigiert durch ein 10x10-Labyrinth von Startpunkt zu Ziel, ohne gegen Wände zu laufen.

**Was sagen, was zeigen:**
- "Ich hab Grid World gewählt, weil es das intuitivste Problem ist — man sieht direkt was der Agent tut."
- "Das Labyrinth ist eine 10x10-Matrix. Nullen sind freie Felder, Einsen sind Wände."
- "Der Agent startet oben links, Ziel ist unten rechts."
- Notebook zeigen: **Zelle 1** (Maze-Array)

**Warum ist das interessant für RL?**
> "Der Agent hat keine Karte — er weiß nicht wo das Ziel ist. Er muss es durch Trial & Error selbst herausfinden."

---

## 2. Algorithm Explanation — 3 Minuten

**Welcher Algorithmus?**
> Q-Learning

**Wie funktioniert es — einfach erklärt:**
> "Stell dir vor du lernst ein neues Videospiel. Am Anfang drückst du random Knöpfe. Mit der Zeit merkst du: wenn ich hier links gehe, komme ich näher ans Ziel. Diese Erfahrung speicherst du."

**Das ist genau Q-Learning:**
- Der Agent speichert für jeden Zustand und jede Aktion einen Wert in der **Q-Tabelle**
- Gute Aktionen → höherer Wert
- Schlechte Aktionen → niedrigerer Wert
- Mit der Zeit lernt die Tabelle den besten Weg

**Key Parameters kurz nennen:**
| Parameter | Was es macht |
|---|---|
| `alpha = 0.1` | Wie schnell er lernt |
| `gamma = 0.9` | Zukünftige Belohnungen zählen fast so viel wie sofortige |
| `epsilon = 0.5 → 0.01` | Startet mit viel Exploration, wird mit der Zeit gezielter |

**Belohnungen:**
- Ziel erreicht: **+50**
- Gegen Wand: **-10**
- Jeden Schritt: **-1** (damit er den kürzesten Weg sucht)

---

## 3. Implementation Demo — 3 Minuten

**Was zeigen, was sagen:**

1. Notebook öffnen, **Zelle 2** zeigen (Parameter)
   > "Hier setze ich alle Parameter. Die Q-Tabelle hat die Form 10x10x4 — für jedes Feld, jede der 4 Richtungen."

2. **Zelle 3** zeigen (choose_action)
   > "ε-greedy: Mit epsilon-Wahrscheinlichkeit zufällig, sonst beste bekannte Aktion."

3. **Zelle 4** — Training laufen lassen
   > "5000 Episoden. Die Formel aktualisiert nach jeder Aktion die Q-Tabelle."

4. **Zelle 6** — Plot Maze zeigen
   > "Das ist der gelernte Pfad — der Agent hat selbst herausgefunden wie er durchkommt."

5. **Zelle 7** — Rewards-Plot zeigen
   > "Hier sieht man wie die Belohnungen mit der Zeit steigen — der Agent wird besser."

---

## 4. Results and Analysis — 2 Minuten

**Wie gut hat es funktioniert?**
> "Der Agent findet nach dem Training zuverlässig einen Weg durch das Labyrinth. Die Learning Curve zeigt einen klaren Aufwärtstrend."

**Herausforderungen:**
> "Epsilon-Decay war tricky — zu schnell und der Agent exploriert zu wenig und steckt in schlechten Lösungen fest. Zu langsam und er konvergiert nicht."

**Was würde ich anders machen?**
> "Ich würde mehr Episoden trainieren und verschiedene Epsilon-Decay-Raten vergleichen. Oder das Labyrinth größer machen."

---

## 5. Resources & Key Insights — 1 Minute

**Ressourcen:**
- GeeksForGeeks — What is Reinforcement Learning
- OpenAI Gym Dokumentation

**Key Insight:**
> "Der interessanteste Teil war das Exploration-Exploitation-Dilemma. Zu viel Exploration = der Agent lernt nicht. Zu wenig = er findet nie den besten Weg. Das gilt übrigens auch im echten Leben."

---

## Q&A — mögliche Fragen & Antworten

**"Warum Q-Learning und nicht SARSA?"**
> "Q-Learning ist off-policy — es lernt die optimale Policy unabhängig davon was der Agent gerade tut. Einfacher zu implementieren für den Anfang."

**"Was ist der Unterschied zu Deep Learning?"**
> "Bei Q-Learning speichern wir eine Tabelle — funktioniert gut bei kleinen Zustandsräumen. Bei Deep Q-Learning ersetzt ein neuronales Netz die Tabelle — nötig wenn der Zustandsraum riesig ist z.B. bei Atari-Spielen."

**"Warum epsilon am Anfang 0.5?"**
> "Am Anfang weiß der Agent nichts — er soll viel ausprobieren. Mit der Zeit sinkt epsilon auf 0.01, er nutzt dann hauptsächlich gelerntes Wissen."

**"Könnte der Agent auch scheitern?"**
> "Ja — wenn epsilon zu schnell fällt oder die Rewards falsch gesetzt sind, konvergiert er nicht. Das ist auch in echten RL-Projekten ein häufiges Problem."
