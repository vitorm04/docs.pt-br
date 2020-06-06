---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855250"
---
# \<filter>

<span data-ttu-id="bc234-101">Define um filtro de roteamento, que determina o tipo de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usado ao avaliar mensagens recebidas, bem como quaisquer dados de suporte ou parâmetros exigidos pelo filtro.</span><span class="sxs-lookup"><span data-stu-id="bc234-101">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**  
  
## <a name="syntax"></a><span data-ttu-id="bc234-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc234-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc234-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bc234-103">Attributes and elements</span></span>

<span data-ttu-id="bc234-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bc234-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc234-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="bc234-105">Attributes</span></span>

| <span data-ttu-id="bc234-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="bc234-106">Attribute</span></span>  | <span data-ttu-id="bc234-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc234-107">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="bc234-108">CustomType</span><span class="sxs-lookup"><span data-stu-id="bc234-108">customType</span></span> | <span data-ttu-id="bc234-109">Uma cadeia de caracteres que contém o nome do tipo totalmente qualificado do tipo personalizado a ser usado como um filtro.</span><span class="sxs-lookup"><span data-stu-id="bc234-109">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="bc234-110">Se `filterType` é definido como `custom` , esse atributo contém o nome de tipo totalmente qualificado da classe a ser criada.</span><span class="sxs-lookup"><span data-stu-id="bc234-110">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="bc234-111">`filterData`também pode conter valores a serem usados durante a avaliação do filtro de tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="bc234-111">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="bc234-112">filterData</span><span class="sxs-lookup"><span data-stu-id="bc234-112">filterData</span></span> | <span data-ttu-id="bc234-113">Uma cadeia de caracteres que contém os dados de filtro.</span><span class="sxs-lookup"><span data-stu-id="bc234-113">A string containing the filter data.</span></span> <span data-ttu-id="bc234-114">Para obter mais informações sobre como especificar esse atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> .</span><span class="sxs-lookup"><span data-stu-id="bc234-114">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="bc234-115">filterType</span><span class="sxs-lookup"><span data-stu-id="bc234-115">filterType</span></span> | <span data-ttu-id="bc234-116">Uma cadeia de caracteres que contém o tipo de filtro.</span><span class="sxs-lookup"><span data-stu-id="bc234-116">A string containing the filter type.</span></span> <span data-ttu-id="bc234-117">Esse atributo é do <xref:System.ServiceModel.Routing.Configuration.FilterType> tipo.</span><span class="sxs-lookup"><span data-stu-id="bc234-117">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="bc234-118">Para obter mais informações sobre como isso funciona com o `filterData` atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> .</span><span class="sxs-lookup"><span data-stu-id="bc234-118">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="bc234-119">name</span><span class="sxs-lookup"><span data-stu-id="bc234-119">name</span></span>       | <span data-ttu-id="bc234-120">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de filtro.</span><span class="sxs-lookup"><span data-stu-id="bc234-120">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="bc234-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bc234-121">Child elements</span></span>

<span data-ttu-id="bc234-122">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="bc234-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bc234-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bc234-123">Parent elements</span></span>

| <span data-ttu-id="bc234-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="bc234-124">Element</span></span> | <span data-ttu-id="bc234-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc234-125">Description</span></span> |
| ------- | ----------- |
| [\<routing>](routing.md) | <span data-ttu-id="bc234-126">Uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usado ao avaliar mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="bc234-126">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="bc234-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="bc234-127">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
