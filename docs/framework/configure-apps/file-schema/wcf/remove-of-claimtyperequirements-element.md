---
title: <remove>do <claimTypeRequirements> elemento
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 84f4208d3f4581cf7e8c4455bf3f5d78f7e13b9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399994"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="a3fe9-102">\<remove>do \<claimTypeRequirements> elemento</span><span class="sxs-lookup"><span data-stu-id="a3fe9-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="a3fe9-103">Especifica os tipos de declarações a serem removidas na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="a3fe9-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="a3fe9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3fe9-104">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3fe9-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a3fe9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a3fe9-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a3fe9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3fe9-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a3fe9-107">Attributes</span></span>  
  
|<span data-ttu-id="a3fe9-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="a3fe9-108">Attribute</span></span>|<span data-ttu-id="a3fe9-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3fe9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3fe9-110">claimType</span><span class="sxs-lookup"><span data-stu-id="a3fe9-110">claimType</span></span>|<span data-ttu-id="a3fe9-111">Um URI que define o tipo de uma declaração a ser removida.</span><span class="sxs-lookup"><span data-stu-id="a3fe9-111">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3fe9-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a3fe9-112">Child Elements</span></span>  
 <span data-ttu-id="a3fe9-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a3fe9-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3fe9-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a3fe9-114">Parent Elements</span></span>  
  
|<span data-ttu-id="a3fe9-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="a3fe9-115">Element</span></span>|<span data-ttu-id="a3fe9-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3fe9-116">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="a3fe9-117">Especifica uma coleção de tipos de declaração necessários.</span><span class="sxs-lookup"><span data-stu-id="a3fe9-117">Specifies a collection of required claim types.</span></span> <span data-ttu-id="a3fe9-118">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="a3fe9-118">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="a3fe9-119">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="a3fe9-119">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="a3fe9-120">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="a3fe9-120">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="a3fe9-121">Cada elemento nessa coleção especifica os tipos de declarações obrigatórias e opcionais que devem aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="a3fe9-121">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3fe9-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="a3fe9-122">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
