---
title: Programação funcional vs. de procedimentos
description: O LINQ to XML dá suporte à construção funcional e técnicas de procedimento para a criação de aplicativos XML. A construção funcional é uma abordagem declarativa. As técnicas de procedimento dão suporte à modificação na memória de árvores XML.
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: a2753a31e88fd338dad61063f559431869b9e17f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551877"
---
# <a name="functional-vs-procedural-programming-linq-to-xml"></a><span data-ttu-id="dfe66-105">Programação funcional vs. de procedimentos (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="dfe66-105">Functional vs. procedural programming (LINQ to XML)</span></span>

<span data-ttu-id="dfe66-106">Há vários tipos de aplicativos XML:</span><span class="sxs-lookup"><span data-stu-id="dfe66-106">There are various types of XML applications:</span></span>

- <span data-ttu-id="dfe66-107">Alguns aplicativos utilizam documentos XML de origem e geram novos documentos XML que estão em um formato diferente do que os documentos de origem.</span><span class="sxs-lookup"><span data-stu-id="dfe66-107">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>
- <span data-ttu-id="dfe66-108">Alguns aplicativos utilizam documentos XML de origem e produzem documentos de resultado em um formato totalmente diferente, como arquivos de texto HTML ou CSV.</span><span class="sxs-lookup"><span data-stu-id="dfe66-108">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>
- <span data-ttu-id="dfe66-109">Alguns aplicativos utilizam documentos XML de origem e inserem registros em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="dfe66-109">Some applications take source XML documents, and insert records into a database.</span></span>
- <span data-ttu-id="dfe66-110">Alguns aplicativos utilizam dados de outra origem, como um banco de dados e criam documentos XML a partir deles.</span><span class="sxs-lookup"><span data-stu-id="dfe66-110">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>

<span data-ttu-id="dfe66-111">Esses não são todos os tipos de aplicativos XML, mas são um conjunto representativo dos tipos de funcionalidade que um programador de XML precisa implementar.</span><span class="sxs-lookup"><span data-stu-id="dfe66-111">These aren't all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>

<span data-ttu-id="dfe66-112">Com todos esses tipos de aplicativos, há duas abordagens contrastantes que um desenvolvedor pode utilizar:</span><span class="sxs-lookup"><span data-stu-id="dfe66-112">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>

- <span data-ttu-id="dfe66-113">Construção funcional usando uma abordagem declarativa.</span><span class="sxs-lookup"><span data-stu-id="dfe66-113">Functional construction using a declarative approach.</span></span>
- <span data-ttu-id="dfe66-114">Modificação da árvore XML na memória usando código procedural.</span><span class="sxs-lookup"><span data-stu-id="dfe66-114">In-memory XML tree modification using procedural code.</span></span>

<span data-ttu-id="dfe66-115">O LINQ to XML oferece suporte às duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="dfe66-115">LINQ to XML supports both approaches.</span></span>

<span data-ttu-id="dfe66-116">Ao usar a abordagem funcional, você escreve as transformações que utilizam os documentos de origem e geram documentos de resultado completamente novos com o formato desejado.</span><span class="sxs-lookup"><span data-stu-id="dfe66-116">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>

<span data-ttu-id="dfe66-117">Ao modificar uma árvore XML no lugar, você escreve o código que percorre e navega por meio de nós em uma árvore XML na memória, inserindo, excluindo e modificando os nós conforme o necessário.</span><span class="sxs-lookup"><span data-stu-id="dfe66-117">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>

<span data-ttu-id="dfe66-118">Você pode usar LINQ to XML com qualquer abordagem.</span><span class="sxs-lookup"><span data-stu-id="dfe66-118">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="dfe66-119">Você usa as mesmas classes e, em alguns casos, os mesmos métodos.</span><span class="sxs-lookup"><span data-stu-id="dfe66-119">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="dfe66-120">No entanto, a estrutura e os objetivos das duas abordagens são diferentes.</span><span class="sxs-lookup"><span data-stu-id="dfe66-120">However, the structure and goals of the two approaches are different.</span></span> <span data-ttu-id="dfe66-121">Por exemplo, em situações diferentes, uma ou outra abordagem terá geralmente melhor desempenho, e usará mais ou menos memória.</span><span class="sxs-lookup"><span data-stu-id="dfe66-121">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="dfe66-122">Além disso, uma ou outra abordagem será mais fácil de escrever e produzirá um código mais sustentável.</span><span class="sxs-lookup"><span data-stu-id="dfe66-122">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>

<span data-ttu-id="dfe66-123">Para ver as duas abordagens contrastadas, consulte [modificação da árvore XML na memória versus construção funcional](in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="dfe66-123">To see the two approaches contrasted, see [In-memory XML tree modification vs. functional construction](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>

<span data-ttu-id="dfe66-124">Para obter um tutorial sobre como escrever transformações funcionais, consulte [introdução às transformações funcionais puras](introduction-pure-functional-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="dfe66-124">For a tutorial on writing functional transformations, see [Introduction to pure functional transformations](introduction-pure-functional-transformations.md).</span></span>
