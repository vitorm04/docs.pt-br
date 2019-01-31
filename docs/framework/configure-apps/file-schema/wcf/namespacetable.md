---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: ee7a0c23adca883af279addf9d1f221bd4056d00
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269569"
---
# <a name="namespacetable"></a><span data-ttu-id="67edc-101">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="67edc-101">\<namespaceTable></span></span>

<span data-ttu-id="67edc-102">Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que pode ser usado em filtros de XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="67edc-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="67edc-103">**\<system.serviceModel>** </span><span class="sxs-lookup"><span data-stu-id="67edc-103">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="67edc-104">&nbsp;&nbsp;**\<routing>** </span><span class="sxs-lookup"><span data-stu-id="67edc-104">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="67edc-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span><span class="sxs-lookup"><span data-stu-id="67edc-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="67edc-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67edc-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67edc-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="67edc-107">Attributes and elements</span></span>

<span data-ttu-id="67edc-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="67edc-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="67edc-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="67edc-109">Attributes</span></span>

<span data-ttu-id="67edc-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="67edc-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="67edc-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="67edc-111">Child elements</span></span>

|     | <span data-ttu-id="67edc-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="67edc-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="67edc-113">**\<filter>**</span><span class="sxs-lookup"><span data-stu-id="67edc-113">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="67edc-114">Define um mapeamento de prefixo de namespace usado para expressões XPath.</span><span class="sxs-lookup"><span data-stu-id="67edc-114">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="67edc-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="67edc-115">Parent elements</span></span>

|     | <span data-ttu-id="67edc-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="67edc-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="67edc-117">**\<routing>**</span><span class="sxs-lookup"><span data-stu-id="67edc-117">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="67edc-118">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como roteamento de tabelas que definem os pontos de extremidade de destino para envie mensagens para quando um filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="67edc-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="67edc-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67edc-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
