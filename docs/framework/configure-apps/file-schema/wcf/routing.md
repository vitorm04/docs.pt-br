---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399967"
---
# \<routing>

<span data-ttu-id="e3740-101">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usado ao avaliar mensagens de entrada, bem como tabelas de roteamento que definem os pontos de extremidade de destino para envio de mensagens quando um filtro é correspondente.</span><span class="sxs-lookup"><span data-stu-id="e3740-101">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**
  
## <a name="syntax"></a><span data-ttu-id="e3740-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3740-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3740-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e3740-103">Attributes and elements</span></span>

<span data-ttu-id="e3740-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e3740-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3740-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="e3740-105">Attributes</span></span>

<span data-ttu-id="e3740-106">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e3740-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3740-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e3740-107">Child elements</span></span>

|     | <span data-ttu-id="e3740-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3740-108">Description</span></span> |
| --- | ----------- |
| [**\<filters>**](filters-of-routing.md) | <span data-ttu-id="e3740-109">Contém um conjunto de filtros de roteamento que determinam o tipo de Windows Communication Foundation (WCF) MessageFilter será usado ao avaliar mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="e3740-109">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [**\<filterTables>**](filtertables.md) | <span data-ttu-id="e3740-110">Contém mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para especificar qual ponto de extremidades usar quando o filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="e3740-110">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="e3740-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e3740-111">Parent elements</span></span>

|     | <span data-ttu-id="e3740-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3740-112">Description</span></span> |
| --- | ----------- |
| **\<system.ServiceModel>** | <span data-ttu-id="e3740-113">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="e3740-113">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="e3740-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="e3740-114">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
