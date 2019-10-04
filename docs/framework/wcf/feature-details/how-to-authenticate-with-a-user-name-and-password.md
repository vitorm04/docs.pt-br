---
title: 'Como: fazer a autenticação com um nome de usuário e senha'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: 33205f9e12fcee53f2f29b63b836ea0cbc792025
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834731"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>Como: fazer a autenticação com um nome de usuário e senha

Este tópico demonstra como habilitar um serviço de Windows Communication Foundation (WCF) para autenticar um cliente com um nome de usuário e senha de domínio do Windows. Ele pressupõe que você tenha um serviço WCF em funcionamento e hospedado internamente. Para obter um exemplo de como criar um serviço WCF auto-hospedado básico, consulte [introdução tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md). Este tópico pressupõe que o serviço esteja configurado no código. Se você quiser ver um exemplo de configuração de um serviço semelhante usando um arquivo de configuração, consulte [Message Security User Name](../samples/message-security-user-name.md).

Para configurar um serviço para autenticar seus clientes usando o nome de usuário e as senhas do domínio do Windows, use o <xref:System.ServiceModel.WSHttpBinding> e defina sua propriedade `Security.Mode` como `Message`. Além disso, você deve especificar um certificado X509 que será usado para criptografar o nome de usuário e a senha à medida que eles forem enviados do cliente para o serviço.

No cliente do, você deve solicitar o nome de usuário e a senha e especificar as credenciais do usuário no proxy do cliente WCF.

## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>Para configurar um serviço WCF para autenticar usando o nome de usuário e a senha do domínio do Windows

1. Crie uma instância do <xref:System.ServiceModel.WSHttpBinding>, defina o modo de segurança da associação como <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, defina o `ClientCredentialType` da associação como <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType> e adicione um ponto de extremidade de serviço usando a associação configurada ao host de serviço, conforme mostrado no código a seguir :

    ```csharp
    // ...
    var userNameBinding = new WSHttpBinding();
    userNameBinding.Security.Mode = SecurityMode.Message;
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");
    // ...
    ```

2. Especifique o certificado do servidor usado para criptografar as informações de nome de usuário e senha enviadas pela conexão. Esse código deve seguir imediatamente o código acima. O exemplo a seguir usa o certificado criado pelo arquivo setup. bat do exemplo de [nome de usuário de segurança de mensagem](../samples/message-security-user-name.md) :

    ```csharp
    // ...
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");
    // ...
    ```

    Você pode usar seu próprio certificado, basta modificar o código para se referir ao seu certificado. Para obter mais informações sobre como criar e usar certificados, consulte [trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Verifique se o certificado está no repositório de certificados pessoas confiáveis para o computador local. Você pode fazer isso executando MMC. exe e selecionando o **arquivo**, **Adicionar/remover snap-in...** item de menu. Na caixa de diálogo **Adicionar ou remover snap-ins** , selecione o **snap-in certificados** e clique em **Adicionar**. Na caixa de diálogo snap-in de certificados, selecione **conta de computador**. Por padrão, o certificado gerado do exemplo de nome de usuário de segurança de mensagem estará localizado na pasta pessoal/certificados.  Ele será listado como "localhost" na coluna emitido para na janela do MMC. Arraste e solte o certificado na pasta **pessoas confiáveis** . Isso permitirá que o WCF trate o certificado como um certificado confiável ao executar a autenticação.

## <a name="to-call-the-service-passing-username-and-password"></a>Para chamar o nome de usuário e a senha do serviço

1. O aplicativo cliente deve solicitar seu nome de usuário e senha. O código a seguir solicita o nome de usuário e a senha:

    > [!WARNING]
    > Esse código não deve ser usado em produção, pois a senha é exibida durante a inserção.

    ```csharp
    public static void GetPassword(out string username, out string password)
    {
        Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");
        Console.WriteLine("   Enter username:");
        username = Console.ReadLine();
        Console.WriteLine("   Enter password:");
        password = Console.ReadLine();
    }
    ```

2. Crie uma instância do proxy do cliente especificando as credenciais do cliente, conforme mostrado no código a seguir:

    ```csharp
    string username;
    string password;

    // Instantiate the proxy.
    var proxy = new Service1Client();

    // Prompt the user for username & password.
    GetPassword(out username, out password);

    // Set the user's credentials on the proxy.
    proxy.ClientCredentials.UserName.UserName = username;
    proxy.ClientCredentials.UserName.Password = password;

    // Treat the test certificate as trusted.
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;
    // Call the service operation using the proxy
    ```

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [Segurança de transporte com autenticação básica](transport-security-with-basic-authentication.md)
- [Segurança de aplicativos distribuídos](distributed-application-security.md)
- [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)
