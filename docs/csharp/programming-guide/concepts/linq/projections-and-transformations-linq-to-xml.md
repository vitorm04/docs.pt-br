---
title: "Projeções e transformações (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bb0457ab-1823-47e6-9d2d-c93c958cc913
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 81172ebb440bc2737bbe3f1de0f1dd3cf6e086c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="projections-and-transformations-linq-to-xml-c"></a><span data-ttu-id="4feee-102">Projeções e transformações (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4feee-102">Projections and Transformations (LINQ to XML) (C#)</span></span>
<span data-ttu-id="4feee-103">Esta seção fornece exemplos de projeções e transformações do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4feee-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] projections and transformations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4feee-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="4feee-104">In This Section</span></span>  
  
|<span data-ttu-id="4feee-105">Tópico</span><span class="sxs-lookup"><span data-stu-id="4feee-105">Topic</span></span>|<span data-ttu-id="4feee-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4feee-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4feee-107">Como trabalhar com dicionários usando LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4feee-107">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-work-with-dictionaries-using-linq-to-xml.md)|<span data-ttu-id="4feee-108">Mostra como dicionários a transformação XML, e como transformar XML em dicionários.</span><span class="sxs-lookup"><span data-stu-id="4feee-108">Shows how to transform dictionaries to XML, and how to transform XML into dictionaries.</span></span>|  
|[<span data-ttu-id="4feee-109">Como transformar a forma de uma árvore XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4feee-109">How to: Transform the Shape of an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-transform-the-shape-of-an-xml-tree.md)|<span data-ttu-id="4feee-110">Mostra como transformar a forma de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="4feee-110">Shows how to transform the shape of an XML document.</span></span>|  
|[<span data-ttu-id="4feee-111">Como controlar o tipo de uma projeção (C#)</span><span class="sxs-lookup"><span data-stu-id="4feee-111">How to: Control the Type of a Projection (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md)|<span data-ttu-id="4feee-112">Mostra como controlar o tipo de uma consulta de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4feee-112">Shows how to control the type of a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="4feee-113">Como projetar um novo tipo (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4feee-113">How to: Project a New Type (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-a-new-type-linq-to-xml.md)|<span data-ttu-id="4feee-114">Mostra como projetar uma coleção de um tipo definido pelo usuário de uma consulta de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4feee-114">Shows how to project a collection of a user-defined type from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="4feee-115">Como projetar um gráfico de objeto (C#)</span><span class="sxs-lookup"><span data-stu-id="4feee-115">How to: Project an Object Graph (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-an-object-graph.md)|<span data-ttu-id="4feee-116">Mostra como projetar um grafo mais complexo do objeto de uma consulta de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4feee-116">Shows how to project a more complex object graph from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="4feee-117">Como projetar um tipo anônimo (C#)</span><span class="sxs-lookup"><span data-stu-id="4feee-117">How to: Project an Anonymous Type (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-an-anonymous-type.md)|<span data-ttu-id="4feee-118">Mostra como projetar uma coleção de objetos anônimos de uma consulta de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4feee-118">Shows how to project a collection of anonymous objects from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="4feee-119">Como gerenciar arquivos de texto de XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4feee-119">How to: Generate Text Files from XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-text-files-from-xml.md)|<span data-ttu-id="4feee-120">Mostra como transformar um arquivo XML para um arquivo de texto não XML.</span><span class="sxs-lookup"><span data-stu-id="4feee-120">Shows how to transform an XML file to a non-XML text file.</span></span>|  
|[<span data-ttu-id="4feee-121">Como gerar um XML de arquivos CSV (C#)</span><span class="sxs-lookup"><span data-stu-id="4feee-121">How to: Generate XML from CSV Files (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)|<span data-ttu-id="4feee-122">Mostra como usar [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para analisar um arquivo CSV e para gerar XML deles.</span><span class="sxs-lookup"><span data-stu-id="4feee-122">Shows how to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to parse a CSV file and generate XML from it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4feee-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4feee-123">See Also</span></span>  
 [<span data-ttu-id="4feee-124">Consultando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4feee-124">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
