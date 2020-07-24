---
title: Programação funcional vs. de procedimentos (LINQ to XML) (C#)
description: Para o processamento XML, o LINQ to XML dá suporte à modificação de árvore XML na memória e a uma construção funcional que usa uma abordagem declarativa.
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: e19f9311c56f4fe2c5e7e5f228aca6c03c6fe04d
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103654"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="ee0bc-103">Programação funcional vs. de procedimentos (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ee0bc-103">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="ee0bc-104">Há vários tipos de aplicativos XML:</span><span class="sxs-lookup"><span data-stu-id="ee0bc-104">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="ee0bc-105">Alguns aplicativos utilizam documentos XML de origem e geram novos documentos XML que estão em um formato diferente do que os documentos de origem.</span><span class="sxs-lookup"><span data-stu-id="ee0bc-105">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="ee0bc-106">Alguns aplicativos utilizam documentos XML de origem e produzem documentos de resultado em um formato totalmente diferente, como arquivos de texto HTML ou CSV.</span><span class="sxs-lookup"><span data-stu-id="ee0bc-106">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="ee0bc-107">Alguns aplicativos utilizam documentos XML de origem e inserem registros em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ee0bc-107">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="ee0bc-108">Alguns aplicativos utilizam dados de outra origem, como um banco de dados e criam documentos XML a partir deles.</span><span class="sxs-lookup"><span data-stu-id="ee0bc-108">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="ee0bc-109">Esses não são todos os tipos de aplicativos XML, mas são um conjunto representativo de tipos de funcionalidade que um programador XML tem que implementar.</span><span class="sxs-lookup"><span data-stu-id="ee0bc-109">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="ee0bc-110">Com todos esses tipos de aplicativos, há duas abordagens contrastantes que um desenvolvedor pode utilizar:</span><span class="sxs-lookup"><span data-stu-id="ee0bc-110">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="ee0bc-111">Construção funcional usando uma abordagem declarativa.</span><span class="sxs-lookup"><span data-stu-id="ee0bc-111">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="ee0bc-112">Modificação da árvore XML na memória usando código procedural.</span><span class="sxs-lookup"><span data-stu-id="ee0bc-112">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="ee0bc-113">O LINQ to XML oferece suporte às duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="ee0bc-113">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="ee0bc-114">Ao usar a abordagem funcional, você escreve as transformações que utilizam os documentos de origem e geram documentos de resultado completamente novos com o formato desejado.</span><span class="sxs-lookup"><span data-stu-id="ee0bc-114">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="ee0bc-115">Ao modificar uma árvore XML no lugar, você escreve o código que percorre e navega por meio de nós em uma árvore XML na memória, inserindo, excluindo e modificando os nós conforme o necessário.</span><span class="sxs-lookup"><span data-stu-id="ee0bc-115">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="ee0bc-116">Você pode usar LINQ to XML com qualquer abordagem.</span><span class="sxs-lookup"><span data-stu-id="ee0bc-116">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="ee0bc-117">Você usa as mesmas classes e, em alguns casos, os mesmos métodos.</span><span class="sxs-lookup"><span data-stu-id="ee0bc-117">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="ee0bc-118">No entanto, a estrutura e as metas das duas abordagens são muito diferentes.</span><span class="sxs-lookup"><span data-stu-id="ee0bc-118">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="ee0bc-119">Por exemplo, em situações diferentes, uma ou outra abordagem terá geralmente melhor desempenho, e usará mais ou menos memória.</span><span class="sxs-lookup"><span data-stu-id="ee0bc-119">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="ee0bc-120">Além disso, uma ou outra abordagem será mais fácil de escrever e produzirá um código mais sustentável.</span><span class="sxs-lookup"><span data-stu-id="ee0bc-120">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="ee0bc-121">Para ver as duas abordagens contrastadas, consulte [modificação da árvore XML na memória versus construção funcional (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ee0bc-121">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="ee0bc-122">Para obter um tutorial sobre como escrever transformações funcionais, consulte [Transformações funcionais puras de XML (C#)](./introduction-to-pure-functional-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="ee0bc-122">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](./introduction-to-pure-functional-transformations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee0bc-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="ee0bc-123">See also</span></span>

- [<span data-ttu-id="ee0bc-124">Visão geral da programação LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="ee0bc-124">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
