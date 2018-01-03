---
title: '&lt;claimType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ae572ff3a8a2335a4259bdce2af5f6922fb0596f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="9cf22-102">&lt;claimType&gt;</span><span class="sxs-lookup"><span data-stu-id="9cf22-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="9cf22-103">Especifica uma única declaração opcional ou obrigatórias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="9cf22-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="9cf22-104">\<System. IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="9cf22-104">\<system.identityModel></span></span>  
<span data-ttu-id="9cf22-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9cf22-105">\<identityConfiguration></span></span>  
<span data-ttu-id="9cf22-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="9cf22-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="9cf22-107">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="9cf22-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cf22-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9cf22-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
      <claimType type=URI optional=xs:boolean >  
      </claimType>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9cf22-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9cf22-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9cf22-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9cf22-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9cf22-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="9cf22-111">Attributes</span></span>  
  
|<span data-ttu-id="9cf22-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="9cf22-112">Attribute</span></span>|<span data-ttu-id="9cf22-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cf22-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9cf22-114">tipo</span><span class="sxs-lookup"><span data-stu-id="9cf22-114">type</span></span>|<span data-ttu-id="9cf22-115">O tipo da declaração.</span><span class="sxs-lookup"><span data-stu-id="9cf22-115">The claim type.</span></span> <span data-ttu-id="9cf22-116">Normalmente um URI.</span><span class="sxs-lookup"><span data-stu-id="9cf22-116">Typically a URI.</span></span> <span data-ttu-id="9cf22-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9cf22-117">Required.</span></span>|  
|<span data-ttu-id="9cf22-118">optional</span><span class="sxs-lookup"><span data-stu-id="9cf22-118">optional</span></span>|<span data-ttu-id="9cf22-119">Um valor booleano que especifica se o tipo de declaração é opcional.</span><span class="sxs-lookup"><span data-stu-id="9cf22-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="9cf22-120">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9cf22-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9cf22-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9cf22-121">Child Elements</span></span>  
 <span data-ttu-id="9cf22-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9cf22-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9cf22-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9cf22-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9cf22-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="9cf22-124">Element</span></span>|<span data-ttu-id="9cf22-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cf22-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9cf22-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="9cf22-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="9cf22-127">Especifica o conjunto de declarações necessárias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="9cf22-127">Specifies the set of required claims for incoming security tokens.</span></span>|
