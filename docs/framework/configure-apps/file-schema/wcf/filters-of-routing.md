---
title: <filters> De <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 8b2c735a19c4cece16dcb77e3ec548eb2d39ec18
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272651"
---
# <a name="filters-of-routing"></a><span data-ttu-id="ce8a7-102">\<Filtros > de \<roteamento ></span><span class="sxs-lookup"><span data-stu-id="ce8a7-102">\<filters> of \<routing></span></span>

<span data-ttu-id="ce8a7-103">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="ce8a7-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="ce8a7-104">[**\<system.serviceModel>**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="ce8a7-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="ce8a7-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="ce8a7-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="ce8a7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span><span class="sxs-lookup"><span data-stu-id="ce8a7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="ce8a7-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce8a7-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce8a7-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ce8a7-108">Attributes and elements</span></span>

<span data-ttu-id="ce8a7-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ce8a7-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ce8a7-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ce8a7-110">Attributes</span></span>

<span data-ttu-id="ce8a7-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ce8a7-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="ce8a7-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ce8a7-112">Child elements</span></span>

|     | <span data-ttu-id="ce8a7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce8a7-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ce8a7-114">**\<filter>**</span><span class="sxs-lookup"><span data-stu-id="ce8a7-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="ce8a7-115">Contém um filtro de roteamento que determina o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> será usada ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="ce8a7-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="ce8a7-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ce8a7-116">Parent elements</span></span>

|     | <span data-ttu-id="ce8a7-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce8a7-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ce8a7-118">**\<routing>**</span><span class="sxs-lookup"><span data-stu-id="ce8a7-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="ce8a7-119">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como roteamento de tabelas que definem os pontos de extremidade de destino para envie mensagens para quando um filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="ce8a7-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="ce8a7-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce8a7-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
