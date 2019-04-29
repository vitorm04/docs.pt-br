---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 6bc185572528d4229ee53f1421eaa5bf27b053e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667217"
---
# <a name="claimtype"></a><span data-ttu-id="2c6b0-101">\<claimType></span><span class="sxs-lookup"><span data-stu-id="2c6b0-101">\<claimType></span></span>
<span data-ttu-id="2c6b0-102">Especifica uma única declaração obrigatórias ou opcional para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="2c6b0-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="2c6b0-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="2c6b0-103">\<system.identityModel></span></span>  
<span data-ttu-id="2c6b0-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="2c6b0-104">\<identityConfiguration></span></span>  
<span data-ttu-id="2c6b0-105">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="2c6b0-105">\<claimTypeRequired></span></span>  
<span data-ttu-id="2c6b0-106">\<claimType></span><span class="sxs-lookup"><span data-stu-id="2c6b0-106">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c6b0-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c6b0-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c6b0-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2c6b0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2c6b0-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2c6b0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c6b0-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="2c6b0-110">Attributes</span></span>  
  
|<span data-ttu-id="2c6b0-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="2c6b0-111">Attribute</span></span>|<span data-ttu-id="2c6b0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c6b0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2c6b0-113">tipo</span><span class="sxs-lookup"><span data-stu-id="2c6b0-113">type</span></span>|<span data-ttu-id="2c6b0-114">O tipo da declaração.</span><span class="sxs-lookup"><span data-stu-id="2c6b0-114">The claim type.</span></span> <span data-ttu-id="2c6b0-115">Normalmente é um URI.</span><span class="sxs-lookup"><span data-stu-id="2c6b0-115">Typically a URI.</span></span> <span data-ttu-id="2c6b0-116">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2c6b0-116">Required.</span></span>|  
|<span data-ttu-id="2c6b0-117">optional</span><span class="sxs-lookup"><span data-stu-id="2c6b0-117">optional</span></span>|<span data-ttu-id="2c6b0-118">Um valor booliano que especifica se o tipo de declaração é opcional.</span><span class="sxs-lookup"><span data-stu-id="2c6b0-118">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="2c6b0-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="2c6b0-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c6b0-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2c6b0-120">Child Elements</span></span>  
 <span data-ttu-id="2c6b0-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2c6b0-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c6b0-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2c6b0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2c6b0-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="2c6b0-123">Element</span></span>|<span data-ttu-id="2c6b0-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c6b0-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c6b0-125">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="2c6b0-125">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="2c6b0-126">Especifica o conjunto de declarações necessárias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="2c6b0-126">Specifies the set of required claims for incoming security tokens.</span></span>|
