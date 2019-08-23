---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 4253aec961b812b6893ee201861d2ab38048032a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942876"
---
# <a name="claimtype"></a><span data-ttu-id="68d06-101">\<> de ClaimType</span><span class="sxs-lookup"><span data-stu-id="68d06-101">\<claimType></span></span>
<span data-ttu-id="68d06-102">Especifica uma única declaração opcional ou necessária para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="68d06-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="68d06-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="68d06-103">\<system.identityModel></span></span>  
<span data-ttu-id="68d06-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="68d06-104">\<identityConfiguration></span></span>  
<span data-ttu-id="68d06-105">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="68d06-105">\<claimTypeRequired></span></span>  
<span data-ttu-id="68d06-106">\<> de ClaimType</span><span class="sxs-lookup"><span data-stu-id="68d06-106">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68d06-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68d06-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68d06-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="68d06-108">Attributes and Elements</span></span>  
 <span data-ttu-id="68d06-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="68d06-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68d06-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="68d06-110">Attributes</span></span>  
  
|<span data-ttu-id="68d06-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="68d06-111">Attribute</span></span>|<span data-ttu-id="68d06-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="68d06-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68d06-113">tipo</span><span class="sxs-lookup"><span data-stu-id="68d06-113">type</span></span>|<span data-ttu-id="68d06-114">O tipo da declaração.</span><span class="sxs-lookup"><span data-stu-id="68d06-114">The claim type.</span></span> <span data-ttu-id="68d06-115">Normalmente um URI.</span><span class="sxs-lookup"><span data-stu-id="68d06-115">Typically a URI.</span></span> <span data-ttu-id="68d06-116">Necessário.</span><span class="sxs-lookup"><span data-stu-id="68d06-116">Required.</span></span>|  
|<span data-ttu-id="68d06-117">optional</span><span class="sxs-lookup"><span data-stu-id="68d06-117">optional</span></span>|<span data-ttu-id="68d06-118">Um valor booliano que especifica se o tipo de declaração é opcional.</span><span class="sxs-lookup"><span data-stu-id="68d06-118">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="68d06-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="68d06-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68d06-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="68d06-120">Child Elements</span></span>  
 <span data-ttu-id="68d06-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="68d06-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="68d06-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="68d06-122">Parent Elements</span></span>  
  
|<span data-ttu-id="68d06-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="68d06-123">Element</span></span>|<span data-ttu-id="68d06-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="68d06-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68d06-125">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="68d06-125">\<claimTypeRequired></span></span>](claimtyperequired.md)|<span data-ttu-id="68d06-126">Especifica o conjunto de declarações necessárias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="68d06-126">Specifies the set of required claims for incoming security tokens.</span></span>|
