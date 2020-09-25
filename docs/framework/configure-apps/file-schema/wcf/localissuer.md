---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: e08d2c0b42cfd8e302223915f0256f8cb2d1468b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204951"
---
# \<localIssuer>

<span data-ttu-id="d0af6-101">Especifica o endereço e a associação do emissor local a ser usado para obter um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="d0af6-101">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**  
  
## <a name="syntax"></a><span data-ttu-id="d0af6-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0af6-102">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0af6-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d0af6-103">Attributes and Elements</span></span>  

 <span data-ttu-id="d0af6-104">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="d0af6-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0af6-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="d0af6-105">Attributes</span></span>  
  
|<span data-ttu-id="d0af6-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="d0af6-106">Attribute</span></span>|<span data-ttu-id="d0af6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0af6-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0af6-108">address</span><span class="sxs-lookup"><span data-stu-id="d0af6-108">address</span></span>|<span data-ttu-id="d0af6-109">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="d0af6-109">Required string.</span></span> <span data-ttu-id="d0af6-110">Especifica o URI do emissor local.</span><span class="sxs-lookup"><span data-stu-id="d0af6-110">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="d0af6-111">associação</span><span class="sxs-lookup"><span data-stu-id="d0af6-111">binding</span></span>|<span data-ttu-id="d0af6-112">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="d0af6-112">Optional string.</span></span> <span data-ttu-id="d0af6-113">Uma das associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="d0af6-113">One of the system-provided bindings.</span></span> <span data-ttu-id="d0af6-114">Para obter uma lista, consulte [associações fornecidas pelo sistema](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="d0af6-114">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="d0af6-115">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="d0af6-115">bindingConfiguration</span></span>|<span data-ttu-id="d0af6-116">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="d0af6-116">Optional string.</span></span> <span data-ttu-id="d0af6-117">Especifica uma configuração de associação encontrada no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d0af6-117">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0af6-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d0af6-118">Child Elements</span></span>  
  
|<span data-ttu-id="d0af6-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="d0af6-119">Element</span></span>|<span data-ttu-id="d0af6-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0af6-120">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="d0af6-121">Especifica informações de identidade para o emissor local.</span><span class="sxs-lookup"><span data-stu-id="d0af6-121">Specifies identity information for the local issuer.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="d0af6-122">Uma coleção de cabeçalhos de endereço que são necessários para resolver corretamente o emissor local.</span><span class="sxs-lookup"><span data-stu-id="d0af6-122">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="d0af6-123">Você pode usar a `add` palavra-chave para adicionar um cabeçalho a essa coleção.</span><span class="sxs-lookup"><span data-stu-id="d0af6-123">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0af6-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d0af6-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d0af6-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="d0af6-125">Element</span></span>|<span data-ttu-id="d0af6-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0af6-126">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="d0af6-127">Especifica um token personalizado usado para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="d0af6-127">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0af6-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0af6-128">Remarks</span></span>  

 <span data-ttu-id="d0af6-129">Ao obter um token emitido de um serviço de token de segurança (STS), o aplicativo cliente deve ser configurado com o endereço e a associação a serem usados para se comunicar com o STS.</span><span class="sxs-lookup"><span data-stu-id="d0af6-129">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="d0af6-130">Quando o não <xref:System.ServiceModel.WSFederationHttpBinding> fornece uma URL para o serviço de token de segurança, ou quando o endereço do emissor de uma associação federada é `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` ou `null` , o canal de Windows Communication Foundation do cliente (WCF) usa os valores especificados por `address` e `binding` para se comunicar com o STS para obter o token emitido.</span><span class="sxs-lookup"><span data-stu-id="d0af6-130">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="d0af6-131">Para obter mais informações sobre como configurar um emissor local, consulte [como configurar um emissor local](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="d0af6-131">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0af6-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0af6-132">Example</span></span>  

 <span data-ttu-id="d0af6-133">O exemplo a seguir define `address` os `binding` atributos, e `bindingConfiguration` de um `localIssuer` elemento.</span><span class="sxs-lookup"><span data-stu-id="d0af6-133">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d0af6-134">Veja também</span><span class="sxs-lookup"><span data-stu-id="d0af6-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="d0af6-135">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="d0af6-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="d0af6-136">Como: configurar um emissor local</span><span class="sxs-lookup"><span data-stu-id="d0af6-136">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="d0af6-137">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="d0af6-137">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d0af6-138">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="d0af6-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="d0af6-139">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="d0af6-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d0af6-140">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d0af6-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d0af6-141">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="d0af6-141">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="d0af6-142">Como: criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="d0af6-142">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="d0af6-143">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="d0af6-143">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
