---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 3c7e9cb1284ab55c8dd199d9fb47a223698814f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934135"
---
# <a name="routing"></a><span data-ttu-id="256f2-101">\<> de roteamento</span><span class="sxs-lookup"><span data-stu-id="256f2-101">\<routing></span></span>

<span data-ttu-id="256f2-102">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation <xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) a ser usado ao avaliar mensagens de entrada, bem como tabelas de roteamento que definem os pontos de extremidade de destino para enviar mensagens para quando um filtro corresponder.</span><span class="sxs-lookup"><span data-stu-id="256f2-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="256f2-103">[ **\<system.serviceModel>** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="256f2-103">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="256f2-104">&nbsp;&nbsp; **\<routing>**</span><span class="sxs-lookup"><span data-stu-id="256f2-104">&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="256f2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="256f2-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="256f2-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="256f2-106">Attributes and elements</span></span>

<span data-ttu-id="256f2-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="256f2-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="256f2-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="256f2-108">Attributes</span></span>

<span data-ttu-id="256f2-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="256f2-109">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="256f2-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="256f2-110">Child elements</span></span>

|     | <span data-ttu-id="256f2-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="256f2-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="256f2-112"> **\<filters>** </span><span class="sxs-lookup"><span data-stu-id="256f2-112">**\<filters>**</span></span>](filters-of-routing.md) | <span data-ttu-id="256f2-113">Contém um conjunto de filtros de roteamento que determinam o tipo de Windows Communication Foundation (WCF) MessageFilter será usado ao avaliar mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="256f2-113">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="256f2-114"> **\<filterTables>** </span><span class="sxs-lookup"><span data-stu-id="256f2-114">**\<filterTables>**</span></span>](filtertables.md) | <span data-ttu-id="256f2-115">Contém mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para especificar qual ponto de extremidades usar quando o filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="256f2-115">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="256f2-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="256f2-116">Parent elements</span></span>

|     | <span data-ttu-id="256f2-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="256f2-117">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="256f2-118">**\<system.ServiceModel>**</span><span class="sxs-lookup"><span data-stu-id="256f2-118">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="256f2-119">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="256f2-119">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="256f2-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="256f2-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
