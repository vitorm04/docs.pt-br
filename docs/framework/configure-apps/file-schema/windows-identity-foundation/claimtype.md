---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: a46e9129bd27319abb4d7519444568af622170fc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252066"
---
# <a name="claimtype"></a><span data-ttu-id="15c11-101">\<> de ClaimType</span><span class="sxs-lookup"><span data-stu-id="15c11-101">\<claimType></span></span>
<span data-ttu-id="15c11-102">Especifica uma única declaração opcional ou necessária para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="15c11-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
<span data-ttu-id="15c11-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="15c11-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="15c11-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="15c11-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="15c11-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="15c11-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="15c11-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> claimTypeRequired**](claimtyperequired.md)</span><span class="sxs-lookup"><span data-stu-id="15c11-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)</span></span>\  
<span data-ttu-id="15c11-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de ClaimType**</span><span class="sxs-lookup"><span data-stu-id="15c11-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15c11-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15c11-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15c11-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="15c11-109">Attributes and Elements</span></span>  
 <span data-ttu-id="15c11-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="15c11-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15c11-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="15c11-111">Attributes</span></span>  
  
|<span data-ttu-id="15c11-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="15c11-112">Attribute</span></span>|<span data-ttu-id="15c11-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="15c11-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="15c11-114">tipo</span><span class="sxs-lookup"><span data-stu-id="15c11-114">type</span></span>|<span data-ttu-id="15c11-115">O tipo da declaração.</span><span class="sxs-lookup"><span data-stu-id="15c11-115">The claim type.</span></span> <span data-ttu-id="15c11-116">Normalmente um URI.</span><span class="sxs-lookup"><span data-stu-id="15c11-116">Typically a URI.</span></span> <span data-ttu-id="15c11-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="15c11-117">Required.</span></span>|  
|<span data-ttu-id="15c11-118">optional</span><span class="sxs-lookup"><span data-stu-id="15c11-118">optional</span></span>|<span data-ttu-id="15c11-119">Um valor booliano que especifica se o tipo de declaração é opcional.</span><span class="sxs-lookup"><span data-stu-id="15c11-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="15c11-120">Opcional.</span><span class="sxs-lookup"><span data-stu-id="15c11-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15c11-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="15c11-121">Child Elements</span></span>  
 <span data-ttu-id="15c11-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="15c11-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15c11-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="15c11-123">Parent Elements</span></span>  
  
|<span data-ttu-id="15c11-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="15c11-124">Element</span></span>|<span data-ttu-id="15c11-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="15c11-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15c11-126">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="15c11-126">\<claimTypeRequired></span></span>](claimtyperequired.md)|<span data-ttu-id="15c11-127">Especifica o conjunto de declarações necessárias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="15c11-127">Specifies the set of required claims for incoming security tokens.</span></span>|
