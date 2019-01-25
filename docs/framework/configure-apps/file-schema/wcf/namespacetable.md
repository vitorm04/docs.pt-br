---
title: '&lt;namespaceTable&gt;'
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: fb2b324a2c128b470f1a9a21343408280c5e1862
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743234"
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="c7838-102">&lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="c7838-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="c7838-103">Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que pode ser usado em filtros de XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="c7838-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="c7838-104">**\<system.serviceModel>** </span><span class="sxs-lookup"><span data-stu-id="c7838-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="c7838-105">&nbsp;&nbsp;**\<routing>** </span><span class="sxs-lookup"><span data-stu-id="c7838-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="c7838-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span><span class="sxs-lookup"><span data-stu-id="c7838-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="c7838-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7838-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7838-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c7838-108">Attributes and elements</span></span>

<span data-ttu-id="c7838-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c7838-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c7838-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c7838-110">Attributes</span></span>

<span data-ttu-id="c7838-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c7838-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="c7838-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c7838-112">Child elements</span></span>

|     | <span data-ttu-id="c7838-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7838-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c7838-114">**\<filter>**</span><span class="sxs-lookup"><span data-stu-id="c7838-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="c7838-115">Define um mapeamento de prefixo de namespace usado para expressões XPath.</span><span class="sxs-lookup"><span data-stu-id="c7838-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="c7838-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c7838-116">Parent elements</span></span>

|     | <span data-ttu-id="c7838-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7838-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c7838-118">**\<routing>**</span><span class="sxs-lookup"><span data-stu-id="c7838-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="c7838-119">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como roteamento de tabelas que definem os pontos de extremidade de destino para envie mensagens para quando um filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="c7838-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="c7838-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7838-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
