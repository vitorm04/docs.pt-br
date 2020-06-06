---
title: <filters> de <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: c9bc3a2c379e14d8cf687676a3ec40702d150e1e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855241"
---
# <a name="filters-of-routing"></a><span data-ttu-id="48873-102">\<filters> de \<routing></span><span class="sxs-lookup"><span data-stu-id="48873-102">\<filters> of \<routing></span></span>

<span data-ttu-id="48873-103">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usado ao avaliar mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="48873-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**  
  
## <a name="syntax"></a><span data-ttu-id="48873-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48873-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48873-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="48873-105">Attributes and elements</span></span>

<span data-ttu-id="48873-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="48873-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="48873-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="48873-107">Attributes</span></span>

<span data-ttu-id="48873-108">Nenhum</span><span class="sxs-lookup"><span data-stu-id="48873-108">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="48873-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="48873-109">Child elements</span></span>

|     | <span data-ttu-id="48873-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="48873-110">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="48873-111">Contém um filtro de roteamento que determina o tipo de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> será usado ao avaliar mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="48873-111">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="48873-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="48873-112">Parent elements</span></span>

|     | <span data-ttu-id="48873-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="48873-113">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="48873-114">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usado ao avaliar mensagens de entrada, bem como tabelas de roteamento que definem os pontos de extremidade de destino para envio de mensagens quando um filtro é correspondente.</span><span class="sxs-lookup"><span data-stu-id="48873-114">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="48873-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="48873-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
