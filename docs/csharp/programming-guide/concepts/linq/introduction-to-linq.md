---
title: "Introdução ao LINQ (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cc654dd020d3a20b028cd6545b00de84193174ac
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="introduction-to-linq-c"></a><span data-ttu-id="27444-102">Introdução ao LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="27444-102">Introduction to LINQ (C#)</span></span>
<span data-ttu-id="27444-103">O LINQ (consulta integrada à linguagem) é uma inovação introduzida no .NET Framework versão 3.5 que preenche a lacuna entre o mundo dos objetos e o mundo dos dados.</span><span class="sxs-lookup"><span data-stu-id="27444-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="27444-104">Tradicionalmente, consultas feitas em dados são expressas como cadeias de caracteres simples sem verificação de tipo no tempo de compilação ou suporte a IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="27444-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="27444-105">Além disso, você precisará aprender uma linguagem de consulta diferente para cada tipo de fonte de dados: bancos de dados SQL, documentos XML, vários serviços Web etc.</span><span class="sxs-lookup"><span data-stu-id="27444-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="27444-106">O LINQ faz da *consulta* um constructo de linguagem de primeira classe no C#.</span><span class="sxs-lookup"><span data-stu-id="27444-106">LINQ makes a *query* a first-class language construct in C#.</span></span> <span data-ttu-id="27444-107">Você escreve consultas em coleções fortemente tipadas de objetos usando palavras-chave da linguagem e operadores familiares.</span><span class="sxs-lookup"><span data-stu-id="27444-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="27444-108">É possível escrever consultas do LINQ em C# para bancos de dados do SQL Server, documentos XML, conjuntos de dados ADO.NET e qualquer coleção de objetos que dá suporte a <xref:System.Collections.IEnumerable> ou à interface genérica <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="27444-108">You can write LINQ queries in C# for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="27444-109">O suporte ao LINQ também é fornecido por terceiros para muitos serviços Web e outras implementações de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="27444-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="27444-110">É possível usar consultas do LINQ em novos projetos ou em conjunto com consultas que não são do LINQ em projetos existentes.</span><span class="sxs-lookup"><span data-stu-id="27444-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="27444-111">O único requisito é que o projeto tenha como alvo o .NET Framework 3.5 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="27444-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="27444-112">A ilustração a seguir do Visual Studio mostra uma consulta do LINQ parcialmente concluída em um banco de dados do SQL Server no C# e no Visual Basic, com verificação de tipo completa e suporte a IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="27444-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 <span data-ttu-id="27444-113">![Consulta de LINQ com Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span><span class="sxs-lookup"><span data-stu-id="27444-113">![LINQ query with Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="27444-114">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="27444-114">Next Steps</span></span>  
 <span data-ttu-id="27444-115">Para obter mais detalhes sobre o LINQ, comece se familiarizando com alguns conceitos básicos na seção de introdução [Introdução a LINQ em C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) e, em seguida, leia a documentação da tecnologia do LINQ na qual você está interessado:</span><span class="sxs-lookup"><span data-stu-id="27444-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
-   <span data-ttu-id="27444-116">Bancos de dados do SQL Server: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="27444-116">SQL Server databases: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span></span>  
  
-   <span data-ttu-id="27444-117">Documentos XML: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="27444-117">XML documents: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="27444-118">Conjuntos de dados ADO.NET: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="27444-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
-   <span data-ttu-id="27444-119">Coleções do .NET, arquivos, cadeias de caracteres etc.: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="27444-119">.NET collections, files, strings and so on: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27444-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27444-120">See Also</span></span>  
 [<span data-ttu-id="27444-121">LINQ (Consulta Integrada à Linguagem) (C#)</span><span class="sxs-lookup"><span data-stu-id="27444-121">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
