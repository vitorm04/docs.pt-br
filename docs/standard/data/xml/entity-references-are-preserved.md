---
title: Referências a entidades são preservadas
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
ms.openlocfilehash: e4c902df1b0cd2bd9e97b49c0ec1d10df91ef1c7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290338"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="4eba1-102">Referências a entidades são preservadas</span><span class="sxs-lookup"><span data-stu-id="4eba1-102">Entity References are Preserved</span></span>
<span data-ttu-id="4eba1-103">Quando a referência de entidade não é expandida, mas é preservada, o modelo de objeto (DOM) de documento XML cria um nó de **XmlEntityReference** quando encontra uma referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="4eba1-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="4eba1-104">Usando o seguinte XML,</span><span class="sxs-lookup"><span data-stu-id="4eba1-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="4eba1-105">o DOM cria um nó **XmlEntityReference** quando encontra a referência `&publisher;`.</span><span class="sxs-lookup"><span data-stu-id="4eba1-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="4eba1-106">**XmlEntityReference** contém os nós filho copiados de conteúdo na declaração de entidade.</span><span class="sxs-lookup"><span data-stu-id="4eba1-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="4eba1-107">O exemplo de código anterior contém o texto na declaração de entidade. Assim, um nó **XmlText** é criado como o nó filho do nó de referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="4eba1-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="4eba1-108">![Estrutura de árvore para referências de entidade preservadas](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="4eba1-108">![Tree structure for preserved entity references](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="4eba1-109">Estrutura de árvore para as referências de entidade que são preservadas</span><span class="sxs-lookup"><span data-stu-id="4eba1-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="4eba1-110">Os nós filho de **XmlEntityReference** são cópias de todos os nós filho criados do nó **XmlEntity** quando a declaração de entidade foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="4eba1-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4eba1-111">Os nós copiados de **XmlEntity** não são sempre cópias exatas quando colocados no nó de referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="4eba1-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="4eba1-112">Pode haver namespaces que estão no escopo no nó de referência de entidade, e que afetam a configuração final dos nós filho.</span><span class="sxs-lookup"><span data-stu-id="4eba1-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="4eba1-113">Por padrão, entidades gerais como `&abc;` são preservadas, e nós **XmlEntityReference** são sempre criados.</span><span class="sxs-lookup"><span data-stu-id="4eba1-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eba1-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="4eba1-114">See also</span></span>

- [<span data-ttu-id="4eba1-115">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="4eba1-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
