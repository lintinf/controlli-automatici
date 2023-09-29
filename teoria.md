---
documentclass: extarticle
geometry: margin=1.5cm
fontsize: 14pt
output: pdf_document
papersize: a4
---

**Presentare e dimostrare formule di inversione per la sintesi in frequenza delle reti correttrici.**

Le reti correttrici sono una tipologia di controllori a struttura fissa, vengono progettati per ”correggere” il comportamento dinamico di anello di retroazione, per esempio: rete integratice, rete derivatrice, rete ritardatrice e rete antipatrice.

**DEF**. $f : D \rightarrow f(D)$ è BIETTIVA (e quindi invertibile) e la funzione inversa $f^{-1} : f(D) \rightarrow D(M, \phi) \rightarrow (\alpha, \tau\omega)$ è definita da:

$$ 
\alpha = \frac{M \cos(\phi-1)}{M(M-cos(\phi))} 
\quad
\tau\omega = \frac{M-\cos(\phi)}{\sin(\phi)}
$$

Dove $D := (0,1) \times (0, \infty)$, $M$ è il modulo della risposta armonica $\frac{a+j\tau\omega}{1+j\alpha\tau\omega}$ e $\phi$ è la fase della risposta armonica.

**DIM**. Per la dimostrazione bisogna prima introdurre il **lemma**: siano $M, \phi, \alpha, x$ valori reali con modulo maggiore di 1 e $\sin \phi \ne 0$, allora le seguenti relazioni sono equivalenti:

$$
Me^{j\phi} = \frac{1+jx}{1+j\alpha x}
$$

$$
\begin{cases}
\alpha = \frac{M \cos \phi - 1}{M(M - \cos \phi)} \\
x = \frac{M - \cos \phi}{\sin \phi}
\end{cases}
$$

$f : D \rightarrow f(D)$ è SURIETTIVA per la definizione di codominio.

$f : D \rightarrow f(D)$ è INIETTIVA. Sia $(M, \phi) \in f(D)$ quindi $M > 1$ e $\phi \in (0, \frac{\pi}{2})$ ed esistono $\alpha \in (0,1), \tau\omega > 0$ tali che $Me^{j\phi} = \frac{1+j\tau x}{1+j\alpha\tau x}$

Per il lemma precedente valgono:

- $\alpha = \frac{M \cos \phi - 1}{M(M - \cos \phi)}$
- $\tau\omega = \frac{M - \cos \phi}{\sin \phi}$

e quindi questi valori sono gli unici per i quali $f(\alpha, \tau\omega) = (M, \phi)$

(inserire immagine)

**Rete ANTICIPATRICE con margine DI FASE $M_f$**

a. Scegliere $\omega _0$ affinché con $\phi _0 := M_f - \arg L(j\omega_{0}) - \pi$ valga $(\frac{1}{|L(j\omega _0)|}, \phi _0) \in f(D)$, quindi $\cos(\phi _0) > |L(j\omega _0)|$
b. Definiti $M = \frac{a}{|L(j\omega _0)|}$ e $\phi := \phi _0$ segue $\tau = \frac{M - \cos \phi}{\omega _ 0 \sin \phi}$ e $\alpha = \frac{M \cos \phi -1}{M(M - \cos \phi)}$

**Rete ANTICIPATRICE con margine DI AMPIEZZA $M_a$**

a. Scegliere $\omega _0$ affinché con $\phi _0 := - \arg L(j\omega _ 0) - \pi$ valga $(\frac{1}{M_a |L(j\omega _0)|},\phi _0) \in f(D)$, quindi $\cos(\phi _0) > M_a |L(j\omega _0)|$
b. Definiti $M =\frac{1}{M_a |L(j\omega _0)|}$ e $\phi := \phi _0$ segue $\tau = \frac{M - \cos \phi}{\omega _ 0 \sin \phi}$ e $\alpha = \frac{M \cos \phi -1}{M(M - \cos \phi)}$

**Rete RITARDATRICE con margine DI FASE $M_f$**

a. Scegliere $\omega _0$ affinché con $\phi _0 := \arg L(j\omega _0) + \pi - M_f$ valga $(|L(j\omega _0)|), \phi _0 \in f(D)$, quindi $\cos(\phi _0) > \frac{1}{|L(j\omega _0)|}$
b. Definiti $M = |L(j\omega _0)|$ e $\phi := \phi _0$ segue $\tau = \frac{M - \cos \phi}{\omega _ 0 \sin \phi}$ e $\alpha = \frac{M \cos \phi -1}{M(M - \cos \phi)}$

