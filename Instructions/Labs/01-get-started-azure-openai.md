# Laboratorio 01: Comenzar a usar el Servicio Azure OpenAI

### Duración Estimada: 40 minutos

## Escenario del Laboratorio
El Servicio Azure OpenAI incorpora los modelos de IA generativa desarrollados por OpenAI a la plataforma Azure, lo que le permite desarrollar potentes soluciones de IA que se benefician de la seguridad, la escalabilidad y la integración de los servicios que ofrece la plataforma de nube de Azure. En este ejercicio, aprenderá cómo comenzar con Azure OpenAI mediante el aprovisionamiento del servicio como un recurso de Azure y el uso de Azure OpenAI Studio para implementar y explorar los modelos de OpenAI.

## Objetivos del laboratorio
En este laboratorio, completará las siguientes tareas:

- Tarea 1: Aprovisionar un recurso de Azure OpenAI
- Tarea 2: Implementar un modelo
- Tarea 3: Explorar un modelo en el Área de juegos (Playground) Completions
- Tarea 4: Utilizar el Área de juegos Chat
- Tarea 5: Explorar prompts y parámetros 
- Tarea 6: Explorar la generación de código

### Tarea 1: Aprovisionar un recurso de Azure OpenAI

Antes de poder usar modelos de Azure OpenAI, debe aprovisionar un recurso de Azure OpenAI en su suscripción de Azure.

1. En el **Portal de Azure**, busque **OpenAI** y seleccione **Azure OpenAI**.

   ![](../media/openai8.png)

2. En la hoja **Servicios de IA de Azure | Azure OpenAI**, haga clic en **+ Crear**.

   ![](../media/openai_create1.png)

3. Cree un recurso **Azure OpenAI** con la siguiente configuración:
   
    - **Suscripción**: Predeterminada - Suscripción preasignada.
    - **Grupo de recursos**: openai-<inject key="DeploymentID" enableCopy="false"></inject>
    - **Región**: Seleccione <inject key="Region" enableCopy="false" />
    - **Nombre**: OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject>
    - **Plan de tarifa**: Standard S0
  
   ![](../media/openai-lab01_01.png "Create Azure OpenAI resource")

4. Haga clic en **Siguiente** tres veces y haga clic en **Crear**.

4. Espere a que se complete la implementación. Luego, vaya al recurso de Azure OpenAI implementado en el Portal de Azure.

#### Validación

> ¡**Felicitaciones** por completar la tarea! Ahora es momento de validarla. Estos son los pasos:
> - Presione el botón Validar para la tarea correspondiente. Si recibe un mensaje de éxito, puede continuar con la siguiente tarea. 
> - De lo contrario, lea atentamente el mensaje de error y vuelva a intentar el paso, siguiendo las instrucciones de la guía de laboratorio.
> - Si necesita ayuda, comuníquese con nosotros a labs-support@spektrasystems.com. Estamos disponibles las 24 horas del día, los 7 días de la semana para ayudarlo.

   <validation step="1fa0e87b-eb46-463d-b63b-edf6e2282e16" />

### Tarea 2: Implementar un modelo

Azure OpenAI ofrece un portal basado en la web llamado **Azure OpenAI Studio**, que puede usar para implementar, administrar y explorar modelos. Comenzará su exploración de Azure OpenAI usando Azure OpenAI Studio para implementar un modelo.

1. En el **Portal de Azure**, busque **OpenAI** y seleccione **Azure OpenAI**.

   ![](../media/openai8.png)

2. En la hoja **Azure AI Services | Azure OpenAI**, seleccione **OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject>**

   ![](../media/OpenAI_select.png)

3. En el panel de recursos de Azure OpenAI, haga clic en **Ir a Azure OpenAI Studio** para navegar a **Azure AI Studio**.

   ![](../media/openai_studio.png)

4. Después de navegar a Azure AI Studio, haga clic en la ventana emergente **Explorar la nueva experiencia** en la parte superior.

   ![](../media/explore_new-exp.jpg)

5. Haga clic en **Implementaciones (1)** en el panel de navegación izquierdo, haga clic en **+ Implementar modelo** y seleccione **Implementación del modelo base (2)**.

   ![](../media/deploy-2.jpg)

6. En la ventana **Seleccionar un modelo**, seleccione **gpt-35-turbo (1)** y haga clic en **Confirmar (2)**.

   ![](../media/mew5.png)

