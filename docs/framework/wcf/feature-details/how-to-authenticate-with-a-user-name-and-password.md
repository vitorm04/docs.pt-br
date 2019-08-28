---
title: 'Como: fazer a autenticação com um nome de usuário e senha'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: e1db413dfdcfa18403e1b67361cea710b203fe5d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045951"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="055d9-102">Como: fazer a autenticação com um nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="055d9-102">How to: Authenticate with a User Name and Password</span></span>

<span data-ttu-id="055d9-103">Este tópico demonstra como habilitar um serviço de Windows Communication Foundation (WCF) para autenticar um cliente com um nome de usuário e senha de domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="055d9-103">This topic demonstrates how to enable a Windows Communication Foundation (WCF) service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="055d9-104">Ele pressupõe que você tenha um serviço WCF em funcionamento e hospedado internamente.</span><span class="sxs-lookup"><span data-stu-id="055d9-104">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="055d9-105">Para obter um exemplo de como criar um serviço WCF auto-hospedado básico, consulte [introdução tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="055d9-105">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="055d9-106">Este tópico pressupõe que o serviço esteja configurado no código.</span><span class="sxs-lookup"><span data-stu-id="055d9-106">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="055d9-107">Se você quiser ver um exemplo de configuração de um serviço semelhante usando um arquivo de configuração, consulte [mensagem segurança nome de usuário](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span><span class="sxs-lookup"><span data-stu-id="055d9-107">If you would like to see an example of configuring a similar service using a configuration file see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span></span>

<span data-ttu-id="055d9-108">Para configurar um serviço para autenticar seus clientes usando o nome de usuário e as <xref:System.ServiceModel.WSHttpBinding> senhas do domínio `Security.Mode` do Windows `Message`, use o e defina sua propriedade como.</span><span class="sxs-lookup"><span data-stu-id="055d9-108">To configure a service to authenticate its clients using Windows Domain username and passwords use the <xref:System.ServiceModel.WSHttpBinding> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="055d9-109">Além disso, você deve especificar um certificado X509 que será usado para criptografar o nome de usuário e a senha à medida que eles forem enviados do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="055d9-109">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>

<span data-ttu-id="055d9-110">No cliente do, você deve solicitar o nome de usuário e a senha e especificar as credenciais do usuário no proxy do cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="055d9-110">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>

## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="055d9-111">Para configurar um serviço WCF para autenticar usando o nome de usuário e a senha do domínio do Windows</span><span class="sxs-lookup"><span data-stu-id="055d9-111">To configure a WCF service to authenticate using Windows domain username and password</span></span>

1. <span data-ttu-id="055d9-112"><xref:System.ServiceModel.WSHttpBinding>Crie uma instância do, defina o modo de segurança da associação como <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, defina o `ClientCredentialType` da associação como <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>e adicione um ponto de extremidade de serviço usando a associação configurada ao host de serviço, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="055d9-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding>, set the security mode of the binding to <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, set the `ClientCredentialType` of the binding to <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>

    ```csharp
    // ...
    WSHttpBinding userNameBinding = new WSHttpBinding();
    userNameBinding.Security.Mode = SecurityMode.Message;
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");
    // ...
    ```

2. <span data-ttu-id="055d9-113">Especifique o certificado do servidor usado para criptografar as informações de nome de usuário e senha enviadas pela conexão.</span><span class="sxs-lookup"><span data-stu-id="055d9-113">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="055d9-114">Esse código deve seguir imediatamente o código acima.</span><span class="sxs-lookup"><span data-stu-id="055d9-114">This code should immediately follow the code above.</span></span> <span data-ttu-id="055d9-115">O exemplo a seguir usa o certificado criado pelo arquivo setup. bat do exemplo de [nome de usuário de segurança de mensagem](../../../../docs/framework/wcf/samples/message-security-user-name.md) :</span><span class="sxs-lookup"><span data-stu-id="055d9-115">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md) sample:</span></span>

    ```csharp
    // ...
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");
    // ...
    ```

    <span data-ttu-id="055d9-116">Você pode usar seu próprio certificado, basta modificar o código para se referir ao seu certificado.</span><span class="sxs-lookup"><span data-stu-id="055d9-116">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="055d9-117">Para obter mais informações sobre como criar e usar certificados, consulte [trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="055d9-117">For more information about creating and using certificates see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="055d9-118">Verifique se o certificado está no repositório de certificados pessoas confiáveis para o computador local.</span><span class="sxs-lookup"><span data-stu-id="055d9-118">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="055d9-119">Você pode fazer isso executando MMC. exe e selecionando o **arquivo**, **Adicionar/remover snap-in...** item de menu.</span><span class="sxs-lookup"><span data-stu-id="055d9-119">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="055d9-120">Na caixa de diálogo **Adicionar ou remover snap-ins** , selecione o **snap-in certificados** e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="055d9-120">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="055d9-121">Na caixa de diálogo snap-in de certificados, selecione **conta de computador**.</span><span class="sxs-lookup"><span data-stu-id="055d9-121">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="055d9-122">Por padrão, o certificado gerado do exemplo de nome de usuário de segurança de mensagem estará localizado na pasta pessoal/certificados.</span><span class="sxs-lookup"><span data-stu-id="055d9-122">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="055d9-123">Ele será listado como "localhost" na coluna emitido para na janela do MMC.</span><span class="sxs-lookup"><span data-stu-id="055d9-123">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="055d9-124">Arraste e solte o certificado na pasta **pessoas confiáveis** .</span><span class="sxs-lookup"><span data-stu-id="055d9-124">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="055d9-125">Isso permitirá que o WCF trate o certificado como um certificado confiável ao executar a autenticação.</span><span class="sxs-lookup"><span data-stu-id="055d9-125">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>

## <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="055d9-126">Para chamar o nome de usuário e a senha do serviço</span><span class="sxs-lookup"><span data-stu-id="055d9-126">To call the service passing username and password</span></span>

1. <span data-ttu-id="055d9-127">O aplicativo cliente deve solicitar seu nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="055d9-127">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="055d9-128">O código a seguir solicita o nome de usuário e a senha.</span><span class="sxs-lookup"><span data-stu-id="055d9-128">The following code asks the user for username and password.</span></span>

    > [!WARNING]
    > <span data-ttu-id="055d9-129">Esse código não deve ser usado em produção, pois a senha é exibida durante a inserção.</span><span class="sxs-lookup"><span data-stu-id="055d9-129">This code should not be used in production as the password is displayed while being entered.</span></span>

    ```csharp
    public static void GetPassword(out string username, out string password)
    {
        Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");
        Console.WriteLine("   Enter username:");
        username = Console.ReadLine();
        Console.WriteLine("   Enter password:");
        password = Console.ReadLine();
        return;
    }
    ```

2. <span data-ttu-id="055d9-130">Crie uma instância do proxy do cliente especificando as credenciais do cliente, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="055d9-130">Create an instance of the client proxy specifying the client’s credentials as shown in the following code:</span></span>

    ```csharp
    string username;
    string password;

    // Instantiate the proxy
    Service1Client proxy = new Service1Client();

    // Prompt the user for username & password
    GetPassword(out username, out password);

    // Set the user’s credentials on the proxy
    proxy.ClientCredentials.UserName.UserName = username;
    proxy.ClientCredentials.UserName.Password = password;

    // Treat the test certificate as trusted
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;
    // Call the service operation using the proxy
    ```

## <a name="see-also"></a><span data-ttu-id="055d9-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="055d9-131">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [<span data-ttu-id="055d9-132">Segurança de transporte com autenticação básica</span><span class="sxs-lookup"><span data-stu-id="055d9-132">Transport Security with Basic Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)
- [<span data-ttu-id="055d9-133">Segurança de aplicativos distribuídos</span><span class="sxs-lookup"><span data-stu-id="055d9-133">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)
- [<span data-ttu-id="055d9-134">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="055d9-134">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
