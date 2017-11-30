---
title: "Referências a entidades são preservadas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 770c714e8f5942ea733c417ae9b06f69e4acf1a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="e1b53-102">Referências a entidades são preservadas</span><span class="sxs-lookup"><span data-stu-id="e1b53-102">Entity References are Preserved</span></span>
<span data-ttu-id="e1b53-103">Quando a referência de entidade não é expandida, mas preservada, o modelo de objeto de documento (DOM) XML cria uma **XmlEntityReference** nó quando ele encontra uma referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="e1b53-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="e1b53-104">Usando o seguinte XML,</span><span class="sxs-lookup"><span data-stu-id="e1b53-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="e1b53-105">o DOM cria um **XmlEntityReference** nó quando ele encontra a `&publisher;` referência.</span><span class="sxs-lookup"><span data-stu-id="e1b53-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="e1b53-106">O **XmlEntityReference** contém nós filho copiados do conteúdo na declaração da entidade.</span><span class="sxs-lookup"><span data-stu-id="e1b53-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="e1b53-107">O exemplo de código anterior contém texto na declaração da entidade, então um **XmlText** nó será criado como o nó filho do nó de referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="e1b53-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="e1b53-108">![Árvore de estrutura para referências de entidade preservadas](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="e1b53-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="e1b53-109">Estrutura de árvore para as referências de entidade que são preservadas</span><span class="sxs-lookup"><span data-stu-id="e1b53-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="e1b53-110">Os nós filho do **XmlEntityReference** são criados a partir de nós de cópias de todos os filhos de **XmlEntity** nó quando a declaração de entidade foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="e1b53-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1b53-111">Os nós copiados do **XmlEntity** nem sempre são cópias exatas de uma vez colocadas sob o nó de referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="e1b53-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="e1b53-112">Pode haver namespaces que estão no escopo no nó de referência de entidade, e que afetam a configuração final dos nós filho.</span><span class="sxs-lookup"><span data-stu-id="e1b53-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="e1b53-113">Por padrão, como entidades gerais `&abc;` são preservados e **XmlEntityReference** nós sempre criados.</span><span class="sxs-lookup"><span data-stu-id="e1b53-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1b53-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1b53-114">See Also</span></span>  
 [<span data-ttu-id="e1b53-115">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="e1b53-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
