# Enviar mensagem acionável via Microsoft Graph

Um exemplo de linha de comando que usa a [Biblioteca de Autenticação da Microsoft](https://www.nuget.org/packages/Microsoft.Identity.Client) e a [Biblioteca de Clientes do Microsoft Graph](https://www.nuget.org/packages/Microsoft.Graph/) para enviar uma mensagem com um [cartão de mensagem acionável ao usuário autenticado](https://docs.microsoft.com/en-us/outlook/actionable-messages/).

## Execução do exemplo

Para executar o exemplo, você precisará registrar um aplicativo no [Portal de Registro de Aplicativo](https://apps.dev.microsoft.com) para obter uma ID de aplicativo e, em seguida, copiar essa ID de aplicativo para o arquivo [App.config](./App.config).

### Registrar o aplicativo

1. Vá para o [Portal de Registro de Aplicativo](https://apps.dev.microsoft.com) e entre com uma conta da Microsoft ou com uma conta do Office 365.
1. Clique no botão **Adicionar um aplicativo**. Forneça um Nome para seu aplicativo e clique em **Criar aplicativos**.
1. Clique no botão **Adicionar Plataforma** e escolha **Aplicativos Móveis**.
1. Clique em **Salvar**

> **Observação:** A partir do momento da elaboração deste artigo, há um bug no portal que adiciona uma entrada de plataforma **Web** ao seu registro quando você clica em **Salvar**. Se isso acontecer, basta clicar no botão **Excluir** na plataforma **Web** e clicar em**Salvar** novamente.

Quando terminar, o registro deverá ser semelhante a este:

![Uma captura de tela do registro do aplicativo concluído no Portal de Registro de Aplicativos](readme-images/app-registration.PNG)

Copie o valor de **ID do Aplicativo**.

### Adicionar a ID do aplicativo ao projeto

1. Abra o arquivo [App.config](App.config) no Gerenciador de soluções.
1. Encontre a seguinte linha: 

    ```xml
    <add key="applicationId" value="" />
    ```
1. Cole a ID do aplicativo que você copiou do portal para o `valor` e salve o arquivo. Por exemplo, usando a ID de aplicativo da captura de tela acima, a linha seria atualizada para:

    ```xml
    <add key="applicationId" value="b9831d46-3f6b-4c77-82d3-220a9ea4e5ba" />
    ```

### Criar e executar o aplicativo

Pressione **F5** no Visual Studio para criar e executar o aplicativo. Será exibida uma janela de linha de comando e será exibida uma janela de pop-up de autenticação.

![Uma captura de tela da janela pop-up de autenticação](readme-images/auth-popup.PNG)

Faça logon com uma conta da Microsoft (com uma caixa de correio do Outlook.com) ou com a conta do Office 365 (com o Exchange Online). Examine a lista de permissões solicitadas e clique em **Aceitar** ou **Cancelar**. (**Observação:** escolher **Cancelar** resultará no aplicativo que retorna um erro e não envia uma mensagem.)

A janela do linha de comando deve exibir`Mensagem enviada` para indicar sucesso. Verifique a mensagem na caixa de entrada usando o Outlook na Web.

### Modificar o cartão ou o corpo da mensagem

Você pode experimentar diferentes formatos para o cartão e corpo da mensagem modificando [Card.json](Card.json) e [MessageBody.html](MessageBody.html), respectivamente. Para criar rapidamente cargas de cartão de teste, visite [https://messagecardplayground.azurewebsites.net/](https://messagecardplayground.azurewebsites.net/).