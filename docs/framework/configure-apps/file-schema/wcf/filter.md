---
title: '&lt;Filtro&gt;'
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 93d47fc6b25a75eedae43cd70582abc863a74e6c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747204"
---
# <a name="ltfiltergt"></a><span data-ttu-id="9f216-102">&lt;Filtro&gt;</span><span class="sxs-lookup"><span data-stu-id="9f216-102">&lt;filter&gt;</span></span>

<span data-ttu-id="9f216-103">Define um filtro de roteamento, que determina o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, como também quaisquer dados de apoio ou parâmetros exigidos pelo filtro.</span><span class="sxs-lookup"><span data-stu-id="9f216-103">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="9f216-104">\<System. ServiceModel > \<roteamento > \<filtros > \<filtro ></span><span class="sxs-lookup"><span data-stu-id="9f216-104">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>

## <a name="syntax"></a><span data-ttu-id="9f216-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f216-105">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="9f216-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9f216-106">Attributes and elements</span></span>

<span data-ttu-id="9f216-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9f216-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9f216-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="9f216-108">Attributes</span></span>

| <span data-ttu-id="9f216-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="9f216-109">Attribute</span></span>  | <span data-ttu-id="9f216-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f216-110">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="9f216-111">customType</span><span class="sxs-lookup"><span data-stu-id="9f216-111">customType</span></span> | <span data-ttu-id="9f216-112">Uma cadeia de caracteres que contém o nome de tipo totalmente qualificado do tipo personalizado a ser usado como um filtro.</span><span class="sxs-lookup"><span data-stu-id="9f216-112">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="9f216-113">Se `filterType` é definido como `custom`, este atributo contém o nome de tipo totalmente qualificado da classe para criar.</span><span class="sxs-lookup"><span data-stu-id="9f216-113">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="9f216-114">`filterData` também pode conter valores a serem usados durante a avaliação do filtro de tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="9f216-114">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="9f216-115">filterData</span><span class="sxs-lookup"><span data-stu-id="9f216-115">filterData</span></span> | <span data-ttu-id="9f216-116">Uma cadeia de caracteres que contém os dados de filtro.</span><span class="sxs-lookup"><span data-stu-id="9f216-116">A string containing the filter data.</span></span> <span data-ttu-id="9f216-117">Para obter mais informações sobre como especificar esse atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f216-117">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="9f216-118">filterType</span><span class="sxs-lookup"><span data-stu-id="9f216-118">filterType</span></span> | <span data-ttu-id="9f216-119">Uma cadeia de caracteres que contém o tipo de filtro.</span><span class="sxs-lookup"><span data-stu-id="9f216-119">A string containing the filter type.</span></span> <span data-ttu-id="9f216-120">Esse atributo é de <xref:System.ServiceModel.Routing.Configuration.FilterType> tipo.</span><span class="sxs-lookup"><span data-stu-id="9f216-120">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="9f216-121">Para obter mais informações sobre como isso funciona com o `filterData` de atributo, consulte <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f216-121">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="9f216-122">name</span><span class="sxs-lookup"><span data-stu-id="9f216-122">name</span></span>       | <span data-ttu-id="9f216-123">Uma cadeia de caracteres que contém o nome exclusivo deste elemento de filtro.</span><span class="sxs-lookup"><span data-stu-id="9f216-123">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="9f216-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9f216-124">Child elements</span></span>

<span data-ttu-id="9f216-125">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9f216-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9f216-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9f216-126">Parent elements</span></span>

| <span data-ttu-id="9f216-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="9f216-127">Element</span></span> | <span data-ttu-id="9f216-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f216-128">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="9f216-129">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="9f216-129">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="9f216-130">Uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="9f216-130">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="9f216-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f216-131">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
