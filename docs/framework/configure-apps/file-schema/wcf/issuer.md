---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 9e92bbcacf529a97e1ae936e93e38c98eab19cab
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157259"
---
# \<issuer>

<span data-ttu-id="ab889-101">Especifica o serviço de token de segurança (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="ab889-101">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="ab889-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="ab889-102">Syntax</span></span>  
  
```xml  
<issuer address="Uri">
  <headers>
    <add name="String"
         namespace="String" />
  </headers>
  <identity>
    <certificate encodedValue="String" />
    <certificateReference findValue="String"
                          isChainIncluded="Boolean"
                          storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                          storeLocation="LocalMachine/CurrentUser"
                          x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
    <dns value="String" />
    <rsa value="String" />
    <servicePrincipalName value="String" />
    <usePrincipalName value="String" />
  </identity>
</issuer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab889-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ab889-103">Attributes and Elements</span></span>  

 <span data-ttu-id="ab889-104">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="ab889-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab889-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="ab889-105">Attributes</span></span>  
  
|<span data-ttu-id="ab889-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="ab889-106">Attribute</span></span>|<span data-ttu-id="ab889-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab889-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab889-108">address</span><span class="sxs-lookup"><span data-stu-id="ab889-108">address</span></span>|<span data-ttu-id="ab889-109">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="ab889-109">Required string.</span></span> <span data-ttu-id="ab889-110">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="ab889-110">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab889-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ab889-111">Child Elements</span></span>  
  
|<span data-ttu-id="ab889-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="ab889-112">Element</span></span>|<span data-ttu-id="ab889-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab889-113">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="ab889-114">Uma coleção de cabeçalhos de endereço para os pontos de extremidade que o construtor pode criar.</span><span class="sxs-lookup"><span data-stu-id="ab889-114">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="ab889-115">Ao usar um token emitido, especifica as configurações que permitem que o cliente autentique o servidor.</span><span class="sxs-lookup"><span data-stu-id="ab889-115">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab889-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ab889-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ab889-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="ab889-117">Element</span></span>|<span data-ttu-id="ab889-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab889-118">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="ab889-119">Define as configurações para a segurança em nível de mensagem para o [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="ab889-119">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab889-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="ab889-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="ab889-121">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="ab889-121">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ab889-122">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="ab889-122">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ab889-123">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="ab889-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ab889-124">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="ab889-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ab889-125">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="ab889-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="ab889-126">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="ab889-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
