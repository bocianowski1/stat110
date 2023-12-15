# STAT110

## Diskrete Fordelinger

### Binomisk

Brukes når det er to mulige utfall (kron/mynt) og det er et gitt antall uavhengige forsøk.

### Geometrisk

Brukes når man er interessert i tiden det tar før første suksess inntreffer i en serie uavhengige Bernoulli (binomisk) forsøk.

### Hypergeometrisk

Brukes når man trekker uten tilbakelegging fra en begrenset populasjon der man er interessert i antall suksesser i utvalget.

**Intuisjon for at en hypergeometrisk fordeling er tilnærmet lik en binomisk fordeling**

Når den totale populasjonen $n$ er mye større enn utvalget man trekker, $m$, er det ikke viktig om man trekker med eller uten tilbakelegging.

$$X\sim\text{Bin}(m, \frac{r}{n})$$

Det betyr at utvalget vi trekker er populasjonen i den binomiske fordelingen og sannsynligheten $p=\frac{r}{n}$ altså antallet ønskede ($r$) over totale mulige.

### Poisson

Brukes når vi er interessert i å finne sannsynligheten for at en hendelse skjer innenfor $X$ tidsperioder.

## Kontinuerlige Fordelinger

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

## Konfidensintervall

**Z-intervall** for $\mu$ dersom $\sigma$ er kjent:

$$\Bigl[ \bar{X}-z_{\alpha/2}\cdot \frac{\sigma}{\sqrt{n}} \space , \space \bar{X}+z_{\alpha/2}\cdot \frac{\sigma}{\sqrt{n}}\Bigl]$$

**T-intervall** for $\mu$ dersom $\sigma$ **ikke** er kjent:

$$\Bigl[ \bar{X}-t_{\alpha/2}\cdot \frac{S}{\sqrt{n}} \space , \space \bar{X}+t_{\alpha/2}\cdot \frac{S}{\sqrt{n}}\Bigl]$$

### V22.3a

Det blir gjort 5 målinger for luftforurensning: $X_1,...,X_5$ som er uavhengige og identisk normalfordelt med $\mu$ og varians $\sigma^2$. Begge er **ukjente**. De 5 målingene er: $M=252, 311, 268, 287, 302$, og $\sum_{i=1}^n(x_i-\bar{x})^2=2342$.

**_Finn 95% konfidensintervall_**

$\sigma$ er ukjent så dette er et T-intervall.

$$\bar{x}=\frac{1}{5}\sum M=284$$

$$s=\sqrt{\frac{1}{5-1}\sum(x_i-\bar{x})^2}=\sqrt{2342/4}=24.2$$

$$t_{\alpha/2,n-1}=t_{0.025,4}=2.776$$

Sett inn i formelen over som gir $[254, 314]$

```python
x, s, t, n = 284, 24.2, 2.776, 5

x - ((s * t) / np.sqrt(n)), x + ((s * t) / np.sqrt(n))
# (253.9565, 314.0434)
```
