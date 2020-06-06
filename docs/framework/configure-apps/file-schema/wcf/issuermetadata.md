---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: a28223127f7987a80bdf12d2dcf42878f717a377
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397887"
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
  
## <a name="syntax"></a><span data-ttu-id="3eaa7-101">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3eaa7-101">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3eaa7-102">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3eaa7-102">Attributes and Elements</span></span>  
 <span data-ttu-id="3eaa7-103">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3eaa7-103">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3eaa7-104">Atributos</span><span class="sxs-lookup"><span data-stu-id="3eaa7-104">Attributes</span></span>  
  
|<span data-ttu-id="3eaa7-105">Atributo</span><span class="sxs-lookup"><span data-stu-id="3eaa7-105">Attribute</span></span>|<span data-ttu-id="3eaa7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3eaa7-106">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3eaa7-107">address</span><span class="sxs-lookup"><span data-stu-id="3eaa7-107">address</span></span>|<span data-ttu-id="3eaa7-108">Atributo `string` obrigatório.</span><span class="sxs-lookup"><span data-stu-id="3eaa7-108">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="3eaa7-109">Especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3eaa7-109">Specifies the address of the endpoint.</span></span> <span data-ttu-id="3eaa7-110">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="3eaa7-110">The address must be an absolute URI.</span></span> <span data-ttu-id="3eaa7-111">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="3eaa7-111">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3eaa7-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3eaa7-112">Child Elements</span></span>  
  
|<span data-ttu-id="3eaa7-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="3eaa7-113">Element</span></span>|<span data-ttu-id="3eaa7-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3eaa7-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="3eaa7-115">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="3eaa7-115">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="3eaa7-116">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidades que trocam mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="3eaa7-116">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3eaa7-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3eaa7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3eaa7-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="3eaa7-118">Element</span></span>|<span data-ttu-id="3eaa7-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="3eaa7-119">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="3eaa7-120">Define as configurações para a segurança em nível de mensagem para o [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="3eaa7-120">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3eaa7-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="3eaa7-121">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="3eaa7-122">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="3eaa7-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="3eaa7-123">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="3eaa7-123">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3eaa7-124">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="3eaa7-124">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="3eaa7-125">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="3eaa7-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
