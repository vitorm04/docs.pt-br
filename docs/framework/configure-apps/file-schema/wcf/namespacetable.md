---
title: '&lt;namespaceTable&gt;'
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 31d661f39f9e3de0f7012c7fa52d4964e7ee4a69
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="87fe5-102">&lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="87fe5-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="87fe5-103">Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que podem ser usadas em filtros de XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="87fe5-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="87fe5-104">**\<System. ServiceModel >** </span><span class="sxs-lookup"><span data-stu-id="87fe5-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="87fe5-105">&nbsp;&nbsp;**\<roteamento >** </span><span class="sxs-lookup"><span data-stu-id="87fe5-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="87fe5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="87fe5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>

## <a name="syntax"></a><span data-ttu-id="87fe5-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87fe5-107">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String" prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
``` 

## <a name="attributes-and-elements"></a><span data-ttu-id="87fe5-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="87fe5-108">Attributes and elements</span></span>

<span data-ttu-id="87fe5-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="87fe5-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="87fe5-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="87fe5-110">Attributes</span></span>

<span data-ttu-id="87fe5-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="87fe5-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="87fe5-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="87fe5-112">Child elements</span></span>

|     | <span data-ttu-id="87fe5-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="87fe5-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="87fe5-114">**\<Filtro >**</span><span class="sxs-lookup"><span data-stu-id="87fe5-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="87fe5-115">Define um mapeamento de prefixo de namespace usado para expressões XPath.</span><span class="sxs-lookup"><span data-stu-id="87fe5-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="87fe5-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="87fe5-116">Parent elements</span></span>

|     | <span data-ttu-id="87fe5-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="87fe5-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="87fe5-118">**\<roteamento >**</span><span class="sxs-lookup"><span data-stu-id="87fe5-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="87fe5-119">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como o roteamento de tabelas que definem os pontos de extremidade de destino para envie mensagens para quando houver correspondência de filtro.</span><span class="sxs-lookup"><span data-stu-id="87fe5-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="87fe5-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87fe5-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
