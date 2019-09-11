---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4ef5890d52c3f2af42322f023b9a2a23cb583035
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855053"
---
# <a name="policyimporter"></a><span data-ttu-id="5b31f-101">\<> policyImporter</span><span class="sxs-lookup"><span data-stu-id="5b31f-101">\<policyImporter></span></span>
<span data-ttu-id="5b31f-102">Especifica um importador de política que controla a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="5b31f-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
<span data-ttu-id="5b31f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5b31f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5b31f-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5b31f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5b31f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do cliente**](client.md)</span><span class="sxs-lookup"><span data-stu-id="5b31f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="5b31f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de metadados**](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="5b31f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)</span></span>\
<span data-ttu-id="5b31f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> policyImporters**](policyimporters.md)</span><span class="sxs-lookup"><span data-stu-id="5b31f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)</span></span>  
<span data-ttu-id="5b31f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> policyImporter**</span><span class="sxs-lookup"><span data-stu-id="5b31f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b31f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b31f-109">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b31f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5b31f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5b31f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5b31f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b31f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5b31f-112">Attributes</span></span>  
  
|<span data-ttu-id="5b31f-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="5b31f-113">Attribute</span></span>|<span data-ttu-id="5b31f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b31f-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="5b31f-115">O tipo deste elemento.</span><span class="sxs-lookup"><span data-stu-id="5b31f-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b31f-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5b31f-116">Child Elements</span></span>  
 <span data-ttu-id="5b31f-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5b31f-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5b31f-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5b31f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5b31f-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="5b31f-119">Element</span></span>|<span data-ttu-id="5b31f-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b31f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b31f-121">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="5b31f-121">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="5b31f-122">Especifica todos os importadores de política que controlam a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="5b31f-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b31f-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="5b31f-123">Remarks</span></span>  
 <span data-ttu-id="5b31f-124">Um importador de política é usado para pesquisar declarações de política personalizadas sobre recursos de associação, bem como anexar um elemento de ligação personalizado que implementa os recursos exigidos pela declaração.</span><span class="sxs-lookup"><span data-stu-id="5b31f-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b31f-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b31f-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="5b31f-126">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="5b31f-126">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="5b31f-127">Clientes</span><span class="sxs-lookup"><span data-stu-id="5b31f-127">Clients</span></span>](../../../wcf/feature-details/clients.md)
