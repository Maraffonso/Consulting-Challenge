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

**Fuente complementaria:** [Stack Overflow Developer Survey, ediciones 2016 a 2026](https://survey.stackoverflow.co/) —  Se usa para medir tendencias (punto 3), porque el dataset principal es una foto de junio 2026 y no tiene historia. Aporta la perspectiva de los propios desarrolladores: qué tecnologías usan y cuáles quieren usar. Mide uso e interés del talento, no vacantes.

_Pendiente: período cubierto y variables a usar del dataset, a confirmar durante la limpieza y el EDA._

## Metodología

1. **Obtención de datos** — descarga del dataset principal de Kaggle y, como complemento, de la encuesta de Stack Overflow.
2. **Limpieza** — tratamiento de duplicados, valores nulos y conversión de tipos de datos, siguiendo el flujo estado inicial → duplicados → nulos → tipos → estado final.
3. **Análisis exploratorio (EDA)** — estadística descriptiva, distribuciones y relaciones entre variables.
4. **Tendencias del mercado** — evolución 2016–2026 de adopción de tecnologías, perfiles y modalidad de trabajo con la encuesta de Stack Overflow, y cruce con las ofertas (notebooks/03_tendencias_mercados.ipynb).
5. **Comparación de perfiles** — cruce de tecnologías, experiencia requerida y modalidad de trabajo (remoto/híbrido/presencial) entre roles tecnológicos.
6. **Síntesis de hallazgos y recomendaciones** accionables para el diseño del bootcamp.

_Pendiente: detalle de las preguntas de negocio concretas a contrastar, a definir una vez cerrado el EDA inicial._

## Hallazgos

Se completa luego del análisis exploratorio. 
 Que se descubre? 
 1. Un modelo estándar muy rígido: las ofertas de empleo piden, en casi todos los casos sin excepción un promedio exacto de 8 habilidades o tecnologías por puesto, sin importar si el trabajo es para un puesto Jrs o Srs.
 2. Las herramientas estrella: El lenguaje de Python lidera el mercado con 438 ofertas, luego le sigue SQL y herramientas de automatización y despliegue (CI/CD), además de plataformas en la nube como AWS y Kubernetes.
 3. Los roles mas buscados: son los puestos de ingeniería en la nube (Cloud Engineer) y desarrollo web (Full stack developer), estos concentran el mayor volumen de oportunidades.
 4. El perfil ideal: las empresas buscan perfiles con experiencia intermedia, alta (semi sr y sr). Además casi no piden títulos universitarios formales en los requisitos, enfocándose en lo que la persona sabe hacer en la práctica. 

Para el negocio muestra que dado que se piden 8 habilidades queda demostrado que las descripciones de los puestos suelen responder a plantillas estándar o requisitos fijos, lo que puede significar que a veces se piden tecnologías por inercia y no por una necesidad real del proyecto. Además el hecho que se ignoren los títulos educativos indica que el mercado tecnológico valora la agilidad, las certificaciones y las habilidades técnicas directas por sobre la información tradicional. Y por último el peso que tiene la nube, los contenedores y la automatización refleja que las empresas operan bajo infraestructuras modernas y flexibles, exigiendo profesionales capaces de adaptarse rápidamente a entornos digitales complejos.

Tendencias del mercado (punto 3)
Desarrolladores profesionales, Stack Overflow Developer Survey 2016–2026. Detalle, salvedades y explicaciones alternativas en la sección 7 de notebooks/03_tendencias_mercados.ipynb.

1. Python, SQL y TypeScript son el núcleo. Python pasó de 36 % a 56 % de adopción (2018–2026) y es la skill más pedida en las ofertas (47 %). TypeScript es la mayor subida de la serie (19 % → 49 %). Java (42 % → 27 %) y PHP (29 % → 18 %) pierden peso.
2. PostgreSQL desplazó a MySQL (30 % → 50 % contra 48 % → 29 %).
3. Cloud y contenedores dejaron de ser especialización. Docker 33 % (2019) → 47 %, Kubernetes 9 % → 21 %; en las ofertas, Kubernetes (22 %) y AWS (21 %) son las skills más pedidas después de Python y SQL.
4. El uso de IA en el trabajo pasó de 44 % (2023) a 87 % (2026).
5. Perfiles y modalidad. Datos e IA es la única familia de roles que crece desde 2023 (4,3 % → 7,2 %), empujada por el rol nuevo de ingeniero de IA; los roles clásicos de datos están planos. Dentro del desarrollo web, el front-end puro pierde peso (de 11 a 8 de cada 100 entre 2023 y 2026).
6. Interés no es demanda. Lo que más quieren aprender los desarrolladores es Rust, que aparece en el 0,1 % de las ofertas.

## Recomendaciones
Según lo analizado podemos recomendar: 
1. Optimizar los perfiles de búsqueda: se deben ajustar las descripciones de los puestos para así evitar pedir una lista excesiva o muy rígida de 8 habilidades solo por seguir un estándar. Enfocarse en 3 o 4 habilidades que verdaderamente sean críticas para el éxito del rol.
2. Priorizar evaluaciones prácticas: al momento de reclutar, invertir los esfuerzos  en pruebas técnicas y demostraciones de habilidades en lugar de filtrar candidatos por títulos o años de experiencia teóricos que no sabemos si es real.
3. Impulsar planes de capacitación: ya que los perfiles de Sr y Semi Sr son los más solicitados y escasos, recomendamos diseñar programas de formación interna para así poder potenciar a los perfiles Jrs en tecnologías clave como Python, bases de datos y herramientas Cloud.
4. Armar la base del programa con lo que se pide hoy y además crece: Python, SQL sobre PostgreSQL, TypeScript, Docker y un proveedor de nube. Python es lo más pedido en las ofertas (47 %) y pasó de 36 % a 56 % de uso entre 2018 y 2026; PostgreSQL pasó de 30 % a 50 % mientras MySQL cayó de 48 % a 29 %.
5. Enseñar nube y contenedores a todos los perfiles, no solo a Cloud Engineer. Docker pasó de 33 % (2019) a 47 % de uso y Kubernetes de 9 % a 21 %, y en las ofertas Kubernetes (22 %) y AWS (21 %) son lo más pedido después de Python y SQL.
6. Incluir el trabajo con asistentes de inteligencia artificial como práctica en todos los cursos, sin atarlo a una herramienta. Su uso en el trabajo pasó de 44 % en 2023 a 87 % en 2026, y la herramienta más usada cambia de un año al otro.
7. No basar el programa en tecnologías que vienen perdiendo lugar. Java (de 42 % a 27 %), PHP (de 29 % a 18 %) y MySQL como motor principal caen de forma sostenida. Java todavía aparece en el 16 % de las ofertas, así que puede quedar como contenido optativo.
8. Revisar el programa una vez por año con datos nuevos. En ocho años cambió cuál es la base de datos más usada y apareció una categoría entera de herramientas (IA) que hoy usa la gran mayoría; un programa fijo queda desactualizado rápido. 


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
