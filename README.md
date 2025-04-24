# Anàlisi psicomètric dels ítems

**Tipus d’ítems**

- **Dicotòmics (0/1)**: resposta única (1 = correcta, 0 = incorrecta).
- **Resposta múltiple**: més d’una opció correcta; cada opció es codifica com un ítem dicotòmic separat (1 si l’estudiant marca i és correcta, 0 en cas contrari) per poder aplicar les mateixes mètriques.

---

## 1. Dificultat
Calcula la proporció de respostes correctes per cada ítem.
```r
# Exemple en R
Dificultat_i <- mean(dades$Q1)
```
- Valor entre 0 i 1.
- Propers a 1: fàcil; propers a 0: difícil.
- Objectiu: 0.3–0.8.

---

## 2. Discriminació
Mesura l’habilitat de l’ítem per distingir estudiants amb rendiment alt i baix.
```r
# Es basa en itemTotalCorr del resultat de itemAnalysis()
library(CTT)
res_CTT <- itemAnalysis(dades)
Discriminacio_i <- res_CTT$itemReport["Q1", "itemTotalCorr"]
```
- Valor esperat > 0.2.
- Baix (< 0.1): revisar l’ítem.

---

## 3. Correlació Punt-Biserial (Pbis)
Correlació entre la resposta dicotòmica i la puntuació total.
```r
Pbis_i <- res_CTT$itemReport["Q1", "pBis"]
```
- Ha de superar 0.2.
- Negatiu: indica problema.

---

## 4. Fiabilitat (Alfa de Cronbach)
Consistència interna del test.
```r
library(psych)
alfa <- cronbach.alpha(dades)
alfa$alpha
```
- > 0.9: excel·lent.
- 0.8–0.9: bona.
- 0.7–0.8: acceptable.
- < 0.7: poc fiable.

---

## Execució completa en R
```r
# Instal·lació de paquets
install.packages(c("ltm", "psych", "CTT"))

# Carregar biblioteques
library(ltm); library(psych); library(CTT)

# Preparació de dades i anàlisi
# ... (mira el teu script complet)
```