**Rete RITARDATRICE con margine DI AMPIEZZA $M_a$**

a. Scegliere $\omega _0$ affinché con $\phi _0 := \arg L(j\omega _0) + \pi$ valga $(M_a |L(j\omega _0)|), \phi _0 \in f(D)$, quindi $\cos(\phi _0) > \frac{1}{M_a |L(j\omega _0)|}$
b. Definiti $M = M_a|L(j\omega _0)|$ e $\phi := \phi _0$ segue $\tau = \frac{M - \cos \phi}{\omega _ 0 \sin \phi}$ e $\alpha = \frac{M \cos \phi -1}{M(M - \cos \phi)}$

**Formule di antitrasformazione zeta, integrale a curva chiusa per determinare $X(k)$ sapendo che $X(k) = \mathcal{Z}[x(k)]$**

Sia $X(z)$ la trasformata zeta di $x(k)$, allora:

$$
x(k) = \frac{1}{2\pi} \oint_{\gamma} X(z)z^{k-1}dz
$$

dove $\gamma$ è una curva chiusa che racchiude tutti i poli di $X(z)$, percorsa in senso antiorario, che circonda la regione di convergenza di $X(z)$, cioé $\mathcal{Z}[x(k)]$.

**DIM**:

$$
\mathcal{Z}^{-1}[X(z)] = \frac{1}{2\pi j} \oint_{\gamma} X(z)z^{k-1}dz =
\frac{1}{2\pi j} \oint_{\gamma} (\sum_{i=0}^{+\infty}x(i)z^{-i})z^{k-1}dz = 
$$
$$
= \frac{1}{2\pi j} \sum_{i=0}^{+\infty}x(i) \oint_{\gamma} z^{k-i-1}dz = 
\frac{1}{2\pi j}x(k) \cdot 2\pi j = x(k)
$$

**Dato un segnale a tempo discreto $x(k)$, $K \in Z$ determinare la trasformata dei segnali anticipati e ritardati di $n$ passi del tipo: $\mathcal{Z}[k(k-n)]$**

- Segnale ritardato: $\mathcal{Z}[x(k-n)] = z^{-n}\mathcal{Z}[x(k)] + \sum_{i=0}^{n-1}x(k-n)z^{-k}$
- Segnale anticipato: $\mathcal{Z}[x(k+n)] = z^{n}\mathcal{Z}[x(k)] - \sum_{i=0}^{n-1}x(i)z^{n-i}$

**Sia dato un sistema in retroazione unitaria con guadagno di anello $L(n)$ si presentie discuta l'analisi a regime della risposta armonica**

Assunzioni: sistemi in retroazione unitaria, sistema retroazionato asintoticamente stabile.

- $r(t) \in \{r_0 1(t), r_0t 1(t), r_0 \frac{t^2}{2}1(t)\}$
- $e(t) := r(t)-y(t)$ $E(s)= \frac{1}{1+G(s)}R(s)$
- $e_r := \lim_{t \rightarrow \infty} e(t)$

Gradino:

- $r(t) = r_0 1(t)$ $R(s)=\frac{r_0}{s}$
- $e_r = \lim_{s \rightarrow 0} s E(s) = \lim_{s \rightarrow 0} s \frac{1}{1+G(s)} \cdot \frac{r_0}{s}$
- $e_r = \frac{r_0}{1+K+_p}$ dove $K_p := \lim_{s \rightarrow 0} G(s)$ (costante di posizione)

Rampa:

- $r(t) = r_0 t 1(t)$ $R(s)=\frac{r_0}{s^2}$
- $e_r = \lim_{s \rightarrow 0} s E(s) = \lim_{s \rightarrow 0} s \frac{1}{1+G(s)} \cdot \frac{r_0}{s^2} = \lim_{s \rightarrow 0} \frac{r_0}{s+sG(s)}$
- $e_r = \frac{r_0}{K_v}$ dove $K_v := \lim_{s \rightarrow 0} sG(s)$ (costante di velocità)

Parabola:

- $r(t) = r_0 \frac{t^2}{2} 1(t)$ $R(s)=\frac{r_0}{s^3}$
- $e_r = \lim_{s \rightarrow 0} s E(s) = \lim_{s \rightarrow 0} s \frac{1}{1+G(s)} \cdot \frac{r_0}{s^3} = \lim_{s \rightarrow 0} \frac{r_0}{s^2+s^2 G(s)}$
- $e_r = \frac{r_0}{K_a}$ dove $K_a := \lim_{s^2 \rightarrow 0} sG(s)$ (costante di accelerazione)

