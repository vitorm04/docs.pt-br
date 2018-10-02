---
title: '&lt;claimTypeRequired&gt;'
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: df4494de6b76943849db2bedef8f43ad894b6bd1
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48031858"
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="9ea60-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="9ea60-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="9ea60-103">Especifica o conjunto de declarações necessárias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="9ea60-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="9ea60-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="9ea60-104">\<system.identityModel></span></span>  
<span data-ttu-id="9ea60-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="9ea60-105">\<identityConfiguration></span></span>  
<span data-ttu-id="9ea60-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="9ea60-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ea60-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ea60-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ea60-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9ea60-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9ea60-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9ea60-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ea60-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9ea60-110">Attributes</span></span>  
 <span data-ttu-id="9ea60-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9ea60-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9ea60-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9ea60-112">Child Elements</span></span>  
  
|<span data-ttu-id="9ea60-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="9ea60-113">Element</span></span>|<span data-ttu-id="9ea60-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ea60-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ea60-115">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="9ea60-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="9ea60-116">Especifica uma única declaração obrigatórias ou opcional para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="9ea60-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9ea60-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9ea60-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9ea60-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="9ea60-118">Element</span></span>|<span data-ttu-id="9ea60-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ea60-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ea60-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9ea60-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="9ea60-121">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="9ea60-121">Specifies service-level identity settings.</span></span>|
