## Anàlisi d'Items
Aquest document descriu els principals índexs utilitzats en l'anàlisi d'items per a l'avaluació psicomètrica d'un qüestionari o prova.

---

### 1. Dificultat
- **Definició**: Mesura la facilitat o dificultat d'un ítem segons la proporció d'estudiants que l'han resolt correctament.
- **Càlcul**:
  ```text
  p = N_correctes / N_total
  ```
  - `N_correctes`: nombre de respostes correctes.
  - `N_total`: nombre total de respostes.
- **Interpretació**:
  - `p` proper a 1: ítem molt fàcil.
  - `p` proper a 0: ítem molt difícil.
  - Rang recomanat: 0,20 ≤ `p` ≤ 0,80.

---

### 2. Discriminació
- **Definició**: Grau en què un ítem diferencia entre individus amb alt i baix rendiment global.
- **Índex de discriminació (D)**:
  1. Ordena els participants segons la puntuació total.
  2. Selecciona els grups superior i inferior (aprox. 27% de la mostra cada un).
  3. Calcula:
     ```text
     D = p_superior - p_inferior
     ```
     - `p_superior`: proporció de respostes correctes al grup d'alt rendiment.
     - `p_inferior`: proporció de respostes correctes al grup de baix rendiment.
- **Interpretació**:
  - `D` ≥ 0,30: bona discriminació.
  - `D` ≤ 0,10: discriminació pobra; considerar eliminar o revisar l'ítem.

---

### 3. Correlació Punt-Biserial
- **Definició**: Correlació entre la puntuació dicotòmica d'un ítem (0 = incorrecte, 1 = correcte) i la puntuació total dels participants.
- **Càlcul**:
  ```text
  r_pb = ((Xbar_1 - Xbar_0) / S_X) * sqrt(p * q)
  ```
  - `Xbar_1`: mitjana de la puntuació total dels participants que van encertar l'ítem.
  - `Xbar_0`: mitjana de la puntuació total dels participants que van fallar l'ítem.
  - `S_X`: desviació estàndard de la puntuació total.
  - `p`: proporció d'encerts (N_correctes / N_total).
  - `q`: 1 - p.
- **Interpretació**:
  - `r_pb` ≥ 0,20: l'ítem s'alinea bé amb la mesura global.
  - `r_pb` proper a 0 o negatiu: l'ítem no cohesiona amb la resta.

---

### 4. Fiabilitat (Alfa de Cronbach)
- **Definició**: Mesura la consistència interna d'un conjunt d'ítems.
- **Càlcul**:
  ```text
  alpha = (k / (k - 1)) * [1 - (sum(variance_i) / variance_total)]
  ```
  - `k`: nombre d'ítems.
  - `variance_i`: variància de l'ítem i.
  - `variance_total`: variància de la puntuació total.
- **Interpretació**:
  - `alpha` ≥ 0,90: excel·lent.
  - 0,80 ≤ `alpha` < 0,90: bona.
  - 0,70 ≤ `alpha` < 0,80: acceptable.
  - `alpha` < 0,70: consistència baixa; revisar els ítems.

---

*Per a més detalls i exemples d'implementació, consulta la bibliografia especialitzada en anàlisi psicomètrica o els repositoris de codi associats.*


