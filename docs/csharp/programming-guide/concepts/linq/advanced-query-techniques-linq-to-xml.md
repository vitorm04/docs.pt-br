---
title: "Técnicas avançadas de consulta (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 028d978e-215b-4d50-ba70-adce0659386d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5898813d5773f13fa2c969b065e5ab1412726e9e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="advanced-query-techniques-linq-to-xml-c"></a><span data-ttu-id="4c6a9-102">Técnicas avançadas de consulta (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4c6a9-102">Advanced Query Techniques (LINQ to XML) (C#)</span></span>
<span data-ttu-id="4c6a9-103">Esta seção fornece exemplos de técnicas mais avançadas de consulta do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4c6a9-103">This section provides examples of more advanced [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query techniques.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c6a9-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="4c6a9-104">In This Section</span></span>  
  
|<span data-ttu-id="4c6a9-105">Tópico</span><span class="sxs-lookup"><span data-stu-id="4c6a9-105">Topic</span></span>|<span data-ttu-id="4c6a9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c6a9-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4c6a9-107">Como unir duas coleções (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4c6a9-107">How to: Join Two Collections (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-join-two-collections-linq-to-xml.md)|<span data-ttu-id="4c6a9-108">Mostra como usar a cláusula `Join` para aproveitar relações em dados XML.</span><span class="sxs-lookup"><span data-stu-id="4c6a9-108">Shows how to use the `Join` clause to take advantage of relationships in XML data.</span></span>|  
|[<span data-ttu-id="4c6a9-109">Como criar uma hierarquia usando o agrupamento (C#)</span><span class="sxs-lookup"><span data-stu-id="4c6a9-109">How to: Create Hierarchy Using Grouping (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-hierarchy-using-grouping.md)|<span data-ttu-id="4c6a9-110">Mostra como agrupar dados e, em seguida, gerar XML baseado no agrupamento.</span><span class="sxs-lookup"><span data-stu-id="4c6a9-110">Shows how to group data, and then generate XML based on the grouping.</span></span>|  
|[<span data-ttu-id="4c6a9-111">Como consultar o LINQ to XML usando o XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="4c6a9-111">How to: Query LINQ to XML Using XPath (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-linq-to-xml-using-xpath.md)|<span data-ttu-id="4c6a9-112">Mostra como recuperar as coleções com base em consultas XPath.</span><span class="sxs-lookup"><span data-stu-id="4c6a9-112">Shows how to retrieve collections based on XPath queries.</span></span>|  
|[<span data-ttu-id="4c6a9-113">Como gravar um método do eixo LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4c6a9-113">How to: Write a LINQ to XML Axis Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md)|<span data-ttu-id="4c6a9-114">Mostra como escrever um método de eixo do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4c6a9-114">Shows how to write a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axis method.</span></span>|  
|[<span data-ttu-id="4c6a9-115">Como executar transformações de streaming de texto para XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4c6a9-115">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transformations-of-text-to-xml.md)|<span data-ttu-id="4c6a9-116">Mostra como transformar arquivos de texto muito grandes em XML mantendo um requisito pequeno de memória.</span><span class="sxs-lookup"><span data-stu-id="4c6a9-116">Shows how to transform very large text files into XML while maintaining a small memory footprint.</span></span>|  
|[<span data-ttu-id="4c6a9-117">Como listar todos os nós em uma árvore (C#)</span><span class="sxs-lookup"><span data-stu-id="4c6a9-117">How to: List All Nodes in a Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-list-all-nodes-in-a-tree.md)|<span data-ttu-id="4c6a9-118">Apresenta um método utilitário que lista todos os nós em uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="4c6a9-118">Presents a utility method that lists all nodes in an XML tree.</span></span> <span data-ttu-id="4c6a9-119">Isso é útil para depurar o código que modifica uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="4c6a9-119">This is useful for debugging code that modifies an XML tree.</span></span>|  
|[<span data-ttu-id="4c6a9-120">Como recuperar parágrafos de um documento do Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4c6a9-120">How to: Retrieve Paragraphs from an Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-paragraphs-from-an-office-open-xml-document.md)|<span data-ttu-id="4c6a9-121">Apresenta o código que abre um documento do Office Open XML, recupera os parágrafos em uma coleção de objetos XElement, o texto dos parágrafos e o estilo dos parágrafos.</span><span class="sxs-lookup"><span data-stu-id="4c6a9-121">Presents code that opens an Office Open XML Document, retrieves the paragraphs in a collection of XElement objects, the text of the paragraphs, and the style of the paragraphs.</span></span>|  
|[<span data-ttu-id="4c6a9-122">Como modificar um documento do Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4c6a9-122">How to: Modify an Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-modify-an-office-open-xml-document.md)|<span data-ttu-id="4c6a9-123">Apresenta o código que abre, modifica e salva um documento do Office Open XML.</span><span class="sxs-lookup"><span data-stu-id="4c6a9-123">Presents code that opens, modifies, and saves an Office Open XML Document.</span></span>|  
|[<span data-ttu-id="4c6a9-124">Como preencher uma árvore XML do sistema de arquivos (C#)</span><span class="sxs-lookup"><span data-stu-id="4c6a9-124">How to: Populate an XML Tree from the File System (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-an-xml-tree-from-the-file-system.md)|<span data-ttu-id="4c6a9-125">Apresenta o código que cria uma árvore XML do sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="4c6a9-125">Presents code that creates an XML tree from the file system.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c6a9-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c6a9-126">See Also</span></span>  
 [<span data-ttu-id="4c6a9-127">Consultando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4c6a9-127">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
