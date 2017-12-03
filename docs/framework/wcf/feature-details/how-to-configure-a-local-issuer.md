---
title: Como configurar um emissor local
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 90edf0735d890e0abc1560de5a7f523ee2faa7c8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="a8004-102">Como configurar um emissor local</span><span class="sxs-lookup"><span data-stu-id="a8004-102">How to: Configure a Local Issuer</span></span>
<span data-ttu-id="a8004-103">Este tópico descreve como configurar um cliente para usar um emissor local para tokens emitidos.</span><span class="sxs-lookup"><span data-stu-id="a8004-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>  
  
 <span data-ttu-id="a8004-104">Geralmente, quando um cliente se comunica com um serviço federado, o serviço Especifica o endereço do serviço de token é esperado para emitir o token que o cliente usará para se autenticar para o serviço federado de segurança de.</span><span class="sxs-lookup"><span data-stu-id="a8004-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="a8004-105">Em determinadas situações, o cliente pode ser configurado para usar um *emissor local*.</span><span class="sxs-lookup"><span data-stu-id="a8004-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="a8004-106">usa um emissor local em casos em que o endereço do emissor de uma associação federada é http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous ou `null`.</span><span class="sxs-lookup"><span data-stu-id="a8004-106"> uses a local issuer in cases where the issuer address of a federated binding is http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous or `null`.</span></span> <span data-ttu-id="a8004-107">Nesses casos, você deve configurar o <xref:System.ServiceModel.Description.ClientCredentials> com o endereço do emissor local e a associação a ser usado para se comunicar com esse emissor.</span><span class="sxs-lookup"><span data-stu-id="a8004-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8004-108">Se o <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> propriedade o `ClientCredentials` classe é definida como `true`, um endereço do emissor local não for especificado e o endereço do emissor especificado pelo [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ou outros associação federada é http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self, http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous, ou `null`, em seguida, o Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] emissor é usado.</span><span class="sxs-lookup"><span data-stu-id="a8004-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self, http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous, or is `null`, then the Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] issuer is used.</span></span>  
  
### <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="a8004-109">Para configurar o emissor local no código</span><span class="sxs-lookup"><span data-stu-id="a8004-109">To configure the local issuer in code</span></span>  
  
1.  <span data-ttu-id="a8004-110">Criar uma variável de tipo<xref:System.ServiceModel.Security.IssuedTokenClientCredential></span><span class="sxs-lookup"><span data-stu-id="a8004-110">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>  
  
2.  <span data-ttu-id="a8004-111">Defina a variável para a instância retornada do <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> propriedade o `ClientCredentials` classe.</span><span class="sxs-lookup"><span data-stu-id="a8004-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="a8004-112">Essa instância é retornada pelo <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade do cliente (herdado de <xref:System.ServiceModel.ClientBase%601>) ou o <xref:System.ServiceModel.ChannelFactory.Credentials%2A> propriedade o <xref:System.ServiceModel.ChannelFactory>:</span><span class="sxs-lookup"><span data-stu-id="a8004-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3.  <span data-ttu-id="a8004-113">Definir o <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> propriedade para uma nova instância do <xref:System.ServiceModel.EndpointAddress>, com o endereço do emissor local como um argumento para o construtor.</span><span class="sxs-lookup"><span data-stu-id="a8004-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     <span data-ttu-id="a8004-114">Como alternativa, crie um novo <xref:System.Uri> instância como um argumento para o construtor.</span><span class="sxs-lookup"><span data-stu-id="a8004-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     <span data-ttu-id="a8004-115">O `addressHeaders` parâmetro é uma matriz de <xref:System.ServiceModel.Channels.AddressHeader> instâncias, conforme mostrado.</span><span class="sxs-lookup"><span data-stu-id="a8004-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4.  <span data-ttu-id="a8004-116">Define a associação para o emissor local usando o <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a8004-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5.  <span data-ttu-id="a8004-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a8004-117">Optional.</span></span> <span data-ttu-id="a8004-118">Adicionar comportamentos de ponto de extremidade configurado para o emissor local, adicionando desses comportamentos a coleção retornada pelo <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a8004-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="a8004-119">Para configurar o emissor local na configuração</span><span class="sxs-lookup"><span data-stu-id="a8004-119">To configure the local issuer in configuration</span></span>  
  
1.  <span data-ttu-id="a8004-120">Criar um [ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) elemento como um filho de [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) que é um filho do elemento a [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elemento em um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a8004-120">Create a [\<localIssuer>](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>  
  
2.  <span data-ttu-id="a8004-121">Definir o `address` de atributo para o endereço do emissor local que aceita solicitações de token.</span><span class="sxs-lookup"><span data-stu-id="a8004-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>  
  
3.  <span data-ttu-id="a8004-122">Definir o `binding` e `bindingConfiguration` atributos com valores que fazem referência a ligação apropriada para usar ao se comunicar com o ponto de extremidade do emissor local.</span><span class="sxs-lookup"><span data-stu-id="a8004-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>  
  
4.  <span data-ttu-id="a8004-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a8004-123">Optional.</span></span> <span data-ttu-id="a8004-124">Definido o [ \<identidade >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elemento como um filho de <`localIssuer`> elemento e especifique as informações de identidade para o emissor local.</span><span class="sxs-lookup"><span data-stu-id="a8004-124">Set the [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>  
  
5.  <span data-ttu-id="a8004-125">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a8004-125">Optional.</span></span> <span data-ttu-id="a8004-126">Definido o [ \<cabeçalhos >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) elemento como um filho de <`localIssuer`> elemento e especificar cabeçalhos adicionais que são necessárias para tratar corretamente o emissor local.</span><span class="sxs-lookup"><span data-stu-id="a8004-126">Set the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a8004-127">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a8004-127">.NET Framework Security</span></span>  
 <span data-ttu-id="a8004-128">Observe que, se um endereço do emissor e a associação especificadas para uma associação de determinado, o emissor local não é usado para pontos de extremidade que utilizam essa associação.</span><span class="sxs-lookup"><span data-stu-id="a8004-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="a8004-129">Clientes que pretende usar sempre o emissor local devem garantir que eles não usam essa associação ou que eles modificar a associação para que o endereço do emissor é `null`.</span><span class="sxs-lookup"><span data-stu-id="a8004-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8004-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8004-130">See Also</span></span>  
 [<span data-ttu-id="a8004-131">Como: configurar as credenciais em um serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="a8004-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="a8004-132">Como: criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="a8004-132">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="a8004-133">Como: criar uma WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="a8004-133">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
