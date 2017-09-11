---
title: "Técnicas avançadas de consulta (LINQ to XML) (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 79be877c-fadc-4dfb-9f03-426082b13656
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6983fa5b9637210bb3c56e8f693eb4f956dab0a8
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017


---
# <a name="advanced-query-techniques-linq-to-xml-visual-basic"></a><span data-ttu-id="1ffdb-102">Técnicas avançadas de consulta (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ffdb-102">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="1ffdb-103">Esta seção fornece exemplos de técnicas mais avançadas de consulta do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ffdb-103">This section provides examples of more advanced [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query techniques.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ffdb-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1ffdb-104">In This Section</span></span>  
  
|<span data-ttu-id="1ffdb-105">Tópico</span><span class="sxs-lookup"><span data-stu-id="1ffdb-105">Topic</span></span>|<span data-ttu-id="1ffdb-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ffdb-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1ffdb-107">Como: unir duas coleções (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ffdb-107">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-two-collections-linq-to-xml.md)|<span data-ttu-id="1ffdb-108">Mostra como usar a cláusula `Join` para aproveitar relações em dados XML.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-108">Shows how to use the `Join` clause to take advantage of relationships in XML data.</span></span>|  
|[<span data-ttu-id="1ffdb-109">Como: criar a hierarquia usando o agrupamento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ffdb-109">How to: Create Hierarchy Using Grouping (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-hierarchy-using-grouping.md)|<span data-ttu-id="1ffdb-110">Mostra como agrupar dados e, em seguida, gerar XML baseado no agrupamento.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-110">Shows how to group data, and then generate XML based on the grouping.</span></span>|  
|[<span data-ttu-id="1ffdb-111">Como: consulta LINQ to XML usando XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ffdb-111">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-linq-to-xml-using-xpath.md)|<span data-ttu-id="1ffdb-112">Mostra como recuperar as coleções com base em consultas XPath.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-112">Shows how to retrieve collections based on XPath queries.</span></span>|  
|[<span data-ttu-id="1ffdb-113">Como: gravar um LINQ para o método de eixo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ffdb-113">How to: Write a LINQ to XML Axis Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md)|<span data-ttu-id="1ffdb-114">Mostra como escrever um método de eixo do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ffdb-114">Shows how to write a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] axis method.</span></span>|  
|[<span data-ttu-id="1ffdb-115">Como: listar todos os nós em uma árvore (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ffdb-115">How to: List All Nodes in a Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-list-all-nodes-in-a-tree.md)|<span data-ttu-id="1ffdb-116">Apresenta um método utilitário que lista todos os nós em uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-116">Presents a utility method that lists all nodes in an XML tree.</span></span> <span data-ttu-id="1ffdb-117">Isso é útil para depurar o código que modifica uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-117">This is useful for debugging code that modifies an XML tree.</span></span>|  
|[<span data-ttu-id="1ffdb-118">Como: recuperar parágrafos de um documento do Office Open XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ffdb-118">How to: Retrieve Paragraphs from an Office Open XML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-paragraphs-from-an-office-open-xml-document.md)|<span data-ttu-id="1ffdb-119">Apresenta o código que abre um documento do Office Open XML, recupera os parágrafos em uma coleção de objetos XElement, o texto dos parágrafos e o estilo dos parágrafos.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-119">Presents code that opens an Office Open XML Document, retrieves the paragraphs in a collection of XElement objects, the text of the paragraphs, and the style of the paragraphs.</span></span>|  
|[<span data-ttu-id="1ffdb-120">Como: modificar um documento do Office Open XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ffdb-120">How to: Modify an Office Open XML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-modify-an-office-open-xml-document.md)|<span data-ttu-id="1ffdb-121">Apresenta o código que abre, modifica e salva um documento do Office Open XML.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-121">Presents code that opens, modifies, and saves an Office Open XML Document.</span></span>|  
|[<span data-ttu-id="1ffdb-122">Como: preencher uma árvore XML do sistema de arquivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ffdb-122">How to: Populate an XML Tree from the File System (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-an-xml-tree-from-the-file-system.md)|<span data-ttu-id="1ffdb-123">Apresenta o código que cria uma árvore XML do sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-123">Presents code that creates an XML tree from the file system.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ffdb-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ffdb-124">See Also</span></span>  
 [<span data-ttu-id="1ffdb-125">Consultando árvores XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ffdb-125">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
