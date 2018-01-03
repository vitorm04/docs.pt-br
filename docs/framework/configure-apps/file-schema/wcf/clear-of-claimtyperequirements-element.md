---
title: '&lt;limpar&gt; elemento &lt;claimTypeRequirements&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71cc4516362691484408ae2f81dfee462bd560d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="dc204-102">&lt;limpar&gt; elemento &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="dc204-102">&lt;clear&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="dc204-103">Especifica que todas as declarações de tipos a serem removidos na credencial federada.</span><span class="sxs-lookup"><span data-stu-id="dc204-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="dc204-104">Isso garante que a coleção começa vazia.</span><span class="sxs-lookup"><span data-stu-id="dc204-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="dc204-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="dc204-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="dc204-106">\<associações ></span><span class="sxs-lookup"><span data-stu-id="dc204-106">\<bindings></span></span>  
<span data-ttu-id="dc204-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="dc204-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="dc204-108">\<associação ></span><span class="sxs-lookup"><span data-stu-id="dc204-108">\<binding></span></span>  
<span data-ttu-id="dc204-109">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="dc204-109">\<security></span></span>  
<span data-ttu-id="dc204-110">\<mensagem ></span><span class="sxs-lookup"><span data-stu-id="dc204-110">\<message></span></span>  
<span data-ttu-id="dc204-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="dc204-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc204-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc204-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <clear />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc204-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dc204-113">Attributes and Elements</span></span>  
 <span data-ttu-id="dc204-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dc204-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc204-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="dc204-115">Attributes</span></span>  
 <span data-ttu-id="dc204-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="dc204-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dc204-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dc204-117">Child Elements</span></span>  
 <span data-ttu-id="dc204-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="dc204-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc204-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dc204-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dc204-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="dc204-120">Element</span></span>|<span data-ttu-id="dc204-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc204-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc204-122">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="dc204-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="dc204-123">Especifica uma coleção de tipos de declaração necessária.</span><span class="sxs-lookup"><span data-stu-id="dc204-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="dc204-124">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="dc204-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="dc204-125">Em um cenário federado, serviços de estado os requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="dc204-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="dc204-126">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="dc204-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="dc204-127">Cada elemento na coleção Especifica os tipos de declarações obrigatórias e opcionais que deve aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="dc204-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc204-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc204-128">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
