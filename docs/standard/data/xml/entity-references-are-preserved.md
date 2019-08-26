---
title: Referências a entidades são preservadas
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e512f2077c2e6b9feba5024c4eabc2568357ecab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965911"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="c513f-102">Referências a entidades são preservadas</span><span class="sxs-lookup"><span data-stu-id="c513f-102">Entity References are Preserved</span></span>
<span data-ttu-id="c513f-103">Quando a referência de entidade não é expandida, mas é preservada, o modelo de objeto (DOM) de documento XML cria um nó de **XmlEntityReference** quando encontra uma referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="c513f-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="c513f-104">Usando o seguinte XML,</span><span class="sxs-lookup"><span data-stu-id="c513f-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="c513f-105">o DOM cria um nó **XmlEntityReference** quando encontra a referência `&publisher;`.</span><span class="sxs-lookup"><span data-stu-id="c513f-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="c513f-106">**XmlEntityReference** contém os nós filho copiados de conteúdo na declaração de entidade.</span><span class="sxs-lookup"><span data-stu-id="c513f-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="c513f-107">O exemplo de código anterior contém o texto na declaração de entidade. Assim, um nó **XmlText** é criado como o nó filho do nó de referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="c513f-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="c513f-108">![Estrutura de árvore para referências de entidade preservadas](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="c513f-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="c513f-109">Estrutura de árvore para as referências de entidade que são preservadas</span><span class="sxs-lookup"><span data-stu-id="c513f-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="c513f-110">Os nós filho de **XmlEntityReference** são cópias de todos os nós filho criados do nó **XmlEntity** quando a declaração de entidade foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="c513f-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c513f-111">Os nós copiados de **XmlEntity** não são sempre cópias exatas quando colocados no nó de referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="c513f-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="c513f-112">Pode haver namespaces que estão no escopo no nó de referência de entidade, e que afetam a configuração final dos nós filho.</span><span class="sxs-lookup"><span data-stu-id="c513f-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="c513f-113">Por padrão, entidades gerais como `&abc;` são preservadas, e nós **XmlEntityReference** são sempre criados.</span><span class="sxs-lookup"><span data-stu-id="c513f-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c513f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c513f-114">See also</span></span>

- [<span data-ttu-id="c513f-115">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="c513f-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
