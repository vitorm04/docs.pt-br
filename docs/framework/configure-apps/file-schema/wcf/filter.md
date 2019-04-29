---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: bff19f106d86c73dea80b8b57bb73442eaa2cf9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704031"
---
# <a name="filter"></a><span data-ttu-id="f906b-101">\<filter></span><span class="sxs-lookup"><span data-stu-id="f906b-101">\<filter></span></span>

<span data-ttu-id="f906b-102">Define um filtro de roteamento, que determina o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, como também quaisquer dados de apoio ou parâmetros exigidos pelo filtro.</span><span class="sxs-lookup"><span data-stu-id="f906b-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="f906b-103">\<system.serviceModel> \<routing> \<filters> \<filter></span><span class="sxs-lookup"><span data-stu-id="f906b-103">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>
  
## <a name="syntax"></a><span data-ttu-id="f906b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f906b-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f906b-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f906b-105">Attributes and elements</span></span>

<span data-ttu-id="f906b-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f906b-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f906b-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="f906b-107">Attributes</span></span>

| <span data-ttu-id="f906b-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="f906b-108">Attribute</span></span>  | <span data-ttu-id="f906b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f906b-109">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="f906b-110">customType</span><span class="sxs-lookup"><span data-stu-id="f906b-110">customType</span></span> | <span data-ttu-id="f906b-111">Uma cadeia de caracteres que contém o nome de tipo totalmente qualificado do tipo a ser usado como um filtro personalizado.</span><span class="sxs-lookup"><span data-stu-id="f906b-111">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="f906b-112">Se `filterType` é definido como `custom`, este atributo contém o nome do tipo totalmente qualificado da classe para criar.</span><span class="sxs-lookup"><span data-stu-id="f906b-112">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="f906b-113">`filterData` também pode conter valores a serem usados durante a avaliação do filtro de tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="f906b-113">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="f906b-114">filterData</span><span class="sxs-lookup"><span data-stu-id="f906b-114">filterData</span></span> | <span data-ttu-id="f906b-115">Uma cadeia de caracteres que contém os dados de filtro.</span><span class="sxs-lookup"><span data-stu-id="f906b-115">A string containing the filter data.</span></span> <span data-ttu-id="f906b-116">Para obter mais informações sobre como especificar esse atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="f906b-116">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="f906b-117">filterType</span><span class="sxs-lookup"><span data-stu-id="f906b-117">filterType</span></span> | <span data-ttu-id="f906b-118">Uma cadeia de caracteres que contém o tipo de filtro.</span><span class="sxs-lookup"><span data-stu-id="f906b-118">A string containing the filter type.</span></span> <span data-ttu-id="f906b-119">Esse atributo é do <xref:System.ServiceModel.Routing.Configuration.FilterType> tipo.</span><span class="sxs-lookup"><span data-stu-id="f906b-119">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="f906b-120">Para obter mais informações sobre como isso funciona com o `filterData` atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="f906b-120">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="f906b-121">name</span><span class="sxs-lookup"><span data-stu-id="f906b-121">name</span></span>       | <span data-ttu-id="f906b-122">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de filtro.</span><span class="sxs-lookup"><span data-stu-id="f906b-122">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="f906b-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f906b-123">Child elements</span></span>

<span data-ttu-id="f906b-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f906b-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f906b-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f906b-125">Parent elements</span></span>

| <span data-ttu-id="f906b-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="f906b-126">Element</span></span> | <span data-ttu-id="f906b-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="f906b-127">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="f906b-128">\<routing></span><span class="sxs-lookup"><span data-stu-id="f906b-128">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="f906b-129">Uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="f906b-129">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f906b-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f906b-130">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
