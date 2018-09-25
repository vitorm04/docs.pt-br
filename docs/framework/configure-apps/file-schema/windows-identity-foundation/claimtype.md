---
title: '&lt;ClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 805377565b6e835fd9ffba915a003bc56529a3b6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084209"
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="c0bc4-102">&lt;ClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="c0bc4-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="c0bc4-103">Especifica uma única declaração obrigatórias ou opcional para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="c0bc4-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="c0bc4-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="c0bc4-104">\<system.identityModel></span></span>  
<span data-ttu-id="c0bc4-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c0bc4-105">\<identityConfiguration></span></span>  
<span data-ttu-id="c0bc4-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="c0bc4-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="c0bc4-107">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="c0bc4-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0bc4-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0bc4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0bc4-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c0bc4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c0bc4-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c0bc4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0bc4-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="c0bc4-111">Attributes</span></span>  
  
|<span data-ttu-id="c0bc4-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="c0bc4-112">Attribute</span></span>|<span data-ttu-id="c0bc4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0bc4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0bc4-114">tipo</span><span class="sxs-lookup"><span data-stu-id="c0bc4-114">type</span></span>|<span data-ttu-id="c0bc4-115">O tipo da declaração.</span><span class="sxs-lookup"><span data-stu-id="c0bc4-115">The claim type.</span></span> <span data-ttu-id="c0bc4-116">Normalmente é um URI.</span><span class="sxs-lookup"><span data-stu-id="c0bc4-116">Typically a URI.</span></span> <span data-ttu-id="c0bc4-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c0bc4-117">Required.</span></span>|  
|<span data-ttu-id="c0bc4-118">optional</span><span class="sxs-lookup"><span data-stu-id="c0bc4-118">optional</span></span>|<span data-ttu-id="c0bc4-119">Um valor booliano que especifica se o tipo de declaração é opcional.</span><span class="sxs-lookup"><span data-stu-id="c0bc4-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="c0bc4-120">Opcional.</span><span class="sxs-lookup"><span data-stu-id="c0bc4-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0bc4-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c0bc4-121">Child Elements</span></span>  
 <span data-ttu-id="c0bc4-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c0bc4-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0bc4-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c0bc4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c0bc4-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="c0bc4-124">Element</span></span>|<span data-ttu-id="c0bc4-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0bc4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0bc4-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="c0bc4-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="c0bc4-127">Especifica o conjunto de declarações necessárias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="c0bc4-127">Specifies the set of required claims for incoming security tokens.</span></span>|