**Definire $M_a$ e $M_f$ enunciare e dimostrare le proprietà geometriche. Definire procedure per il calcolo nel caso di intersezioni multiple del d.p**

$$
M_a := sup \{ M>1 : |1+\gamma L(j\omega)| > 0 \forall \gamma \in [ \frac{1}{M}, M ] \text{ e } \forall \omega \ge 0 \}
$$

$$
M_f := sup \{\phi > 0 : |1 + e^{-j\rho} L(j\omega)| > 0 \forall \rho \in [- \phi, \phi] \text{ e } \forall \omega \ge 0\}
$$

I margini di stabilità sono "norme" che misurano la distanza del punto critico $-1+j0$ dal diagramma polare di $L(j\omega)$.

**Proprietà geometriche**:

Sia $M > 1$. Vale la disequazione $|1+L(j\omega)| > 0 \forall \gamma \in [\frac{1}{M}, M] \text{ e } \forall \omega \ge 0$ se e solo se il segmento dell'asse reale compreso tra $-M$ e $-\frac{1}{M}$ non interseca il diagramma polare di $L(j\omega)$.

Dimostrazione:

- $\{|1+\gamma L(j\omega)| > 0 \forall \gamma \in  [\frac{1}{M}, M] \text{ e } \forall \omega \ge 0\}$
- Divido dentro il modulo per $\gamma$ che dovrà quindi essere diverso da 0
- $\{|\frac{1}{\gamma}+ L(j\omega)| > 0 \forall \gamma \in  [\frac{1}{M}, M] \text{ e } \forall \omega \ge 0\}$

Si noti che $\frac{1}{M} \le \gamma \le M \Rightarrow -M \le -\frac{1}{\gamma} \le -\frac{1}{M}$. Quindi abbiamo i due punti sull'asse reale corrispondenti a $M$ e al suo reciproco e vediamo che $-\frac{1}{\gamma}$ (il vettore blu) deve essere compreso tra questi due punti. Se la diseguaglianza è soddisfatta, il vettore rosso non si annulla mai.

![](./immagini/margini.png)

Continuare con la proprietà e le procedure di calcolo

**Presentare e dedurre le f.d.t a $t$ discreto $Pd(z)$ di un sistema a t continuo $P(s)$ con all'ingresso...**

![](./immagini/pdz.png)

Il tempo di campionamento sia $T(\overline{y}(k) = y(kT))$ e il convertitore D/A sia un mantenitore (dispositivo di tenuta) di ordine zero. Si determini la f.d.t. a $t$ discreto $Pd(z)$ del sistema.

Si determina $P_d(z)$ come trasformata zeta della risposta all'impulso applicato all'ingresso del mantenitore di ordine zero: $\overline{u}(k) = \delta(k)$.

- $u(t) = 1(t) - 1(t-T)$
- quindi $y(t) = p_s(t)-p_s(t-T)$
- con $p_s(t) = \mathcal{L}^{-1}[P(s)]$ risposta di $P(s)$ al gradino unitario $1(t)$
- $\overline{y}(k) = p_s(kT) - p_s(kT-T)$
- $P_d(z) = \mathcal{Z}[\overline{y}(k)] = (1-z^{-1}) \mathcal{Z}[p_s(kT)] = (1-z^{-1}) \mathcal{Z}[\frac{P(s)}{s}, T]$
- $P_d(z) = \frac{z-1}{z} \mathcal{Z}[\frac{P(s)}{s}, T]$

**Definire la stab. asint. per un s.r. Enunciare una condizione necessaria e sufficiente che garantisca questa stabilità**

DEF. Un sistwema retroazionato è asintoticamente e internamente stabile quando tutte le f.d.t fra gli ingressi e le uscite del sistema sono asintoticamente stabili.

Il sistema retroazionato è asintoticamente e internamente stabile se e solo se tutti i poli di $1+L(s)$ hanno parte reale negativa e le eventuali cancellazioni polo-zero fra $C(s)$ e $P(s)$ avvengono in $\mathbb{C}$

**Sia $X(z)$ un segnale a tempo discreto x. Presentare e dimostrare la relazione tra $\frac{dX}{dz}$ e $X(z)$. Calcolare la tr. zeta della funzione armonica $\sin(\omega k)$ con $k \in \mathbb{Z}$**