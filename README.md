# Anàlisi Psicomètric d'Ítems

Aquest repositori conté un script en R per a l’anàlisi psicomètric d’un qüestionari de respostes binàries (0/1), incloent ítems de resposta múltiple transformats en dicotòmics.

---

## Instal·lació

Instal·la els paquets necessaris en R:

```r
install.packages(c("ltm", "psych", "CTT"))
```

Carrega les biblioteques:

```r
library(ltm)
library(psych)
library(CTT)
```

---

## 1. Dificultat

**Definició:** La dificultat d’un ítem és la proporció d’estudiants que responen correctament, definida com $p = N_{correctes} / N_{total}$, on $N_{correctes}$ és el nombre de respostes correctes i $N_{total}$ el total de respostes.

**Interpretació:** Valors de $p$ propers a 1 indiquen un ítem fàcil, propers a 0 un ítem difícil. Rang recomanat: $0{,}30 \le p \le 0{,}80$.

**Càlcul en R:**

```r
Dificultat_Q1 <- mean(dades$Q1)
```

---

## 2. Discriminació

**Definició:** Mesura la capacitat de l’ítem per diferenciar estudiants d’alt i baix rendiment, mitjançant la correlació ítem-test corregida.

**Fórmula:** $D = \text{itemTotalCorr}(i)$, extreta de l’objecte `itemReport` generat per `itemAnalysis()`.

**Interpretació:** $D > 0{,}30$ indica bona discriminació; $D < 0{,}10$ és pobra.

**Càlcul en R:**

```r
res_CTT <- itemAnalysis(dades, NA.Delete = TRUE)
Discriminacio_Q1 <- res_CTT$itemReport["Q1", "itemTotalCorr"]
```

---

## 3. Correlació Punt-Biserial (Pbis)

**Definició:** Correlació entre la resposta dicotòmica de l’ítem (0/1) i la puntuació total contínua.

**Fórmula:** $r_{pb} = (\overline{X}_1 - \overline{X}_0) / S_X \times \sqrt{p\,(1-p)}$, on $\overline{X}_1$ i $\overline{X}_0$ són les mitjanes de la puntuació total per als qui encerten i qui fallen respectivament, $S_X$ és la desviació estàndard de la puntuació total i $p$ la proporció d’encerts.

**Interpretació:** $r_{pb} \ge 0{,}20$ és desitjable; valors <= 0 poden indicar incoherència.

**Càlcul en R:**

```r
Pbis_Q1 <- res_CTT$itemReport["Q1", "pBis"]
```

---

## 4. Fiabilitat (Alfa de Cronbach)

**Definició:** Consistència interna del conjunt d’ítems.

**Fórmula:** $\alpha = \frac{k}{k-1} (1 - \sum_{i=1}^k \sigma_i^2 / \sigma_X^2)$, amb $k$ el nombre d’ítems, $\sigma_i^2$ la variància de l’ítem $i$ i $\sigma_X^2$ la variància de la puntuació total.

**Interpretació:** $\alpha > 0{,}90$: excel·lent
$\alpha < 0{,}80$: bona
$\alpha <0{,}70$: acceptable
$\alpha < 0{,}70$: baixa.

**Càlcul en R:**

```r
alfa <- cronbach.alpha(dades)
alpha_value <- alfa$alpha
```

---

## Tractament d’ítems de resposta múltiple

Cada opció es tracta com un ítem dicotòmic separat (0/1). Per exemple, l’ítem Q5 amb 4 opcions passa a Q5_1, Q5_2, Q5_3 i Q5_4.

---

## Execució completa

```r
# Eliminar `Estudiant` si existeix
dades <- dades[, !(names(dades) == "Estudiant")]
# Forçar numeric i eliminar NA
dades <- as.data.frame(lapply(dades, as.numeric))
dades <- na.omit(dades)
# Anàlisi CTT
res_CTT <- itemAnalysis(dades, NA.Delete = TRUE)
# Resultats
resultats <- data.frame(
  Item = colnames(dades),
  Dificultat = colMeans(dades),
  Discriminacio = res_CTT$itemReport[, "itemTotalCorr"],
  Pbis = res_CTT$itemReport[, "pBis"]
)
# Alfa de Cronbach
alfa <- cronbach.alpha(dades)
print(resultats)
cat("Alpha de Cronbach:", round(alfa$alpha, 3), "\n")
```

