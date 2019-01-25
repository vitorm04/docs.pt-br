---
title: '&lt;localIssuer&gt;'
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 893ac2cb0e6c54beae68e2607c31564baafd95fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527543"
---
# <a name="ltlocalissuergt"></a><span data-ttu-id="10753-102">&lt;localIssuer&gt;</span><span class="sxs-lookup"><span data-stu-id="10753-102">&lt;localIssuer&gt;</span></span>
<span data-ttu-id="10753-103">Especifica o endereço e a associação do emissor local a ser usado para obter um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="10753-103">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="10753-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="10753-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="10753-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="10753-105">\<behaviors></span></span>  
<span data-ttu-id="10753-106">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="10753-106">endpointBehaviors section</span></span>  
<span data-ttu-id="10753-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="10753-107">\<behavior></span></span>  
<span data-ttu-id="10753-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="10753-108">\<clientCredentials></span></span>  
<span data-ttu-id="10753-109">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="10753-109">\<issuedToken></span></span>  
<span data-ttu-id="10753-110">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="10753-110">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10753-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10753-111">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10753-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="10753-112">Attributes and Elements</span></span>  
 <span data-ttu-id="10753-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="10753-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10753-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="10753-114">Attributes</span></span>  
  
|<span data-ttu-id="10753-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="10753-115">Attribute</span></span>|<span data-ttu-id="10753-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="10753-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="10753-117">endereço</span><span class="sxs-lookup"><span data-stu-id="10753-117">address</span></span>|<span data-ttu-id="10753-118">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="10753-118">Required string.</span></span> <span data-ttu-id="10753-119">Especifica o URI do emissor local.</span><span class="sxs-lookup"><span data-stu-id="10753-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="10753-120">associação</span><span class="sxs-lookup"><span data-stu-id="10753-120">binding</span></span>|<span data-ttu-id="10753-121">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="10753-121">Optional string.</span></span> <span data-ttu-id="10753-122">Uma das associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="10753-122">One of the system-provided bindings.</span></span> <span data-ttu-id="10753-123">Para obter uma lista, consulte [System-Provided associações](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="10753-123">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="10753-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="10753-124">bindingConfiguration</span></span>|<span data-ttu-id="10753-125">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="10753-125">Optional string.</span></span> <span data-ttu-id="10753-126">Especifica uma configuração de associação encontrada no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="10753-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10753-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="10753-127">Child Elements</span></span>  
  
|<span data-ttu-id="10753-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="10753-128">Element</span></span>|<span data-ttu-id="10753-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="10753-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10753-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="10753-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="10753-131">Especifica informações de identidade para o emissor local.</span><span class="sxs-lookup"><span data-stu-id="10753-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="10753-132">\<headers></span><span class="sxs-lookup"><span data-stu-id="10753-132">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="10753-133">Uma coleção de cabeçalhos de endereço que são necessários para tratar corretamente o emissor local.</span><span class="sxs-lookup"><span data-stu-id="10753-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="10753-134">Você pode usar o `add` palavra-chave para adicionar um cabeçalho a esta coleção.</span><span class="sxs-lookup"><span data-stu-id="10753-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="10753-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="10753-135">Parent Elements</span></span>  
  
|<span data-ttu-id="10753-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="10753-136">Element</span></span>|<span data-ttu-id="10753-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="10753-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10753-138">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="10753-138">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="10753-139">Especifica um token personalizado usado para autenticar um cliente a um serviço.</span><span class="sxs-lookup"><span data-stu-id="10753-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10753-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="10753-140">Remarks</span></span>  
 <span data-ttu-id="10753-141">Ao obter um token emitido de um Security Token Service (STS), o aplicativo cliente deve ser configurado com o endereço e associação a ser usada para se comunicar com o STS.</span><span class="sxs-lookup"><span data-stu-id="10753-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="10753-142">Quando o <xref:System.ServiceModel.WSFederationHttpBinding> não fornece uma URL para o serviço de token de segurança, ou quando é o endereço do emissor de uma associação federado `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` ou `null`, o canal do cliente Windows Communication Foundation (WCF) usa os valores especificados pelo `address`e `binding` para se comunicar com o STS a fim de obter o token emitido.</span><span class="sxs-lookup"><span data-stu-id="10753-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="10753-143">Para obter mais informações sobre como configurar um emissor local, consulte [como: Configurar um emissor Local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="10753-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10753-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10753-144">Example</span></span>  
 <span data-ttu-id="10753-145">O exemplo a seguir define o `address`, `binding`, e `bindingConfiguration` atributos de um `localIssuer` elemento.</span><span class="sxs-lookup"><span data-stu-id="10753-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="10753-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10753-146">See also</span></span>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="10753-147">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="10753-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="10753-148">Como: Configurar um emissor Local</span><span class="sxs-lookup"><span data-stu-id="10753-148">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="10753-149">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="10753-149">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="10753-150">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="10753-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="10753-151">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="10753-151">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="10753-152">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="10753-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="10753-153">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="10753-153">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="10753-154">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="10753-154">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="10753-155">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="10753-155">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
