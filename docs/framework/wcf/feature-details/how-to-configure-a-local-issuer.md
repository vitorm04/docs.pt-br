---
title: Como configurar um emissor local
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 7da3cd34d0840eea48c9ef0bb89fb6580b87623b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601238"
---
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="4d213-102">Como configurar um emissor local</span><span class="sxs-lookup"><span data-stu-id="4d213-102">How to: Configure a Local Issuer</span></span>

<span data-ttu-id="4d213-103">Este tópico descreve como configurar um cliente para usar um emissor local para tokens emitidos.</span><span class="sxs-lookup"><span data-stu-id="4d213-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>

<span data-ttu-id="4d213-104">Geralmente, quando um cliente se comunica com um serviço federado, o serviço especifica o endereço do serviço de token de segurança que deve emitir o token que o cliente usará para se autenticar no serviço federado.</span><span class="sxs-lookup"><span data-stu-id="4d213-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="4d213-105">Em determinadas situações, o cliente pode ser configurado para usar um *emissor local*.</span><span class="sxs-lookup"><span data-stu-id="4d213-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>

<span data-ttu-id="4d213-106">Windows Communication Foundation (WCF) usa um emissor local em casos em que o endereço do emissor de uma associação federada é `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` ou `null` .</span><span class="sxs-lookup"><span data-stu-id="4d213-106">Windows Communication Foundation (WCF) uses a local issuer in cases where the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="4d213-107">Nesses casos, você deve configurar o <xref:System.ServiceModel.Description.ClientCredentials> com o endereço do emissor local e a associação a ser usada para se comunicar com esse emissor.</span><span class="sxs-lookup"><span data-stu-id="4d213-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>

> [!NOTE]
> <span data-ttu-id="4d213-108">Se a <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> propriedade da `ClientCredentials` classe for definida como `true` , um endereço de emissor local não será especificado e o endereço do emissor especificado pelo [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ou outra associação federada será, `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` ou será `null` , o emissor do Windows CardSpace será usado.</span><span class="sxs-lookup"><span data-stu-id="4d213-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, or is `null`, then the Windows CardSpace issuer is used.</span></span>

## <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="4d213-109">Para configurar o emissor local no código</span><span class="sxs-lookup"><span data-stu-id="4d213-109">To configure the local issuer in code</span></span>

1. <span data-ttu-id="4d213-110">Criar uma variável do tipo<xref:System.ServiceModel.Security.IssuedTokenClientCredential></span><span class="sxs-lookup"><span data-stu-id="4d213-110">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>

2. <span data-ttu-id="4d213-111">Defina a variável para a instância retornada da <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> propriedade da `ClientCredentials` classe.</span><span class="sxs-lookup"><span data-stu-id="4d213-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="4d213-112">Essa instância é retornada pela <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Propriedade do cliente (herdada de <xref:System.ServiceModel.ClientBase%601> ) ou a <xref:System.ServiceModel.ChannelFactory.Credentials%2A> propriedade de <xref:System.ServiceModel.ChannelFactory> :</span><span class="sxs-lookup"><span data-stu-id="4d213-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. <span data-ttu-id="4d213-113">Defina a <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> propriedade para uma nova instância do <xref:System.ServiceModel.EndpointAddress> , com o endereço do emissor local como um argumento para o construtor.</span><span class="sxs-lookup"><span data-stu-id="4d213-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     <span data-ttu-id="4d213-114">Como alternativa, crie uma nova <xref:System.Uri> instância como um argumento para o construtor.</span><span class="sxs-lookup"><span data-stu-id="4d213-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     <span data-ttu-id="4d213-115">O `addressHeaders` parâmetro é uma matriz de <xref:System.ServiceModel.Channels.AddressHeader> instâncias, como mostrado.</span><span class="sxs-lookup"><span data-stu-id="4d213-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. <span data-ttu-id="4d213-116">Defina a associação para o emissor local usando a <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d213-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. <span data-ttu-id="4d213-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4d213-117">Optional.</span></span> <span data-ttu-id="4d213-118">Adicione comportamentos de ponto de extremidade configurados para o emissor local adicionando esses comportamentos à coleção retornada pela <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d213-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="4d213-119">Para configurar o emissor local na configuração</span><span class="sxs-lookup"><span data-stu-id="4d213-119">To configure the local issuer in configuration</span></span>

1. <span data-ttu-id="4d213-120">Crie um [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) elemento como um filho do [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) elemento que é, em si, um filho do [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) elemento em um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="4d213-120">Create a [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>

2. <span data-ttu-id="4d213-121">Defina o `address` atributo como o endereço do emissor local que aceitará solicitações de token.</span><span class="sxs-lookup"><span data-stu-id="4d213-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>

3. <span data-ttu-id="4d213-122">Defina os `binding` `bindingConfiguration` atributos e como valores que fazem referência à associação apropriada a ser usada na comunicação com o ponto de extremidade do emissor local.</span><span class="sxs-lookup"><span data-stu-id="4d213-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>

4. <span data-ttu-id="4d213-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4d213-123">Optional.</span></span> <span data-ttu-id="4d213-124">Defina o [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elemento como um filho do elemento <`localIssuer`> e especifique informações de identidade para o emissor local.</span><span class="sxs-lookup"><span data-stu-id="4d213-124">Set the [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>

5. <span data-ttu-id="4d213-125">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4d213-125">Optional.</span></span> <span data-ttu-id="4d213-126">Defina o [\<headers>](../../configure-apps/file-schema/wcf/headers.md) elemento como um filho do elemento <`localIssuer`> e especifique cabeçalhos adicionais que são necessários para resolver corretamente o emissor local.</span><span class="sxs-lookup"><span data-stu-id="4d213-126">Set the [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="4d213-127">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4d213-127">.NET Framework Security</span></span>

<span data-ttu-id="4d213-128">Observe que, se um endereço de emissor e uma associação forem especificados para uma determinada associação, o emissor local não será usado para pontos de extremidade que usam essa associação.</span><span class="sxs-lookup"><span data-stu-id="4d213-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="4d213-129">Os clientes que esperam sempre usar o emissor local devem garantir que eles não usem essa associação ou que modifiquem a associação para que o endereço do emissor seja `null` .</span><span class="sxs-lookup"><span data-stu-id="4d213-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d213-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d213-130">See also</span></span>

- [<span data-ttu-id="4d213-131">Como configurar credenciais em um serviço de federação</span><span class="sxs-lookup"><span data-stu-id="4d213-131">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="4d213-132">Como criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="4d213-132">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)
- [<span data-ttu-id="4d213-133">Como criar um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="4d213-133">How to: Create a WSFederationHttpBinding</span></span>](how-to-create-a-wsfederationhttpbinding.md)
