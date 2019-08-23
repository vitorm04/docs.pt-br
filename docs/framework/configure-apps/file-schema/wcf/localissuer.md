---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 4ec5a99139112ae600c1c2bc44feb6d3f62da1e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931733"
---
# <a name="localissuer"></a><span data-ttu-id="488e8-101">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="488e8-101">\<localIssuer></span></span>
<span data-ttu-id="488e8-102">Especifica o endereço e a associação do emissor local a ser usado para obter um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="488e8-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="488e8-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="488e8-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="488e8-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="488e8-104">\<behaviors></span></span>  
<span data-ttu-id="488e8-105">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="488e8-105">endpointBehaviors section</span></span>  
<span data-ttu-id="488e8-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="488e8-106">\<behavior></span></span>  
<span data-ttu-id="488e8-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="488e8-107">\<clientCredentials></span></span>  
<span data-ttu-id="488e8-108">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="488e8-108">\<issuedToken></span></span>  
<span data-ttu-id="488e8-109">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="488e8-109">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="488e8-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="488e8-110">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="488e8-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="488e8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="488e8-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="488e8-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="488e8-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="488e8-113">Attributes</span></span>  
  
|<span data-ttu-id="488e8-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="488e8-114">Attribute</span></span>|<span data-ttu-id="488e8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="488e8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="488e8-116">endereço</span><span class="sxs-lookup"><span data-stu-id="488e8-116">address</span></span>|<span data-ttu-id="488e8-117">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="488e8-117">Required string.</span></span> <span data-ttu-id="488e8-118">Especifica o URI do emissor local.</span><span class="sxs-lookup"><span data-stu-id="488e8-118">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="488e8-119">associação</span><span class="sxs-lookup"><span data-stu-id="488e8-119">binding</span></span>|<span data-ttu-id="488e8-120">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="488e8-120">Optional string.</span></span> <span data-ttu-id="488e8-121">Uma das associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="488e8-121">One of the system-provided bindings.</span></span> <span data-ttu-id="488e8-122">Para obter uma lista, consulte [associações fornecidas pelo sistema](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="488e8-122">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="488e8-123">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="488e8-123">bindingConfiguration</span></span>|<span data-ttu-id="488e8-124">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="488e8-124">Optional string.</span></span> <span data-ttu-id="488e8-125">Especifica uma configuração de associação encontrada no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="488e8-125">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="488e8-126">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="488e8-126">Child Elements</span></span>  
  
|<span data-ttu-id="488e8-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="488e8-127">Element</span></span>|<span data-ttu-id="488e8-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="488e8-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="488e8-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="488e8-129">\<identity></span></span>](identity.md)|<span data-ttu-id="488e8-130">Especifica informações de identidade para o emissor local.</span><span class="sxs-lookup"><span data-stu-id="488e8-130">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="488e8-131">\<headers></span><span class="sxs-lookup"><span data-stu-id="488e8-131">\<headers></span></span>](headers-element.md)|<span data-ttu-id="488e8-132">Uma coleção de cabeçalhos de endereço que são necessários para resolver corretamente o emissor local.</span><span class="sxs-lookup"><span data-stu-id="488e8-132">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="488e8-133">Você pode usar a `add` palavra-chave para adicionar um cabeçalho a essa coleção.</span><span class="sxs-lookup"><span data-stu-id="488e8-133">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="488e8-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="488e8-134">Parent Elements</span></span>  
  
|<span data-ttu-id="488e8-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="488e8-135">Element</span></span>|<span data-ttu-id="488e8-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="488e8-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="488e8-137">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="488e8-137">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="488e8-138">Especifica um token personalizado usado para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="488e8-138">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="488e8-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="488e8-139">Remarks</span></span>  
 <span data-ttu-id="488e8-140">Ao obter um token emitido de um serviço de token de segurança (STS), o aplicativo cliente deve ser configurado com o endereço e a associação a serem usados para se comunicar com o STS.</span><span class="sxs-lookup"><span data-stu-id="488e8-140">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="488e8-141">Quando o <xref:System.ServiceModel.WSFederationHttpBinding> não fornece uma URL para o serviço de token de segurança, ou quando o endereço do emissor de uma associação federada `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` é `null`ou, o canal de Windows Communication Foundation do cliente (WCF) usa os valores especificados por `address` e`binding` para se comunicar com o STS para obter o token emitido.</span><span class="sxs-lookup"><span data-stu-id="488e8-141">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="488e8-142">Para obter mais informações sobre como configurar um emissor local, [consulte Como: Configure um emissor](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)local.</span><span class="sxs-lookup"><span data-stu-id="488e8-142">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="488e8-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="488e8-143">Example</span></span>  
 <span data-ttu-id="488e8-144">O exemplo a seguir define `address`os `binding`atributos, `bindingConfiguration` e de um `localIssuer` elemento.</span><span class="sxs-lookup"><span data-stu-id="488e8-144">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="488e8-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="488e8-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="488e8-146">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="488e8-146">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="488e8-147">Como: Configurar um emissor local</span><span class="sxs-lookup"><span data-stu-id="488e8-147">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="488e8-148">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="488e8-148">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="488e8-149">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="488e8-149">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="488e8-150">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="488e8-150">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="488e8-151">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="488e8-151">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="488e8-152">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="488e8-152">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="488e8-153">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="488e8-153">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="488e8-154">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="488e8-154">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
