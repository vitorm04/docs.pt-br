---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399967"
---
# <a name="routing"></a><span data-ttu-id="26a3c-101">\<> de roteamento</span><span class="sxs-lookup"><span data-stu-id="26a3c-101">\<routing></span></span>

<span data-ttu-id="26a3c-102">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation <xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) a ser usado ao avaliar mensagens de entrada, bem como tabelas de roteamento que definem os pontos de extremidade de destino para enviar mensagens para quando um filtro corresponder.</span><span class="sxs-lookup"><span data-stu-id="26a3c-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="26a3c-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="26a3c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="26a3c-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="26a3c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="26a3c-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<> de roteamento**</span><span class="sxs-lookup"><span data-stu-id="26a3c-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="26a3c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26a3c-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26a3c-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="26a3c-107">Attributes and elements</span></span>

<span data-ttu-id="26a3c-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="26a3c-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="26a3c-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="26a3c-109">Attributes</span></span>

<span data-ttu-id="26a3c-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="26a3c-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="26a3c-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="26a3c-111">Child elements</span></span>

|     | <span data-ttu-id="26a3c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="26a3c-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="26a3c-113"> **\<filters>** </span><span class="sxs-lookup"><span data-stu-id="26a3c-113">**\<filters>**</span></span>](filters-of-routing.md) | <span data-ttu-id="26a3c-114">Contém um conjunto de filtros de roteamento que determinam o tipo de Windows Communication Foundation (WCF) MessageFilter será usado ao avaliar mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="26a3c-114">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="26a3c-115"> **\<filterTables>** </span><span class="sxs-lookup"><span data-stu-id="26a3c-115">**\<filterTables>**</span></span>](filtertables.md) | <span data-ttu-id="26a3c-116">Contém mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para especificar qual ponto de extremidades usar quando o filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="26a3c-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="26a3c-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="26a3c-117">Parent elements</span></span>

|     | <span data-ttu-id="26a3c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="26a3c-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="26a3c-119">**\<system.ServiceModel>**</span><span class="sxs-lookup"><span data-stu-id="26a3c-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="26a3c-120">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="26a3c-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="26a3c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26a3c-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
