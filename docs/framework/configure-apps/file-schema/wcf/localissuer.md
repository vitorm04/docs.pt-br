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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8836d9e57dd7c4d9cfdc20c5e4856e384e6d67b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltlocalissuergt"></a><span data-ttu-id="b993e-102">&lt;localIssuer&gt;</span><span class="sxs-lookup"><span data-stu-id="b993e-102">&lt;localIssuer&gt;</span></span>
<span data-ttu-id="b993e-103">Especifica o endereço e a associação do emissor local a ser usado para obter um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="b993e-103">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="b993e-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b993e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b993e-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="b993e-105">\<behaviors></span></span>  
<span data-ttu-id="b993e-106">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="b993e-106">endpointBehaviors section</span></span>  
<span data-ttu-id="b993e-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="b993e-107">\<behavior></span></span>  
<span data-ttu-id="b993e-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="b993e-108">\<clientCredentials></span></span>  
<span data-ttu-id="b993e-109">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="b993e-109">\<issuedToken></span></span>  
<span data-ttu-id="b993e-110">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="b993e-110">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b993e-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b993e-111">Syntax</span></span>  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b993e-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b993e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b993e-113">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="b993e-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b993e-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="b993e-114">Attributes</span></span>  
  
|<span data-ttu-id="b993e-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="b993e-115">Attribute</span></span>|<span data-ttu-id="b993e-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="b993e-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b993e-117">endereço</span><span class="sxs-lookup"><span data-stu-id="b993e-117">address</span></span>|<span data-ttu-id="b993e-118">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="b993e-118">Required string.</span></span> <span data-ttu-id="b993e-119">Especifica o URI do emissor local.</span><span class="sxs-lookup"><span data-stu-id="b993e-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="b993e-120">associação</span><span class="sxs-lookup"><span data-stu-id="b993e-120">binding</span></span>|<span data-ttu-id="b993e-121">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="b993e-121">Optional string.</span></span> <span data-ttu-id="b993e-122">Uma das associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="b993e-122">One of the system-provided bindings.</span></span> <span data-ttu-id="b993e-123">Para obter uma lista, consulte [System-Provided associações](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="b993e-123">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="b993e-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b993e-124">bindingConfiguration</span></span>|<span data-ttu-id="b993e-125">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="b993e-125">Optional string.</span></span> <span data-ttu-id="b993e-126">Especifica uma configuração de associação encontrada no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b993e-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b993e-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b993e-127">Child Elements</span></span>  
  
|<span data-ttu-id="b993e-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="b993e-128">Element</span></span>|<span data-ttu-id="b993e-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="b993e-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b993e-130">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="b993e-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="b993e-131">Especifica informações de identidade para o emissor local.</span><span class="sxs-lookup"><span data-stu-id="b993e-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="b993e-132">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="b993e-132">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="b993e-133">Uma coleção de cabeçalhos de endereço são necessárias para tratar corretamente o emissor local.</span><span class="sxs-lookup"><span data-stu-id="b993e-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="b993e-134">Você pode usar o `add` palavra-chave para adicionar um cabeçalho para esta coleção.</span><span class="sxs-lookup"><span data-stu-id="b993e-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b993e-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b993e-135">Parent Elements</span></span>  
  
|<span data-ttu-id="b993e-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="b993e-136">Element</span></span>|<span data-ttu-id="b993e-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="b993e-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b993e-138">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="b993e-138">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="b993e-139">Especifica um token personalizado usado para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="b993e-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b993e-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="b993e-140">Remarks</span></span>  
 <span data-ttu-id="b993e-141">Ao obter um token emitido de um Token de segurança Service (STS), o aplicativo cliente deve ser configurado com o endereço e a associação a ser usada para se comunicar com o STS.</span><span class="sxs-lookup"><span data-stu-id="b993e-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="b993e-142">Quando o <xref:System.ServiceModel.WSFederationHttpBinding> não fornecer uma URL para o serviço de token de segurança, ou quando o endereço do emissor de uma associação federada é http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous ou `null`, o cliente [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] canal usa os valores especificados pelo `address` e `binding` para se comunicar com o STS para obter o token emitido.</span><span class="sxs-lookup"><span data-stu-id="b993e-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous or `null`, the client's [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="b993e-143">Para obter mais informações sobre como configurar um emissor local, consulte [como: configurar um emissor Local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="b993e-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b993e-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b993e-144">Example</span></span>  
 <span data-ttu-id="b993e-145">O exemplo a seguir define o `address`, `binding`, e `bindingConfiguration` atributos de uma `localIssuer` elemento.</span><span class="sxs-lookup"><span data-stu-id="b993e-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b993e-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b993e-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="b993e-147">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="b993e-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="b993e-148">Como: configurar um emissor Local</span><span class="sxs-lookup"><span data-stu-id="b993e-148">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="b993e-149">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="b993e-149">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="b993e-150">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="b993e-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="b993e-151">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="b993e-151">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="b993e-152">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b993e-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="b993e-153">[Securing Clients](../../../../../docs/framework/wcf/securing-clients.md) (Protegendo clientes)</span><span class="sxs-lookup"><span data-stu-id="b993e-153">[Securing Clients](../../../../../docs/framework/wcf/securing-clients.md)</span></span>  
 [<span data-ttu-id="b993e-154">Como: criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="b993e-154">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="b993e-155">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="b993e-155">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
