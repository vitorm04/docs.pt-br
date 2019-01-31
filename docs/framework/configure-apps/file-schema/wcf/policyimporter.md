---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: ab9193d5974ccffcbfa3e741ac4d32ff357ed372
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269231"
---
# <a name="policyimporter"></a><span data-ttu-id="58c11-101">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="58c11-101">\<policyImporter></span></span>
<span data-ttu-id="58c11-102">Especifica um importador de política que controla a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="58c11-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="58c11-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="58c11-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="58c11-104">\<client></span><span class="sxs-lookup"><span data-stu-id="58c11-104">\<client></span></span>  
<span data-ttu-id="58c11-105">\<metadata></span><span class="sxs-lookup"><span data-stu-id="58c11-105">\<metadata></span></span>  
<span data-ttu-id="58c11-106">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="58c11-106">\<policyImporters></span></span>  
<span data-ttu-id="58c11-107">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="58c11-107">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58c11-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58c11-108">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58c11-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="58c11-109">Attributes and Elements</span></span>  
 <span data-ttu-id="58c11-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="58c11-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58c11-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="58c11-111">Attributes</span></span>  
  
|<span data-ttu-id="58c11-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="58c11-112">Attribute</span></span>|<span data-ttu-id="58c11-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="58c11-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="58c11-114">O tipo deste elemento.</span><span class="sxs-lookup"><span data-stu-id="58c11-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58c11-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="58c11-115">Child Elements</span></span>  
 <span data-ttu-id="58c11-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="58c11-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58c11-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="58c11-117">Parent Elements</span></span>  
  
|<span data-ttu-id="58c11-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="58c11-118">Element</span></span>|<span data-ttu-id="58c11-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="58c11-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58c11-120">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="58c11-120">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="58c11-121">Especifica todos os importadores de políticas que controlam a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="58c11-121">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58c11-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="58c11-122">Remarks</span></span>  
 <span data-ttu-id="58c11-123">Um importador de política é usado para pesquisar as declarações de política personalizadas sobre recursos de associação, bem como anexar a um elemento de associação personalizado que implementa os recursos que exige que a asserção.</span><span class="sxs-lookup"><span data-stu-id="58c11-123">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58c11-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58c11-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="58c11-125">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="58c11-125">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="58c11-126">Clientes</span><span class="sxs-lookup"><span data-stu-id="58c11-126">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
