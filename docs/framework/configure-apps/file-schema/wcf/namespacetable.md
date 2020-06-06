---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: aefe7beec7335d80341e670961800907c2bd0200
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855098"
---
# \<namespaceTable>

<span data-ttu-id="b6c11-101">Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que podem ser usados em filtros XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="b6c11-101">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**  
  
## <a name="syntax"></a><span data-ttu-id="b6c11-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6c11-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6c11-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b6c11-103">Attributes and elements</span></span>

<span data-ttu-id="b6c11-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b6c11-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b6c11-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="b6c11-105">Attributes</span></span>

<span data-ttu-id="b6c11-106">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b6c11-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="b6c11-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b6c11-107">Child elements</span></span>

|     | <span data-ttu-id="b6c11-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6c11-108">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="b6c11-109">Define um mapeamento de prefixo de namespace usado para expressões XPath.</span><span class="sxs-lookup"><span data-stu-id="b6c11-109">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="b6c11-110">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b6c11-110">Parent elements</span></span>

|     | <span data-ttu-id="b6c11-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6c11-111">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="b6c11-112">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usado ao avaliar mensagens de entrada, bem como tabelas de roteamento que definem os pontos de extremidade de destino para envio de mensagens quando um filtro é correspondente.</span><span class="sxs-lookup"><span data-stu-id="b6c11-112">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="b6c11-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="b6c11-113">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
