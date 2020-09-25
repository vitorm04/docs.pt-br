---
title: <clear> do <claimTypeRequirements> elemento
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: aa94a012da11bcec6fb5fe270ad9f3574f88e6d7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172899"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="01c44-102">\<clear> do \<claimTypeRequirements> elemento</span><span class="sxs-lookup"><span data-stu-id="01c44-102">\<clear> of \<claimTypeRequirements> element</span></span>

<span data-ttu-id="01c44-103">Especifica que todos os tipos de declaração sejam removidos na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="01c44-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="01c44-104">Isso garante que a coleção comece vazia.</span><span class="sxs-lookup"><span data-stu-id="01c44-104">This ensures that the collection starts empty.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="01c44-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01c44-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01c44-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="01c44-106">Attributes and Elements</span></span>  

 <span data-ttu-id="01c44-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="01c44-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01c44-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="01c44-108">Attributes</span></span>  

 <span data-ttu-id="01c44-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="01c44-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="01c44-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="01c44-110">Child Elements</span></span>  

 <span data-ttu-id="01c44-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="01c44-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01c44-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="01c44-112">Parent Elements</span></span>  
  
|<span data-ttu-id="01c44-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="01c44-113">Element</span></span>|<span data-ttu-id="01c44-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="01c44-114">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="01c44-115">Especifica uma coleção de tipos de declaração necessários.</span><span class="sxs-lookup"><span data-stu-id="01c44-115">Specifies a collection of required claim types.</span></span> <span data-ttu-id="01c44-116">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="01c44-116">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="01c44-117">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="01c44-117">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="01c44-118">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="01c44-118">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="01c44-119">Cada elemento nessa coleção especifica os tipos de declarações obrigatórias e opcionais que devem aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="01c44-119">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01c44-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="01c44-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
