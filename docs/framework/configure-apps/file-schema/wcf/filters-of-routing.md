---
title: <filters> de <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: ba60958ad33b46b40285f3f70001273bb3af3a63
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925613"
---
# <a name="filters-of-routing"></a><span data-ttu-id="6c01e-102">\<Filtros > do \<> de roteamento</span><span class="sxs-lookup"><span data-stu-id="6c01e-102">\<filters> of \<routing></span></span>

<span data-ttu-id="6c01e-103">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation <xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) a ser usado ao avaliar mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="6c01e-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="6c01e-104">[ **\<system.serviceModel>** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="6c01e-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="6c01e-105">&nbsp;&nbsp;[ **\<routing>** ](routing.md) </span><span class="sxs-lookup"><span data-stu-id="6c01e-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="6c01e-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<filters>**</span><span class="sxs-lookup"><span data-stu-id="6c01e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="6c01e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c01e-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c01e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6c01e-108">Attributes and elements</span></span>

<span data-ttu-id="6c01e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6c01e-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6c01e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="6c01e-110">Attributes</span></span>

<span data-ttu-id="6c01e-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6c01e-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="6c01e-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6c01e-112">Child elements</span></span>

|     | <span data-ttu-id="6c01e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c01e-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6c01e-114"> **\<filter>** </span><span class="sxs-lookup"><span data-stu-id="6c01e-114">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="6c01e-115">Contém um filtro de roteamento que determina o tipo de Windows Communication Foundation (WCF<xref:System.ServiceModel.Dispatcher.MessageFilter> ) será usado ao avaliar mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="6c01e-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="6c01e-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6c01e-116">Parent elements</span></span>

|     | <span data-ttu-id="6c01e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c01e-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6c01e-118"> **\<routing>** </span><span class="sxs-lookup"><span data-stu-id="6c01e-118">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="6c01e-119">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) a ser usado ao avaliar mensagens de entrada, bem como tabelas de roteamento que definem os pontos de extremidade de destino para enviar mensagens para quando um filtro corresponder.</span><span class="sxs-lookup"><span data-stu-id="6c01e-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="6c01e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c01e-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
