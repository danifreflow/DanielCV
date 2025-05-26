---
title: "CV Infográfico"
url: "/cv-infografico/"
---

<style>
.vertical-timeline {
  position: relative;
  margin: 3rem auto;
  max-width: 800px;
  padding: 2rem 0;
  font-family: sans-serif;
}
.vertical-timeline::before {
  content: '';
  position: absolute;
  top: 0;
  bottom: 0;
  left: 50%;
  width: 4px;
  background: #ccc;
  transform: translateX(-50%);
}
.timeline-block {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  width: 100%;
  margin: 2rem 0;
  position: relative;
}
.timeline-block:nth-child(odd) {
  flex-direction: row-reverse;
}
.timeline-content {
  background-color: #2196f3;
  color: white;
  padding: 1rem;
  border-radius: 50%;
  width: 160px;
  height: 160px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  font-weight: bold;
  font-size: 0.9rem;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
  z-index: 1;
}
.estudios .timeline-content {
  background-color: #fbc02d;
}
.trabajo .timeline-content {
  background-color: #2196f3;
}
.connector {
  flex: 1;
  height: 4px;
  background: transparent;
}

/* Leyenda */
.legend {
  display: flex;
  justify-content: center;
  gap: 2rem;
  margin: 2rem auto 1rem auto;
  font-family: sans-serif;
}
.legend-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
.legend-color {
  width: 20px;
  height: 20px;
  border-radius: 50%;
}
.legend-estudios {
  background: #fbc02d;
}
.legend-trabajo {
  background: #2196f3;
}
</style>

<div style="display: flex; justify-content: center; align-items: center; gap: 2rem; flex-wrap: wrap;">
  <img src="/images/tecnologias.png" alt="Tecnologías" style="width: 30%; max-width: 300px; height: auto;" />
  <img src="/images/idiomas.png" alt="Idiomas" style="width: 30%; max-width: 300px; height: auto;" />
</div>

<div style="display: flex; justify-content: center; align-items: center; gap: 2rem; flex-wrap: wrap;">
    <img src="/images/hsociales.png" alt="habilidades sociales" style="width: 30%; max-width: 300px; height: auto;" />
    <img src="/images/infograma1.png" alt="Infograma" style="width: 30%; max-width: 300px; height: auto;" />
</div>


<!-- LEYENDA -->
<div class="legend">
  <div class="legend-item"><div class="legend-color legend-estudios"></div> Vida Estudiantil</div>
  <div class="legend-item"><div class="legend-color legend-trabajo"></div> Vida Laboral</div>
</div>

<!-- LÍNEA DE TIEMPO -->
<div class="vertical-timeline">

<!-- VIDA ESTUDIANTIL -->
<div class="timeline-block estudios">
  <div class="connector"></div>
  <div class="timeline-content">Bachillerato<br>(2016–2018)</div>
</div>

<div class="timeline-block estudios">
  <div class="connector"></div>
  <div class="timeline-content">Cambridge B2<br>(2018)</div>
</div>

<div class="timeline-block estudios">
  <div class="connector"></div>
  <div class="timeline-content">Ingeniería Informática<br>(2018–Actualidad)</div>
</div>

<!-- VIDA LABORAL -->
<div class="timeline-block trabajo">
  <div class="connector"></div>
  <div class="timeline-content">Aprender@Aprender<br>(2020–2021)</div>
</div>

<div class="timeline-block trabajo">
  <div class="connector"></div>
  <div class="timeline-content">The Creative Minds<br>(2021–2024)</div>
</div>

<div class="timeline-block trabajo">
  <div class="connector"></div>
  <div class="timeline-content">La Emboscadura<br>(2023)</div>
</div>

<div class="timeline-block trabajo">
  <div class="connector"></div>
  <div class="timeline-content">Baobab Soluciones<br>(2023–2024)</div>
</div>

<div class="timeline-block trabajo">
  <div class="connector"></div>
  <div class="timeline-content">I+D Tecnologías Cuánticas<br>(2025–Actualidad)</div>
</div>

</div>

