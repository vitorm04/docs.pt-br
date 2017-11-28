---
title: '&lt;roteamento&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed2dd4e68584d6e79e18fc9b61fcc8f078615dac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltroutinggt"></a><span data-ttu-id="e2991-102">&lt;roteamento&gt;</span><span class="sxs-lookup"><span data-stu-id="e2991-102">&lt;routing&gt;</span></span>

<span data-ttu-id="e2991-103">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como o roteamento de tabelas que definem os pontos de extremidade de destino para enviar mensagens quando um corresponde ao filtro.</span><span class="sxs-lookup"><span data-stu-id="e2991-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="e2991-104">[**\<System. ServiceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="e2991-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="e2991-105">&nbsp;&nbsp;**\<roteamento >**</span><span class="sxs-lookup"><span data-stu-id="e2991-105">&nbsp;&nbsp;**\<routing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e2991-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e2991-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e2991-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e2991-107">Attributes and elements</span></span>

<span data-ttu-id="e2991-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e2991-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2991-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="e2991-109">Attributes</span></span>

<span data-ttu-id="e2991-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e2991-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2991-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e2991-111">Child elements</span></span>

|     | <span data-ttu-id="e2991-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2991-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e2991-113">**\<Filtros >**</span><span class="sxs-lookup"><span data-stu-id="e2991-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="e2991-114">Contém um conjunto de filtros de roteamento que determinam o tipo de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter será usada ao avaliar mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="e2991-114">Contains a set of routing filters that determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="e2991-115">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="e2991-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="e2991-116">Contém os mapeamentos entre os filtros de roteamento e os pontos de extremidade de destino para especificar qual ponto de extremidade a ser usado ao correspondências de filtro.</span><span class="sxs-lookup"><span data-stu-id="e2991-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="e2991-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e2991-117">Parent elements</span></span>

|     | <span data-ttu-id="e2991-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2991-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="e2991-119">**\<sistema. ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="e2991-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="e2991-120">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="e2991-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="e2991-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2991-121">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
