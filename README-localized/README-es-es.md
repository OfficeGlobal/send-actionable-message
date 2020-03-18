# Enviar un mensaje que requiere acción mediante Microsoft Graph

Ejemplo de línea de comandos que usa la biblioteca [Microsoft Authentication](https://www.nuget.org/packages/Microsoft.Identity.Client) y la biblioteca de cliente [Microsoft Graph](https://www.nuget.org/packages/Microsoft.Graph/) para enviar un mensaje mediante una [tarjeta de mensaje que requiere acción](https://docs.microsoft.com/es-es/outlook/actionable-messages/) al usuario autenticado.

## Ejecución del ejemplo

Para ejecutar el ejemplo, debe registrar una aplicación en el [Portal de registro de aplicaciones](https://apps.dev.microsoft.com) para obtener un Id. de aplicación y luego copiar ese Id.en el archivo [App.config](./App.config).

### Registrar la aplicación

1. Vaya al [Portal de registro de aplicaciones de Microsoft](https://apps.dev.microsoft.com) e inicie sesión con las credenciales de su cuenta de Microsoft o de Office 365.
1. Haga clic en el botón **Agregar una aplicación**. Especifique un nombre para la aplicación y haga clic en **Crear aplicación**.
1. Haga clic en el botón **Agregar plataforma** y elija **Aplicación móvil**.
1. Haga clic en **Guardar**.

> **Nota:** En el momento de la redacción de este artículo, hay un error en el portal que agrega una entrada de plataforma **Web** al registro cuando se hace clic en **Guardar**. Si esto ocurre, simplemente haga clic en el botón **Eliminar** de la plataforma **Web** y haga clic en **Guardar** nuevamente.

Cuando termine, el registro debería ser similar al siguiente:

![Captura de pantalla del registro de la aplicación completado en el Portal de registro de aplicaciones](readme-images/app-registration.PNG)

Copie el valor de **Id. de aplicación**.

### Agregar el Id. de aplicación al proyecto

1. En el Explorador de soluciones, abra el archivo [App.config](App.config).
1. Busque la línea siguiente: 

    ```xml
    <add key="applicationId" value="" />
    ```
1. Pegue el Id. de aplicación que copió del portal en `value` y guarde el archivo. Por ejemplo, si usa el Id. de aplicación de la captura de pantalla anterior, la línea se actualizará a lo siguiente:

    ```xml
    <add key="applicationId" value="b9831d46-3f6b-4c77-82d3-220a9ea4e5ba" />
    ```

### Compilar y ejecutar la aplicación

Presione **F5** en Visual Studio para compilar y ejecutar la aplicación. Debe aparecer una ventana de símbolo del sistema y, a continuación, una ventana emergente de autenticación.

![Captura de pantalla de la ventana emergente de autenticación](readme-images/auth-popup.PNG)

Inicie sesión con una cuenta de Microsoft (con un buzón de Outlook.com) o con una cuenta de Office 365 (con Exchange Online). Revise la lista de permisos solicitados y haga clic en **Aceptar** o **Cancelar**. (**Nota:** elegir **Cancelar** provocará que la aplicación devuelva un error y no envíe un mensaje).

La ventana del símbolo del sistema debe mostrar `Message sent` para indicar que se envió con éxito. Vaya a la bandeja de entrada con Outlook en la Web para comprobar que el mensaje llegó.

### Modificar la tarjeta o el cuerpo del mensaje

Puede probar diferentes formatos para la tarjeta y el cuerpo del mensaje si modifica [Card.json](Card.json) y [MessageBody.html](MessageBody.html), respectivamente. Para crear cargas de tarjetas de prueba rápidamente, visite [https://messagecardplayground.azurewebsites.net/](https://messagecardplayground.azurewebsites.net/).