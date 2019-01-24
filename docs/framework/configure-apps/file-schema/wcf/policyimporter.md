---
title: '&lt;policyImporter&gt;'
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4075f7fcb1c65da3d9e2e5e5dab52452ca2c9b60
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632160"
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="9da85-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="9da85-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="9da85-103">Especifica um importador de política que controla a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="9da85-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="9da85-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9da85-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9da85-105">\<client></span><span class="sxs-lookup"><span data-stu-id="9da85-105">\<client></span></span>  
<span data-ttu-id="9da85-106">\<metadata></span><span class="sxs-lookup"><span data-stu-id="9da85-106">\<metadata></span></span>  
<span data-ttu-id="9da85-107">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="9da85-107">\<policyImporters></span></span>  
<span data-ttu-id="9da85-108">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="9da85-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9da85-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9da85-109">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9da85-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9da85-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9da85-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9da85-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9da85-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="9da85-112">Attributes</span></span>  
  
|<span data-ttu-id="9da85-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="9da85-113">Attribute</span></span>|<span data-ttu-id="9da85-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9da85-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="9da85-115">O tipo deste elemento.</span><span class="sxs-lookup"><span data-stu-id="9da85-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9da85-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9da85-116">Child Elements</span></span>  
 <span data-ttu-id="9da85-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9da85-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9da85-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9da85-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9da85-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="9da85-119">Element</span></span>|<span data-ttu-id="9da85-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="9da85-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9da85-121">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="9da85-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="9da85-122">Especifica todos os importadores de políticas que controlam a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="9da85-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9da85-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="9da85-123">Remarks</span></span>  
 <span data-ttu-id="9da85-124">Um importador de política é usado para pesquisar as declarações de política personalizadas sobre recursos de associação, bem como anexar a um elemento de associação personalizado que implementa os recursos que exige que a asserção.</span><span class="sxs-lookup"><span data-stu-id="9da85-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da85-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9da85-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="9da85-126">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="9da85-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="9da85-127">Clientes</span><span class="sxs-lookup"><span data-stu-id="9da85-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
