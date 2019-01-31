---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: eafaf253e27db632f17acfce4445a07d18b109aa
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277441"
---
# <a name="claimtyperequired"></a><span data-ttu-id="ff243-101">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="ff243-101">\<claimTypeRequired></span></span>
<span data-ttu-id="ff243-102">Especifica o conjunto de declarações necessárias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="ff243-102">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="ff243-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="ff243-103">\<system.identityModel></span></span>  
<span data-ttu-id="ff243-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ff243-104">\<identityConfiguration></span></span>  
<span data-ttu-id="ff243-105">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="ff243-105">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff243-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff243-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff243-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ff243-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ff243-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ff243-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff243-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ff243-109">Attributes</span></span>  
 <span data-ttu-id="ff243-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ff243-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ff243-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ff243-111">Child Elements</span></span>  
  
|<span data-ttu-id="ff243-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="ff243-112">Element</span></span>|<span data-ttu-id="ff243-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff243-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff243-114">\<claimType></span><span class="sxs-lookup"><span data-stu-id="ff243-114">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="ff243-115">Especifica uma única declaração obrigatórias ou opcional para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="ff243-115">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff243-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ff243-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ff243-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="ff243-117">Element</span></span>|<span data-ttu-id="ff243-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff243-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff243-119">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ff243-119">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="ff243-120">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="ff243-120">Specifies service-level identity settings.</span></span>|
