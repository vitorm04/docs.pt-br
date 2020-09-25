---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 10a6d2aaad7d63d00b3a57032d0d218f756454d8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175948"
---
# \<issuerMetadata>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="c5a38-101">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5a38-101">Syntax</span></span>  
  
```xml  
<issuerMetadata address="String">
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
</issuerMetadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5a38-102">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c5a38-102">Attributes and Elements</span></span>  

 <span data-ttu-id="c5a38-103">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c5a38-103">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5a38-104">Atributos</span><span class="sxs-lookup"><span data-stu-id="c5a38-104">Attributes</span></span>  
  
|<span data-ttu-id="c5a38-105">Atributo</span><span class="sxs-lookup"><span data-stu-id="c5a38-105">Attribute</span></span>|<span data-ttu-id="c5a38-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5a38-106">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5a38-107">address</span><span class="sxs-lookup"><span data-stu-id="c5a38-107">address</span></span>|<span data-ttu-id="c5a38-108">Atributo `string` obrigatório.</span><span class="sxs-lookup"><span data-stu-id="c5a38-108">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="c5a38-109">Especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c5a38-109">Specifies the address of the endpoint.</span></span> <span data-ttu-id="c5a38-110">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="c5a38-110">The address must be an absolute URI.</span></span> <span data-ttu-id="c5a38-111">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="c5a38-111">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5a38-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c5a38-112">Child Elements</span></span>  
  
|<span data-ttu-id="c5a38-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="c5a38-113">Element</span></span>|<span data-ttu-id="c5a38-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5a38-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="c5a38-115">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="c5a38-115">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="c5a38-116">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidades que trocam mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="c5a38-116">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5a38-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c5a38-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c5a38-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="c5a38-118">Element</span></span>|<span data-ttu-id="c5a38-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5a38-119">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="c5a38-120">Define as configurações para a segurança em nível de mensagem para o [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="c5a38-120">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5a38-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="c5a38-121">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="c5a38-122">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="c5a38-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c5a38-123">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="c5a38-123">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c5a38-124">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="c5a38-124">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="c5a38-125">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="c5a38-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
