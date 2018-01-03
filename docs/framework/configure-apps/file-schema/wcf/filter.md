---
title: '&lt;filtro&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 186c511cd8a69cef5e30e369641628a10a0972d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltergt"></a><span data-ttu-id="ac771-102">&lt;filtro&gt;</span><span class="sxs-lookup"><span data-stu-id="ac771-102">&lt;filter&gt;</span></span>

<span data-ttu-id="ac771-103">Define um filtro de roteamento, que determina o tipo de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, como também quaisquer dados de apoio ou parâmetros exigidos pelo filtro.</span><span class="sxs-lookup"><span data-stu-id="ac771-103">Defines a routing filter, which determines the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="ac771-104">\<System. ServiceModel > \<roteamento > \<filtros > \<filtro ></span><span class="sxs-lookup"><span data-stu-id="ac771-104">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>

## <a name="syntax"></a><span data-ttu-id="ac771-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac771-105">Syntax</span></span>

```xml
<routing>
  <filters>
    <filter customType="String" 
            filterData="String" 
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
            name="String" />
  </filters>
</routing>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ac771-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ac771-106">Attributes and elements</span></span>

<span data-ttu-id="ac771-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ac771-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ac771-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="ac771-108">Attributes</span></span>

| <span data-ttu-id="ac771-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="ac771-109">Attribute</span></span>  | <span data-ttu-id="ac771-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac771-110">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="ac771-111">customType</span><span class="sxs-lookup"><span data-stu-id="ac771-111">customType</span></span> | <span data-ttu-id="ac771-112">Uma cadeia de caracteres que contém o nome de tipo totalmente qualificado do tipo personalizado a ser usado como um filtro.</span><span class="sxs-lookup"><span data-stu-id="ac771-112">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="ac771-113">Se `filterType` é definido como `custom`, este atributo contém o nome de tipo totalmente qualificado da classe para criar.</span><span class="sxs-lookup"><span data-stu-id="ac771-113">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="ac771-114">`filterData`também pode conter valores a serem usados durante a avaliação do filtro de tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="ac771-114">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="ac771-115">filterData</span><span class="sxs-lookup"><span data-stu-id="ac771-115">filterData</span></span> | <span data-ttu-id="ac771-116">Uma cadeia de caracteres que contém os dados de filtro.</span><span class="sxs-lookup"><span data-stu-id="ac771-116">A string containing the filter data.</span></span> <span data-ttu-id="ac771-117">Para obter mais informações sobre como especificar esse atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="ac771-117">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="ac771-118">filterType</span><span class="sxs-lookup"><span data-stu-id="ac771-118">filterType</span></span> | <span data-ttu-id="ac771-119">Uma cadeia de caracteres que contém o tipo de filtro.</span><span class="sxs-lookup"><span data-stu-id="ac771-119">A string containing the filter type.</span></span> <span data-ttu-id="ac771-120">Esse atributo é de <xref:System.ServiceModel.Routing.Configuration.FilterType> tipo.</span><span class="sxs-lookup"><span data-stu-id="ac771-120">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="ac771-121">Para obter mais informações sobre como isso funciona com o `filterData` de atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="ac771-121">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="ac771-122">name</span><span class="sxs-lookup"><span data-stu-id="ac771-122">name</span></span>       | <span data-ttu-id="ac771-123">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de filtro.</span><span class="sxs-lookup"><span data-stu-id="ac771-123">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="ac771-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ac771-124">Child elements</span></span>

<span data-ttu-id="ac771-125">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ac771-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ac771-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ac771-126">Parent elements</span></span>

| <span data-ttu-id="ac771-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="ac771-127">Element</span></span> | <span data-ttu-id="ac771-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac771-128">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="ac771-129">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="ac771-129">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="ac771-130">Uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="ac771-130">A configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="ac771-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac771-131">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
