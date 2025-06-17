## Controlli automatici

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

Se vuoi, posso mostrarti un **esempio numerico** con matrici per chiarire questi concetti. Vuoi procedere così?
