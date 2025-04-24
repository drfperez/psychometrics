# Anàlisi Psicromètric d'Ítems
Aquest repositori conté un script en R per a l’anàlisi psicomètric d’un qüestionari de respostes binàries (0/1), incloent ítems de resposta múltiple transformats en dicotòmics. A continuació tens la definició i la fórmula matemàtica de cada mètrica, seguida del fragment de codi corresponent per a R.

---

## Instal·lació
```r
install.packages(c("ltm", "psych", "CTT"))
```
```r
library(ltm)
library(psych)
library(CTT)
```

---

## 1. Dificultat

**Definició**: Mesura la facilitació o dificultat d’un ítem, és a dir, la proporció d’estudiants que responen correctament.

**Fórmula**:
$$
  p \,=\, \frac{N_{\text{correctes}}}{N_{\text{total}}}
$$
- On $N_{\text{correctes}}$ és el nombre de respostes correctes i $N_{\text{total}}$ el nombre total de respostes.
- **Interpretació**:
  - $p\approx1$: ítem molt fàcil.
  - $p\approx0$: ítem molt difícil.
  - Rang recomanat: $0.30 \le p \le 0.80$.

**Càlcul en R**:
```r
# Mitjana de correctes per ítem Q1
Dificultat_Q1 <- mean(dades$Q1)
```

---

## 2. Discriminació

**Definició**: Grau en què un ítem diferencia entre estudiants de rendiment alt i baix. S’utilitza la correlació ítem-test corregida.

**Fórmula**:
En aquest cas, s’aprofita la sortida del paquet CTT:
$$
  D \,=\, \text{itemTotalCorr}\,(i)
$$
- On $\text{itemTotalCorr}(i)$ és la correlació corregida de l’ítem $i$ amb la puntuació total.
- **Interpretació**:
  - $D > 0.30$: bona discriminació.
  - $D < 0.10$: discriminació pobra; cal revisar l’ítem.

**Càlcul en R**:
```r
res_CTT <- itemAnalysis(dades, NA.Delete=TRUE)
Discriminacio_Q1 <- res_CTT$itemReport["Q1", "itemTotalCorr"]
```

---

## 3. Correlació Punt-Biserial (Pbis)

**Definició**: Correlació entre la resposta dicotòmica a l’ítem (0/1) i la puntuació total contínua del test.

**Fórmula**:
$$
  r_{pb} \,=\, \frac{\overline{X}_1 - \overline{X}_0}{S_X} \;\sqrt{p\,(1-p)}
$$
- $\overline{X}_1$: mitjana de puntuacions totals dels que encerten l’ítem.
- $\overline{X}_0$: mitjana de puntuacions totals dels que fallen l’ítem.
- $S_X$: desviació estàndard de la puntuació total.
- $p$: proporció d’encerts de l’ítem.

- **Interpretació**:
  - $r_{pb}\ge0.20$: l’ítem s’alinea bé amb la mesura global.
  - $r_{pb}\le0$ o aprox.
: pot indicar un problema de coherència.

**Càlcul en R**:
```r
Pbis_Q1 <- res_CTT$itemReport["Q1", "pBis"]
```

---

## 4. Fiabilitat (Alfa de Cronbach)

**Definició**: Mesura la consistència interna d’un conjunt d’ítems.

**Fórmula**:
$$
  \alpha \,=\, \frac{k}{k-1} \left(1 - \frac{\sum_{i=1}^k \sigma_i^2}{\sigma_X^2}\right)
$$
- $k$: nombre total d’ítems.
- $\sigma_i^2$: variància de l’ítem $i$.
- $\sigma_X^2$: variància de la puntuació total.

- **Interpretació**:
  - $\alpha>0.90$: excel·lent.
  - $0.80\le\alpha\le0.90$: bona.
  - $0.70\le\alpha<0.80$: acceptable.
  - $\alpha<0.70$: consistència baixa; cal revisar els ítems.

**Càlcul en R**:
```r
alfa <- cronbach.alpha(dades)
alpha_value <- alfa$alpha
```

---

## Tractament d’ítems de resposta múltiple

Si un ítem té més d’una opció correcta, codifica cada opció com un ítem dicotòmic (0/1). Per exemple, l’ítem Q5 amb 4 opcions és representat com Q5_1, Q5_2, Q5_3 i Q5_4.

---

## Execució completa
```r
# Eliminar columna Estudiant si existeix
if("Estudiant" %in% colnames(dades)) dades <- dades[ , -which(names(dades)=="Estudiant")]
# Forçar numeric i eliminar NA
dades <- as.data.frame(lapply(dades, as.numeric)); dades <- na.omit(dades)
# CTT
res_CTT <- itemAnalysis(dades, NA.Delete=TRUE)
# Resultats per ítem
resultats <- data.frame(
  Item = colnames(dades),
  Dificultat = colMeans(dades),
  Discriminacio = res_CTT$itemReport[,"itemTotalCorr"],
  Pbis = res_CTT$itemReport[,"pBis"]
)
# Alfa de Cronbach
alfa <- cronbach.alpha(dades)
print(resultats)
cat("Alpha de Cronbach:", round(alfa$alpha,3),"\n")
```


