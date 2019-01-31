---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: bff19f106d86c73dea80b8b57bb73442eaa2cf9f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278779"
---
# <a name="filter"></a><span data-ttu-id="e54c8-101">\<filter></span><span class="sxs-lookup"><span data-stu-id="e54c8-101">\<filter></span></span>

<span data-ttu-id="e54c8-102">Define um filtro de roteamento, que determina o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, como também quaisquer dados de apoio ou parâmetros exigidos pelo filtro.</span><span class="sxs-lookup"><span data-stu-id="e54c8-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="e54c8-103">\<system.serviceModel> \<routing> \<filters> \<filter></span><span class="sxs-lookup"><span data-stu-id="e54c8-103">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>
  
## <a name="syntax"></a><span data-ttu-id="e54c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e54c8-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e54c8-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e54c8-105">Attributes and elements</span></span>

<span data-ttu-id="e54c8-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e54c8-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e54c8-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="e54c8-107">Attributes</span></span>

| <span data-ttu-id="e54c8-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="e54c8-108">Attribute</span></span>  | <span data-ttu-id="e54c8-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e54c8-109">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="e54c8-110">customType</span><span class="sxs-lookup"><span data-stu-id="e54c8-110">customType</span></span> | <span data-ttu-id="e54c8-111">Uma cadeia de caracteres que contém o nome de tipo totalmente qualificado do tipo a ser usado como um filtro personalizado.</span><span class="sxs-lookup"><span data-stu-id="e54c8-111">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="e54c8-112">Se `filterType` é definido como `custom`, este atributo contém o nome do tipo totalmente qualificado da classe para criar.</span><span class="sxs-lookup"><span data-stu-id="e54c8-112">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="e54c8-113">`filterData` também pode conter valores a serem usados durante a avaliação do filtro de tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="e54c8-113">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="e54c8-114">filterData</span><span class="sxs-lookup"><span data-stu-id="e54c8-114">filterData</span></span> | <span data-ttu-id="e54c8-115">Uma cadeia de caracteres que contém os dados de filtro.</span><span class="sxs-lookup"><span data-stu-id="e54c8-115">A string containing the filter data.</span></span> <span data-ttu-id="e54c8-116">Para obter mais informações sobre como especificar esse atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="e54c8-116">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="e54c8-117">filterType</span><span class="sxs-lookup"><span data-stu-id="e54c8-117">filterType</span></span> | <span data-ttu-id="e54c8-118">Uma cadeia de caracteres que contém o tipo de filtro.</span><span class="sxs-lookup"><span data-stu-id="e54c8-118">A string containing the filter type.</span></span> <span data-ttu-id="e54c8-119">Esse atributo é do <xref:System.ServiceModel.Routing.Configuration.FilterType> tipo.</span><span class="sxs-lookup"><span data-stu-id="e54c8-119">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="e54c8-120">Para obter mais informações sobre como isso funciona com o `filterData` atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="e54c8-120">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="e54c8-121">name</span><span class="sxs-lookup"><span data-stu-id="e54c8-121">name</span></span>       | <span data-ttu-id="e54c8-122">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de filtro.</span><span class="sxs-lookup"><span data-stu-id="e54c8-122">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="e54c8-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e54c8-123">Child elements</span></span>

<span data-ttu-id="e54c8-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e54c8-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e54c8-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e54c8-125">Parent elements</span></span>

| <span data-ttu-id="e54c8-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="e54c8-126">Element</span></span> | <span data-ttu-id="e54c8-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="e54c8-127">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="e54c8-128">\<routing></span><span class="sxs-lookup"><span data-stu-id="e54c8-128">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="e54c8-129">Uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="e54c8-129">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="e54c8-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e54c8-130">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
