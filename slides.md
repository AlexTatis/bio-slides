---
theme: seriph
background: https://images.unsplash.com/photo-1628091917832-3ddaee0a3221?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1176&q=80
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
lineNumbers: false
info: |
  ## Los ecosistemas y el ser humano
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
# page transition
transition: slide-left
# use UnoCSS
css: unocss
---

# Los ecosistemas y el ser humano
<p class="font-italic">Por Alejandro Campo</p>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: slide-left
---

# Los impactos medioambientales

<div class="p-3 mt-10 border border-black rounded">
  Los impactos medioambientales son modificaciones que causa una acción humana sobre el medioambiente.
</div>

Una vez el medioambiente se ve modificado, pueden ocurrir tres tipos de problemas principales:

  - Problemas de abastecimiento <mdi-arrow-right /> Desaparición de alimentos, materiales o fuentes de energía.
  - Problemas de regulación <mdi-arrow-right /> Descontrol de las cadenas tróficas, cambio climático...
  - Problemas sociales y socioculturales <mdi-arrow-right /> División por nivel adquisitivo, pobreza...

---
transition: slide-left
---

# La contaminación
<div class="p-3 mt-10 border border-black rounded">
  La contaminación es la introducción de efectos nocivos al medio ambiente. Al tratarse de un cambio que introduce el ser humano en la mayoría de los casos, la contaminación es considerada un tipo de impacto medioambiental.  
</div>

Dependiendo que sección del medio físico contaminemos, hay tres tipos de contaminación:
  - De la atmósfera <mdi-arrow-right /> Debido a la emisión de gases, como el CO2, CO, compuestos de azufre...
  - De la hidrosfera <mdi-arrow-right /> Vertido de residuos y compuestos químicos nocivos.
  - De la geosfera <mdi-arrow-right /> Acumulación de residuos, insecticidas...
  
Algunos de los principales problemas son el efecto invernadero, problemas de salud, lluvias ácidas, pérdida de espacio de cultivo, contaminación del agua potable, exceso de CO2 en zonas urbanas...

<!-- <Cards :data='[
  { 
    title: "La atmósfera", 
    text: `Debido a la emisión de gases, como el CO2, CO, compuestos de azufre... <img src="https://source.unsplash.com/collection/94734566/1920x1080" />`, 
    color: "00ff00"
  },
  { 
    title: "La sdffdf", 
    text: `Debido a la emisión de gases, como el CO2, CO, compuestos de azufre... <img src="https://source.unsplash.com/collection/94734566/1920x1080" />`, 
    color: "00ff00"
  }
]' :init="0" /> -->


---
transition: slide-left
---
<Suspense>
  <Chart />
  <template #fallback>
    <h2>Cargando...</h2>
  </template>
</Suspense>

---
transition: slide-left
---

# Los residuos
<div class="p-3 mt-10 border border-black rounded">
  Un residuo es todo material procedente de actividades humanas que no tienen valor suficiente para retenerlo, por lo que se desecha.
</div>

Los principales tipos de residuos que producimos son:
  - Residuos urbanos sólidos
  - Residuos industriales, mineros y agroganaderos
  - Residuos peligrosos 

Estos residuos pueden producir múltiples problemas (ocupación de espacio, desequilibrio en los ecosistemas, envenenamiento...) por lo que es primordial eliminarlos.

En nuestro día a día, todos producimos *RUSs*. La mejor forma de reducirlos es mediante las tres R: reducir, recliclar y reutilizar.

---
transition: slide-left
layout: two-cols
---

# Agotamiento de los recursos

<div class="text-sm">
  <div class="p-3 mt-10 border border-black rounded">
    El agotamiento de los recursos se debe a la sobreexplotación, es decir, la tasa de extracción es mucho mayor que la de regeneración.
  </div>
  
  Los efectos de la sobreexplotación son múltiples: escaseza de recursos, deforestación, pérdida de la biodiversidad... y la desertificación.
  
  <div class="p-3 mt-10 border border-black rounded">
    La desertificación es la creación de zonas áridas a partir de aquellas que antes eran fértiles, debido a la pérdida excesiva de masa forestal y agua.
  </div>
</div>

::right::

<div class="flex flex-col items-center content-center h-full pl-16 m-0">
  <img src="https://upload.wikimedia.org/wikipedia/commons/9/94/ShrinkingLakeChad-1973-1997-EO.jpg" class=" w-96">
  <p class="text-sm italic">La desaparición periódica del Lago Chad, África</p>
</div>

---
transition: slide-left
---

# La deterioración de los ecosistemas

<div class="p-3 mt-10 border border-black rounded">
  <p>La rápida deterioración que están sufriendos los ecosistemas actualmente se debe al inmenso impacto ambiental de la sociedad actual.</p>
</div>

Debido la industrialización y al aumento de población, los cambios que introducimos a los ecosistemas son tan profundos que superan a los mecanismos de autorregulación.

Además, casi todas las actividades humanas producen de una forma u otra un impacto ambiental:
  - Transporte <mdi-arrow-right /> El CO2 expulsado al quemar combustible, los recursos y energía necesaria para construir el vehículo...
  - Alimentación <mdi-arrow-right /> La agricultura agota suelos fértiles y el agua, y la ganadería produce gases de efecto invernadero y desertización debido a las fincas.
  - Turismo <mdi-arrow-right /> Similar al transporte, pero también hace variar el consumo de recursos en las zonas de recepción y emisión de turistas.

---
transition: slide-left
layout: two-cols
---

<h2 class="text-[#5d8392] text-md">Desenvolvimiento sostenible</h2>

<div class="p-3 mt-10 text-xs border border-black rounded">
  El desenvolvimiento sostenible pretende mantener las necesidades de la generación actual sin comprometer el futuro de la especie.
</div>

Para esto, consta de tres principios:
  - Los recursos naturales no deben ser sobreexplotados <mdi-arrow-right /> Mediante la correcta gestión de estos:
    - Optimización del proceso extracción, en vez expansión de la zona de extracción.
    - Favorecer la ganadería más integrada con la naturaleza.
    - Repartición de alimentos.
  - La emisión de contaminantes y residuos no puede superar la capacidad de la Tierra para eliminarlos <mdi-arrow-right /> Reducir la extracción de materiales no renovables, distribuir los recursos equitativamente...
  - Todos los países tienen derecho al desarrollo.

Para cumplir estos principios, la UNESCO lleva promoviendo desde su fundación acuerdos internacionales ecologistas, como el Protocolo de Montreal y el Protocolo de Kyoto.

::right::

<div class="flex flex-col justify-center object-contain w-full h-full ml-10 text-center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/3/31/Kyoto_Protocol_participation_map_2010.png">
  <p>Los distintos países del mundo respecto a su <i>status</i> en el Protocol de Kyoto</p>
</div>

<style>
  p, ul {
    @apply text-xs
  }
</style>