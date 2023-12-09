# STAT110

## Fordelinger

## Sannsynlighet

## Estimatorer

En estimator er forventningsrett hvis den gir den forventede verdien til en variabel, dvs:

$$E(\hat\theta)=\theta$$

### V22.4a

Det selges _3-kilos poser_. Siden det er et helt antall epler i posen vil vekten variere. En tilfeldig pose veier $X$ kg, hvor $X$ er normalfordelt med $\mu$ som ukjent og $\sigma^2=0.4^2$.

Det blir gjort et tilfeldig utvalg på $n=3$ med vekter: $X_1,X_2,X_3$. Estimator for forventet vekt $\mu$ er gitt ved:

$$\hat\mu=\frac{1}{3}\sum_{i=1}^{3}X_i=\bar{X}$$

**_Forklar hvorfor estimatoren er normalfordelt_**

$\hat\mu$ er normalfordelt fordi den er summen av $X_1,X_2,X_3$ som er normalfordelt og uavhengige. De er uavhengige: posen med vekt $X_1$ har ingen påvirkning på pose 2.

$$\frac{X_1+X_2+X_3}{3}=\bar{X}\text{ (gjennomsnitt)}$$

**_Utled uttrykk for forventning og varians til normalfordelingen_**

Forventning:
$$E(\hat\mu)=\frac{1}{n}\sum_{i=1}^nE(X_i)$$
$$\text{Bruker at: } E(X_i)=\mu$$
$$E(\hat\mu)=\frac{1}{n}\sum_{i=1}^n\mu=\frac{1}{n}\mu\cdot n=\mu$$

Varians:
$$Var(\hat\mu)=(\frac{1}{n})^2\sum_{i=1}^nVar(X_i)$$
$$\text{Bruker at: } Var(X_i)=\sigma^2$$
$$Var(\hat\mu)=(\frac{1}{n})^2\sum_{i=1}^n\mu=(\frac{1}{n})^2\sigma^2\cdot n=\frac{\sigma^2}{n}$$

**_Når er en estimator forventningsrett?_**

Ved uendelig mange forsøk vil gjennomsnittet av de tilhørende estimatene være lik den sanne parameteren.

**_Er denne estimatoren forventningsrett?_**

Ja, i dette tilfellet er $\hat\mu$ forventningsrett siden den sanne forventningen for en normalfordeling er $\mu$.

## Hypotesetesting

### V22.4b

Er forventet vekt av posene, $\mu$, mindre enn 3 kg?

$H_0:\mu=3\hspace{2em} H_a:\mu<3\hspace{2em}\alpha=0.05$

Estimatoren $\hat\mu$ er testobservator.

**_Hvilke verdier av estimatoren gjør at vi forkaster nullhypotesen?_**

$$H_0:\mu=\mu_0\hspace{2em}H_1:\mu<\mu_0\hspace{2em}Z=\frac{\bar{X}-\mu_0}{\sigma / \sqrt{n}}$$

Dette betyr at vi har forkastningsområdet $Z$ og vi forkaster nullhypotesen når $Z\leq-z_{\alpha}$

La $k$ være den kritiske verdien:

$$\frac{k-3}{\sigma / \sqrt{n}}=-z_{\sigma}\Rightarrow k=3-z_{\alpha}\sqrt{\frac{\sigma^2}{n}}$$
$$...$$
$$k=2.62$$

Forkast $H_0$ hvis $\hat\mu<2.62$
