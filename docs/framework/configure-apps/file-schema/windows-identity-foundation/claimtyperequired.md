---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: 1c40c5e4b4a24a3c1bbd6e096f12b7b044331c88
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252057"
---
# <a name="claimtyperequired"></a><span data-ttu-id="ecceb-101">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="ecceb-101">\<claimTypeRequired></span></span>
<span data-ttu-id="ecceb-102">Especifica o conjunto de declarações necessárias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="ecceb-102">Specifies the set of required claims for incoming security tokens.</span></span>  
  
<span data-ttu-id="ecceb-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ecceb-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ecceb-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="ecceb-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="ecceb-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="ecceb-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="ecceb-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> claimTypeRequired**</span><span class="sxs-lookup"><span data-stu-id="ecceb-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecceb-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ecceb-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecceb-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ecceb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ecceb-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ecceb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecceb-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ecceb-110">Attributes</span></span>  
 <span data-ttu-id="ecceb-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ecceb-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ecceb-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ecceb-112">Child Elements</span></span>  
  
|<span data-ttu-id="ecceb-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="ecceb-113">Element</span></span>|<span data-ttu-id="ecceb-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ecceb-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecceb-115">\<claimType></span><span class="sxs-lookup"><span data-stu-id="ecceb-115">\<claimType></span></span>](claimtype.md)|<span data-ttu-id="ecceb-116">Especifica uma única declaração opcional ou necessária para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="ecceb-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ecceb-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ecceb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ecceb-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="ecceb-118">Element</span></span>|<span data-ttu-id="ecceb-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ecceb-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecceb-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ecceb-120">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="ecceb-121">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="ecceb-121">Specifies service-level identity settings.</span></span>|
