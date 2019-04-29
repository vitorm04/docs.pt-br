---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: cc7c1a64f9481a7ab41cf35241ade04bd690dae0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786380"
---
# <a name="routing"></a><span data-ttu-id="c9d9a-101">\<routing></span><span class="sxs-lookup"><span data-stu-id="c9d9a-101">\<routing></span></span>

<span data-ttu-id="c9d9a-102">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como roteamento de tabelas que definem os pontos de extremidade de destino para envie mensagens para quando um filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="c9d9a-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="c9d9a-103">[**\<system.serviceModel>**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="c9d9a-103">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="c9d9a-104">&nbsp;&nbsp;**\<routing>**</span><span class="sxs-lookup"><span data-stu-id="c9d9a-104">&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="c9d9a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9d9a-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String"
               filterName="String"
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9d9a-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c9d9a-106">Attributes and elements</span></span>

<span data-ttu-id="c9d9a-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c9d9a-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9d9a-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="c9d9a-108">Attributes</span></span>

<span data-ttu-id="c9d9a-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c9d9a-109">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="c9d9a-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c9d9a-110">Child elements</span></span>

|     | <span data-ttu-id="c9d9a-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9d9a-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c9d9a-112">**\<filters>**</span><span class="sxs-lookup"><span data-stu-id="c9d9a-112">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="c9d9a-113">Contém um conjunto de filtros de roteamento que determinam que o tipo de MessageFilter do Windows Communication Foundation (WCF) será usado ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="c9d9a-113">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="c9d9a-114">**\<filterTables>**</span><span class="sxs-lookup"><span data-stu-id="c9d9a-114">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="c9d9a-115">Contém mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para especificar qual ponto de extremidade usado quando o filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="c9d9a-115">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="c9d9a-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c9d9a-116">Parent elements</span></span>

|     | <span data-ttu-id="c9d9a-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9d9a-117">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="c9d9a-118">**\<system.ServiceModel>**</span><span class="sxs-lookup"><span data-stu-id="c9d9a-118">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="c9d9a-119">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="c9d9a-119">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="c9d9a-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9d9a-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
