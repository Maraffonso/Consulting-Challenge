# TalentHub — Demanda de habilidades en el mercado laboral tech

## Descripción

**TalentHub** es una empresa de tecnología que planea lanzar un nuevo bootcamp de formación profesional. Antes de definir el programa académico, necesita entender qué tecnologías, herramientas y habilidades está demandando el mercado laboral actual, para asegurar que sus estudiantes egresen con competencias alineadas a oportunidades reales de empleo.

Este proyecto analiza ofertas de empleo del sector tecnológico para identificar tendencias, perfiles buscados y herramientas con mayor demanda.

## Objetivo del cliente

Identificar las habilidades más demandadas por el mercado, cubriendo al menos:

- Qué tecnologías y herramientas aparecen con mayor frecuencia en las ofertas de empleo.
- Qué perfil de profesional buscan las empresas (años de experiencia, seniority, formación, certificaciones, idiomas, habilidades blandas).
- Cómo varía la demanda entre roles tecnológicos (Data Analyst, Data Scientist, Full Stack Developer, QA Engineer, Cloud Engineer).
- Tendencias del mercado: tecnologías emergentes, crecimiento de nuevos perfiles.

## Fuente de datos

**Fuente principal:** [Kaggle — nextgig/global-job-postings-multi-ats-2026-06](https://www.kaggle.com/datasets/nextgig/global-job-postings-multi-ats-2026-06) — ofertas de empleo agregadas de múltiples ATS (Applicant Tracking Systems) a nivel global. Dataset ya disponible en el repo como `nextgig_jobs_2026-06.parquet`.

**Fuente complementaria:** [Stack Overflow Developer Survey 2026](https://survey.stackoverflow.co/) — se usa para contrastar y enriquecer los hallazgos sobre tecnologías y perfiles con la perspectiva de los propios desarrolladores.

_Pendiente: período cubierto y variables a usar del dataset, a confirmar durante la limpieza y el EDA._

## Metodología

1. **Obtención de datos** — descarga del dataset principal de Kaggle y, como complemento, de la encuesta de Stack Overflow.
2. **Limpieza** — tratamiento de duplicados, valores nulos y conversión de tipos de datos, siguiendo el flujo estado inicial → duplicados → nulos → tipos → estado final.
3. **Análisis exploratorio (EDA)** — estadística descriptiva, distribuciones y relaciones entre variables.
4. **Comparación de perfiles** — cruce de tecnologías, experiencia requerida y modalidad de trabajo (remoto/híbrido/presencial) entre roles tecnológicos.
5. **Síntesis de hallazgos y recomendaciones** accionables para el diseño del bootcamp.

_Pendiente: detalle de las preguntas de negocio concretas a contrastar, a definir una vez cerrado el EDA inicial._

## Hallazgos

Se completa luego del análisis exploratorio. 
 Que se descubre? 
 1. Un modelo estándar muy rígido: las ofertas de empleo piden, en casi todos los casos sin excepción un promedio exacto de 8 habilidades o tecnologías por puesto, sin importar si el trabajo es para un puesto Jrs o Srs.
 2. Las herramientas estrella: El lenguaje de Python lidera el mercado con 438 ofertas, luego le sigue SQL y herramientas de automatización y despliegue (CI/CD), además de plataformas en la nube como AWS y Kubernetes.
 3. Los roles mas buscados: son los puestos de ingeniería en la nube (Cloud Engineer) y desarrollo web (Full stack developer), estos concentran el mayor volumen de oportunidades.
 4. El perfil ideal: las empresas buscan perfiles con experiencia intermedia, alta (semi sr y sr). Además casi no piden títulos universitarios formales en los requisitos, enfocándose en lo que la persona sabe hacer en la práctica. 

Para el negocio muestra que dado que se piden 8 habilidades queda demostrado que las descripciones de los puestos suelen responder a plantillas estándar o requisitos fijos, lo que puede significar que a veces se piden tecnologías por inercia y no por una necesidad real del proyecto. Además el hecho que se ignoren los títulos educativos indica que el mercado tecnológico valora la agilidad, las certificaciones y las habilidades técnicas directas por sobre la información tradicional. Y por último el peso que tiene la nube, los contenedores y la automatización refleja que las empresas operan bajo infraestructuras modernas y flexibles, exigiendo profesionales capaces de adaptarse rápidamente a entornos digitales complejos. 

## Recomendaciones
Según lo analizado podemos recomendar: 
1. Optimizar los perfiles de búsqueda: se deben ajustar las descripciones de los puestos para así evitar pedir una lista excesiva o muy rígida de 8 habilidades solo por seguir un estándar. Enfocarse en 3 o 4 habilidades que verdaderamente sean críticas para el éxito del rol.
2. Priorizar evaluaciones prácticas: al momento de reclutar, invertir los esfuerzos  en pruebas técnicas y demostraciones de habilidades en lugar de filtrar candidatos por títulos o años de experiencia teóricos que no sabemos si es real.
3. Impulsar planes de capacitación: ya que los perfiles de Sr y Semi Sr son los más solicitados y escasos, recomendamos diseñar programas de formación interna para así poder potenciar a los perfiles Jrs en tecnologías clave como Python, bases de datos y herramientas Cloud. 


## Cómo reproducir

1. Clonar este repositorio.
2. Crear un entorno virtual e instalar las dependencias necesarias.

   _Pendiente: publicar `requirements.txt` con las librerías utilizadas (pandas, etc.)._
3. El dataset principal (`nextgig_jobs_2026-06.parquet`) ya está disponible en la raíz del repositorio.
4. Ejecutar `notebooks/01_limpieza.ipynb` para generar el dataset limpio en `data/processed/`.
5. _Pendiente: notebooks de EDA y visualización, a agregar en etapas posteriores._

## Estructura del repositorio

```text
Consulting-Challenge/
│
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
├── images/
├── presentation/
└── README.md
```
