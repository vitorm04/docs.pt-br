---
title: '&lt;filtro&gt;'
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: f7224eab9f3c21bce9839298b50c52e9da08b6f7
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146401"
---
# <a name="ltfiltergt"></a><span data-ttu-id="cdf7d-102">&lt;filtro&gt;</span><span class="sxs-lookup"><span data-stu-id="cdf7d-102">&lt;filter&gt;</span></span>

<span data-ttu-id="cdf7d-103">Define um filtro de roteamento, que determina o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, como também quaisquer dados de apoio ou parâmetros exigidos pelo filtro.</span><span class="sxs-lookup"><span data-stu-id="cdf7d-103">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="cdf7d-104">\<System. ServiceModel > \<roteamento > \<filtros > \<filtro ></span><span class="sxs-lookup"><span data-stu-id="cdf7d-104">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>
  
## <a name="syntax"></a><span data-ttu-id="cdf7d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cdf7d-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdf7d-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cdf7d-106">Attributes and elements</span></span>

<span data-ttu-id="cdf7d-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cdf7d-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cdf7d-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="cdf7d-108">Attributes</span></span>

| <span data-ttu-id="cdf7d-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="cdf7d-109">Attribute</span></span>  | <span data-ttu-id="cdf7d-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="cdf7d-110">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="cdf7d-111">CustomType</span><span class="sxs-lookup"><span data-stu-id="cdf7d-111">customType</span></span> | <span data-ttu-id="cdf7d-112">Uma cadeia de caracteres que contém o nome de tipo totalmente qualificado do tipo a ser usado como um filtro personalizado.</span><span class="sxs-lookup"><span data-stu-id="cdf7d-112">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="cdf7d-113">Se `filterType` é definido como `custom`, este atributo contém o nome do tipo totalmente qualificado da classe para criar.</span><span class="sxs-lookup"><span data-stu-id="cdf7d-113">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="cdf7d-114">`filterData` também pode conter valores a serem usados durante a avaliação do filtro de tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="cdf7d-114">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="cdf7d-115">filterData</span><span class="sxs-lookup"><span data-stu-id="cdf7d-115">filterData</span></span> | <span data-ttu-id="cdf7d-116">Uma cadeia de caracteres que contém os dados de filtro.</span><span class="sxs-lookup"><span data-stu-id="cdf7d-116">A string containing the filter data.</span></span> <span data-ttu-id="cdf7d-117">Para obter mais informações sobre como especificar esse atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdf7d-117">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="cdf7d-118">filterType</span><span class="sxs-lookup"><span data-stu-id="cdf7d-118">filterType</span></span> | <span data-ttu-id="cdf7d-119">Uma cadeia de caracteres que contém o tipo de filtro.</span><span class="sxs-lookup"><span data-stu-id="cdf7d-119">A string containing the filter type.</span></span> <span data-ttu-id="cdf7d-120">Esse atributo é do <xref:System.ServiceModel.Routing.Configuration.FilterType> tipo.</span><span class="sxs-lookup"><span data-stu-id="cdf7d-120">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="cdf7d-121">Para obter mais informações sobre como isso funciona com o `filterData` atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdf7d-121">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="cdf7d-122">name</span><span class="sxs-lookup"><span data-stu-id="cdf7d-122">name</span></span>       | <span data-ttu-id="cdf7d-123">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de filtro.</span><span class="sxs-lookup"><span data-stu-id="cdf7d-123">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="cdf7d-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cdf7d-124">Child elements</span></span>

<span data-ttu-id="cdf7d-125">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="cdf7d-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cdf7d-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cdf7d-126">Parent elements</span></span>

| <span data-ttu-id="cdf7d-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="cdf7d-127">Element</span></span> | <span data-ttu-id="cdf7d-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="cdf7d-128">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="cdf7d-129">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="cdf7d-129">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="cdf7d-130">Uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="cdf7d-130">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="cdf7d-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdf7d-131">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
