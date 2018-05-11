---
title: '&lt;claimTypeRequired&gt;'
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6fb600aac46b3ee5cb54fa904d35ac7b7ed90719
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="12cc1-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="12cc1-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="12cc1-103">Especifica o conjunto de declarações necessárias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="12cc1-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="12cc1-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="12cc1-104">\<system.identityModel></span></span>  
<span data-ttu-id="12cc1-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="12cc1-105">\<identityConfiguration></span></span>  
<span data-ttu-id="12cc1-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="12cc1-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12cc1-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12cc1-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12cc1-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="12cc1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="12cc1-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="12cc1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12cc1-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="12cc1-110">Attributes</span></span>  
 <span data-ttu-id="12cc1-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="12cc1-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="12cc1-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="12cc1-112">Child Elements</span></span>  
  
|<span data-ttu-id="12cc1-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="12cc1-113">Element</span></span>|<span data-ttu-id="12cc1-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="12cc1-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12cc1-115">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="12cc1-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="12cc1-116">Especifica uma única declaração opcional ou obrigatórias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="12cc1-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="12cc1-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="12cc1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="12cc1-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="12cc1-118">Element</span></span>|<span data-ttu-id="12cc1-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="12cc1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12cc1-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="12cc1-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="12cc1-121">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="12cc1-121">Specifies service-level identity settings.</span></span>|
