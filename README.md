# AlexaSkillArmando
Creación de una skill basada en el clima para Alexa, práctica en el salón.

## DESCRIPCION:

Práctica de Clase para la Unidad 3 de la Asignatura de Desarrollo Móvil Integral (DMI) impartida  
por el M.T.I Marco A. Ramírez Hernández

## HISTORIAL DE PRÁCTICAS:  
| No. | Nombre                                                  | Firmas | Estatus |  
|-----|---------------------------------------------------------|-------------|---------|  
| 26   | Creación de skill clima                                 | 6        | Activa  |  

## LISTA DE HERRAMIENTAS  
- Amazon Developer  
- OpenWeatherMap  

## AUTOR  
Elaborado por: [Armando Carrasco Vargas](https://github.com/MandoCV)


## Datos del Estudiante
- **Alumno**: Armando Carrasco Vargas
- **Carrera**: Ingeniería en Desarrollo y Gestión de Software
- **Grado**: 10
- **Grupo**: A
- **Matrícula**: 210124

## OBJETIVO  
Crear una skill para Alexa que se conecte a una API externa (como OpenWeatherMap) para recuperar y comunicar información actual sobre el clima de una ciudad. Los participantes aprenderán a desarrollar una skill básica para Alexa, integrando servicios web para obtener datos en vivo y ofrecer respuestas precisas a las consultas de los usuarios.

### Objetivos Generales:

1. **Desarrollar habilidades para crear skills en Alexa**  
   Los participantes aprenderán a crear una skill para Alexa, comprendiendo todo el proceso desde la configuración inicial en la consola de desarrolladores hasta la implementación de la lógica mediante AWS Lambda.

2. **Integrar servicios externos mediante APIs**  
   Se enseñará cómo conectar la skill con APIs externas, como una fuente de datos meteorológicos, para obtener información en tiempo real y presentarla de manera interactiva a los usuarios.

3. **Gestionar la lógica en la nube con AWS Lambda**  
   Los participantes se familiarizarán con AWS Lambda, aprendiendo a manejar la lógica y las funciones que permiten que la skill responda de manera eficiente a las solicitudes de los usuarios.

4. **Mejorar la interacción con los usuarios y aplicar buenas prácticas de desarrollo**  
   Se enfocarán en diseñar una experiencia de usuario fluida, capturando intenciones correctamente y proporcionando respuestas dinámicas, mientras aplican buenas prácticas para crear una skill robusta y escalable.

### Objetivos Específicos:

1. **Diseñar modelos de interacción eficientes**  
   Los participantes aprenderán a definir intenciones y frases de activación que permitan a los usuarios interactuar de manera intuitiva y fluida con la skill de Alexa.

2. **Integrar datos reales en tiempo real**  
   Se enseñará cómo obtener información actualizada desde una API externa y cómo hacer que Alexa entregue esos datos a los usuarios de manera clara y comprensible.

3. **Garantizar la robustez y fiabilidad de la skill**  
   Los participantes aprenderán a manejar errores y excepciones de forma adecuada, asegurando que la skill funcione correctamente incluso ante situaciones imprevistas.

4. **Crear una skill escalable y fácil de mantener**  
   Se enfocará en la importancia de estructurar el código de manera modular y eficiente, permitiendo que la skill se pueda ampliar o modificar con facilidad en el futuro.
# Descripción del Proceso

## 1. **Crear una cuenta de desarrollador en Amazon**  
Si no se tiene una cuenta de desarrollador en Amazon, se debe crear una en [Amazon Developer Console](https://developer.amazon.com/). Luego, se debe iniciar sesión y acceder a la consola de desarrollador.

![Imagen de cuenta Amazon Developer](Img/image.png)

## 2. **Crear un nuevo proyecto de Alexa**  
- En la consola de Alexa, se debe seleccionar "Create Skill" (Crear Skill).
- Elegir el idioma (por ejemplo, "Español").
- Seleccionar el tipo de skill "Custom" (Personalizado).
- Asignar un nombre a la skill (por ejemplo, "Clima Alexa").

![Captura de pantalla](<Img/Captura de pantalla 2024-12-05 001432.png>)

## 3. **Configurar las intenciones de la Skill**  
- Se debe crear una intención llamada `Clima`.
- Configurar frases de activación como se muestra en la imagen:  

![Configuración de intenciones](<Img/Captura de pantalla 2024-12-04 225146.png>)

## 4. **Verificación de intenciones en JSON**  
![Verificación en JSON](<Img/Captura de pantalla 2024-12-04 225318.png>)

## 5. **Reemplazar el `skillCode` de Lambda por el proporcionado por el docente**  
![Reemplazo de código Lambda](<Img/Captura de pantalla 2024-12-04 225833.png>)

![Configuración Lambda](<Img/Captura de pantalla 2024-12-04 225859.png>)

## 6. **Crear un API para la conectividad**  
![Creación de API](<Img/Captura de pantalla 2024-12-04 230046.png>)

## 7. **Aplicar las coordenadas**  
![Aplicación de coordenadas](<Img/Captura de pantalla 2024-12-04 230810.png>)

## 8. **Configurar el nombre de invocación**  
![Configuración de invocación](<Img/Captura de pantalla 2024-12-04 231508.png>)

## 9. **Personalizar el icono y agregarlo**  
![Personalización de icono](<Img/Captura de pantalla 2024-12-04 232033.png>)

## 10. **Configurar la privacidad y esperar a que validen**  
![Configuración de privacidad](<Img/Captura de pantalla 2024-12-04 232407.png>)  
![Validación](<Img/Captura de pantalla 2024-12-04 232444.png>)

## 11. **Realizar las pruebas**  
![Pruebas](<Img/Captura de pantalla 2024-12-04 233242.png>)

## 12. **Descargar e iniciar sesión con la misma cuenta para sincronizar y verificar en la app de Alexa móvil (sin dispositivo Alexa físico)**  
![Verificación en Alexa móvil](<Img/WhatsApp Image 2024-12-04 at 11.57.43 PM.jpeg>)

## 13. **Desarrollar la lógica de la skill usando AWS Lambda**  
- **Configurar AWS Lambda**: Se debe crear una nueva función Lambda en la consola de AWS, utilizando el código proporcionado por el docente.
- **Código para obtener el clima**: Se utilizará la API de OpenWeatherMap y se configurará el archivo `index` para interactuar con esta API. A continuación, se presenta un ejemplo de código para la función Lambda:

```javascript
const Alexa = require('ask-sdk-core');
const axios = require('axios');

const LaunchRequestHandler = {
  canHandle(handlerInput) {
    return Alexa.getRequestType(handlerInput.requestEnvelope) === 'LaunchRequest';
  },
  handle(handlerInput) {
    const speakOutput = 'Armando Carrasco skill Amazon';

    return handlerInput.responseBuilder
      .speak(speakOutput)
      .reprompt(speakOutput)
      .getResponse();
  }
};

const WeatherIntentHandler = {
  canHandle(handlerInput) {
    return (
      Alexa.getRequestType(handlerInput.requestEnvelope) === 'IntentRequest' &&
      Alexa.getIntentName(handlerInput.requestEnvelope) === 'Clima'
    );
  },
  async handle(handlerInput) {
    try {
      const apiKey = 'ea97d92f204870f342dc880f113943d3'; // Reemplaza con tu clave de API de OpenWeatherMap
      const lat = 19.050; // Reemplaza con la latitud deseada
      const lon = -98.200; // Reemplaza con la longitud deseada

      const response = await axios.get(
        `https://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&appid=${apiKey}&units=metric`
      );

      const temperature = response.data.main.temp;
      const weatherDescription = response.data.weather[0].description;
      const location = response.data.name;
      const humedad = response.data.main.humidity;
      const tem_max = response.data.main.temp_min;
      //NUEVO
      const sepone = response.data.sys.sunset;
      const sunsetDate = new Date(sepone);
      const sunsetHour = sunsetDate.getHours();
      const sunsetMinutes = sunsetDate.getMinutes();

      

      const speakOutput = `La temperatura actual en ${location} es de ${temperature} grados Celsius y la humedad es de ${humedad} y el sol se oculta a las ${sunsetHour}:${sunsetMinutes}.`;

      return handlerInput.responseBuilder.speak(speakOutput).getResponse();
    } catch (error) {
      console.log('Error al obtener el clima:', error);

      const speakOutput = 'Lo siento, no pude obtener la información del clima en este momento.';
      return handlerInput.responseBuilder.speak(speakOutput).getResponse();
    }
  },
};

