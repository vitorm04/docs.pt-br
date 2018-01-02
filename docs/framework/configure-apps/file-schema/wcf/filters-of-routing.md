---
title: '&lt;filtros&gt; de &lt;roteamento&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2687101aa868ae77ce0ae818afd9df906f8525c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="8c41b-102">&lt;filtros&gt; de &lt;roteamento&gt;</span><span class="sxs-lookup"><span data-stu-id="8c41b-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="8c41b-103">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="8c41b-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="8c41b-104">[**\<System. ServiceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="8c41b-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="8c41b-105">&nbsp;&nbsp;[**\<roteamento >**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="8c41b-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="8c41b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Filtros >**</span><span class="sxs-lookup"><span data-stu-id="8c41b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="8c41b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c41b-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="8c41b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8c41b-108">Attributes and elements</span></span>

<span data-ttu-id="8c41b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8c41b-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8c41b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8c41b-110">Attributes</span></span>

<span data-ttu-id="8c41b-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8c41b-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="8c41b-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8c41b-112">Child elements</span></span>

|     | <span data-ttu-id="8c41b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c41b-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8c41b-114">**\<Filtro >**</span><span class="sxs-lookup"><span data-stu-id="8c41b-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="8c41b-115">Contém um filtro de roteamento que determina o tipo de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> será usada ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="8c41b-115">Contains a routing filter that determines the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="8c41b-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8c41b-116">Parent elements</span></span>

|     | <span data-ttu-id="8c41b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c41b-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8c41b-118">**\<roteamento >**</span><span class="sxs-lookup"><span data-stu-id="8c41b-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="8c41b-119">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como o roteamento de tabelas que definem os pontos de extremidade de destino para enviar mensagens quando um corresponde ao filtro.</span><span class="sxs-lookup"><span data-stu-id="8c41b-119">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="8c41b-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c41b-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
