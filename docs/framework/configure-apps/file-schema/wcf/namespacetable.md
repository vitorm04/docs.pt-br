---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: aefe7beec7335d80341e670961800907c2bd0200
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855098"
---
# <a name="namespacetable"></a><span data-ttu-id="a82f2-101">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="a82f2-101">\<namespaceTable></span></span>

<span data-ttu-id="a82f2-102">Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que podem ser usados em filtros XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="a82f2-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="a82f2-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a82f2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a82f2-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a82f2-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a82f2-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de roteamento**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="a82f2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="a82f2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de NamespaceTable**</span><span class="sxs-lookup"><span data-stu-id="a82f2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a82f2-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a82f2-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a82f2-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a82f2-108">Attributes and elements</span></span>

<span data-ttu-id="a82f2-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a82f2-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a82f2-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="a82f2-110">Attributes</span></span>

<span data-ttu-id="a82f2-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a82f2-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="a82f2-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a82f2-112">Child elements</span></span>

|     | <span data-ttu-id="a82f2-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a82f2-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a82f2-114"> **\<filter>** </span><span class="sxs-lookup"><span data-stu-id="a82f2-114">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="a82f2-115">Define um mapeamento de prefixo de namespace usado para expressões XPath.</span><span class="sxs-lookup"><span data-stu-id="a82f2-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="a82f2-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a82f2-116">Parent elements</span></span>

|     | <span data-ttu-id="a82f2-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a82f2-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a82f2-118"> **\<routing>** </span><span class="sxs-lookup"><span data-stu-id="a82f2-118">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="a82f2-119">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) a ser usado ao avaliar mensagens de entrada, bem como tabelas de roteamento que definem os pontos de extremidade de destino para enviar mensagens para quando um filtro corresponder.</span><span class="sxs-lookup"><span data-stu-id="a82f2-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="a82f2-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a82f2-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
