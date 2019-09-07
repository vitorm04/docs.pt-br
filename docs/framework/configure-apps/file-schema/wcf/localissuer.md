---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 055b7b49d1f775d49ac20de18c18ca0433716a23
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397856"
---
# <a name="localissuer"></a><span data-ttu-id="eefb0-101">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="eefb0-101">\<localIssuer></span></span>
<span data-ttu-id="eefb0-102">Especifica o endereço e a associação do emissor local a ser usado para obter um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="eefb0-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
<span data-ttu-id="eefb0-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="eefb0-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="eefb0-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="eefb0-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="eefb0-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="eefb0-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="eefb0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="eefb0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="eefb0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="eefb0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="eefb0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="eefb0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="eefb0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> issuedToken**](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="eefb0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="eefb0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> localIssuer**</span><span class="sxs-lookup"><span data-stu-id="eefb0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eefb0-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eefb0-111">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eefb0-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="eefb0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="eefb0-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="eefb0-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eefb0-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="eefb0-114">Attributes</span></span>  
  
|<span data-ttu-id="eefb0-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="eefb0-115">Attribute</span></span>|<span data-ttu-id="eefb0-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="eefb0-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eefb0-117">endereço</span><span class="sxs-lookup"><span data-stu-id="eefb0-117">address</span></span>|<span data-ttu-id="eefb0-118">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="eefb0-118">Required string.</span></span> <span data-ttu-id="eefb0-119">Especifica o URI do emissor local.</span><span class="sxs-lookup"><span data-stu-id="eefb0-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="eefb0-120">associação</span><span class="sxs-lookup"><span data-stu-id="eefb0-120">binding</span></span>|<span data-ttu-id="eefb0-121">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="eefb0-121">Optional string.</span></span> <span data-ttu-id="eefb0-122">Uma das associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="eefb0-122">One of the system-provided bindings.</span></span> <span data-ttu-id="eefb0-123">Para obter uma lista, consulte [associações fornecidas pelo sistema](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="eefb0-123">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="eefb0-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="eefb0-124">bindingConfiguration</span></span>|<span data-ttu-id="eefb0-125">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="eefb0-125">Optional string.</span></span> <span data-ttu-id="eefb0-126">Especifica uma configuração de associação encontrada no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="eefb0-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eefb0-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="eefb0-127">Child Elements</span></span>  
  
|<span data-ttu-id="eefb0-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="eefb0-128">Element</span></span>|<span data-ttu-id="eefb0-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="eefb0-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eefb0-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="eefb0-130">\<identity></span></span>](identity.md)|<span data-ttu-id="eefb0-131">Especifica informações de identidade para o emissor local.</span><span class="sxs-lookup"><span data-stu-id="eefb0-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="eefb0-132">\<headers></span><span class="sxs-lookup"><span data-stu-id="eefb0-132">\<headers></span></span>](headers-element.md)|<span data-ttu-id="eefb0-133">Uma coleção de cabeçalhos de endereço que são necessários para resolver corretamente o emissor local.</span><span class="sxs-lookup"><span data-stu-id="eefb0-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="eefb0-134">Você pode usar a `add` palavra-chave para adicionar um cabeçalho a essa coleção.</span><span class="sxs-lookup"><span data-stu-id="eefb0-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eefb0-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="eefb0-135">Parent Elements</span></span>  
  
|<span data-ttu-id="eefb0-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="eefb0-136">Element</span></span>|<span data-ttu-id="eefb0-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="eefb0-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eefb0-138">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="eefb0-138">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="eefb0-139">Especifica um token personalizado usado para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="eefb0-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eefb0-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="eefb0-140">Remarks</span></span>  
 <span data-ttu-id="eefb0-141">Ao obter um token emitido de um serviço de token de segurança (STS), o aplicativo cliente deve ser configurado com o endereço e a associação a serem usados para se comunicar com o STS.</span><span class="sxs-lookup"><span data-stu-id="eefb0-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="eefb0-142">Quando o <xref:System.ServiceModel.WSFederationHttpBinding> não fornece uma URL para o serviço de token de segurança, ou quando o endereço do emissor de uma associação federada `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` é `null`ou, o canal de Windows Communication Foundation do cliente (WCF) usa os valores especificados por `address` e`binding` para se comunicar com o STS para obter o token emitido.</span><span class="sxs-lookup"><span data-stu-id="eefb0-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="eefb0-143">Para obter mais informações sobre como configurar um emissor local, [consulte Como: Configure um emissor](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)local.</span><span class="sxs-lookup"><span data-stu-id="eefb0-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eefb0-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eefb0-144">Example</span></span>  
 <span data-ttu-id="eefb0-145">O exemplo a seguir define `address`os `binding`atributos, `bindingConfiguration` e de um `localIssuer` elemento.</span><span class="sxs-lookup"><span data-stu-id="eefb0-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eefb0-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eefb0-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="eefb0-147">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="eefb0-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="eefb0-148">Como: Configurar um emissor local</span><span class="sxs-lookup"><span data-stu-id="eefb0-148">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="eefb0-149">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="eefb0-149">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="eefb0-150">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="eefb0-150">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="eefb0-151">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="eefb0-151">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="eefb0-152">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="eefb0-152">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="eefb0-153">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="eefb0-153">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="eefb0-154">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="eefb0-154">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="eefb0-155">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="eefb0-155">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
