---
title: "Como especificar credenciais de segurança de canal"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 2a1b2ba0ab49ebf470c0245f0827f82e1fe20ce8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-channel-security-credentials"></a><span data-ttu-id="1b76c-102">Como especificar credenciais de segurança de canal</span><span class="sxs-lookup"><span data-stu-id="1b76c-102">How to: Specify Channel Security Credentials</span></span>
<span data-ttu-id="1b76c-103">O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Moniker de serviço permite que aplicativos de COM chamar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços.</span><span class="sxs-lookup"><span data-stu-id="1b76c-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Service Moniker allows COM applications to call [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="1b76c-104">A maioria dos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services requer que o cliente especificar credenciais para autenticação e autorização.</span><span class="sxs-lookup"><span data-stu-id="1b76c-104">Most [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services require the client to specify credentials for authentication and authorization.</span></span> <span data-ttu-id="1b76c-105">Ao chamar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente, você pode especificar essas credenciais no código gerenciado ou em um arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1b76c-105">When calling a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, you can specify these credentials in managed code or in an application configuration file.</span></span> <span data-ttu-id="1b76c-106">Ao chamar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço de um aplicativo COM, você pode usar o <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface para especificar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="1b76c-106">When calling a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from a COM application, you can use the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface to specify credentials.</span></span> <span data-ttu-id="1b76c-107">Este tópico ilustrará várias maneiras de especificar credenciais usando o <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.</span><span class="sxs-lookup"><span data-stu-id="1b76c-107">This topic will illustrate various ways to specify credentials using the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b76c-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials>é uma interface baseada em IDispatch e você não terá a funcionalidade do IntelliSense no ambiente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1b76c-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> is an IDispatch-based interface and you will not get IntelliSense functionality in the Visual Studio environment.</span></span>  
  
 <span data-ttu-id="1b76c-109">Este artigo usará o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço definido no [exemplo de segurança de mensagem](../../../../docs/framework/wcf/samples/message-security-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1b76c-109">This article will use the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service defined in the [Message Security Sample](../../../../docs/framework/wcf/samples/message-security-sample.md).</span></span>  
  
### <a name="to-specify-a-client-certificate"></a><span data-ttu-id="1b76c-110">Para especificar um certificado de cliente</span><span class="sxs-lookup"><span data-stu-id="1b76c-110">To specify a client certificate</span></span>  
  
1.  <span data-ttu-id="1b76c-111">Execute o arquivo bat no diretório de segurança de mensagem para criar e instalar os certificados de teste necessário.</span><span class="sxs-lookup"><span data-stu-id="1b76c-111">Run the Setup.bat file in the Message Security directory to create and install the required test certificates.</span></span>  
  
2.  <span data-ttu-id="1b76c-112">Abra o projeto de segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="1b76c-112">Open the Message Security project.</span></span>  
  
3.  <span data-ttu-id="1b76c-113">Adicionar `[ServiceBehavior(Namespace=``http://Microsoft.ServiceModel.Samples``)]` para o `ICalculator` definição de interface.</span><span class="sxs-lookup"><span data-stu-id="1b76c-113">Add `[ServiceBehavior(Namespace=``http://Microsoft.ServiceModel.Samples``)]` to the `ICalculator` interface definition.</span></span>  
  
4.  <span data-ttu-id="1b76c-114">Adicionar `bindingNamespace=``http://Microsoft.ServiceModel.Samples` à marca de ponto de extremidade no App. config para o serviço.</span><span class="sxs-lookup"><span data-stu-id="1b76c-114">Add `bindingNamespace=``http://Microsoft.ServiceModel.Samples` to the endpoint tag in the App.config for the service.</span></span>  
  
5.  <span data-ttu-id="1b76c-115">Criar o exemplo de segurança de mensagem e executar Service.exe.</span><span class="sxs-lookup"><span data-stu-id="1b76c-115">Build the Message Security Sample and run Service.exe.</span></span> <span data-ttu-id="1b76c-116">Use o Internet Explorer e navegue até o URI do serviço (ServiceModelSamples/http://localhost:8000/serviço) para garantir que o serviço está funcionando.</span><span class="sxs-lookup"><span data-stu-id="1b76c-116">Use Internet Explorer and browse to the service's URI (http://localhost:8000/ServiceModelSamples/Service) to ensure that the service is working.</span></span>  
  
6.  <span data-ttu-id="1b76c-117">Abra o Visual Basic 6.0 e crie um novo arquivo .exe padrão.</span><span class="sxs-lookup"><span data-stu-id="1b76c-117">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="1b76c-118">Adicione um botão ao formulário e clique duas vezes no botão para adicionar o código a seguir para o manipulador de cliques:</span><span class="sxs-lookup"><span data-stu-id="1b76c-118">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
        monString = monString + ", binding=BasicHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
        Set monikerProxy = GetObject(monString)  
  
        'Set the Service Certificate.  
     monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetDefaultServiceCertificateFromStore "CurrentUser", "TrustedPeople", "FindBySubjectName", "localhost"  
  
        'Set the Client Certificate.  
        monikerProxy.ChannelCredentials.SetClientCertificateFromStoreByName "CN=client.com", "CurrentUser", "My"  
        MsgBox monikerProxy.Add(3, 4)  
    ```  
  
7.  <span data-ttu-id="1b76c-119">Execute o aplicativo do Visual Basic e verificar os resultados.</span><span class="sxs-lookup"><span data-stu-id="1b76c-119">Run the Visual Basic application and verify the results.</span></span>  
  
     <span data-ttu-id="1b76c-120">O aplicativo do Visual Basic exibirá uma caixa de mensagem com o resultado de chamar o método Add (3, 4).</span><span class="sxs-lookup"><span data-stu-id="1b76c-120">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span> <span data-ttu-id="1b76c-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29>ou <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> também pode ser usado no lugar de <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> para definir o certificado de cliente:</span><span class="sxs-lookup"><span data-stu-id="1b76c-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> or <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> can also be used in place of <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> to set the Client Certificate:</span></span>  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="1b76c-122">Para esta chamada funcionar, o certificado de cliente precisa ser confiável no computador que cliente está em execução no.</span><span class="sxs-lookup"><span data-stu-id="1b76c-122">For this call to work, the client certificate needs to be trusted on the machine the client is running on.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b76c-123">Se o identificador de origem está malformado ou se o serviço está indisponível, a chamada para `GetObject` retornará um erro dizendo "Sintaxe inválida".</span><span class="sxs-lookup"><span data-stu-id="1b76c-123">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span> <span data-ttu-id="1b76c-124">Se você receber esse erro, verifique se você estiver usando o identificador de origem está correto e o serviço está disponível.</span><span class="sxs-lookup"><span data-stu-id="1b76c-124">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
### <a name="to-specify-user-name-and-password"></a><span data-ttu-id="1b76c-125">Para especificar o nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="1b76c-125">To specify user name and password</span></span>  
  
1.  <span data-ttu-id="1b76c-126">Modificar o arquivo App. config do serviço para usar o `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="1b76c-126">Modify the Service App.config file to use the `wsHttpBinding`.</span></span> <span data-ttu-id="1b76c-127">Isso é necessário para a validação de nome e a senha do usuário:</span><span class="sxs-lookup"><span data-stu-id="1b76c-127">This is required for user name and password validation:</span></span>  
  
  
  
2.  <span data-ttu-id="1b76c-128">Definir o `clientCredentialType` para o nome de usuário:</span><span class="sxs-lookup"><span data-stu-id="1b76c-128">Set the `clientCredentialType` to UserName:</span></span>  
  
  
  
3.  <span data-ttu-id="1b76c-129">Abra o Visual Basic 6.0 e crie um novo arquivo .exe padrão.</span><span class="sxs-lookup"><span data-stu-id="1b76c-129">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="1b76c-130">Adicione um botão ao formulário e clique duas vezes no botão para adicionar o código a seguir para o manipulador de cliques:</span><span class="sxs-lookup"><span data-stu-id="1b76c-130">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set monikerProxy = GetObject(monString)  
  
    monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetUserNameCredential "username", "password"  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
4.  <span data-ttu-id="1b76c-131">Execute o aplicativo do Visual Basic e verificar os resultados.</span><span class="sxs-lookup"><span data-stu-id="1b76c-131">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="1b76c-132">O aplicativo do Visual Basic exibirá uma caixa de mensagem com o resultado de chamar o método Add (3, 4).</span><span class="sxs-lookup"><span data-stu-id="1b76c-132">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1b76c-133">A associação especificada no apelido serviço neste exemplo foi alterada para WSHttpBinding_ICalculator.</span><span class="sxs-lookup"><span data-stu-id="1b76c-133">The binding specified in the service moniker in this sample has been changed to WSHttpBinding_ICalculator.</span></span> <span data-ttu-id="1b76c-134">Observe também que você deve fornecer um nome de usuário válido e uma senha na chamada para <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="1b76c-134">Also note that you must supply a valid user name and password in the call to <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span></span>  
  
### <a name="to-specify-windows-credentials"></a><span data-ttu-id="1b76c-135">Para especificar as credenciais do Windows</span><span class="sxs-lookup"><span data-stu-id="1b76c-135">To specify Windows Credentials</span></span>  
  
1.  <span data-ttu-id="1b76c-136">Definir `clientCredentialType` para Windows no arquivo App. config do serviço:</span><span class="sxs-lookup"><span data-stu-id="1b76c-136">Set `clientCredentialType` to Windows in the Service App.config file:</span></span>  
  
  
  
2.  <span data-ttu-id="1b76c-137">Abra o Visual Basic 6.0 e crie um novo arquivo .exe padrão.</span><span class="sxs-lookup"><span data-stu-id="1b76c-137">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="1b76c-138">Adicione um botão ao formulário e clique duas vezes no botão para adicionar o código a seguir para o manipulador de cliques:</span><span class="sxs-lookup"><span data-stu-id="1b76c-138">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", upnidentity=domain\userID"  
  
    Set monikerProxy = GetObject(monString)  
     monikerProxy.ChannelCredentials.SetWindowsCredential "domain", "userID", "password", 1, True  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
3.  <span data-ttu-id="1b76c-139">Execute o aplicativo do Visual Basic e verificar os resultados.</span><span class="sxs-lookup"><span data-stu-id="1b76c-139">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="1b76c-140">O aplicativo do Visual Basic exibirá uma caixa de mensagem com o resultado de chamar o método Add (3, 4).</span><span class="sxs-lookup"><span data-stu-id="1b76c-140">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1b76c-141">Você deve substituir "domínio", "userID" e "password" com os valores válidos.</span><span class="sxs-lookup"><span data-stu-id="1b76c-141">You must replace "domain", "userID", and "password" with valid values.</span></span>  
  
### <a name="to-specify-an-issue-token"></a><span data-ttu-id="1b76c-142">Para especificar um token de problema</span><span class="sxs-lookup"><span data-stu-id="1b76c-142">To specify an issue token</span></span>  
  
1.  <span data-ttu-id="1b76c-143">Emitir tokens são usados apenas para aplicativos que usam segurança federada.</span><span class="sxs-lookup"><span data-stu-id="1b76c-143">Issue tokens are used only for applications using federated security.</span></span> <span data-ttu-id="1b76c-144">Para obter mais informações sobre segurança federada, consulte [federação e Tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) e [federação exemplo](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1b76c-144">For more information about federated security, see [Federation and Issued Tokens](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) and [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
     <span data-ttu-id="1b76c-145">O seguinte exemplo de código do Visual Basic mostra como chamar o <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> método:</span><span class="sxs-lookup"><span data-stu-id="1b76c-145">The following Visual Basic code example illustrates how to call the <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> method:</span></span>  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     <span data-ttu-id="1b76c-146">Para obter mais informações sobre os parâmetros para este método, consulte <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="1b76c-146">For more information about the parameters for this method, see <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b76c-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b76c-147">See Also</span></span>  
 [<span data-ttu-id="1b76c-148">Federação</span><span class="sxs-lookup"><span data-stu-id="1b76c-148">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)  
 [<span data-ttu-id="1b76c-149">Como: configurar as credenciais em um serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="1b76c-149">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="1b76c-150">Como: criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="1b76c-150">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="1b76c-151">Segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="1b76c-151">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [<span data-ttu-id="1b76c-152">Associações e segurança</span><span class="sxs-lookup"><span data-stu-id="1b76c-152">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
