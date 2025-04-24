## Anàlisi psicomètrica dels ítems

Aquest script realitza una anàlisi psicomètrica bàsica d’un qüestionari de respostes binàries (0/1), utilitzant els paquets **`CTT`**, **`psych`** i **`ltm`** en R. Les mètriques analitzades són:

### 1. Dificultat
La dificultat es calcula com la mitjana de respostes correctes per ítem.

```r
Dificultat = mean(respostes_correctes)
```

- Valor entre 0 i 1.
- Ítems amb valors propers a 0 són molt difícils; propers a 1 són molt fàcils.
- Idealment entre 0.3 i 0.8.

### 2. Discriminació
Mesura fins a quin punt un ítem distingeix entre estudiants amb rendiment alt i baix. S'utilitza la correlació ítem-test corregida.

```r
Discriminacio = itemTotalCorr  # columna 4 de l’objecte itemReport
```

- Valor desitjat: superior a 0.2.
- Valors baixos poden indicar que l’ítem no aporta informació útil.

### 3. Correlació Punt-Biserial (Pbis)
És la correlació entre la resposta binària a l’ítem i la puntuació total (numèrica) del test.

```r
Pbis = resultats_CTT$itemReport[, 5]
```

- També hauria de ser superior a 0.2.
- Valors negatius són indicadors clars de problemes.

### 4. Fiabilitat (Alfa de Cronbach)
Mesura la consistència interna del qüestionari.

```r
alfa <- cronbach.alpha(dades)
```

- Valors recomanats:
  - > 0.9: Excel·lent
  - 0.8–0.9: Bona
  - 0.7–0.8: Acceptable
  - < 0.7: Millorable

### Ítems problemàtics
El codi identifica ítems problemàtics si tenen:
- `Discriminació < 0.2` **o**
- `Pbis < 0.2`

---
