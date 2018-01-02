---
title: '&lt;policyImporter&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2226b4f55025c9dec3fdeb4f9b4f51016ffd3e8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="570d2-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="570d2-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="570d2-103">Especifica um importador de política que controla a importação de declarações de políticas personalizadas sobre associações.</span><span class="sxs-lookup"><span data-stu-id="570d2-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="570d2-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="570d2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="570d2-105">\<cliente ></span><span class="sxs-lookup"><span data-stu-id="570d2-105">\<client></span></span>  
<span data-ttu-id="570d2-106">\<metadados ></span><span class="sxs-lookup"><span data-stu-id="570d2-106">\<metadata></span></span>  
<span data-ttu-id="570d2-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="570d2-107">\<policyImporters></span></span>  
<span data-ttu-id="570d2-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="570d2-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="570d2-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="570d2-109">Syntax</span></span>  
  
```xml  
<metadata>  
   <policyImporters>  
      <policyImporter type="string" />  
   </policyImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="570d2-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="570d2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="570d2-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="570d2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="570d2-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="570d2-112">Attributes</span></span>  
  
|<span data-ttu-id="570d2-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="570d2-113">Attribute</span></span>|<span data-ttu-id="570d2-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="570d2-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="570d2-115">O tipo de elemento.</span><span class="sxs-lookup"><span data-stu-id="570d2-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="570d2-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="570d2-116">Child Elements</span></span>  
 <span data-ttu-id="570d2-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="570d2-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="570d2-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="570d2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="570d2-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="570d2-119">Element</span></span>|<span data-ttu-id="570d2-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="570d2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="570d2-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="570d2-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="570d2-122">Especifica todos os importadores de políticas que controlam a importação de declarações de políticas personalizadas sobre associações.</span><span class="sxs-lookup"><span data-stu-id="570d2-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="570d2-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="570d2-123">Remarks</span></span>  
 <span data-ttu-id="570d2-124">Um importador de política é usado para declarações de políticas personalizadas sobre associação de recursos de pesquisa, bem como anexar um elemento de associação personalizada que implementa os recursos que requer a asserção.</span><span class="sxs-lookup"><span data-stu-id="570d2-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="570d2-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="570d2-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="570d2-126">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="570d2-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="570d2-127">Clientes</span><span class="sxs-lookup"><span data-stu-id="570d2-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
