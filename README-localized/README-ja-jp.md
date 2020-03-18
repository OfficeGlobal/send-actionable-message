# Microsoft Graph を使用してアクション可能メッセージを送信する

[Microsoft 認証ライブラリ](https://www.nuget.org/packages/Microsoft.Identity.Client)と [Microsoft Graph クライアント ライブラリ](https://www.nuget.org/packages/Microsoft.Graph/)を使用して、メッセージと[アクション可能メッセージ カード](https://docs.microsoft.com/en-us/outlook/actionable-messages/)を認証済みのユーザーに送信するコマンド ラインのサンプルです。

## サンプルの実行

サンプルを実行するには、アプリケーション ID を取得するためにアプリケーションを[アプリケーション登録ポータル](https://apps.dev.microsoft.com)に登録し、そのアプリケーション ID を [App.config](./App.config) ファイルにコピーする必要があります。

### アプリケーションの登録

1. [アプリケーション登録ポータル](https://apps.dev.microsoft.com) に移動し、Microsoft アカウントまたは Office 365 アカウントのいずれかでサインインします。
1. [**アプリの追加**] ボタンをクリックします。アプリケーションの名前を入力し、[**アプリケーションの作成**] をクリックします。
1. [**プラットフォームの追加**] ボタンをクリックし、[**モバイル アプリケーション**] を選択します。
1. [**保存**] をクリックします。

> **注:**この記述の時点では、[**保存**] をクリックすると **Web** プラットフォーム エントリが登録に追加される不具合がポータルにあります。この場合は、**Web** プラットフォームの [**削除**] ボタンをクリックし、もう一度 [**保存**] をクリックします。

完了すると、登録は次のようになります。

![アプリケーション登録ポータルで登録が完了したアプリのスクリーンショット](readme-images/app-registration.PNG)

[**アプリケーション ID**]の値をコピーします。

### アプリケーション ID をプロジェクトに追加する

1. ソリューション エクスプローラーで、[App.config](App.config) ファイルを開きます。
1. 次の行を探します。 

    ```xml
    <add key="applicationId" value="" />
    ```
1. ポータルからコピーしたアプリケーション ID を`値`に貼り付け、ファイルを保存します。たとえば、上記のスクリーンショットのアプリケーション ID を使用すると、次のように更新されます。

    ```xml
    <add key="applicationId" value="b9831d46-3f6b-4c77-82d3-220a9ea4e5ba" />
    ```

### アプリの構築と実行

Visual Studio で **F5** を押して、アプリを構築して実行します。コマンド プロンプト ウィンドウが表示され、ポップアップ認証ウィンドウが表示されます。

![認証ポップアップ ウィンドウのスクリーンショット](readme-images/auth-popup.PNG)

Microsoft アカウント (Outlook.com メールボックスを使用) または Office 365 アカウント (Exchange Online を使用) でログインします。要求されたアクセス許可のリストを確認し、[**承諾**] または [**キャンセル**] をクリックします。(**注**: [**キャンセル**] を選択すると、アプリでエラーが返され、メッセージは送信されません。)

コマンド プロンプト ウィンドウに、成功を示すために [`メッセージが送信されました`] が表示されるはずです。Outlook on the web を使用して受信トレイからメッセージを確認します。

### メッセージ カードや本文を変更する

[Card.json](Card.json) と [MessageBody.html](MessageBody.html) をそれぞれ変更することにより、カードとメッセージ本文に異なる形式を試すことができます。テスト カードのペイロードをすばやく構築するには、[https://messagecardplayground.azurewebsites.net/](https://messagecardplayground.azurewebsites.net/) にアクセスします。