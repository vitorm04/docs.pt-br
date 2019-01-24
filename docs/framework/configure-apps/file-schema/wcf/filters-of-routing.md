---
title: '&lt;filtros&gt; de &lt;roteamento&gt;'
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 468c10bc06b60f80ce93cf413c02582fe3861f70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704427"
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="ebd0c-102">&lt;filtros&gt; de &lt;roteamento&gt;</span><span class="sxs-lookup"><span data-stu-id="ebd0c-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="ebd0c-103">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="ebd0c-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="ebd0c-104">[**\<system.serviceModel>**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="ebd0c-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="ebd0c-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="ebd0c-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="ebd0c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span><span class="sxs-lookup"><span data-stu-id="ebd0c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="ebd0c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ebd0c-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebd0c-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ebd0c-108">Attributes and elements</span></span>

<span data-ttu-id="ebd0c-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ebd0c-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ebd0c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ebd0c-110">Attributes</span></span>

<span data-ttu-id="ebd0c-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ebd0c-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="ebd0c-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ebd0c-112">Child elements</span></span>

|     | <span data-ttu-id="ebd0c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ebd0c-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ebd0c-114">**\<filter>**</span><span class="sxs-lookup"><span data-stu-id="ebd0c-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="ebd0c-115">Contém um filtro de roteamento que determina o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> será usada ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="ebd0c-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="ebd0c-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ebd0c-116">Parent elements</span></span>

|     | <span data-ttu-id="ebd0c-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="ebd0c-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ebd0c-118">**\<routing>**</span><span class="sxs-lookup"><span data-stu-id="ebd0c-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="ebd0c-119">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como roteamento de tabelas que definem os pontos de extremidade de destino para envie mensagens para quando um filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="ebd0c-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="ebd0c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebd0c-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
