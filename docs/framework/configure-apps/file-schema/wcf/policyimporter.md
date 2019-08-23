---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 273bd0d5e68a661c639b82264b440b83d8127427
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933785"
---
# <a name="policyimporter"></a><span data-ttu-id="c18b7-101">\<> policyImporter</span><span class="sxs-lookup"><span data-stu-id="c18b7-101">\<policyImporter></span></span>
<span data-ttu-id="c18b7-102">Especifica um importador de política que controla a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="c18b7-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="c18b7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c18b7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c18b7-104">\<client></span><span class="sxs-lookup"><span data-stu-id="c18b7-104">\<client></span></span>  
<span data-ttu-id="c18b7-105">\<> de metadados</span><span class="sxs-lookup"><span data-stu-id="c18b7-105">\<metadata></span></span>  
<span data-ttu-id="c18b7-106">\<> policyImporters</span><span class="sxs-lookup"><span data-stu-id="c18b7-106">\<policyImporters></span></span>  
<span data-ttu-id="c18b7-107">\<> policyImporter</span><span class="sxs-lookup"><span data-stu-id="c18b7-107">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c18b7-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c18b7-108">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c18b7-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c18b7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c18b7-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c18b7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c18b7-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="c18b7-111">Attributes</span></span>  
  
|<span data-ttu-id="c18b7-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="c18b7-112">Attribute</span></span>|<span data-ttu-id="c18b7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c18b7-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="c18b7-114">O tipo deste elemento.</span><span class="sxs-lookup"><span data-stu-id="c18b7-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c18b7-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c18b7-115">Child Elements</span></span>  
 <span data-ttu-id="c18b7-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c18b7-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c18b7-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c18b7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c18b7-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="c18b7-118">Element</span></span>|<span data-ttu-id="c18b7-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c18b7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c18b7-120">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="c18b7-120">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="c18b7-121">Especifica todos os importadores de política que controlam a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="c18b7-121">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c18b7-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="c18b7-122">Remarks</span></span>  
 <span data-ttu-id="c18b7-123">Um importador de política é usado para pesquisar declarações de política personalizadas sobre recursos de associação, bem como anexar um elemento de ligação personalizado que implementa os recursos exigidos pela declaração.</span><span class="sxs-lookup"><span data-stu-id="c18b7-123">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c18b7-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c18b7-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="c18b7-125">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="c18b7-125">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="c18b7-126">Clientes</span><span class="sxs-lookup"><span data-stu-id="c18b7-126">Clients</span></span>](../../../wcf/feature-details/clients.md)
