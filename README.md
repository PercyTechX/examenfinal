### 01. Módulo de Análisis: Definición Ontológica y Representación (Base para Entregables 1 y 4)

> "Actúa como un Analista de Conocimiento. Basado en la 'Descripción del Problema' (Sección 6.1 del examen), desarrolla los siguientes componentes:
>
> 1.  **Definición Ontológica (Sección 5.1):**
>     * Identifica todos los **Conceptos** clave (ej. 'Víctima', 'Rescatista', 'UnidadMóvil', 'Ubicación', 'Puente', etc.).
>     * Define las **Relaciones** entre ellos (ej. `transporta_a`, `se_encuentra_en`, `requiere_para_construir`).
>     * Lista los **Atributos** (ej. 'Capacidad' de UnidadMóvil, 'Estado' de Víctima).
>     * Define las **Restricciones** (ej. 'Unidad UM solo puede transportar 8 personas').
> 2.  **Red Semántica (Sección 5.1):** Proporciona una descripción textual o un formato (como DOT/Graphviz) que represente visualmente la ontología.
> 3.  **Representación del Problema (Sección 6.2):**
>     * **Entidades:** Lista todas las instancias específicas por enumeración (ej. `medico-01`, `um-01`, `um-02`, `tecnico-c1-01`, `ubicacion-C0`, `ubicacion-M`, etc.).
>     * **Predicados:** Define la lógica de predicados para representar el estado del mundo. Explica cada predicado (ej. `En(persona, ubicacion)`, `PuedeCruzar(ubicacion)`, `Estabilizado(victima)`, `Construido(puente)`).
> 4.  **Estado Inicial y Meta:**
>     * Usando los predicados definidos, describe el **Estado Inicial** (ej. `En(medico-01, C0)`, `En(victima-grave-01, M)`, `NoConstruido(puente-C1)`).
>     * Describe el **Objetivo/Meta** (ej. `En(victima-grave-01, C0)`, `En(victima-estable-01, C0)`, `En(medico-01, C0)`, `En(operador-c3-01, C0)`)."

---

### 02. Módulo de Diseño: Arquitectura del Agente Planificador (Base para Entregable 1)

> "Basado en el Módulo 01 y la Sección 5 del examen, diseña la arquitectura del agente planificador:
>
> 1.  **Tipo de Agente (Sección 5.2):** Justifica la elección (ej. Proactivo, Agente basado en metas).
> [cite_start]2.  **Medio Ambiente (Sección 5.3):** Clasifica el entorno según las 5 propiedades (ej. ¿Es accesible? ¿Determinista? ¿Estático?). [cite: 89-92]
> 3.  **Sensores y Percepciones (Sección 5.4, 5.5):** Describe cómo el agente "sabe" el estado del mundo. (Para PDDL, la percepción es el estado completo del mundo).
> 4.  **Espacio de Estados (Sección 5.6):** Explica qué constituye un 'estado' y da una estimación del tamaño del espacio de estados.
> 5.  **Acciones (Sección 5.7):** Define formalmente las acciones PDDL. Para cada acción (ej. `Mover(vehiculo, de, a)`, `ConstruirPuente(tecnicos, puente, ubicacion)`, `Estabilizar(medico, victima)`, `CargarPersona(persona, vehiculo, ubicacion)`):
>     * **Parámetros:**
>     * **Precondiciones:** (ej. para `Mover(UM-01, C0, C1)`, la precondición es `En(UM-01, C0)` y `Conectado(C0, C1)`).
>     * **Efectos:** (ej. `No(En(UM-01, C0))`, `En(UM-01, C1)`)."

---

### 03. Módulo de Implementación: Programas Fuentes (Entregable 02)

> "Genera los 'Programas Fuentes' en Python y PDDL para resolver el problema de planificación:
>
> 1.  **Dominio PDDL (`dominio.pddl`):** Escribe el archivo de dominio PDDL completo. Debe incluir:
>     * `:requirements` (ej. `:strips`, `:typing`)
>     * `:types` (ej. `persona`, `vehiculo`, `ubicacion`, `item` - `victima`, `rescatista`, `tecnico`, `UM`, `UP`, `PCP`, etc.)
>     * `:predicates` (Basados en el Módulo 01)
>     * `:actions` (Basadas en el Módulo 02, con sus `:parameters`, `:precondition` y `:effect`)
> 2.  **Problema PDDL (`problema.pddl`):** Escribe el archivo del problema. Debe incluir:
>     * `:domain` (que coincida con el nombre del dominio)
>     * `:objects` (Todas las entidades del Módulo 01)
>     * `:init` (El estado inicial del Módulo 01)
>     * `:goal` (El estado meta del Módulo 01)
> 3.  **Script Python (`resolver.py`):** Escribe un script de Python que utilice una biblioteca (como `python-planner`) para leer los archivos `dominio.pddl` y `problema.pddl`, llame a un planificador (ej. 'fast-downward'), y muestre el plan resultante."

---

### 04. Módulo de Ejecución y Evaluación (Base para Entregables 1 y 3)


> "Ahora, simula la ejecución y evalúa los resultados:
>
> 1.  **Procedimiento de Ejecución (Entregable 03):** Escribe las instrucciones paso a paso para ejecutar el `resolver.py` (ej. '1. Instalar biblioteca `python-planner`. 2. Instalar el planificador 'fast-downward'. 3. Ejecutar `python resolver.py`).
> 2.  **Plan de Salida (Resultados):** Muestra el plan de acción (la secuencia de acciones) que generó el planificador.
> 3.  **Análisis de Resultados (Sección 7.1):** Analiza el plan. ¿Es lógico? ¿Hay pasos innecesarios? ¿Resuelve el problema completamente?
> 4.  **Métricas de Racionalidad (Sección 5.10):** Propón 3 métricas para medir la racionalidad o rendimiento del agente (ej. 'Costo total del plan' (número de acciones), 'Eficiencia de transporte' (viajes realizados), 'Tiempo de cómputo'). Calcula estas métricas para el plan generado."

---

### 05. Módulo de Consolidación: Documento Final (Entregable 01)


> "Usando los resultados de los Módulos 01, 02 y 04, redacta el **Documento Final (Entregable 01)**. :
>
> 1.  **Título, Autores, Resumen, Palabras Clave**
> 2.  **Introducción:** (Describe el problema de rescate y el objetivo de usar un planificador de IA).
> 3.  **Planteamiento del Problema:** (Inserta aquí la **Definición Ontológica** y la **Red Semántica** del Módulo 01).
> 4.  **Metodología de Desarrollo:** (Describe la metodología. Inserta aquí el **Diseño del Agente** (Tipo, Entorno, etc.) del Módulo 02).
> 5.  **Construcción de ComponentEscribe la lógica de predicados para representar el mundo, explique cada predicado, presente ejemplos de los predicados usando las entidades identificadas.s:** (Explica cómo se construyó la solución. Inserta aquí la **Representación del Problema** (Predicados, Entidades) del Módulo 01 y la **Definición de Acciones** del Módulo 02. Incluye fragmentos clave del código PDDL del Módulo 03 como explicación).
> 6.  **Experimentación y Análisis:** (Inserta aquí los **Resultados** (el plan), el **Análisis de Resultados** y las **Métricas** del Módulo 04).
> 7.  **Conclusiones:** (Concluye sobre el rendimiento y la viabilidad de la solución basada en las métricas).
> 8.  **Recomendaciones:** (Propón 3 mejoras).
> 9.  **Referencias:** (Lista las bibliotecas o papers usados)."
