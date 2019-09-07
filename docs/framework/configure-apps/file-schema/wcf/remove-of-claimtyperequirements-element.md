---
title: <remove>do <claimTypeRequirements> elemento
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 84f4208d3f4581cf7e8c4455bf3f5d78f7e13b9f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399994"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="8630c-102">\<Remover > do \<elemento de > ClaimTypeRequirements</span><span class="sxs-lookup"><span data-stu-id="8630c-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="8630c-103">Especifica os tipos de declarações a serem removidas na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="8630c-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
<span data-ttu-id="8630c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8630c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8630c-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8630c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8630c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="8630c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="8630c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> wsFederationHttpBinding**](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="8630c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="8630c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="8630c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="8630c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="8630c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="8630c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de mensagem**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="8630c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="8630c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> claimTypeRequirements**](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="8630c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="8630c-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Remover >**</span><span class="sxs-lookup"><span data-stu-id="8630c-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8630c-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8630c-113">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8630c-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8630c-114">Attributes and Elements</span></span>  
 <span data-ttu-id="8630c-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8630c-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8630c-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="8630c-116">Attributes</span></span>  
  
|<span data-ttu-id="8630c-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="8630c-117">Attribute</span></span>|<span data-ttu-id="8630c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="8630c-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8630c-119">claimType</span><span class="sxs-lookup"><span data-stu-id="8630c-119">claimType</span></span>|<span data-ttu-id="8630c-120">Um URI que define o tipo de uma declaração a ser removida.</span><span class="sxs-lookup"><span data-stu-id="8630c-120">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8630c-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8630c-121">Child Elements</span></span>  
 <span data-ttu-id="8630c-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8630c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8630c-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8630c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8630c-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="8630c-124">Element</span></span>|<span data-ttu-id="8630c-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="8630c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8630c-126">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="8630c-126">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="8630c-127">Especifica uma coleção de tipos de declaração necessários.</span><span class="sxs-lookup"><span data-stu-id="8630c-127">Specifies a collection of required claim types.</span></span> <span data-ttu-id="8630c-128">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="8630c-128">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="8630c-129">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="8630c-129">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="8630c-130">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="8630c-130">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="8630c-131">Cada elemento nessa coleção especifica os tipos de declarações obrigatórias e opcionais que devem aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="8630c-131">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8630c-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8630c-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
