<div align="center">

<!-- BANNER · nube de puntos que recorre cuatro transformaciones -->
<a href="https://github.com/LuisContreras73">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/banner-dark.svg">
    <source media="(prefers-color-scheme: light)" srcset="assets/banner-light.svg">
    <img src="assets/banner-dark.svg" width="960" alt="Luis A. Contreras — Data Scientist en recursos hídricos">
  </picture>
</a>

<a href="https://github.com/LuisContreras73">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=700&size=25&duration=2800&pause=900&color=0EA5E9&center=true&vCenter=true&width=900&lines=Luis+A.+Contreras+%E2%80%94+Data+Scientist;Recursos+h%C3%ADdricos+%7C+Hidroinform%C3%A1tica;Neural+Operators+%E2%80%A2+Generative+%E2%80%A2+World+Models" alt="Data Scientist en recursos hídricos e hidroinformática">
</a>

</div>

**Data Scientist** especializado en **recursos hídricos**. Ingeniero ambiental de formación.
Construyo modelos de agua que se pueden **verificar**: pronóstico de caudal, hidrogeología
numérica y aprendizaje de operadores, con el sensor en campo contrastando lo que el modelo
prometió.

---

## `$ ls -la proyectos/`

### 🏆 HidroAlerta Chancay–Huaral

Pronóstico de caudal y alerta temprana en una cuenca andina. **Tres modelos, uno por escala de decisión:**

| Modelo | Plazo | Acierto |
|---|---|---|
| **HydroST** — atención espacial sobre 9 subcuencas | 1 día | NSE **0,97** |
| **TFT canónico + GRU** — subestacional | 14 días | NSE **0,76** |
| **LightGBM cuantílico** — disponibilidad | 1 mes | KGE **0,77** |

No entrega un número: entrega una **banda P10–P90** que después se contrasta contra el nivel
que mide un nodo IoT propio en campo. Aguanta **30 días sin telemetría** perdiendo solo 0,07 de NSE.

🥇 **1.er puesto** — Concurso de Ciencia y Tecnología para la Seguridad Hídrica,
Autoridad Nacional del Agua (2026). En implementación operativa.

