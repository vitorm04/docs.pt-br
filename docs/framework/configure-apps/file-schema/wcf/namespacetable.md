---
title: '&lt;namespaceTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 470dd2dcc2e8554bb89eec159c6b96b24795c5d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="ad307-102">&lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="ad307-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="ad307-103">Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que podem ser usadas em filtros de XPath para roteamento.</span><span class="sxs-lookup"><span data-stu-id="ad307-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="ad307-104">**\<System. ServiceModel >** </span><span class="sxs-lookup"><span data-stu-id="ad307-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="ad307-105">&nbsp;&nbsp;**\<roteamento >** </span><span class="sxs-lookup"><span data-stu-id="ad307-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="ad307-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="ad307-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ad307-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad307-107">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String" prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
``` 

## <a name="attributes-and-elements"></a><span data-ttu-id="ad307-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ad307-108">Attributes and elements</span></span>

<span data-ttu-id="ad307-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ad307-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ad307-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ad307-110">Attributes</span></span>

<span data-ttu-id="ad307-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ad307-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="ad307-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ad307-112">Child elements</span></span>

|     | <span data-ttu-id="ad307-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad307-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ad307-114">**\<Filtro >**</span><span class="sxs-lookup"><span data-stu-id="ad307-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="ad307-115">Define um mapeamento de prefixo de namespace usado para expressões XPath.</span><span class="sxs-lookup"><span data-stu-id="ad307-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="ad307-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ad307-116">Parent elements</span></span>

|     | <span data-ttu-id="ad307-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad307-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ad307-118">**\<roteamento >**</span><span class="sxs-lookup"><span data-stu-id="ad307-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="ad307-119">Representa uma seção de configuração para definir um conjunto de filtros de roteamento, que determinam o tipo de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como o roteamento de tabelas que definem os pontos de extremidade de destino para enviar mensagens quando um corresponde ao filtro.</span><span class="sxs-lookup"><span data-stu-id="ad307-119">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="ad307-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad307-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
