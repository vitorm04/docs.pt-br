---
title: <clear>do <claimTypeRequirements> elemento
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 01f101f7d0dd5da6a834a4ffb2c7e09df0e23cd8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400521"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="6331b-102">\<limpar > do \<elemento de > ClaimTypeRequirements</span><span class="sxs-lookup"><span data-stu-id="6331b-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="6331b-103">Especifica que todos os tipos de declaração sejam removidos na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="6331b-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="6331b-104">Isso garante que a coleção comece vazia.</span><span class="sxs-lookup"><span data-stu-id="6331b-104">This ensures that the collection starts empty.</span></span>  
  
<span data-ttu-id="6331b-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6331b-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6331b-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6331b-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6331b-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="6331b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6331b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> wsFederationHttpBinding**](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6331b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="6331b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="6331b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6331b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6331b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="6331b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de mensagem**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6331b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="6331b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> claimTypeRequirements**](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="6331b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="6331b-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<limpar >**</span><span class="sxs-lookup"><span data-stu-id="6331b-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6331b-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6331b-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6331b-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6331b-115">Attributes and Elements</span></span>  
 <span data-ttu-id="6331b-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6331b-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6331b-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="6331b-117">Attributes</span></span>  
 <span data-ttu-id="6331b-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6331b-118">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6331b-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6331b-119">Child Elements</span></span>  
 <span data-ttu-id="6331b-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6331b-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6331b-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6331b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6331b-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="6331b-122">Element</span></span>|<span data-ttu-id="6331b-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="6331b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6331b-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="6331b-124">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="6331b-125">Especifica uma coleção de tipos de declaração necessários.</span><span class="sxs-lookup"><span data-stu-id="6331b-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="6331b-126">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="6331b-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="6331b-127">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="6331b-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="6331b-128">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="6331b-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="6331b-129">Cada elemento nessa coleção especifica os tipos de declarações obrigatórias e opcionais que devem aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="6331b-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6331b-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6331b-130">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
