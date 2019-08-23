---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 0316e983446644671ead2f8f843dc91b493b29c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933163"
---
# <a name="namespacetable"></a><span data-ttu-id="59a68-101">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="59a68-101">\<namespaceTable></span></span>

<span data-ttu-id="59a68-102">Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que podem ser usados em filtros XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="59a68-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="59a68-103">**\<system.serviceModel>**  </span><span class="sxs-lookup"><span data-stu-id="59a68-103">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="59a68-104">&nbsp;&nbsp; **\<routing>**  </span><span class="sxs-lookup"><span data-stu-id="59a68-104">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="59a68-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<namespaceTable>**</span><span class="sxs-lookup"><span data-stu-id="59a68-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="59a68-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59a68-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String"
           prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59a68-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="59a68-107">Attributes and elements</span></span>

<span data-ttu-id="59a68-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="59a68-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="59a68-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="59a68-109">Attributes</span></span>

<span data-ttu-id="59a68-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="59a68-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="59a68-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="59a68-111">Child elements</span></span>

|     | <span data-ttu-id="59a68-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="59a68-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="59a68-113"> **\<filter>** </span><span class="sxs-lookup"><span data-stu-id="59a68-113">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="59a68-114">Define um mapeamento de prefixo de namespace usado para expressões XPath.</span><span class="sxs-lookup"><span data-stu-id="59a68-114">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="59a68-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="59a68-115">Parent elements</span></span>

|     | <span data-ttu-id="59a68-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="59a68-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="59a68-117"> **\<routing>** </span><span class="sxs-lookup"><span data-stu-id="59a68-117">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="59a68-118">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) a ser usado ao avaliar mensagens de entrada, bem como tabelas de roteamento que definem os pontos de extremidade de destino para enviar mensagens para quando um filtro corresponder.</span><span class="sxs-lookup"><span data-stu-id="59a68-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="59a68-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59a68-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
