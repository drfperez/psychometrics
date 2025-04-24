Anàlisi psicomètrica de tests. 

Anàlisi d'items:
1. Dificultat
2. Discriminació
3. Correlació Punt-Biserial 
4. Fiabilitat (alfa de Cronbach)

Respostes a questions 1 (correcta), 0 (incorrecta) de prova de 100 estudiants en dades.csv
## Anàlisi d'Items
Aquest document descriu els principals índexs utilitzats en l'anàlisi d'items per a l'avaluació psicomètrica d'un qüestionari o prova.

---

### 1. Dificultat
- **Definició**: Mesura la facilitat o dificultat d'un ítem segons la proporció d'estudiants que l'han resolt correctament.
- **Càlcul**:
  ```math
  p = \frac{N_{correctes}}{N_{total}}
  ```
  - _N<sub>correctes</sub>_: nombre de respostes correctes.
  - _N<sub>total</sub>_: nombre total de respostes.
- **Interpretació**:
  - Valors de _p_ propers a 1: ítem molt fàcil.
  - Valors de _p_ propers a 0: ítem molt difícil.
  - Rang recomanat: 0,20 ≤ _p_ ≤ 0,80.

---

### 2. Discriminació
- **Definició**: Grau en què un ítem diferencia entre individus amb alt i baix rendiment global.
- **Índex de discriminació (D)**:
  1. Ordena els participants segons la puntuació total.
  2. Selecciona els grups superior i inferior (tipus 27% cada un).
  3. Calcula:
     ```math
     D = p_{superior} - p_{inferior}
     ```
     - _p<sub>superior</sub>_: proporció de correctes al grup superior.
     - _p<sub>inferior</sub>_: proporció de correctes al grup inferior.
- **Interpretació**:
  - _D_ elevat (≥ 0,30): bona discriminació.
  - _D_ baix (≤ 0,10): pobra discriminació; considerar eliminar l'ítem.

---

### 3. Correlació Punt-Biserial
- **Definició**: Correlació entre la puntuació dicotòmica de l'ítem (0/1) i la puntuació total (contínua).
- **Fórmula**:
  ```math
  r_{pb} = \frac{\bar{X}_{1} - \bar{X}_{0}}{S_X} \sqrt{pq}
  ```
  - _\bar{X}<sub>1</sub>_: mitjana de la puntuació total dels que van encertar l'ítem.
  - _\bar{X}<sub>0</sub>_: mitjana de la puntuació total dels que van fallar.
  - _S_X_: desviació estàndard de la puntuació total.
  - _p_: proporció d'encerts (_p_ = N<sub>correctes</sub> / N).
  - _q_ = 1 - _p_.
- **Interpretació**:
  - Valors positius i més alts (≥ 0,20) indiquen que l'ítem s'alinea amb la mesura global.
  - Valors propers a 0 o negatius: l'ítem no cohesiona amb la resta.

---

### 4. Fiabilitat (Alfa de Cronbach)
- **Definició**: Mesura la consistència interna d'un conjunt d'items.
- **Fórmula**:
  ```math
  \alpha = \frac{k}{k - 1} \left(1 - \frac{\sum_{i=1}^{k} \sigma_{i}^{2}}{\sigma_{X}^{2}}\right)
  ```
  - _k_: nombre d'items.
  - _\sigma_{i}^{2}_: variància de l'ítem _i_.
  - _\sigma_{X}^{2}_: variància de la puntuació total.
- **Interpretació**:
  - _\alpha_ ≥ 0,90: excel·lent.
  - 0,80 ≤ _\alpha_ < 0,90: bona.
  - 0,70 ≤ _\alpha_ < 0,80: acceptable.
  - _\alpha_ < 0,70: nivell baix; revisar el conjunt d'items.

---

*Per a més detalls i exemples de càlcul, podeu consultar bibliografia especialitzada en anàlisi psicomètrica.*

