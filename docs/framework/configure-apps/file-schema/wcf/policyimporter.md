---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4ef5890d52c3f2af42322f023b9a2a23cb583035
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855053"
---
# \<policyImporter>
<span data-ttu-id="c3a24-101">Especifica um importador de política que controla a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="c3a24-101">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="c3a24-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3a24-102">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3a24-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c3a24-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c3a24-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c3a24-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3a24-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="c3a24-105">Attributes</span></span>  
  
|<span data-ttu-id="c3a24-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="c3a24-106">Attribute</span></span>|<span data-ttu-id="c3a24-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3a24-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="c3a24-108">O tipo deste elemento.</span><span class="sxs-lookup"><span data-stu-id="c3a24-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3a24-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c3a24-109">Child Elements</span></span>  
 <span data-ttu-id="c3a24-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c3a24-110">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c3a24-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c3a24-111">Parent Elements</span></span>  
  
|<span data-ttu-id="c3a24-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="c3a24-112">Element</span></span>|<span data-ttu-id="c3a24-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3a24-113">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="c3a24-114">Especifica todos os importadores de política que controlam a importação de declarações de política personalizada sobre associações.</span><span class="sxs-lookup"><span data-stu-id="c3a24-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3a24-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3a24-115">Remarks</span></span>  
 <span data-ttu-id="c3a24-116">Um importador de política é usado para pesquisar declarações de política personalizadas sobre recursos de associação, bem como anexar um elemento de ligação personalizado que implementa os recursos exigidos pela declaração.</span><span class="sxs-lookup"><span data-stu-id="c3a24-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a24-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="c3a24-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="c3a24-118">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="c3a24-118">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="c3a24-119">Clientes</span><span class="sxs-lookup"><span data-stu-id="c3a24-119">Clients</span></span>](../../../wcf/feature-details/clients.md)
