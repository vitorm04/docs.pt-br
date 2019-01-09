---
title: '&lt;policyImporter&gt;'
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 22d90ff9d0cd5325300cf42437836f075cbf8c31
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148481"
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="400cf-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="400cf-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="400cf-103">Especifica um importador de política que controla a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="400cf-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="400cf-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="400cf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="400cf-105">\<client></span><span class="sxs-lookup"><span data-stu-id="400cf-105">\<client></span></span>  
<span data-ttu-id="400cf-106">\<metadados ></span><span class="sxs-lookup"><span data-stu-id="400cf-106">\<metadata></span></span>  
<span data-ttu-id="400cf-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="400cf-107">\<policyImporters></span></span>  
<span data-ttu-id="400cf-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="400cf-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="400cf-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="400cf-109">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="400cf-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="400cf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="400cf-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="400cf-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="400cf-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="400cf-112">Attributes</span></span>  
  
|<span data-ttu-id="400cf-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="400cf-113">Attribute</span></span>|<span data-ttu-id="400cf-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="400cf-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="400cf-115">O tipo deste elemento.</span><span class="sxs-lookup"><span data-stu-id="400cf-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="400cf-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="400cf-116">Child Elements</span></span>  
 <span data-ttu-id="400cf-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="400cf-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="400cf-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="400cf-118">Parent Elements</span></span>  
  
|<span data-ttu-id="400cf-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="400cf-119">Element</span></span>|<span data-ttu-id="400cf-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="400cf-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="400cf-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="400cf-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="400cf-122">Especifica todos os importadores de políticas que controlam a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="400cf-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="400cf-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="400cf-123">Remarks</span></span>  
 <span data-ttu-id="400cf-124">Um importador de política é usado para pesquisar as declarações de política personalizadas sobre recursos de associação, bem como anexar a um elemento de associação personalizado que implementa os recursos que exige que a asserção.</span><span class="sxs-lookup"><span data-stu-id="400cf-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="400cf-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="400cf-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="400cf-126">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="400cf-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="400cf-127">Clientes</span><span class="sxs-lookup"><span data-stu-id="400cf-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
