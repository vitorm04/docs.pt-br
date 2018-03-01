---
title: "Programação de segurança do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 4b296d9bf9b52dfc8e782f6e324be1de8c76d349
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="programming-wcf-security"></a><span data-ttu-id="e9766-102">Programação de segurança do WCF</span><span class="sxs-lookup"><span data-stu-id="e9766-102">Programming WCF Security</span></span>
<span data-ttu-id="e9766-103">Este tópico descreve as tarefas de programação fundamentais usadas para criar um site seguro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e9766-103">This topic describes the fundamental programming tasks used to create a secure [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="e9766-104">Este tópico aborda somente autenticação, confidencialidade e integridade, coletivamente conhecido como *transferir segurança*.</span><span class="sxs-lookup"><span data-stu-id="e9766-104">This topic covers only authentication, confidentiality, and integrity, collectively known as *transfer security*.</span></span> <span data-ttu-id="e9766-105">Este tópico não abrange a autorização (o controle de acesso aos recursos ou serviços); Para obter informações sobre autorização, consulte [autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="e9766-105">This topic does not cover authorization (the control of access to resources or services); for information on authorization, see [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9766-106">Para obter uma introdução valiosa para conceitos de segurança, especialmente em relação ao [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consulte o conjunto de padrões e práticas recomendadas tutoriais no MSDN em [cenários, padrões e diretrizes de implementação para aprimoramentos de WSE (Web Services) 3.0](http://go.microsoft.com/fwlink/?LinkID=88250).</span><span class="sxs-lookup"><span data-stu-id="e9766-106">For a valuable introduction to security concepts, especially in regard to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], see the set of patterns and practices tutorials on MSDN at [Scenarios, Patterns, and Implementation Guidance for Web Services Enhancements (WSE) 3.0](http://go.microsoft.com/fwlink/?LinkID=88250).</span></span>  
  
 <span data-ttu-id="e9766-107">Programação [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é baseada em três etapas de configuração a seguir: o modo de segurança, um tipo de credencial de cliente e os valores de credencial.</span><span class="sxs-lookup"><span data-stu-id="e9766-107">Programming [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security is based on three steps setting the following: the security mode, a client credential type, and the credential values.</span></span> <span data-ttu-id="e9766-108">Você pode executar essas etapas por meio de código ou de configuração.</span><span class="sxs-lookup"><span data-stu-id="e9766-108">You can perform these steps either through code or configuration.</span></span>  
  
## <a name="setting-the-security-mode"></a><span data-ttu-id="e9766-109">Configurando o modo de segurança</span><span class="sxs-lookup"><span data-stu-id="e9766-109">Setting the Security Mode</span></span>  
 <span data-ttu-id="e9766-110">A seguir explica as etapas gerais para programação com o modo de segurança no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="e9766-110">The following explains the general steps for programming with the security mode in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
1.  <span data-ttu-id="e9766-111">Selecione uma das associações predefinidas adequadas aos seus requisitos de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e9766-111">Select one of the predefined bindings appropriate to your application requirements.</span></span> <span data-ttu-id="e9766-112">Para obter uma lista das opções de associação, consulte [System-Provided associações](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="e9766-112">For a list of the binding choices, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="e9766-113">Por padrão, quase todas as associações tem segurança habilitada.</span><span class="sxs-lookup"><span data-stu-id="e9766-113">By default, nearly every binding has security enabled.</span></span> <span data-ttu-id="e9766-114">A única exceção é o <xref:System.ServiceModel.BasicHttpBinding> classe (usando a configuração, o [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).</span><span class="sxs-lookup"><span data-stu-id="e9766-114">The one exception is the <xref:System.ServiceModel.BasicHttpBinding> class (using configuration, the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).</span></span>  
  
     <span data-ttu-id="e9766-115">A associação que você seleciona determina o transporte.</span><span class="sxs-lookup"><span data-stu-id="e9766-115">The binding you select determines the transport.</span></span> <span data-ttu-id="e9766-116">Por exemplo, <xref:System.ServiceModel.WSHttpBinding> usa HTTP como o transporte; <xref:System.ServiceModel.NetTcpBinding> usa o TCP.</span><span class="sxs-lookup"><span data-stu-id="e9766-116">For example, <xref:System.ServiceModel.WSHttpBinding> uses HTTP as the transport; <xref:System.ServiceModel.NetTcpBinding> uses TCP.</span></span>  
  
2.  <span data-ttu-id="e9766-117">Selecione um dos modos de segurança para a associação.</span><span class="sxs-lookup"><span data-stu-id="e9766-117">Select one of the security modes for the binding.</span></span> <span data-ttu-id="e9766-118">Observe que a associação que você seleciona determina as opções de modo disponível.</span><span class="sxs-lookup"><span data-stu-id="e9766-118">Note that the binding you select determines the available mode choices.</span></span> <span data-ttu-id="e9766-119">Por exemplo, o <xref:System.ServiceModel.WSDualHttpBinding> não permite que a segurança de transporte (não é uma opção).</span><span class="sxs-lookup"><span data-stu-id="e9766-119">For example, the <xref:System.ServiceModel.WSDualHttpBinding> does not allow transport security (it is not an option).</span></span> <span data-ttu-id="e9766-120">Da mesma forma, não o <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nem o <xref:System.ServiceModel.NetNamedPipeBinding> permite que a segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="e9766-120">Similarly, neither the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nor the <xref:System.ServiceModel.NetNamedPipeBinding> allows message security.</span></span>  
  
     <span data-ttu-id="e9766-121">Você tem três opções:</span><span class="sxs-lookup"><span data-stu-id="e9766-121">You have three choices:</span></span>  
  
    1.  `Transport`  
  
         <span data-ttu-id="e9766-122">Segurança de transporte depende do mecanismo que usa a associação selecionada.</span><span class="sxs-lookup"><span data-stu-id="e9766-122">Transport security depends on the mechanism that the binding you have selected uses.</span></span> <span data-ttu-id="e9766-123">Por exemplo, se você estiver usando `WSHttpBinding` , em seguida, o mecanismo de segurança é o protocolo (SSL) (também o mecanismo para o protocolo HTTPS).</span><span class="sxs-lookup"><span data-stu-id="e9766-123">For example, if you are using `WSHttpBinding` then the security mechanism is Secure Sockets Layer (SSL) (also the mechanism for the HTTPS protocol).</span></span> <span data-ttu-id="e9766-124">Em geral, a vantagem principal de segurança de transporte é que ele oferece uma taxa de transferência não importa qual transporte você está usando.</span><span class="sxs-lookup"><span data-stu-id="e9766-124">Generally speaking, the main advantage of transport security is that it delivers good throughput no matter which transport you are using.</span></span> <span data-ttu-id="e9766-125">No entanto, ele tem duas limitações: A primeira é que o mecanismo de transporte determina o tipo de credencial usado para autenticar um usuário.</span><span class="sxs-lookup"><span data-stu-id="e9766-125">However, it does have two limitations: The first is that the transport mechanism dictates the credential type used to authenticate a user.</span></span> <span data-ttu-id="e9766-126">Isso é uma desvantagem somente se um serviço precisa interoperar com outros serviços que exigem tipos diferentes de credenciais.</span><span class="sxs-lookup"><span data-stu-id="e9766-126">This is a drawback only if a service needs to interoperate with other services that demand different types of credentials.</span></span> <span data-ttu-id="e9766-127">A segunda é que, como a segurança não é aplicada no nível da mensagem, a segurança é implementada em uma maneira de salto por salto em vez de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="e9766-127">The second is that, because the security is not applied at the message level, security is implemented in a hop-by-hop manner rather than end-to-end.</span></span> <span data-ttu-id="e9766-128">Essa última limitação é um problema apenas se o caminho de mensagem entre cliente e serviço inclui intermediários.</span><span class="sxs-lookup"><span data-stu-id="e9766-128">This latter limitation is an issue only if the message path between client and service includes intermediaries.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e9766-129">qual transporte deve ser usado, consulte [selecionando um transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).</span><span class="sxs-lookup"><span data-stu-id="e9766-129"> which transport to use, see [Choosing a Transport](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e9766-130">usando a segurança de transporte, consulte [visão geral de segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e9766-130"> using transport security, see [Transport Security Overview](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span></span>  
  
    2.  `Message`  
  
         <span data-ttu-id="e9766-131">Segurança de mensagem significa que cada mensagem inclui os cabeçalhos necessários e seguro de dados para manter a mensagem.</span><span class="sxs-lookup"><span data-stu-id="e9766-131">Message security means that every message includes the necessary headers and data to keep the message secure.</span></span> <span data-ttu-id="e9766-132">Como a composição dos cabeçalhos varia, você pode incluir qualquer número de credenciais.</span><span class="sxs-lookup"><span data-stu-id="e9766-132">Because the composition of the headers varies, you can include any number of credentials.</span></span> <span data-ttu-id="e9766-133">Isso é um fator importante, se você está interoperando com outros serviços que exigem um tipo de credencial específico que não pode fornecer um mecanismo de transporte, ou se a mensagem deve ser usada com mais de um serviço, em que cada serviço exige um tipo de credencial diferente.</span><span class="sxs-lookup"><span data-stu-id="e9766-133">This becomes a factor if you are interoperating with other services that demand a specific credential type that a transport mechanism can't supply, or if the message must be used with more than one service, where each service demands a different credential type.</span></span>  
  
         [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="e9766-134">[Segurança](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="e9766-134"> [Message Security](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>  
  
    3.  `TransportWithMessageCredential`  
  
         <span data-ttu-id="e9766-135">Essa opção usa a camada de transporte para proteger a transferência de mensagem, enquanto cada mensagem inclui as credenciais avançadas necessário outros serviços.</span><span class="sxs-lookup"><span data-stu-id="e9766-135">This choice uses the transport layer to secure the message transfer, while every message includes the rich credentials other services need.</span></span> <span data-ttu-id="e9766-136">Ele combina a vantagem de desempenho de segurança de transporte com a vantagem de rich credenciais de segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="e9766-136">This combines the performance advantage of transport security with the rich credentials advantage of message security.</span></span> <span data-ttu-id="e9766-137">Isso está disponível com as seguintes associações: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, e <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="e9766-137">This is available with the following bindings: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, and <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3.  <span data-ttu-id="e9766-138">Se você decidir usar a segurança de transporte HTTP (em outras palavras, HTTPS), você também deve configurar o host com um certificado SSL e habilitar o SSL em uma porta.</span><span class="sxs-lookup"><span data-stu-id="e9766-138">If you decide to use transport security for HTTP (in other words, HTTPS), you must also configure the host with an SSL certificate and enable SSL on a port.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="e9766-139">[Segurança de transporte HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="e9766-139"> [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
4.  <span data-ttu-id="e9766-140">Se você estiver usando o <xref:System.ServiceModel.WSHttpBinding> e não é necessário estabelecer uma sessão segura, defina o <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> propriedade `false`.</span><span class="sxs-lookup"><span data-stu-id="e9766-140">If you are using the <xref:System.ServiceModel.WSHttpBinding> and do not need to establish a secure session, set the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="e9766-141">Uma sessão segura ocorre quando um cliente e o serviço criam um canal usando uma chave simétrica (cliente e servidor para usar a mesma chave para o comprimento de uma conversa, até que a caixa de diálogo é fechada).</span><span class="sxs-lookup"><span data-stu-id="e9766-141">A secure session occurs when a client and service create a channel using a symmetric key (both client and server use the same key for the length of a conversation, until the dialog is closed).</span></span>  
  
## <a name="setting-the-client-credential-type"></a><span data-ttu-id="e9766-142">Definir o tipo de credencial de cliente</span><span class="sxs-lookup"><span data-stu-id="e9766-142">Setting the Client Credential Type</span></span>  
 <span data-ttu-id="e9766-143">Selecione um tipo de credencial de cliente conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="e9766-143">Select a client credential type as appropriate.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="e9766-144">[Selecionando um tipo de credencial](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).</span><span class="sxs-lookup"><span data-stu-id="e9766-144"> [Selecting a Credential Type](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).</span></span> <span data-ttu-id="e9766-145">Os seguintes tipos de credencial de cliente estão disponíveis:</span><span class="sxs-lookup"><span data-stu-id="e9766-145">The following client credential types are available:</span></span>  
  
-   `Windows`  
  
-   `Certificate`  
  
-   `Digest`  
  
-   `Basic`  
  
-   `UserName`  
  
-   `NTLM`  
  
-   `IssuedToken`  
  
 <span data-ttu-id="e9766-146">Dependendo de como você define o modo, você deve definir o tipo de credencial.</span><span class="sxs-lookup"><span data-stu-id="e9766-146">Depending on how you set the mode, you must set the credential type.</span></span> <span data-ttu-id="e9766-147">Por exemplo, se você tiver selecionado o `wsHttpBinding`e tiver definido o modo de "Mensagem", em seguida, você também pode definir o `clientCredentialType` atributo do elemento de mensagem para um dos seguintes valores: `None`, `Windows`, `UserName`, `Certificate` , e `IssuedToken`, conforme mostrado no exemplo de configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="e9766-147">For example, if you have selected the `wsHttpBinding`, and have set the mode to "Message," then you can also set the `clientCredentialType` attribute of the Message element to one of the following values: `None`, `Windows`, `UserName`, `Certificate`, and `IssuedToken`, as shown in the following configuration example.</span></span>  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>  
</bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="e9766-148">Ou no código:</span><span class="sxs-lookup"><span data-stu-id="e9766-148">Or in code:</span></span>  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a><span data-ttu-id="e9766-149">Valores de credencial de serviço de configuração</span><span class="sxs-lookup"><span data-stu-id="e9766-149">Setting Service Credential Values</span></span>  
 <span data-ttu-id="e9766-150">Quando você seleciona um tipo de credencial de cliente, você deve definir as credenciais reais para o serviço e o cliente para usar.</span><span class="sxs-lookup"><span data-stu-id="e9766-150">Once you select a client credential type, you must set the actual credentials for the service and client to use.</span></span> <span data-ttu-id="e9766-151">No serviço, as credenciais são definidas usando o <xref:System.ServiceModel.Description.ServiceCredentials> classe e retornado pelo <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> propriedade o <xref:System.ServiceModel.ServiceHostBase> classe.</span><span class="sxs-lookup"><span data-stu-id="e9766-151">On the service, credentials are set using the <xref:System.ServiceModel.Description.ServiceCredentials> class and returned by the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property of the <xref:System.ServiceModel.ServiceHostBase> class.</span></span> <span data-ttu-id="e9766-152">A associação em uso indica o tipo de credencial de serviço, o modo de segurança escolhido e o tipo da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="e9766-152">The binding in use implies the service credential type, the security mode chosen, and the type of the client credential.</span></span> <span data-ttu-id="e9766-153">O código a seguir define um certificado para uma credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="e9766-153">The following code sets a certificate for a service credential.</span></span>  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a><span data-ttu-id="e9766-154">Definindo valores de credencial de cliente</span><span class="sxs-lookup"><span data-stu-id="e9766-154">Setting Client Credential Values</span></span>  
 <span data-ttu-id="e9766-155">No cliente, definir valores de credencial de cliente usando o <xref:System.ServiceModel.Description.ClientCredentials> classe e retornado pelo <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade o <xref:System.ServiceModel.ClientBase%601> classe.</span><span class="sxs-lookup"><span data-stu-id="e9766-155">On the client, set client credential values using the <xref:System.ServiceModel.Description.ClientCredentials> class and returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class.</span></span> <span data-ttu-id="e9766-156">O código a seguir define um certificado como uma credencial em um cliente usando o protocolo TCP.</span><span class="sxs-lookup"><span data-stu-id="e9766-156">The following code sets a certificate as a credential on a client using the TCP protocol.</span></span>  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e9766-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9766-157">See Also</span></span>  
 [<span data-ttu-id="e9766-158">Programação básica do WCF</span><span class="sxs-lookup"><span data-stu-id="e9766-158">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="e9766-159">Cenários comuns de segurança</span><span class="sxs-lookup"><span data-stu-id="e9766-159">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
