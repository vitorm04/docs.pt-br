---
title: 'Como: configurar um emissor local'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 0028a0522447588ee0fb183b5b2f93d334a7b2b2
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972078"
---
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="39d55-102">Como: configurar um emissor local</span><span class="sxs-lookup"><span data-stu-id="39d55-102">How to: Configure a Local Issuer</span></span>

<span data-ttu-id="39d55-103">Este tópico descreve como configurar um cliente para usar um emissor local para tokens emitidos.</span><span class="sxs-lookup"><span data-stu-id="39d55-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>

<span data-ttu-id="39d55-104">Geralmente, quando um cliente se comunica com um serviço federado, o serviço especifica o endereço do serviço de token de segurança que deve emitir o token que o cliente usará para se autenticar no serviço federado.</span><span class="sxs-lookup"><span data-stu-id="39d55-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="39d55-105">Em determinadas situações, o cliente pode ser configurado para usar um *emissor local*.</span><span class="sxs-lookup"><span data-stu-id="39d55-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>

<span data-ttu-id="39d55-106">Windows Communication Foundation (WCF) usa um emissor local em casos em que o endereço do emissor de uma associação federada é `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` ou `null`.</span><span class="sxs-lookup"><span data-stu-id="39d55-106">Windows Communication Foundation (WCF) uses a local issuer in cases where the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="39d55-107">Nesses casos, você deve configurar o <xref:System.ServiceModel.Description.ClientCredentials> com o endereço do emissor local e a associação a ser usada para se comunicar com esse emissor.</span><span class="sxs-lookup"><span data-stu-id="39d55-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>

> [!NOTE]
> <span data-ttu-id="39d55-108">Se a <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> `ClientCredentials` propriedade da classe for definida como `true`, um endereço de emissor local não será especificado [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e o endereço do emissor especificado pelo > WSFederationHttpBinding ou outra associação federada será `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` ,`http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`ou é`null`, o emissor do Windows CardSpace é usado.</span><span class="sxs-lookup"><span data-stu-id="39d55-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, or is `null`, then the Windows CardSpace issuer is used.</span></span>

## <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="39d55-109">Para configurar o emissor local no código</span><span class="sxs-lookup"><span data-stu-id="39d55-109">To configure the local issuer in code</span></span>

1. <span data-ttu-id="39d55-110">Criar uma variável do tipo<xref:System.ServiceModel.Security.IssuedTokenClientCredential></span><span class="sxs-lookup"><span data-stu-id="39d55-110">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>

2. <span data-ttu-id="39d55-111">Defina a variável para a instância retornada da <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> propriedade `ClientCredentials` da classe.</span><span class="sxs-lookup"><span data-stu-id="39d55-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="39d55-112">Essa <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> instância é retornada pela propriedade do cliente (herdada de <xref:System.ServiceModel.ClientBase%601>) <xref:System.ServiceModel.ChannelFactory>ou a <xref:System.ServiceModel.ChannelFactory.Credentials%2A> propriedade de:</span><span class="sxs-lookup"><span data-stu-id="39d55-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. <span data-ttu-id="39d55-113">Defina a <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> propriedade para uma nova instância <xref:System.ServiceModel.EndpointAddress>do, com o endereço do emissor local como um argumento para o construtor.</span><span class="sxs-lookup"><span data-stu-id="39d55-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     <span data-ttu-id="39d55-114">Como alternativa, crie uma nova <xref:System.Uri> instância como um argumento para o construtor.</span><span class="sxs-lookup"><span data-stu-id="39d55-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     <span data-ttu-id="39d55-115">O `addressHeaders` parâmetro é uma matriz de <xref:System.ServiceModel.Channels.AddressHeader> instâncias, como mostrado.</span><span class="sxs-lookup"><span data-stu-id="39d55-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. <span data-ttu-id="39d55-116">Defina a associação para o emissor local usando a <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="39d55-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. <span data-ttu-id="39d55-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="39d55-117">Optional.</span></span> <span data-ttu-id="39d55-118">Adicione comportamentos de ponto de extremidade configurados para o emissor local adicionando esses comportamentos à coleção retornada <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> pela propriedade.</span><span class="sxs-lookup"><span data-stu-id="39d55-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="39d55-119">Para configurar o emissor local na configuração</span><span class="sxs-lookup"><span data-stu-id="39d55-119">To configure the local issuer in configuration</span></span>

1. <span data-ttu-id="39d55-120">Crie um [ \<elemento localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) como [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) um filho do elemento issuedToken > que é, por si só, um [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) filho do elemento ClientCredentials > em um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="39d55-120">Create a [\<localIssuer>](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>

2. <span data-ttu-id="39d55-121">Defina o `address` atributo como o endereço do emissor local que aceitará solicitações de token.</span><span class="sxs-lookup"><span data-stu-id="39d55-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>

3. <span data-ttu-id="39d55-122">Defina os `binding` atributos `bindingConfiguration` e como valores que fazem referência à associação apropriada a ser usada na comunicação com o ponto de extremidade do emissor local.</span><span class="sxs-lookup"><span data-stu-id="39d55-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>

4. <span data-ttu-id="39d55-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="39d55-123">Optional.</span></span> <span data-ttu-id="39d55-124">Defina o [ \<elemento Identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) como um filho do elemento <`localIssuer`> e especifique informações de identidade para o emissor local.</span><span class="sxs-lookup"><span data-stu-id="39d55-124">Set the [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>

5. <span data-ttu-id="39d55-125">Opcional.</span><span class="sxs-lookup"><span data-stu-id="39d55-125">Optional.</span></span> <span data-ttu-id="39d55-126">Defina os [ \<cabeçalhos >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) elemento como um filho do elemento <`localIssuer`> e especifique cabeçalhos adicionais que são necessários para resolver corretamente o emissor local.</span><span class="sxs-lookup"><span data-stu-id="39d55-126">Set the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="39d55-127">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="39d55-127">.NET Framework Security</span></span>

<span data-ttu-id="39d55-128">Observe que, se um endereço de emissor e uma associação forem especificados para uma determinada associação, o emissor local não será usado para pontos de extremidade que usam essa associação.</span><span class="sxs-lookup"><span data-stu-id="39d55-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="39d55-129">Os clientes que esperam sempre usar o emissor local devem garantir que eles não usem essa associação ou que modifiquem a associação para que o endereço do emissor seja `null`.</span><span class="sxs-lookup"><span data-stu-id="39d55-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>

## <a name="see-also"></a><span data-ttu-id="39d55-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39d55-130">See also</span></span>

- [<span data-ttu-id="39d55-131">Como: Configurar credenciais em um Serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="39d55-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="39d55-132">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="39d55-132">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="39d55-133">Como: Criar um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="39d55-133">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