const HelpIntentHandler = {
  canHandle(handlerInput) {
    return (
      Alexa.getRequestType(handlerInput.requestEnvelope) === 'IntentRequest' &&
      Alexa.getIntentName(handlerInput.requestEnvelope) === 'AMAZON.HelpIntent'
    );
  },
  handle(handlerInput) {
    const speakOutput = 'Puedes preguntarme sobre el clima diciendo: ¿Cuál es el clima actual?';

    return handlerInput.responseBuilder.speak(speakOutput).getResponse();
  },
};

const CancelAndStopIntentHandler = {
  canHandle(handlerInput) {
    return (
      Alexa.getRequestType(handlerInput.requestEnvelope) === 'IntentRequest' &&
      (Alexa.getIntentName(handlerInput.requestEnvelope) === 'AMAZON.CancelIntent' ||
        Alexa.getIntentName(handlerInput.requestEnvelope) === 'AMAZON.StopIntent')
    );
  },
  handle(handlerInput) {
    const speakOutput = '¡Hasta luego!';

    return handlerInput.responseBuilder.speak(speakOutput).getResponse();
  },
};

const FallbackIntentHandler = {
  canHandle(handlerInput) {
    return (
      Alexa.getRequestType(handlerInput.requestEnvelope) === 'IntentRequest' &&
      Alexa.getIntentName(handlerInput.requestEnvelope) === 'AMAZON.FallbackIntent'
    );
  },
  handle(handlerInput) {
    const speakOutput = 'Lo siento, no puedo ayudarte con eso. Por favor, inténtalo de nuevo.';

    return handlerInput.responseBuilder.speak(speakOutput).getResponse();
  },
};

