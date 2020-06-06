---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 841331f233bb8c42c25c88ad8e9b4fb1a86faa76
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398999"
---
# \<xmlElement>
<span data-ttu-id="9c326-101">Especifica um elemento XML que é enviado no corpo da mensagem para o serviço de token de segurança ao solicitar um token.</span><span class="sxs-lookup"><span data-stu-id="9c326-101">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**  
  
## <a name="syntax"></a><span data-ttu-id="9c326-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c326-102">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c326-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9c326-103">Attributes and Elements</span></span>  
 <span data-ttu-id="9c326-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9c326-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c326-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="9c326-105">Attributes</span></span>  
  
|<span data-ttu-id="9c326-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="9c326-106">Attribute</span></span>|<span data-ttu-id="9c326-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c326-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c326-108">xmlElement</span><span class="sxs-lookup"><span data-stu-id="9c326-108">xmlElement</span></span>|<span data-ttu-id="9c326-109">Uma cadeia de caracteres que especifica um elemento XML que é enviado no corpo da mensagem para o serviço de token de segurança ao solicitar um token.</span><span class="sxs-lookup"><span data-stu-id="9c326-109">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c326-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9c326-110">Child Elements</span></span>  
 <span data-ttu-id="9c326-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9c326-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c326-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9c326-112">Parent Elements</span></span>  
  
|<span data-ttu-id="9c326-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c326-113">Element</span></span>|<span data-ttu-id="9c326-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c326-114">Description</span></span>|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="9c326-115">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="9c326-115">A collection of token request parameters.</span></span> <span data-ttu-id="9c326-116">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="9c326-116">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c326-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="9c326-117">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="9c326-118">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="9c326-118">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="9c326-119">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="9c326-119">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9c326-120">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="9c326-120">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="9c326-121">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="9c326-121">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9c326-122">Associações</span><span class="sxs-lookup"><span data-stu-id="9c326-122">Bindings</span></span>](../../../wcf/bindings.md)
