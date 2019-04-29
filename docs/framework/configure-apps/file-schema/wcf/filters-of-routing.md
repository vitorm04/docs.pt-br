---
title: <filters> de <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 8b2c735a19c4cece16dcb77e3ec548eb2d39ec18
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701028"
---
# <a name="filters-of-routing"></a><span data-ttu-id="3e766-102">\<Filtros > de \<roteamento ></span><span class="sxs-lookup"><span data-stu-id="3e766-102">\<filters> of \<routing></span></span>

<span data-ttu-id="3e766-103">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="3e766-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="3e766-104">[**\<system.serviceModel>**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="3e766-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="3e766-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="3e766-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="3e766-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span><span class="sxs-lookup"><span data-stu-id="3e766-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="3e766-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e766-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e766-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3e766-108">Attributes and elements</span></span>

<span data-ttu-id="3e766-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3e766-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3e766-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="3e766-110">Attributes</span></span>

<span data-ttu-id="3e766-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3e766-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="3e766-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3e766-112">Child elements</span></span>

|     | <span data-ttu-id="3e766-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e766-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3e766-114">**\<filter>**</span><span class="sxs-lookup"><span data-stu-id="3e766-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="3e766-115">Contém um filtro de roteamento que determina o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> será usada ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="3e766-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="3e766-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3e766-116">Parent elements</span></span>

|     | <span data-ttu-id="3e766-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e766-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3e766-118">**\<routing>**</span><span class="sxs-lookup"><span data-stu-id="3e766-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="3e766-119">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como roteamento de tabelas que definem os pontos de extremidade de destino para envie mensagens para quando um filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="3e766-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="3e766-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e766-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