const SessionEndedRequestHandler = {
  canHandle(handlerInput) {
    return Alexa.getRequestType(handlerInput.requestEnvelope) === 'SessionEndedRequest';
  },
  handle(handlerInput) {
    console.log(`Sesión terminada: ${JSON.stringify(handlerInput.requestEnvelope)}`);
    return handlerInput.responseBuilder.getResponse();
  },
};

const IntentReflectorHandler = {
  canHandle(handlerInput) {
    return Alexa.getRequestType(handlerInput.requestEnvelope) === 'IntentRequest';
  },
  handle(handlerInput) {
    const intentName = Alexa.getIntentName(handlerInput.requestEnvelope);
    const speakOutput = `Acabas de activar la intención ${intentName}.`;

    return handlerInput.responseBuilder.speak(speakOutput).getResponse();
  },
};

const ErrorHandler = {
  canHandle() {
    return true;
  },
  handle(handlerInput, error) {
    console.log(`Error manejado: ${JSON.stringify(error)}`);

    const speakOutput = 'Lo siento, hubo un problema al procesar tu solicitud. Por favor, inténtalo de nuevo.';

    return handlerInput.responseBuilder.speak(speakOutput).getResponse();
  },
};

exports.handler = Alexa.SkillBuilders.custom()
  .addRequestHandlers(
    LaunchRequestHandler,
    WeatherIntentHandler,
    HelpIntentHandler,
    CancelAndStopIntentHandler,
    FallbackIntentHandler,
    SessionEndedRequestHandler,
    IntentReflectorHandler
  )
  .addErrorHandlers(ErrorHandler)
  .lambda();

---
