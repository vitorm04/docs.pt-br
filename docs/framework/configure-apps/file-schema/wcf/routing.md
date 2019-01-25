---
title: '&lt;routing&gt;'
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 855faedfd2e9523e939174441b0cfa50e052b375
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565872"
---
# <a name="ltroutinggt"></a><span data-ttu-id="f2da5-102">&lt;routing&gt;</span><span class="sxs-lookup"><span data-stu-id="f2da5-102">&lt;routing&gt;</span></span>

<span data-ttu-id="f2da5-103">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como roteamento de tabelas que definem os pontos de extremidade de destino para envie mensagens para quando um filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="f2da5-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="f2da5-104">[**\<system.serviceModel>**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="f2da5-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="f2da5-105">&nbsp;&nbsp;**\<routing>**</span><span class="sxs-lookup"><span data-stu-id="f2da5-105">&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="f2da5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2da5-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2da5-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f2da5-107">Attributes and elements</span></span>

<span data-ttu-id="f2da5-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f2da5-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2da5-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f2da5-109">Attributes</span></span>

<span data-ttu-id="f2da5-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f2da5-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="f2da5-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f2da5-111">Child elements</span></span>

|     | <span data-ttu-id="f2da5-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2da5-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f2da5-113">**\<filters>**</span><span class="sxs-lookup"><span data-stu-id="f2da5-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="f2da5-114">Contém um conjunto de filtros de roteamento que determinam que o tipo de MessageFilter do Windows Communication Foundation (WCF) será usado ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="f2da5-114">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="f2da5-115">**\<filterTables>**</span><span class="sxs-lookup"><span data-stu-id="f2da5-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="f2da5-116">Contém mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para especificar qual ponto de extremidade usado quando o filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="f2da5-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="f2da5-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f2da5-117">Parent elements</span></span>

|     | <span data-ttu-id="f2da5-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2da5-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="f2da5-119">**\<system.ServiceModel>**</span><span class="sxs-lookup"><span data-stu-id="f2da5-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="f2da5-120">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="f2da5-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f2da5-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2da5-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
