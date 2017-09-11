---
title: "Introdução ao LINQ (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d2c02daacc2674da31715e5fda027b97e6b7bc97
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="3371d-102">Introdução ao LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3371d-102">Introduction to LINQ (Visual Basic)</span></span>
<span data-ttu-id="3371d-103">Consulta integrada à linguagem (LINQ) é que uma inovação introduzido no .NET Framework versão 3.5 que as pontes a lacuna entre o mundo de objetos e o mundo dos dados.</span><span class="sxs-lookup"><span data-stu-id="3371d-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="3371d-104">Tradicionalmente, consultas em dados são expressos como cadeias de caracteres simples sem verificação de tipo em compilar tempo ou suporte a IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="3371d-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="3371d-105">Além disso, você terá de aprender uma linguagem de consulta diferente para cada tipo de fonte de dados: SQL bancos de dados, documentos XML, vários serviços da Web e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="3371d-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="3371d-106">LINQ faz uma *consulta* uma construção de linguagem de primeira classe no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3371d-106">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="3371d-107">Você escrever consultas em relação a coleções com rigidez de tipos de objetos usando palavras-chave e operadores familiares.</span><span class="sxs-lookup"><span data-stu-id="3371d-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="3371d-108">Você pode escrever consultas LINQ no Visual Basic para bancos de dados do SQL Server, documentos XML, Datasets ADO.NET e qualquer coleção de objetos que oferece suporte a <xref:System.Collections.IEnumerable>ou genérica <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="3371d-108">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="3371d-109">Suporte a LINQ também é fornecido por terceiros para muitos serviços da Web e outras implementações de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3371d-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="3371d-110">Você pode usar consultas LINQ em novos projetos ou junto com consultas LINQ não em projetos existentes.</span><span class="sxs-lookup"><span data-stu-id="3371d-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="3371d-111">O único requisito é que o projeto de destino do .NET Framework 3.5 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="3371d-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="3371d-112">A ilustração a seguir do Visual Studio mostra uma consulta LINQ parcialmente concluída com um banco de dados do SQL Server em c# e Visual Basic com verificação de tipo completo e suporte a IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="3371d-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 <span data-ttu-id="3371d-113">![Consulta LINQ com o Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span><span class="sxs-lookup"><span data-stu-id="3371d-113">![LINQ query with Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3371d-114">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3371d-114">Next Steps</span></span>  
 <span data-ttu-id="3371d-115">Para obter mais detalhes sobre o LINQ, comece se familiarizar com alguns conceitos básicos na seção Introdução [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), e, em seguida, leia a documentação para a tecnologia LINQ no qual você está interessado:</span><span class="sxs-lookup"><span data-stu-id="3371d-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
-   <span data-ttu-id="3371d-116">Bancos de dados do SQL Server: [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)</span><span class="sxs-lookup"><span data-stu-id="3371d-116">SQL Server databases: [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)</span></span>  
  
-   <span data-ttu-id="3371d-117">Documentos XML: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="3371d-117">XML documents: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="3371d-118">Conjuntos de dados ADO.NET: [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)</span><span class="sxs-lookup"><span data-stu-id="3371d-118">ADO.NET Datasets: [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)</span></span>  
  
-   <span data-ttu-id="3371d-119">Coleções do .NET, arquivos, cadeias de caracteres e assim por diante: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="3371d-119">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3371d-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3371d-120">See Also</span></span>  
 [<span data-ttu-id="3371d-121">Consulta integrada à linguagem (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3371d-121">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
