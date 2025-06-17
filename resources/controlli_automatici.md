# Controlli automatici

La **teoria dei controlli automatici** si basa su diversi teoremi fondamentali che riguardano concetti come **raggiungibilità** (o *controllabilità*) e **osservabilità**. Eccoli spiegati in modo chiaro:

---

### 📌 1. **Teorema della raggiungibilità (o controllabilità)**

> **Definizione**: Un sistema dinamico è **completamente controllabile** (o raggiungibile) se, partendo da uno stato qualsiasi, è possibile raggiungere qualsiasi altro stato in tempo finito tramite un opportuno ingresso di controllo.

#### Teorema (Kalman – controllabilità):

Per un sistema lineare continuo del tipo

$$
\dot{x}(t) = A x(t) + B u(t)
$$

il sistema è **controllabile** se e solo se la **matrice di controllabilità**

$$
\mathcal{C} = [B \quad AB \quad A^2B \quad \dots \quad A^{n-1}B]
$$

ha rango pieno (cioè $\text{rank}(\mathcal{C}) = n$, dove $n$ è la dimensione dello stato $x$).

---

### 📌 2. **Teorema dell’osservabilità**

> **Definizione**: Un sistema è **osservabile** se, conoscendo l’uscita del sistema in un intervallo finito di tempo, è possibile ricostruire lo stato iniziale del sistema.

#### Teorema (Kalman – osservabilità):

Per il sistema

$$
\dot{x}(t) = A x(t) + B u(t), \quad y(t) = C x(t)
$$

il sistema è **osservabile** se e solo se la **matrice di osservabilità**

$$
\mathcal{O} = \begin{bmatrix}
C \\
CA \\
CA^2 \\
\vdots \\
CA^{n-1}
\end{bmatrix}
$$

ha rango pieno ($\text{rank}(\mathcal{O}) = n$).

---

### 📌 3. **Dualità tra controllabilità e osservabilità**

Esiste una **relazione di dualità** tra i due concetti:
Un sistema $(A, B)$ è controllabile ⇔ il sistema duale $(A^T, C^T)$ è osservabile.

---

## 🎯 **Sistema della levitazione magnetica (MagLev)**

L'esempio riguarda la **"Magnetic Levitation"** (o **MagLev**), cioè il **sistema di levitazione magnetica di una pallina**. È un esempio perfetto per parlare di **controllabilità**, **osservabilità** e **stabilità**.

### 🔹 Descrizione del sistema:

Una **sferetta metallica** (spesso una biglia ferromagnetica) è sospesa verticalmente grazie alla forza di un **elettromagnete** posto sopra di essa. Il campo magnetico viene controllato regolando la **corrente** in ingresso al magnete. L'obiettivo è mantenere la pallina in equilibrio **senza che cada né venga risucchiata nel magnete**.

---

## 🧮 Modello matematico (semplificato)

* **Stato**:
  $x_1 =$ posizione verticale della pallina
  $x_2 =$ velocità verticale della pallina

* **Ingresso**:
  $u =$ corrente che alimenta l’elettromagnete

* **Equazioni del moto** (non lineari, ma linearizzabili):

  $$
  m\ddot{x} = mg - \frac{k u^2}{x^2}
  $$

  dove:

  * $m$ è la massa della pallina
  * $g$ è la gravità
  * $k$ è una costante legata al campo magnetico

---

## ⚙️ Linearizzazione attorno all’equilibrio

Supponiamo che la pallina sia sospesa in un punto di equilibrio $x_e$ con corrente $u_e$. Linearizzando attorno a questi valori, otteniamo un sistema lineare del tipo:

$$
\dot{x}(t) = A x(t) + B u(t), \quad y(t) = C x(t)
$$

con matrici:

$$
A = \begin{bmatrix}
0 & 1 \\
a & 0
\end{bmatrix}, \quad
B = \begin{bmatrix}
0 \\
b
\end{bmatrix}, \quad
C = \begin{bmatrix}
1 & 0
\end{bmatrix}
$$

dove $a < 0$, cioè il sistema è **instabile in assenza di controllo**.

---

## ✅ **Controllabilità del sistema MagLev**

Per verificare se possiamo **stabilizzare** la pallina, calcoliamo la **matrice di controllabilità**:

$$
\mathcal{C} = [B \quad AB] =
\begin{bmatrix}
0 & b \\
b & 0
\end{bmatrix}
$$

Questa matrice ha determinante $-b^2 \ne 0$, quindi **ha rango pieno** ⇒
📌 **Il sistema è completamente controllabile.**

---

## 👀 **Osservabilità del sistema MagLev**

Verifichiamo se possiamo **osservare lo stato** (posizione e velocità) a partire dalla sola misura della posizione $y = x_1$:

$$
\mathcal{O} = \begin{bmatrix}
C \\
CA
\end{bmatrix} =
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}
$$

📌 Anche questa ha rango pieno ⇒
**Il sistema è completamente osservabile.**

---

## ⚠️ Conclusione e altri temi

Il sistema MagLev **è controllabile** e **osservabile**, ma è **instabile** in forma naturale.
Solo tramite un **controllo automatico** (es. un regolatore a retroazione) possiamo mantenerlo in equilibrio.

---

Si potrebbe procedere con:

* Come si progetta un **controllore LQR**
* Come si usa un **osservatore di stato** (es. osservatore di Luenberger)
* Oppure generarti un piccolo **grafico o simulazione** del comportamento

