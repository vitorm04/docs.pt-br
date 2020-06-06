---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 74f5f2fc1a0fa1ffbbb510e4e700c33a13d02ab3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397910"
---
# \<issuer>
<span data-ttu-id="c2dcb-101">Especifica o serviço de token de segurança (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="c2dcb-101">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="c2dcb-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2dcb-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2dcb-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c2dcb-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c2dcb-104">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="c2dcb-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2dcb-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="c2dcb-105">Attributes</span></span>  
  
|<span data-ttu-id="c2dcb-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="c2dcb-106">Attribute</span></span>|<span data-ttu-id="c2dcb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2dcb-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2dcb-108">address</span><span class="sxs-lookup"><span data-stu-id="c2dcb-108">address</span></span>|<span data-ttu-id="c2dcb-109">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="c2dcb-109">Required string.</span></span> <span data-ttu-id="c2dcb-110">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="c2dcb-110">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2dcb-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c2dcb-111">Child Elements</span></span>  
  
|<span data-ttu-id="c2dcb-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="c2dcb-112">Element</span></span>|<span data-ttu-id="c2dcb-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2dcb-113">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="c2dcb-114">Uma coleção de cabeçalhos de endereço para os pontos de extremidade que o construtor pode criar.</span><span class="sxs-lookup"><span data-stu-id="c2dcb-114">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="c2dcb-115">Ao usar um token emitido, especifica as configurações que permitem que o cliente autentique o servidor.</span><span class="sxs-lookup"><span data-stu-id="c2dcb-115">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2dcb-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c2dcb-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c2dcb-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="c2dcb-117">Element</span></span>|<span data-ttu-id="c2dcb-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2dcb-118">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="c2dcb-119">Define as configurações para a segurança em nível de mensagem para o [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="c2dcb-119">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2dcb-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="c2dcb-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="c2dcb-121">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="c2dcb-121">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c2dcb-122">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="c2dcb-122">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c2dcb-123">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="c2dcb-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c2dcb-124">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="c2dcb-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c2dcb-125">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="c2dcb-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="c2dcb-126">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="c2dcb-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
