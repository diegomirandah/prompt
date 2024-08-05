# Prompt

# Code extract
```
criterios_contribucion = """
Una contribución se considera como cualquier aporte que:
- Menciones explícitas de acciones que avanzan hacia la meta, como "sugiero", "propongo", "completé", "investigué sobre".
- Declaraciones que aportan nueva información o ideas relevantes al objetivo grupal.
- Contribuciones directas al problema o proyecto, como resolver una parte del trabajo o presentar un resultado.
"""

context = 'Las siguientes intervenciones son de un equipo ágil de desarrollo que deben estimar la complejidad de una historia de usuario\n'

context = 'Intervenciones previas:\n'
if len(block_before) == 0:
    context += "No hay intervenciones previas\n"
for index, row in block_before.iterrows():
    context += f"{row['speaker']}: {row['text']}\n"

context += f"\nIntervención actual:\n{df.iloc[i]['speaker']}: {df.iloc[i]['text']}\n"

context += '\nIntervenciones posteriores:\n'
if len(block_after) == 0:
    context += "No hay intervenciones posteriores\n"
for index, row in block_after.iterrows():
    context += f"{row['speaker']}: {row['text']}\n"

# Prepara la pregunta para el modelo de OpenAI
prompt = f"{context}\n{criterios_contribucion}\n\n¿La intervención actual, es una contribución según los criterios mencionados?\n"
prompt = prompt + "Si o No"
```
# Example
```
Las siguientes intervenciones son de un equipo ágil de desarrollo que deben estimar la complejidad de una historia de usuario

Intervenciones previas:
Ana: Creo que deberíamos considerar el tiempo que nos tomó la última tarea similar.
Carlos: Sí, y también podríamos dividir esta tarea en partes más pequeñas.
Laura: Ayer investigué sobre herramientas que nos pueden ayudar a automatizar esta parte del proceso.
Miguel: Buena idea, Laura. Podríamos usar esas herramientas para reducir el tiempo de desarrollo.

Intervención actual:
Ana: Sugiero que utilicemos la herramienta que mencionó Laura y probemos su efectividad en una tarea pequeña primero.

Intervenciones posteriores:
Carlos: Me parece bien, así podríamos ver si realmente nos ayuda.
Laura: Estoy de acuerdo, además tengo algunos datos sobre el uso de esa herramienta en otros proyectos.
Miguel: Perfecto, entonces probamos con una tarea pequeña y medimos los resultados.

Una contribución se considera como cualquier aporte que:
- Menciones explícitas de acciones que avanzan hacia la meta, como "sugiero", "propongo", "completé", "investigué sobre".
- Declaraciones que aportan nueva información o ideas relevantes al objetivo grupal.
- Contribuciones directas al problema o proyecto, como resolver una parte del trabajo o presentar un resultado.

¿La intervención actual, es una contribución según los criterios mencionados?
Si o No
```
