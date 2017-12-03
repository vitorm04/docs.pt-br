---
title: "Como fazer a autenticação com um nome de usuário e senha"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31e05709465e429445a2ebdafae719c24d316c8e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="a4d86-102">Como fazer a autenticação com um nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="a4d86-102">How to: Authenticate with a User Name and Password</span></span>
<span data-ttu-id="a4d86-103">Este tópico demonstra como habilitar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service para autenticar um cliente com um nome de usuário de domínio de Windows e uma senha.</span><span class="sxs-lookup"><span data-stu-id="a4d86-103">This topic demonstrates how to enable a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="a4d86-104">Ele pressupõe que você tenha um trabalho, o serviço WCF auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="a4d86-104">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="a4d86-105">Para obter um exemplo de criação de um consulte da serviço WCF auto-hospedado básico, [Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="a4d86-105">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="a4d86-106">Este tópico pressupõe que o serviço está configurado no código.</span><span class="sxs-lookup"><span data-stu-id="a4d86-106">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="a4d86-107">Se você quiser ver um exemplo de como configurar um serviço semelhante usando um arquivo de configuração consulte [nome de usuário de segurança de mensagem](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span><span class="sxs-lookup"><span data-stu-id="a4d86-107">If you would like to see an example of configuring a similar service using a configuration file see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span></span>  
  
 <span data-ttu-id="a4d86-108">Para configurar um serviço para autenticar os clientes usando o uso de nome de usuário e senhas do domínio do Windows a <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> e defina seu `Security.Mode` propriedade `Message`.</span><span class="sxs-lookup"><span data-stu-id="a4d86-108">To configure a service to authenticate its clients using Windows Domain username and passwords use the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="a4d86-109">Além disso, você deve especificar um X509 certificado que será usado para criptografar o nome de usuário e a senha que são enviadas para o serviço do cliente.</span><span class="sxs-lookup"><span data-stu-id="a4d86-109">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>  
  
 <span data-ttu-id="a4d86-110">No cliente, você deve solicitar o nome de usuário e a senha do usuário e especificar as credenciais do usuário no proxy do cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="a4d86-110">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>  
  
### <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="a4d86-111">Para configurar um serviço WCF para autenticar usando a senha e nome de usuário de domínio Windows.</span><span class="sxs-lookup"><span data-stu-id="a4d86-111">To configure a WCF service to authenticate using Windows domain username and password.</span></span>  
  
1.  <span data-ttu-id="a4d86-112">Criar uma instância do <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, definir o modo de segurança da associação com `SecurityMode.Message`, defina o `ClientCredentialType` da associação com `MessageCredentialType.UserName`e adicione um ponto de extremidade de serviço usando a associação configurada para o host de serviço, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="a4d86-112">Create an instance of the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, set the security mode of the binding to `SecurityMode.Message`, set the `ClientCredentialType` of the binding to `MessageCredentialType.UserName`, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  <span data-ttu-id="a4d86-113">Especifique o certificado do servidor usado para criptografar o nome de usuário e informações de senha enviadas eletronicamente.</span><span class="sxs-lookup"><span data-stu-id="a4d86-113">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="a4d86-114">Esse código deve seguir imediatamente o código acima.</span><span class="sxs-lookup"><span data-stu-id="a4d86-114">This code should immediately follow the code above.</span></span> <span data-ttu-id="a4d86-115">O exemplo a seguir usa o certificado que é criado pelo arquivo bat do [nome de usuário de segurança de mensagem](../../../../docs/framework/wcf/samples/message-security-user-name.md) exemplo:</span><span class="sxs-lookup"><span data-stu-id="a4d86-115">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md) sample:</span></span>  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     <span data-ttu-id="a4d86-116">Você pode usar seu próprio certificado, basta modificar o código para fazer referência ao certificado.</span><span class="sxs-lookup"><span data-stu-id="a4d86-116">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="a4d86-117">Para obter mais informações sobre como criar e usar certificados, consulte [trabalhar com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a4d86-117">For more information about creating and using certificates see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="a4d86-118">Verifique se o certificado está no repositório de certificados de pessoas confiáveis para a máquina Local.</span><span class="sxs-lookup"><span data-stu-id="a4d86-118">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="a4d86-119">Você pode fazer isso executando mmc.exe e selecionando o **arquivo**, **Adicionar/Remover Snap-in...**  item de menu.</span><span class="sxs-lookup"><span data-stu-id="a4d86-119">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="a4d86-120">No **adicionar ou Remover Snap-ins** caixa de diálogo, selecione o **snap-in de certificados** e clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="a4d86-120">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="a4d86-121">Na caixa de diálogo Snap-in certificados, selecione **conta de computador**.</span><span class="sxs-lookup"><span data-stu-id="a4d86-121">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="a4d86-122">Por padrão, o certificado gerado a partir do exemplo de nome de usuário de segurança de mensagem será localizado na pasta pessoal/certificados.</span><span class="sxs-lookup"><span data-stu-id="a4d86-122">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="a4d86-123">Ele será listado como "localhost" em emitido para a coluna na janela do MMC.</span><span class="sxs-lookup"><span data-stu-id="a4d86-123">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="a4d86-124">Arrastar e soltar o certificado para o **pessoas confiáveis** pasta.</span><span class="sxs-lookup"><span data-stu-id="a4d86-124">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="a4d86-125">Isso permitirá que o WCF tratar o certificado como um certificado confiável ao executar a autenticação.</span><span class="sxs-lookup"><span data-stu-id="a4d86-125">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>  
  
### <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="a4d86-126">Para chamar o serviço, passando o nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="a4d86-126">To call the service passing username and password</span></span>  
  
1.  <span data-ttu-id="a4d86-127">O aplicativo cliente deve solicitar ao usuário seu nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="a4d86-127">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="a4d86-128">O código a seguir solicita ao usuário para o nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="a4d86-128">The following code asks the user for username and password.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="a4d86-129">Esse código não deve ser usado na produção, como a senha é exibida ao que está sendo inserido.</span><span class="sxs-lookup"><span data-stu-id="a4d86-129">This code should not be used in production as the password is displayed while being entered.</span></span>  
  
    ```  
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
  
2.  <span data-ttu-id="a4d86-130">Crie uma instância do proxy do cliente especificando as credenciais do cliente conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="a4d86-130">Create an instance of the client proxy specifying the client’s credentials as shown in the following code:</span></span>  
  
    ```  
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
  
## <a name="see-also"></a><span data-ttu-id="a4d86-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4d86-131">See Also</span></span>  
 <span data-ttu-id="a4d86-132"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="a4d86-132"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.SecurityMode>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>  
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>  
 [<span data-ttu-id="a4d86-133">Segurança de transporte com autenticação básica</span><span class="sxs-lookup"><span data-stu-id="a4d86-133">Transport Security with Basic Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 [<span data-ttu-id="a4d86-134">Segurança de aplicativos distribuídos</span><span class="sxs-lookup"><span data-stu-id="a4d86-134">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [<span data-ttu-id="a4d86-135">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="a4d86-135">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
