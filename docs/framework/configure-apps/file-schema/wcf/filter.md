---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855250"
---
# <a name="filter"></a><span data-ttu-id="329e1-101">\<filter></span><span class="sxs-lookup"><span data-stu-id="329e1-101">\<filter></span></span>

<span data-ttu-id="329e1-102">Define um filtro de roteamento, que determina o tipo de Windows Communication Foundation (WCF<xref:System.ServiceModel.Dispatcher.MessageFilter> ) a ser usado ao avaliar mensagens recebidas, bem como quaisquer dados de suporte ou parâmetros exigidos pelo filtro.</span><span class="sxs-lookup"><span data-stu-id="329e1-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="329e1-103">[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="329e1-103">[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="329e1-104">&nbsp;&nbsp;[ **\<routing>** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="329e1-104">&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="329e1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Filtros >** ](filters-of-routing.md)</span><span class="sxs-lookup"><span data-stu-id="329e1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)</span></span>\
<span data-ttu-id="329e1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de filtro**</span><span class="sxs-lookup"><span data-stu-id="329e1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="329e1-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="329e1-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="329e1-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="329e1-108">Attributes and elements</span></span>

<span data-ttu-id="329e1-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="329e1-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="329e1-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="329e1-110">Attributes</span></span>

| <span data-ttu-id="329e1-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="329e1-111">Attribute</span></span>  | <span data-ttu-id="329e1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="329e1-112">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="329e1-113">customType</span><span class="sxs-lookup"><span data-stu-id="329e1-113">customType</span></span> | <span data-ttu-id="329e1-114">Uma cadeia de caracteres que contém o nome do tipo totalmente qualificado do tipo personalizado a ser usado como um filtro.</span><span class="sxs-lookup"><span data-stu-id="329e1-114">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="329e1-115">Se `filterType` é definido como `custom`, esse atributo contém o nome de tipo totalmente qualificado da classe a ser criada.</span><span class="sxs-lookup"><span data-stu-id="329e1-115">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="329e1-116">`filterData`também pode conter valores a serem usados durante a avaliação do filtro de tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="329e1-116">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="329e1-117">filterData</span><span class="sxs-lookup"><span data-stu-id="329e1-117">filterData</span></span> | <span data-ttu-id="329e1-118">Uma cadeia de caracteres que contém os dados de filtro.</span><span class="sxs-lookup"><span data-stu-id="329e1-118">A string containing the filter data.</span></span> <span data-ttu-id="329e1-119">Para obter mais informações sobre como especificar esse atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="329e1-119">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="329e1-120">filterType</span><span class="sxs-lookup"><span data-stu-id="329e1-120">filterType</span></span> | <span data-ttu-id="329e1-121">Uma cadeia de caracteres que contém o tipo de filtro.</span><span class="sxs-lookup"><span data-stu-id="329e1-121">A string containing the filter type.</span></span> <span data-ttu-id="329e1-122">Esse atributo é do <xref:System.ServiceModel.Routing.Configuration.FilterType> tipo.</span><span class="sxs-lookup"><span data-stu-id="329e1-122">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="329e1-123">Para obter mais informações sobre como isso funciona com `filterData` o atributo, <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>consulte.</span><span class="sxs-lookup"><span data-stu-id="329e1-123">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="329e1-124">name</span><span class="sxs-lookup"><span data-stu-id="329e1-124">name</span></span>       | <span data-ttu-id="329e1-125">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de filtro.</span><span class="sxs-lookup"><span data-stu-id="329e1-125">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="329e1-126">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="329e1-126">Child elements</span></span>

<span data-ttu-id="329e1-127">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="329e1-127">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="329e1-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="329e1-128">Parent elements</span></span>

| <span data-ttu-id="329e1-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="329e1-129">Element</span></span> | <span data-ttu-id="329e1-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="329e1-130">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="329e1-131">\<routing></span><span class="sxs-lookup"><span data-stu-id="329e1-131">\<routing></span></span>](routing.md) | <span data-ttu-id="329e1-132">Uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) a ser usado ao avaliar mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="329e1-132">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="329e1-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="329e1-133">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