[`código`](https://github.com/LuisContreras73/hidroalerta-chancay-huaral) ·
[`visor en vivo`](https://luiscontreras73.github.io/hidroalerta-dashboard)

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/inference-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="assets/inference-light.svg">
  <img src="assets/inference-dark.svg" width="960" alt="Inferencia: el modelo emite una banda P10–P90 y el caudal medido cae dentro el 82 % de los días del evento de 2024">
</picture>

</div>

> En los 80 días del evento de enero–marzo de 2024 el caudal medido cayó dentro de la banda
> P10–P90 el **82,5 %** de las veces, contra el 80 % nominal. Fuera de eventos la banda queda
> corta y el modelo es sobre-confiado: está medido, está cuantificado y está en el informe.

### 📡 En curso

- **World models** para dinámica de sistemas físicos
- Escalado multi-cuenca con **CAMELS-PE** (136 cuencas peruanas)
- Operativización de HidroAlerta con la ALA Chancay–Huaral

<br>

## `$ ./inspect --model HydroST --show attention`

<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/atencion-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="assets/atencion-light.png">
    <img src="assets/atencion-dark.png" width="940" alt="Atención espacial de HydroST: en crecida el peso se desplaza del valle a las cabeceras">
  </picture>
</div>

> Nadie le dijo al modelo dónde nace el agua. Cuando llega una crecida, la atención espacial se
> desplaza del valle a las tres subcuencas de cabecera sobre los 4 000 m — **del 37 % al 48 %** —
> que son justo las que aportan el 56 % del caudal.
> Pesos reales extraídos de los checkpoints, no una ilustración.

<br>

## `$ ./bench --topics`

Tres cosas que modelo, cada una con su simulación corriendo de verdad detrás:
aprender el **operador** en vez de la solución, el **río** que construye su propia
llanura, y el **agua dentro de una excavación minera**.

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/operador-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="assets/operador-light.svg">
  <img src="assets/operador-dark.svg" width="960" alt="Capa espectral de un operador neuronal: FFT, truncamiento de modos e iFFT">
</picture>

<br><br>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/rio-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="assets/rio-light.svg">
  <img src="assets/rio-dark.svg" width="960" alt="Migración de meandros: el río deforma su cauce, corta cuellos y deja lagos en herradura y barras de acreción">
</picture>

</div>

> Teoría de curva integrada en el tiempo — la migración de cada punto no responde a
> su curvatura local sino a la de **aguas arriba**, con memoria exponencial. Nadie
> dibujó los lagos en herradura: aparecen solos cuando un cuello se estrangula.
> 578 años, 36 cortes, sinuosidad 2,1.

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/tajo-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="assets/tajo-light.svg">
  <img src="assets/tajo-dark.svg" width="960" alt="Tajo abierto girando: bancos, bermas, rampa de acarreo al 10 % y poza de bombeo">
</picture>

</div>

> Las crestas no son círculos escalados: son curvas de nivel de un campo de
> distancias al cuerpo mineralizado, que es lo que hace que un tajo se vea
> excavado y no dibujado. La rampa da **una sola vuelta** porque el 10 % de
> pendiente y los 138 m de profundidad no dan para más.

<br>

<div align="center">

## `$ cat stack.yaml`

<table border="1" cellpadding="14">
  <thead>
    <tr><th colspan="2" align="left"><code>luis@lima:~$ cat stack.yaml</code></th></tr>
  </thead>
  <tbody>
    <tr>
      <td width="50%" valign="top"><code>├─ ∫ operadores_neuronales:</code><br><br>
        <img src="https://skillicons.dev/icons?i=pytorch" alt="PyTorch">
        <img src="https://cdn.simpleicons.org/numpy/0EA5E9" height="48" alt="NumPy">
        <img src="https://cdn.simpleicons.org/scipy/0EA5E9" height="48" alt="SciPy"><br>
        <sub><code>FNO · DeepONet · Neural ODE · G: a(x) ↦ u(x)</code></sub>
      </td>
      <td width="50%" valign="top"><code>├─ ◆ generativos:</code><br><br>
        <img src="https://cdn.simpleicons.org/huggingface/0EA5E9" height="48" alt="Hugging Face">
        <img src="https://skillicons.dev/icons?i=pytorch" alt="PyTorch">
        <img src="https://cdn.simpleicons.org/nvidia/0EA5E9" height="48" alt="NVIDIA"><br>
        <sub><code>Diffusion · VAE · Flow Matching</code></sub>
      </td>
    </tr>
    <tr>
      <td valign="top"><code>├─ ⬡ transformers_y_grafos:</code><br><br>
        <img src="https://cdn.simpleicons.org/huggingface/0EA5E9" height="48" alt="Hugging Face">
        <img src="https://skillicons.dev/icons?i=pytorch" alt="PyTorch Geometric">
        <img src="https://skillicons.dev/icons?i=sklearn" alt="scikit-learn"><br>
        <sub><code>Attention · GNN (GCN/GAT) · TFT · conformal</code></sub>
      </td>
      <td valign="top"><code>├─ ⌬ hidrogeologia_y_fisica:</code><br><br>
        <code>∇·(K∇h) = S<sub>s</sub> ∂h/∂t</code><br><br>
        <sub><code>FEFLOW · MODFLOW · GR4J · PINNs · balance hídrico</code></sub>
      </td>
    </tr>
    <tr>
      <td valign="top"><code>├─ ▤ datos_y_geoespacial:</code><br><br>
        <img src="https://skillicons.dev/icons?i=python,postgres" alt="Python, PostgreSQL">
        <img src="https://cdn.simpleicons.org/duckdb/0EA5E9" height="48" alt="DuckDB">
        <img src="https://cdn.simpleicons.org/googleearthengine/0EA5E9" height="48" alt="Google Earth Engine">
        <img src="https://cdn.simpleicons.org/qgis/0EA5E9" height="48" alt="QGIS"><br>
        <sub><code>SQL · DuckDB · xarray · Earth Engine · QGIS · rasterio</code></sub>
      </td>
      <td valign="top"><code>╰─ ⚙ ingenieria_y_campo:</code><br><br>
        <img src="https://skillicons.dev/icons?i=linux,git,docker,arduino" alt="Linux, Git, Docker, Arduino">
        <img src="https://cdn.simpleicons.org/espressif/0EA5E9" height="48" alt="ESP32"><br>
        <sub><code>Arch · Ubuntu · Git · Docker · ESP32 · LoRa · KiCad</code></sub>
      </td>
    </tr>
  </tbody>
</table>

<br>

## `$ contact --list`

<a href="mailto:luis.contreras@utec.edu.pe">
  <img src="https://img.shields.io/badge/Correo-0EA5E9?style=for-the-badge&logo=gmail&logoColor=white" alt="Correo">
</a>
<a href="https://luiscontreras73.github.io/hidroalerta-dashboard">
  <img src="https://img.shields.io/badge/HidroAlerta-A78BFA?style=for-the-badge&logo=googleearth&logoColor=white" alt="HidroAlerta">
</a>
<a href="https://github.com/LuisContreras73">
  <img src="https://img.shields.io/badge/GitHub-0B0F17?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
</a>

<br><br>

<sub><code>« Un modelo que no se puede falsar no es un modelo. »</code></sub>

</div>