7. Dentro de la interfaz emergente **Implementar modelo**, ingrese los siguientes detalles:
    
    - **Nombre de implementación**: my-gpt-model (1) 
    - **Versión de modelo**: 0613 (2)
    - **Tipo de implementación**: Standard (3)
    - **Tokens por límite de velocidad por minuto (miles)**: 10K (4)
    - **Habilitar cuota dinámica**: Habilitado (5)
    - Haga clic en **Implementar** (6)
  
      ![](../media/new3.png)

8. Esto implementará un modelo con el que podrá experimentar a medida que avanza.

   > **Nota**: Puede ignorar cualquier error relacionado con la asignación de roles para ver los límites de cuota.

   > **Nota**: Azure OpenAI incluye varios modelos, cada uno optimizado para un equilibrio diferente de capacidades y rendimiento. En este ejercicio, usará el modelo **GPT-35-Turbo**, que es un buen modelo general para resumir y generar lenguaje natural y código. Para obtener más información sobre los modelos disponibles en Azure OpenAI, consulte [Modelos](https://learn.microsoft.com/azure/cognitive-services/openai/concepts/models) en la documentación de Azure OpenAI.

#### Validación

   <validation step="3b4a472e-f956-45d8-b828-3e2cc01c2e88" />

> ¡**Felicitaciones** por completar la tarea! Ahora es momento de validarla. Estos son los pasos:
> - Presione el botón Validar para la tarea correspondiente. Si recibe un mensaje de éxito, puede continuar con la siguiente tarea. 
> - De lo contrario, lea atentamente el mensaje de error y vuelva a intentar el paso, siguiendo las instrucciones de la guía de laboratorio.
> - Si necesita ayuda, comuníquese con nosotros a labs-support@spektrasystems.com. Estamos disponibles las 24 horas del día, los 7 días de la semana para ayudarlo.


### Tarea 3: Explorar un modelo en el Área de juegos (Playground) Completions

Los *Playgrounds* (Patios de juego) son interfaces útiles en Azure OpenAI Studio que puede usar para experimentar con sus modelos implementados sin necesidad de desarrollar su propia aplicación cliente.

1. En Azure OpenAI Studio, en el panel izquierdo, bajo **Patios de juego**, seleccione **Finalizaciones**.

2. En la página **Finalizaciones**, asegúrese de que su implementación **my-gpt-model** esté seleccionada y, luego, en la lista **Ejemplos**, seleccione **Generar un cuestionario**.

    El ejemplo de texto resumido consta de un *prompt* que proporciona un texto para indicar al modelo qué tipo de respuesta se requiere e incluye información contextual.

3. En la parte inferior de la página, observe la cantidad de *tokens* detectados en el texto. Los tokens son las unidades básicas de un prompt - esencialmente palabras o partes de palabras en el texto.

4. Use el botón **Generar** para enviar el prompt al modelo y obtener una respuesta.

    La respuesta consta de un cuestionario basado en el ejemplo del prompt.

    >**Nota**: Puede usar el botón **Regenerar** para volver a enviar el prompt (se han realizado nuevos cambios) y tenga en cuenta que la respuesta puede variar con respecto a la original. Un modelo de IA generativa puede producir un nuevo lenguaje cada vez que es llamado.

5. Use el botón **Ver código** para ver el código que usaría una aplicación cliente para enviar el prompt. Puede seleccionar su lenguaje de programación preferido. El aviso contiene el texto que envió al modelo. La solicitud se envía a la API *Completions* para su servicio Azure OpenAI.

### Tarea 4: Utilizar el Área de juegos Chat

El patio de juegos de *Chat* proporciona una interfaz de chatbot para los modelos GPT 3.5 y superiores. Utiliza la API *ChatCompletions* en lugar de la API *Completions* anterior.

1. En la sección **Patios de juego**, seleccione la página **Chat** y asegúrese de que el modelo **my-gpt-model** esté seleccionado en el panel de configuración.

2. En la sección **Configuración**, en el cuadro **Mensaje del sistema**, reemplace el texto actual con la siguiente oración: `The system is an AI teacher that helps people learn about AI`.

3. Debajo del cuadro **Mensaje del sistema**, haga clic en **+ Agregar** e ingrese el siguiente mensaje y respuesta en los cuadros designados:

    - **Usuario**: `What are different types of artificial intelligence?`
    
    - **Asistente**: `There are three main types of artificial intelligence: Narrow or Weak AI (such as virtual assistants like Siri or Alexa, image recognition software, and spam filters), General or Strong AI (AI designed to be as intelligent as a human being. This type of AI does not currently exist and is purely theoretical), and Artificial Superintelligence (AI that is more intelligent than any human being and can perform tasks that are beyond human comprehension. This type of AI is also purely theoretical and has not yet been developed).`

    > **Nota**: Se utilizan algunos ejemplos para proporcionar al modelo ejemplos de los tipos de respuestas que se esperan. El modelo intentará reflejar el tono y el estilo de los ejemplos en sus propias respuestas.
  
4. Haga clic en **Aplicar cambios** y luego en **Continuar** en la pestaña emergente **Actualizar mensaje de sistema** para iniciar una nueva sesión y establecer el contexto de comportamiento del sistema de chat.

5. En el cuadro de consulta en la parte inferior de la página, ingrese el texto `What is artificial intelligence?`

6. Use el botón **Enviar** para enviar el mensaje y ver la respuesta.

    > **Nota**: Es posible que reciba una respuesta que indique que la implementación de la API aún no está lista. Si es así, espere unos minutos e intente nuevamente.

7. Revise la respuesta y luego envíe el siguiente mensaje para continuar la conversación: `How is it related to machine learning?`

8. Revise la respuesta y observe que se conserva el contexto de la interacción anterior (para que el modelo comprenda que "it" se refiere a la inteligencia artificial).

9. Use el botón **Ver código** para ver el código de la interacción. El mensaje consta del mensaje del *sistema*, los pocos ejemplos de mensajes del *usuario* y del *asistente*, y la secuencia de mensajes del *usuario* y del *asistente* en la sesión de chat hasta el momento.

### Tarea 5: Explorar prompts y parámetros 

Puede utilizar el mensaje y los parámetros para maximizar la probabilidad de generar la respuesta que necesita.

1. En el panel **Configuración**, seleccione **Parámetro** y configure los siguientes valores de parámetro:
    - **Temperatura**: 0
    - **Longitud máxima (tokens)**: 500

2. Envíe el siguiente mensaje en la sesión de chat

    ```
    Write three multiple choice questions based on the following text.

    Most computer vision solutions are based on machine learning models that can be applied to visual input from cameras, videos, or images.*

    - Image classification involves training a machine learning model to classify images based on their contents. For example, in a traffic monitoring solution you might use an image classification model to classify images based on the type of vehicle they contain, such as taxis, buses, cyclists, and so on.*

    - Object detection machine learning models are trained to classify individual objects within an image, and identify their location with a bounding box. For example, a traffic monitoring solution might use object detection to identify the location of different classes of vehicle.*

    - Semantic segmentation is an advanced machine learning technique in which individual pixels in the image are classified according to the object to which they belong. For example, a traffic monitoring solution might overlay traffic images with "mask" layers to highlight different vehicles using specific colors.
    ```

3. Revise los resultados, los cuales deben consistir de preguntas de opción múltiple que un maestro podría usar para evaluar a los estudiantes sobre los temas de visión artificial en el prompt. La respuesta total debe ser menor que la longitud máxima que especificó como parámetro.

    Observe lo siguiente sobre el prompt y los parámetros que utilizó:

    - El prompt indica específicamente que el resultado deseado debe ser tres preguntas de opción múltiple.
    
    - Los parámetros incluyen *Temperatura*, que controla el grado en el que la generación de respuestas incluye un elemento de aleatoriedad. El valor **0** utilizado en su envío minimiza la aleatoriedad, lo que da como resultado respuestas estables y predecibles.

### Tarea 6: Explorar la generación de código

Además de generar respuestas en lenguaje natural, puede utilizar modelos GPT para generar código.

1. En el panel **Configuración**, seleccione la plantilla **Ejemplo vacío** y luego haga clic en **Continuar** en la pestaña emergente **Actualizar mensaje de sistema** para restablecer el mensaje del sistema.

2. Ingrese el mensaje del sistema: `You are a Python developer.` y haga clic en **Aplicar cambios** y luego haga clic en **Continuar** en la pestaña emergente **Actualizar mensaje de sistema**.

3. En el panel **Sesión de chat**, seleccione **Borrar chat** y luego haga clic en **Borrar** en la pestaña Borrar chat para borrar el historial de chat e iniciar una nueva sesión.

2. Envíe el siguiente mensaje de usuario:

    ```
    Write a Python function named Multiply that multiplies two numeric parameters.
    ```

5. Revise la respuesta, que debe incluir un código de Python de ejemplo que cumple con el requisito en el prompt.

## Resumen

En este laboratorio, ha logrado lo siguiente:
-   Aprovisionar un recurso de Azure OpenAI
-   Implementar un modelo de Azure OpenAI dentro de Azure OpenAI Studio
-   Usar el área de juegos de chat para utilizar las funcionalidades de prompts, parámetros y generación de código

### Ha completado con éxito el laboratorio
