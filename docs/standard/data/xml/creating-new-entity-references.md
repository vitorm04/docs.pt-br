---
title: "Criando novos referências a entidades"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 76093fbe7095c2aae7caa69147f6181c292ca734
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="creating-new-entity-references"></a><span data-ttu-id="fd64e-102">Criando novos referências a entidades</span><span class="sxs-lookup"><span data-stu-id="fd64e-102">Creating New Entity References</span></span>
<span data-ttu-id="fd64e-103">O método **CreateEntityReference** cria um novo nó **XmlEntityReference**.</span><span class="sxs-lookup"><span data-stu-id="fd64e-103">The **CreateEntityReference** method creates a new **XmlEntityReference** node.</span></span> <span data-ttu-id="fd64e-104">O modelo de objeto de documento XML (DOM) parece para ver se o nome de entidade que está sendo referenciado foi declarado.</span><span class="sxs-lookup"><span data-stu-id="fd64e-104">The XML Document Object Model (DOM) looks to see if the entity name being referenced has already been declared.</span></span> <span data-ttu-id="fd64e-105">Se ele tiver sido, os nós filho do nó **XmlEntityReference** serão copiados do nó de declaração de entidade.</span><span class="sxs-lookup"><span data-stu-id="fd64e-105">If it has, the child nodes of **XmlEntityReference** node are copied from the entity declaration node.</span></span> <span data-ttu-id="fd64e-106">Se não houver nenhuma declaração de entidade que corresponde, um nó vazia de texto é anexado como o único filho do nó de referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="fd64e-106">If there is no entity declaration that matches, an empty text node is attached as the only child of the entity reference node.</span></span> <span data-ttu-id="fd64e-107">Como os nós filho do nó **XmlEntityReference** são cópias de outros nós, esses nós filhos são somente leitura e não podem ser modificados.</span><span class="sxs-lookup"><span data-stu-id="fd64e-107">Because the child nodes of the **XmlEntityReference** node are copies of other nodes, these child nodes are read-only and cannot be modified.</span></span>  
  
 <span data-ttu-id="fd64e-108">Quando os nós são copiados, pode haver namespace no escopo na referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="fd64e-108">When the nodes are copied, there may be a namespace in scope at the point of the entity reference.</span></span> <span data-ttu-id="fd64e-109">Este namespace afeta a configuração de qualquer elemento ou nós de atributo gerado.</span><span class="sxs-lookup"><span data-stu-id="fd64e-109">This namespace affects the configuration of any element or attribute nodes generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd64e-110">O DOM adiciona nós filho a **EntityReference** somente quando você insere o nó **EntityReference** no documento.</span><span class="sxs-lookup"><span data-stu-id="fd64e-110">The DOM adds child nodes to the **EntityReference** only when you insert the **EntityReference** node to the document.</span></span> <span data-ttu-id="fd64e-111">Os nós **EntityReference** recém-criados não têm nós filhos.</span><span class="sxs-lookup"><span data-stu-id="fd64e-111">Newly created **EntityReference** nodes have no child nodes.</span></span>  
  
 <span data-ttu-id="fd64e-112">Embora **XmlDataDocument** seja uma classe derivada de **XmlDocument**, **XmlDataDocument** não dá suporte à criação de referências de entidade.</span><span class="sxs-lookup"><span data-stu-id="fd64e-112">Even though the **XmlDataDocument** is a derived class of the **XmlDocument**, the **XmlDataDocument** does not support the creation of entity references.</span></span> <span data-ttu-id="fd64e-113">Isso ocorre porque os filhos de **EntityReference** são somente leitura.</span><span class="sxs-lookup"><span data-stu-id="fd64e-113">This is because **EntityReference** children are read-only.</span></span> <span data-ttu-id="fd64e-114">Os filhos de um nó **EntityReference** podem abranger mais de uma região.</span><span class="sxs-lookup"><span data-stu-id="fd64e-114">The children of an **EntityReference** node can span more than one region.</span></span> <span data-ttu-id="fd64e-115">Nesse caso, a parte de uma linha associada à região que contém uma parte de **EntityReference** será somente leitura.</span><span class="sxs-lookup"><span data-stu-id="fd64e-115">In this case, part of a row associated with the region that contains a part of an **EntityReference** will be read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd64e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd64e-116">See Also</span></span>  
 [<span data-ttu-id="fd64e-117">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="fd64e-117">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
