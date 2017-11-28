---
title: "Modificando árvores XML (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8ec47e6d-2363-4694-be46-8d5ca4d15fc9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8cf3ffabeb7c3caa5f0e3e38fb6f69551ce791b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-xml-trees-linq-to-xml-c"></a><span data-ttu-id="0f773-102">Modificando árvores XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0f773-102">Modifying XML Trees (LINQ to XML) (C#)</span></span>
<span data-ttu-id="0f773-103">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é um repositório na memória para uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="0f773-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is an in-memory store for an XML tree.</span></span> <span data-ttu-id="0f773-104">Depois que você carrega ou analisa uma árvore XML de uma fonte, o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] permite modificar essa árvore no lugar e, em seguida, serializar a árvore, talvez salvando-a em um arquivo ou enviando-a a um servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="0f773-104">After you load or parse an XML tree from a source, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] lets you modify that tree in place, and then serialize the tree, perhaps saving it to a file or sending it to a remote server.</span></span>  
  
 <span data-ttu-id="0f773-105">Quando você modifica uma árvore no lugar, você usa determinados métodos, como o <xref:System.Xml.Linq.XContainer.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f773-105">When you modify a tree in place, you use certain methods, such as <xref:System.Xml.Linq.XContainer.Add%2A>.</span></span>  
  
 <span data-ttu-id="0f773-106">No entanto, há outra abordagem, que é usar a construção funcional para gerar uma nova árvore com uma outra forma.</span><span class="sxs-lookup"><span data-stu-id="0f773-106">However, there is another approach, which is to use functional construction to generate a new tree with a different shape.</span></span> <span data-ttu-id="0f773-107">Dependendo dos tipos de alterações que você precisa fazer em sua árvore XML e do tamanho da árvore, essa abordagem pode ser mais robusta e mais fácil de desenvolver.</span><span class="sxs-lookup"><span data-stu-id="0f773-107">Depending on the types of changes that you need to make to your XML tree, and depending on the size of the tree, this approach can be more robust and easier to develop.</span></span> <span data-ttu-id="0f773-108">O primeiro tópico desta seção compara essas duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="0f773-108">The first topic in this section compares these two approaches.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f773-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="0f773-109">In This Section</span></span>  
  
|<span data-ttu-id="0f773-110">Tópico</span><span class="sxs-lookup"><span data-stu-id="0f773-110">Topic</span></span>|<span data-ttu-id="0f773-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f773-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="0f773-112">Modificação de árvore XML na memória versus Construção funcional (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0f773-112">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)|<span data-ttu-id="0f773-113">Compara a modificação de uma árvore XML na memória com a construção funcional.</span><span class="sxs-lookup"><span data-stu-id="0f773-113">Compares modifying an XML tree in memory to functional construction.</span></span>|  
|[<span data-ttu-id="0f773-114">Adicionando elementos, atributos e nós a uma árvore XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0f773-114">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|<span data-ttu-id="0f773-115">Fornece informações sobre como adicionar elementos, atributos ou nós a uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="0f773-115">Provides information about adding elements, attributes, or nodes to an XML tree.</span></span>|  
|[<span data-ttu-id="0f773-116">Modificação de elementos, atributos e nós em uma árvore XML</span><span class="sxs-lookup"><span data-stu-id="0f773-116">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|<span data-ttu-id="0f773-117">Fornece informações sobre como modificar elementos, atributos ou nós existentes.</span><span class="sxs-lookup"><span data-stu-id="0f773-117">Provides information about modifying existing elements, attributes, or nodes.</span></span>|  
|[<span data-ttu-id="0f773-118">Removendo elementos, atributos e nós de uma árvore XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0f773-118">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|<span data-ttu-id="0f773-119">Fornece informações sobre como remover elementos, atributos ou nós da árvore XML.</span><span class="sxs-lookup"><span data-stu-id="0f773-119">Provides information about removing elements, attributes, or nodes from the XML tree.</span></span>|  
|[<span data-ttu-id="0f773-120">Mantendo pares nome-valor (C#)</span><span class="sxs-lookup"><span data-stu-id="0f773-120">Maintaining Name/Value Pairs (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|<span data-ttu-id="0f773-121">Descreve como manter informações do aplicativo que são melhor mantidas como pares nome/valor, como informações de configuração ou configurações globais.</span><span class="sxs-lookup"><span data-stu-id="0f773-121">Describes how to maintain application information that is best kept as name/value pairs, such as configuration information or global settings.</span></span>|  
|[<span data-ttu-id="0f773-122">Como alterar o namespace de uma árvore XML inteira (C#)</span><span class="sxs-lookup"><span data-stu-id="0f773-122">How to: Change the Namespace for an Entire XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|<span data-ttu-id="0f773-123">Mostra como mover uma árvore XML de um namespace para outro.</span><span class="sxs-lookup"><span data-stu-id="0f773-123">Shows how to move an XML tree from one namespace into another.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f773-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f773-124">See Also</span></span>  
 [<span data-ttu-id="0f773-125">Guia de Programação (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0f773-125">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
