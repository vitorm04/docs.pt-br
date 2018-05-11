---
title: '&lt;claimType&gt;'
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 94f8586a9ca63b8c1f1128cdda4a74ccfe0f5416
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="5d619-102">&lt;claimType&gt;</span><span class="sxs-lookup"><span data-stu-id="5d619-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="5d619-103">Especifica uma única declaração opcional ou obrigatórias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="5d619-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="5d619-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="5d619-104">\<system.identityModel></span></span>  
<span data-ttu-id="5d619-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="5d619-105">\<identityConfiguration></span></span>  
<span data-ttu-id="5d619-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="5d619-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="5d619-107">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="5d619-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d619-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d619-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d619-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5d619-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5d619-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5d619-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d619-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="5d619-111">Attributes</span></span>  
  
|<span data-ttu-id="5d619-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="5d619-112">Attribute</span></span>|<span data-ttu-id="5d619-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d619-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5d619-114">tipo</span><span class="sxs-lookup"><span data-stu-id="5d619-114">type</span></span>|<span data-ttu-id="5d619-115">O tipo da declaração.</span><span class="sxs-lookup"><span data-stu-id="5d619-115">The claim type.</span></span> <span data-ttu-id="5d619-116">Normalmente um URI.</span><span class="sxs-lookup"><span data-stu-id="5d619-116">Typically a URI.</span></span> <span data-ttu-id="5d619-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5d619-117">Required.</span></span>|  
|<span data-ttu-id="5d619-118">optional</span><span class="sxs-lookup"><span data-stu-id="5d619-118">optional</span></span>|<span data-ttu-id="5d619-119">Um valor booleano que especifica se o tipo de declaração é opcional.</span><span class="sxs-lookup"><span data-stu-id="5d619-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="5d619-120">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5d619-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d619-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5d619-121">Child Elements</span></span>  
 <span data-ttu-id="5d619-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5d619-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d619-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5d619-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5d619-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="5d619-124">Element</span></span>|<span data-ttu-id="5d619-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d619-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d619-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="5d619-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="5d619-127">Especifica o conjunto de declarações necessárias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="5d619-127">Specifies the set of required claims for incoming security tokens.</span></span>|
