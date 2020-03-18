# 通过 Microsoft Graph 发送可操作邮件

一个命令行示例，使用 [Microsoft 身份验证库](https://www.nuget.org/packages/Microsoft.Identity.Client)和 [Microsoft Graph 客户端库](https://www.nuget.org/packages/Microsoft.Graph/)将包含[可操作邮件卡片](https://docs.microsoft.com/en-us/outlook/actionable-messages/)的邮件发送到经过身份验证的用户。

## 运行示例

为了运行该示例，需要在[应用程序注册门户](https://apps.dev.microsoft.com)中注册一个应用程序以获得一个应用程序 ID，然后将该应用程序 ID 复制到 [App.config](./App.config) 文件中。

### 注册应用程序

1. 转到[应用程序注册门户](https://apps.dev.microsoft.com)，并使用 Microsoft 帐户或 Office 365 帐户登录。
1. 单击“**添加应用**”按钮。输入应用程序的“名称”，单击“**创建应用程序**”。
1. 单击“**添加平台**”按钮，然后选择“**移动应用程序**”。
1. 单击“**保存**”

> **注意：**在撰写本文时，门户中存在一个 bug，当你单击“**保存**”时，该 bug 会将 **Web** 平台条目添加到您的注册。如果发生这种情况，只需单击 **Web** 平台上的“**删除**”按钮，然后再次单击“**保存**”。

完成后，注册应看起来如下所示：

![应用注册门户中完成的应用注册的屏幕截图](readme-images/app-registration.PNG)

复制“**应用程序 Id**”的值

### 添加应用程序 ID 至项目

1. 在“解决方案资源管理器”中打开 [App.config](App.config) 文件。
1. 查找下列行： 

    ```xml
    <add key="applicationId" value="" />
    ```
1. 将从门户复制的应用程序 ID 粘贴到`值`并保存文件。例如，使用上面的屏幕截图中的应用程序 ID，该行将更新为：

    ```xml
    <add key="applicationId" value="b9831d46-3f6b-4c77-82d3-220a9ea4e5ba" />
    ```

### 构建并运行应用程序

在 Visual Studio 中按 **F5** 构建并运行应用程序。将出现一个命令提示符窗口，然后将显示一个弹出的身份验证窗口。

![身份验证弹出窗口的屏幕截图](readme-images/auth-popup.PNG)

使用 Microsoft 帐户（通过 Outlook.com 邮箱）或 Office 365 帐户（通过 Exchange Online）登录。查看请求的权限的列表，然后单击“**接受**”或“**取消**”。（**注意：**选择“**取消**”会导致应用返回错误，而不是发送邮件。）

命令提示符窗口应输出“`邮件已发送`”，表示成功。使用 Outlook 网页版查看收件箱中的邮件。

### 修改邮件卡片或正文

可以通过分别修改 [Card.json](Card.json) 和 [MessageBody.html](MessageBody.html) 来尝试卡片和消息正文不同的格式。要快速构建测试卡片有效负载，请访问 [https://messagecardplayground.azurewebsites.net/](https://messagecardplayground.azurewebsites.net/)。