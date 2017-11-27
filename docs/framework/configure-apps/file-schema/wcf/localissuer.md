---
title: '&lt;localIssuer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b11f5cbf2d70b4fff607ac42c2c98af7fb9542b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlocalissuergt"></a><span data-ttu-id="1ef85-102">&lt;localIssuer&gt;</span><span class="sxs-lookup"><span data-stu-id="1ef85-102">&lt;localIssuer&gt;</span></span>
<span data-ttu-id="1ef85-103">Especifica o endereço e a associação do emissor local a ser usado para obter um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="1ef85-103">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="1ef85-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1ef85-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1ef85-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="1ef85-105">\<behaviors></span></span>  
<span data-ttu-id="1ef85-106">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="1ef85-106">endpointBehaviors section</span></span>  
<span data-ttu-id="1ef85-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="1ef85-107">\<behavior></span></span>  
<span data-ttu-id="1ef85-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="1ef85-108">\<clientCredentials></span></span>  
<span data-ttu-id="1ef85-109">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="1ef85-109">\<issuedToken></span></span>  
<span data-ttu-id="1ef85-110">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="1ef85-110">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef85-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ef85-111">Syntax</span></span>  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ef85-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1ef85-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1ef85-113">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="1ef85-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ef85-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="1ef85-114">Attributes</span></span>  
  
|<span data-ttu-id="1ef85-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="1ef85-115">Attribute</span></span>|<span data-ttu-id="1ef85-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ef85-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ef85-117">endereço</span><span class="sxs-lookup"><span data-stu-id="1ef85-117">address</span></span>|<span data-ttu-id="1ef85-118">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="1ef85-118">Required string.</span></span> <span data-ttu-id="1ef85-119">Especifica o URI do emissor local.</span><span class="sxs-lookup"><span data-stu-id="1ef85-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="1ef85-120">associação</span><span class="sxs-lookup"><span data-stu-id="1ef85-120">binding</span></span>|<span data-ttu-id="1ef85-121">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="1ef85-121">Optional string.</span></span> <span data-ttu-id="1ef85-122">Uma das associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="1ef85-122">One of the system-provided bindings.</span></span> <span data-ttu-id="1ef85-123">Para obter uma lista, consulte [System-Provided associações](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="1ef85-123">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="1ef85-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="1ef85-124">bindingConfiguration</span></span>|<span data-ttu-id="1ef85-125">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="1ef85-125">Optional string.</span></span> <span data-ttu-id="1ef85-126">Especifica uma configuração de associação encontrada no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1ef85-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ef85-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1ef85-127">Child Elements</span></span>  
  
|<span data-ttu-id="1ef85-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="1ef85-128">Element</span></span>|<span data-ttu-id="1ef85-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ef85-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ef85-130">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="1ef85-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="1ef85-131">Especifica informações de identidade para o emissor local.</span><span class="sxs-lookup"><span data-stu-id="1ef85-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="1ef85-132">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="1ef85-132">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="1ef85-133">Uma coleção de cabeçalhos de endereço são necessárias para tratar corretamente o emissor local.</span><span class="sxs-lookup"><span data-stu-id="1ef85-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="1ef85-134">Você pode usar o `add` palavra-chave para adicionar um cabeçalho para esta coleção.</span><span class="sxs-lookup"><span data-stu-id="1ef85-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1ef85-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1ef85-135">Parent Elements</span></span>  
  
|<span data-ttu-id="1ef85-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="1ef85-136">Element</span></span>|<span data-ttu-id="1ef85-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ef85-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ef85-138">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="1ef85-138">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="1ef85-139">Especifica um token personalizado usado para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="1ef85-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ef85-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ef85-140">Remarks</span></span>  
 <span data-ttu-id="1ef85-141">Ao obter um token emitido de um Token de segurança Service (STS), o aplicativo cliente deve ser configurado com o endereço e a associação a ser usada para se comunicar com o STS.</span><span class="sxs-lookup"><span data-stu-id="1ef85-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="1ef85-142">Quando o <xref:System.ServiceModel.WSFederationHttpBinding> não fornecer uma URL para o serviço de token de segurança, ou quando o endereço do emissor de uma associação federada é http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous ou `null`, o cliente [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] canal usa os valores especificados pelo `address` e `binding` para se comunicar com o STS para obter o token emitido.</span><span class="sxs-lookup"><span data-stu-id="1ef85-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous or `null`, the client's [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="1ef85-143">Para obter mais informações sobre como configurar um emissor local, consulte [como: configurar um emissor Local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="1ef85-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ef85-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ef85-144">Example</span></span>  
 <span data-ttu-id="1ef85-145">O exemplo a seguir define o `address`, `binding`, e `bindingConfiguration` atributos de uma `localIssuer` elemento.</span><span class="sxs-lookup"><span data-stu-id="1ef85-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
```xml  
<system.serviceModel>  
 <behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <issuedToken cacheIssuedTokens="false"   
                 defaultKeyEntropyMode="ClientEntropy">  
     <localIssuer address="net.tcp://cohowinery/tokens"   
                  binding="netTcpBinding"  
                  bindingConfiguration="myTcpBindingConfig" />  
    </issuedToken>  
   </clientCredentials>  
  </behavior>  
  </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ef85-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ef85-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="1ef85-147">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="1ef85-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="1ef85-148">Como: configurar um emissor Local</span><span class="sxs-lookup"><span data-stu-id="1ef85-148">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="1ef85-149">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="1ef85-149">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="1ef85-150">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="1ef85-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="1ef85-151">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="1ef85-151">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="1ef85-152">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="1ef85-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="1ef85-153">[Securing Clients](../../../../../docs/framework/wcf/securing-clients.md) (Protegendo clientes)</span><span class="sxs-lookup"><span data-stu-id="1ef85-153">[Securing Clients](../../../../../docs/framework/wcf/securing-clients.md)</span></span>  
 [<span data-ttu-id="1ef85-154">Como: criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="1ef85-154">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="1ef85-155">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="1ef85-155">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
