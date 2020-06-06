---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: a46e9129bd27319abb4d7519444568af622170fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252066"
---
# \<claimType>
<span data-ttu-id="48da6-101">Especifica uma única declaração opcional ou necessária para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="48da6-101">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)\  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**  
  
## <a name="syntax"></a><span data-ttu-id="48da6-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48da6-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48da6-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="48da6-103">Attributes and Elements</span></span>  
 <span data-ttu-id="48da6-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="48da6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48da6-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="48da6-105">Attributes</span></span>  
  
|<span data-ttu-id="48da6-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="48da6-106">Attribute</span></span>|<span data-ttu-id="48da6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="48da6-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="48da6-108">type</span><span class="sxs-lookup"><span data-stu-id="48da6-108">type</span></span>|<span data-ttu-id="48da6-109">O tipo da declaração.</span><span class="sxs-lookup"><span data-stu-id="48da6-109">The claim type.</span></span> <span data-ttu-id="48da6-110">Normalmente um URI.</span><span class="sxs-lookup"><span data-stu-id="48da6-110">Typically a URI.</span></span> <span data-ttu-id="48da6-111">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="48da6-111">Required.</span></span>|  
|<span data-ttu-id="48da6-112">opcional</span><span class="sxs-lookup"><span data-stu-id="48da6-112">optional</span></span>|<span data-ttu-id="48da6-113">Um valor booliano que especifica se o tipo de declaração é opcional.</span><span class="sxs-lookup"><span data-stu-id="48da6-113">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="48da6-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="48da6-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48da6-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="48da6-115">Child Elements</span></span>  
 <span data-ttu-id="48da6-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="48da6-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="48da6-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="48da6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="48da6-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="48da6-118">Element</span></span>|<span data-ttu-id="48da6-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="48da6-119">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="48da6-120">Especifica o conjunto de declarações necessárias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="48da6-120">Specifies the set of required claims for incoming security tokens.</span></span>|
