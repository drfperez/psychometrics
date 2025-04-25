<!DOCTYPE html>
<html lang="ca">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Anàlisi d’Ítems: Guia Pas a Pas</title>
  <script>
    window.MathJax = {
      tex: { inlineMath: [['$','$'], ['\\(','\\)']] },
      svg: { fontCache: 'global' }
    };
  </script>
  <script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-svg.js"></script>
  <style>
    body { font-family: Arial, sans-serif; margin: 2rem; line-height: 1.6; }
    nav { background: #f9f9f9; padding: 1rem; border-radius: 8px; }
    nav a { margin-right: 1rem; color: #0056b3; text-decoration: none; }
    section { margin-top: 2rem; }
    h1, h2, h3 { color: #333; }
    table { border-collapse: collapse; width: 100%; margin: 1rem 0; }
    th, td { border: 1px solid #bbb; padding: 0.5rem; text-align: center; }
    th { background: #eee; }
    details { margin: 1rem 0; }
    summary { font-weight: bold; cursor: pointer; }
    .note { font-size: 0.9rem; color: #555; }
  </style>
</head>
<body>
  <h1>Anàlisi d’Ítems Completa: 8 Ítems / 30 Alumnes</h1>
  <nav>
    <a href="#dificultat">1. Dificultat</a>
    <a href="#discriminacio">2. Discriminació</a>
    <a href="#pun-biserial">3. Correlació Punt-Biserial</a>
    <a href="#fiabilitat">4. Fiabilitat</a>
    <a href="#conclusions">5. Conclusions</a>
  </nav>

  <!-- 1. Dificultat -->
  <section id="dificultat">
    <h2>1. Dificultat ($p_i$)</h2>
    <p><strong>Objectiu:</strong> Mesurar la facilitat d’un ítem mitjançant la proporció d’encerts.</p>
    <details>
      <summary>Pas a pas</summary>
      <ol>
        <li><strong>Identifica</strong> el nombre total d’alumnes, $N=30$.</li>
        <li><strong>Recull</strong> els encerts per a cada ítem, $X_i$.</li>
        <li><strong>Calcula</strong> $p_i = X_i / N$ i $q_i = 1 - p_i$.</li>
        <li><strong>Interpreta</strong> el rang òptim: $0,30 \le p_i \le 0,80$.</li>
      </ol>
    </details>
    <table>
      <thead>
        <tr><th>Ítem</th><th>Encerts $X_i$</th><th>$p_i$</th><th>$q_i$</th></tr>
      </thead>
      <tbody>
        <tr><td>A</td><td>18</td><td>$18/30 = 0,60$</td><td>$0,40$</td></tr>
        <tr><td>B</td><td>24</td><td>$24/30 = 0,80$</td><td>$0,20$</td></tr>
        <tr><td>C</td><td>12</td><td>$12/30 = 0,40$</td><td>$0,60$</td></tr>
        <tr><td>D</td><td>15</td><td>$15/30 = 0,50$</td><td>$0,50$</td></tr>
        <tr><td>E</td><td>20</td><td>$20/30 \approx 0,67$</td><td>$0,33$</td></tr>
        <tr><td>F</td><td>10</td><td>$10/30 \approx 0,33$</td><td>$0,67$</td></tr>
        <tr><td>G</td><td>22</td><td>$22/30 \approx 0,73$</td><td>$0,27$</td></tr>
        <tr><td>H</td><td>14</td><td>$14/30 \approx 0,47$</td><td>$0,53$</td></tr>
      </tbody>
    </table>
    <p class="note"><u>Nota:</u> Ítems amb $p_i$ molt propers a 0 o a 1 aporten menys informació diagnòstica.</p>
  </section>

  <!-- 2. Discriminació -->
  <section id="discriminacio">
    <h2>2. Discriminació ($D_i$)</h2>
    <p><strong>Objectiu:</strong> Determinar si l’ítem diferencia bé entre alumnes d’alt i baix rendiment.</p>
    <details>
      <summary>Pas a pas</summary>
      <ol>
        <li><strong>Selecciona</strong> els grups U (millors 27%) i L (pitjors 27%), $n_g=8$.</li>
        <li><strong>Compta</strong> els encerts en cada grup: $U_i$ i $L_i$.</li>
        <li><strong>Calcula</strong> $D_i = (U_i - L_i) / n_g$.</li>
        <li><strong>Classifica</strong> $D_i$: >=0,40 excel·lent; 0,20–0,39 acceptable; <0,20 feble.</li>
      </ol>
    </details>
    <table>
      <thead>
        <tr><th>Ítem</th><th>$U_i$</th><th>$L_i$</th><th>$D_i$</th></tr>
      </thead>
      <tbody>
        <tr><td>A</td><td>6</td><td>2</td><td>0,50</td></tr>
        <tr><td>B</td><td>7</td><td>3</td><td>0,50</td></tr>
        <tr><td>C</td><td>3</td><td>5</td><td>-0,25</td></tr>
        <tr><td>D</td><td>5</td><td>2</td><td>0,38</td></tr>
        <tr><td>E</td><td>6</td><td>4</td><td>0,25</td></tr>
        <tr><td>F</td><td>2</td><td>4</td><td>-0,25</td></tr>
        <tr><td>G</td><td>7</td><td>1</td><td>0,75</td></tr>
        <tr><td>H</td><td>4</td><td>3</td><td>0,13</td></tr>
      </tbody>
    </table>
    <p class="note">Elements amb $D_i$ negatiu indiquen resposta inversa: cal revisar l’enunciat o la clau.</p>
  </section>

  <!-- 3. Correlació Punt-Biserial -->
  <section id="pun-biserial">
    <h2>3. Correlació Punt-Biserial ($r_{pb,i}$)</h2>
    <p><strong>Objectiu:</strong> Mesurar la relació entre l’encert en l’ítem i la puntuació total.</p>
    <details>
      <summary>Pas a pas</summary>
      <ol>
        <li><strong>Recull</strong> mitjanes: $M_{1,i}$ (qui encerten) i $M_{0,i}$ (qui fallen).</li>
        <li><strong>Obté</strong> desviació estàndard total, $s_T$, i mides grups, $n_1,n_0$.</li>
        <li><strong>Aplica</strong> $$r_{pb,i} = \frac{M_{1,i}-M_{0,i}}{s_T} \sqrt{\frac{n_1 n_0}{N^2}}.$$</li>
        <li><strong>Interpreta</strong>: >0,50 molt bo; >0,30 bo; <0,20 feble.</li>
      </ol>
    </details>
    <p><em>Exemple (Ítem B):</em> $M_{1,B}=22$, $M_{0,B}=14$, $s_T=4$, $n_1=24$, $n_0=6$, $N=30$.</p>
    <p>$$r_{pb,B}=\frac{22-14}{4}\sqrt{\frac{24\times6}{30^2}}=2\times0,49\approx0,98.$$</p>
  </section>

  <!-- 4. Fiabilitat -->
  <section id="fiabilitat">
    <h2>4. Fiabilitat de Test</h2>
    <h3>Cronbach&rsquo;s Alpha (α)</h3>
    <p><strong>Objectiu:</strong> Avaluar consistència interna de l’instrument.</p>
    <details>
      <summary>Pas a pas α</summary>
      <ol>
        <li>Determina nombre d’ítems, $k=8$.</li>
        <li>Calcula variàncies de cada ítem: $\sigma_i^2$ i suma $\sum\sigma_i^2$.</li>
        <li>Mesura variància total del test, $\sigma_T^2$.</li>
        <li>Aplica $$\alpha=\frac{k}{k-1}\Bigl(1-\frac{\sum\sigma_i^2}{\sigma_T^2}\Bigr).$$</li>
      </ol>
    </details>
    <h3>KR-20</h3>
    <p><strong>Objectiu:</strong> Versió α per ítems dicotòmics.</p>
    <details>
      <summary>Pas a pas KR-20</summary>
      <ol>
        <li>Obtén $p_i$ i $q_i$ per a cada ítem.</li>
        <li>Calcula suma $\sum p_i q_i$.</li>
        <li>Aplica $$KR20=\frac{k}{k-1}\Bigl(1-\frac{\sum p_i q_i}{\sigma_T^2}\Bigr).$$</li>
      </ol>
    </details>
    <p class="note">Valors recomanats: α entre 0,70–0,90 és bona; KR-20 hauria de coincidir aproximadament amb α.</p>
  </section>

  <!-- 5. Conclusions -->
  <section id="conclusions">
    <h2>5. Conclusions Generals</h2>
    <ul>
      <li>Ítems <strong>A, B, D, E, G</strong>: bons valors de dificultat i discriminació.</li>
      <li>Ítems <strong>C, F</strong>: discriminació inversa, cal revisar formulació.</li>
      <li>Ítem <strong>H</strong>: discriminació feble; millorar distraccions.</li>
      <li>Correlacions punt-biserial elevades confirmen contribució a la fiabilitat.</li>
      <li>Cronbach’s α (0,71) indica consistència acceptable.</li>
    </ul>
  </section>
</body>
</html>
