---
title: '&lt;filtros&gt; de &lt;roteamento&gt;'
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 9f0fa9bf51d264346738172f57a8efca7950fdb7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753109"
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="3d17d-102">&lt;filtros&gt; de &lt;roteamento&gt;</span><span class="sxs-lookup"><span data-stu-id="3d17d-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="3d17d-103">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="3d17d-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="3d17d-104">[**\<System. ServiceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="3d17d-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="3d17d-105">&nbsp;&nbsp;[**\<roteamento >**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="3d17d-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="3d17d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Filtros >**</span><span class="sxs-lookup"><span data-stu-id="3d17d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3d17d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d17d-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="3d17d-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3d17d-108">Attributes and elements</span></span>

<span data-ttu-id="3d17d-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3d17d-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d17d-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="3d17d-110">Attributes</span></span>

<span data-ttu-id="3d17d-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3d17d-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="3d17d-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3d17d-112">Child elements</span></span>

|     | <span data-ttu-id="3d17d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d17d-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3d17d-114">**\<Filtro >**</span><span class="sxs-lookup"><span data-stu-id="3d17d-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="3d17d-115">Contém um filtro de roteamento que determina o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> será usada ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="3d17d-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="3d17d-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3d17d-116">Parent elements</span></span>

|     | <span data-ttu-id="3d17d-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d17d-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3d17d-118">**\<roteamento >**</span><span class="sxs-lookup"><span data-stu-id="3d17d-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="3d17d-119">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como o roteamento de tabelas que definem os pontos de extremidade de destino para envie mensagens para quando houver correspondência de filtro.</span><span class="sxs-lookup"><span data-stu-id="3d17d-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="3d17d-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d17d-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
