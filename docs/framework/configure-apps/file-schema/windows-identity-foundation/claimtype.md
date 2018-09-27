---
title: '&lt;ClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 805377565b6e835fd9ffba915a003bc56529a3b6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47234949"
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="64b97-102">&lt;ClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="64b97-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="64b97-103">Especifica uma única declaração obrigatórias ou opcional para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="64b97-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="64b97-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="64b97-104">\<system.identityModel></span></span>  
<span data-ttu-id="64b97-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="64b97-105">\<identityConfiguration></span></span>  
<span data-ttu-id="64b97-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="64b97-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="64b97-107">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="64b97-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64b97-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64b97-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64b97-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="64b97-109">Attributes and Elements</span></span>  
 <span data-ttu-id="64b97-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="64b97-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64b97-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="64b97-111">Attributes</span></span>  
  
|<span data-ttu-id="64b97-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="64b97-112">Attribute</span></span>|<span data-ttu-id="64b97-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="64b97-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="64b97-114">tipo</span><span class="sxs-lookup"><span data-stu-id="64b97-114">type</span></span>|<span data-ttu-id="64b97-115">O tipo da declaração.</span><span class="sxs-lookup"><span data-stu-id="64b97-115">The claim type.</span></span> <span data-ttu-id="64b97-116">Normalmente é um URI.</span><span class="sxs-lookup"><span data-stu-id="64b97-116">Typically a URI.</span></span> <span data-ttu-id="64b97-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="64b97-117">Required.</span></span>|  
|<span data-ttu-id="64b97-118">optional</span><span class="sxs-lookup"><span data-stu-id="64b97-118">optional</span></span>|<span data-ttu-id="64b97-119">Um valor booliano que especifica se o tipo de declaração é opcional.</span><span class="sxs-lookup"><span data-stu-id="64b97-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="64b97-120">Opcional.</span><span class="sxs-lookup"><span data-stu-id="64b97-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64b97-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="64b97-121">Child Elements</span></span>  
 <span data-ttu-id="64b97-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="64b97-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="64b97-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="64b97-123">Parent Elements</span></span>  
  
|<span data-ttu-id="64b97-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="64b97-124">Element</span></span>|<span data-ttu-id="64b97-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="64b97-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64b97-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="64b97-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="64b97-127">Especifica o conjunto de declarações necessárias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="64b97-127">Specifies the set of required claims for incoming security tokens.</span></span>|
