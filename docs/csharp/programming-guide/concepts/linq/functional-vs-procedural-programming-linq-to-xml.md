---
title: "Programação funcional versus procedural (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b6aa8ce45afdb68f7ff544b8c8f2f5e1e4a79533
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="a400d-102">Programação funcional versus procedural (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a400d-102">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="a400d-103">Há vários tipos de aplicativos XML:</span><span class="sxs-lookup"><span data-stu-id="a400d-103">There are various types of XML applications:</span></span>  
  
-   <span data-ttu-id="a400d-104">Alguns aplicativos utilizam documentos XML de origem e geram novos documentos XML que estão em um formato diferente do que os documentos de origem.</span><span class="sxs-lookup"><span data-stu-id="a400d-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
-   <span data-ttu-id="a400d-105">Alguns aplicativos utilizam documentos XML de origem e produzem documentos de resultado em um formato totalmente diferente, como arquivos de texto HTML ou CSV.</span><span class="sxs-lookup"><span data-stu-id="a400d-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
-   <span data-ttu-id="a400d-106">Alguns aplicativos utilizam documentos XML de origem e inserem registros em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a400d-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
-   <span data-ttu-id="a400d-107">Alguns aplicativos utilizam dados de outra origem, como um banco de dados e criam documentos XML a partir deles.</span><span class="sxs-lookup"><span data-stu-id="a400d-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="a400d-108">Esses não são todos os tipos de aplicativos XML, mas são um conjunto representativo de tipos de funcionalidade que um programador XML tem que implementar.</span><span class="sxs-lookup"><span data-stu-id="a400d-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="a400d-109">Com todos esses tipos de aplicativos, há duas abordagens contrastantes que um desenvolvedor pode utilizar:</span><span class="sxs-lookup"><span data-stu-id="a400d-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
-   <span data-ttu-id="a400d-110">Construção funcional usando uma abordagem declarativa.</span><span class="sxs-lookup"><span data-stu-id="a400d-110">Functional construction using a declarative approach.</span></span>  
  
-   <span data-ttu-id="a400d-111">Modificação da árvore XML na memória usando código procedural.</span><span class="sxs-lookup"><span data-stu-id="a400d-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="a400d-112">O LINQ to XML oferece suporte às duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="a400d-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="a400d-113">Ao usar a abordagem funcional, você escreve as transformações que utilizam os documentos de origem e geram documentos de resultado completamente novos com o formato desejado.</span><span class="sxs-lookup"><span data-stu-id="a400d-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="a400d-114">Ao modificar uma árvore XML no lugar, você escreve o código que percorre e navega por meio de nós em uma árvore XML na memória, inserindo, excluindo e modificando os nós conforme o necessário.</span><span class="sxs-lookup"><span data-stu-id="a400d-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="a400d-115">Você pode usar LINQ to XML com qualquer abordagem.</span><span class="sxs-lookup"><span data-stu-id="a400d-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="a400d-116">Você usa as mesmas classes e, em alguns casos, os mesmos métodos.</span><span class="sxs-lookup"><span data-stu-id="a400d-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="a400d-117">No entanto, a estrutura e as metas das duas abordagens são muito diferentes.</span><span class="sxs-lookup"><span data-stu-id="a400d-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="a400d-118">Por exemplo, em situações diferentes, uma ou outra abordagem terá geralmente melhor desempenho, e usará mais ou menos memória.</span><span class="sxs-lookup"><span data-stu-id="a400d-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="a400d-119">Além disso, uma ou outra abordagem será mais fácil de escrever e produzirá um código mais sustentável.</span><span class="sxs-lookup"><span data-stu-id="a400d-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="a400d-120">Para ver as duas abordagens contrastadas, consulte [Modificação de árvore XML na memória versus construção funcional (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a400d-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="a400d-121">Para obter um tutorial sobre como escrever transformações funcionais, consulte [Transformações funcionais puras de XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a400d-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a400d-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a400d-122">See Also</span></span>  
 [<span data-ttu-id="a400d-123">Visão geral da programação LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a400d-123">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
