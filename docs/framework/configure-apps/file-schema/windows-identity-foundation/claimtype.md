---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 1b5427210142c70c31c5f736c9b5e281dca53f33
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150863"
---
# \<claimType>

<span data-ttu-id="81c03-101">Especifica uma única declaração opcional ou necessária para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="81c03-101">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)\  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**  
  
## <a name="syntax"></a><span data-ttu-id="81c03-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="81c03-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81c03-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="81c03-103">Attributes and Elements</span></span>  

 <span data-ttu-id="81c03-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="81c03-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81c03-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="81c03-105">Attributes</span></span>  
  
|<span data-ttu-id="81c03-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="81c03-106">Attribute</span></span>|<span data-ttu-id="81c03-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="81c03-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81c03-108">type</span><span class="sxs-lookup"><span data-stu-id="81c03-108">type</span></span>|<span data-ttu-id="81c03-109">O tipo da declaração.</span><span class="sxs-lookup"><span data-stu-id="81c03-109">The claim type.</span></span> <span data-ttu-id="81c03-110">Normalmente um URI.</span><span class="sxs-lookup"><span data-stu-id="81c03-110">Typically a URI.</span></span> <span data-ttu-id="81c03-111">Necessário.</span><span class="sxs-lookup"><span data-stu-id="81c03-111">Required.</span></span>|  
|<span data-ttu-id="81c03-112">opcional</span><span class="sxs-lookup"><span data-stu-id="81c03-112">optional</span></span>|<span data-ttu-id="81c03-113">Um valor booliano que especifica se o tipo de declaração é opcional.</span><span class="sxs-lookup"><span data-stu-id="81c03-113">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="81c03-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="81c03-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81c03-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="81c03-115">Child Elements</span></span>  

 <span data-ttu-id="81c03-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="81c03-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81c03-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="81c03-117">Parent Elements</span></span>  
  
|<span data-ttu-id="81c03-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="81c03-118">Element</span></span>|<span data-ttu-id="81c03-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="81c03-119">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="81c03-120">Especifica o conjunto de declarações necessárias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="81c03-120">Specifies the set of required claims for incoming security tokens.</span></span>|
