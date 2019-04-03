---
title: Introdução ao LINQ (C#)
ms.date: 07/20/2015
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
ms.openlocfilehash: ea17de41bbbc03158179f207aa0bc9fc9cceb863
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410687"
---
# <a name="introduction-to-linq-c"></a><span data-ttu-id="8a938-102">Introdução ao LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="8a938-102">Introduction to LINQ (C#)</span></span>
<span data-ttu-id="8a938-103">O LINQ (consulta integrada à linguagem) é uma inovação introduzida no .NET Framework versão 3.5 que preenche a lacuna entre o mundo dos objetos e o mundo dos dados.</span><span class="sxs-lookup"><span data-stu-id="8a938-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="8a938-104">Tradicionalmente, consultas em dados são expressas como cadeias de caracteres simples sem verificação de tipo no tempo de compilação ou no suporte a IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="8a938-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="8a938-105">Além disso, você precisará aprender uma linguagem de consulta diferente para cada tipo de fonte de dados: Bancos de dados SQL, documentos XML, vários serviços Web e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="8a938-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="8a938-106">O LINQ faz da *consulta* um constructo de linguagem de primeira classe no C#.</span><span class="sxs-lookup"><span data-stu-id="8a938-106">LINQ makes a *query* a first-class language construct in C#.</span></span> <span data-ttu-id="8a938-107">Você escreve consultas em coleções fortemente tipadas de objetos usando palavras-chave da linguagem e operadores familiares.</span><span class="sxs-lookup"><span data-stu-id="8a938-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="8a938-108">É possível escrever consultas do LINQ em C# para bancos de dados do SQL Server, documentos XML, conjuntos de dados ADO.NET e qualquer coleção de objetos que dá suporte a <xref:System.Collections.IEnumerable> ou à interface genérica <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="8a938-108">You can write LINQ queries in C# for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="8a938-109">O suporte ao LINQ também é fornecido por terceiros para muitos serviços Web e outras implementações de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="8a938-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="8a938-110">É possível usar consultas do LINQ em novos projetos ou em conjunto com consultas que não são do LINQ em projetos existentes.</span><span class="sxs-lookup"><span data-stu-id="8a938-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="8a938-111">O único requisito é que o projeto tenha como alvo o .NET Framework 3.5 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="8a938-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="8a938-112">A seguinte ilustração do Visual Studio mostra uma consulta LINQ parcialmente concluída em um banco de dados do SQL Server no C# e no Visual Basic, com verificação de tipo completa e suporte ao IntelliSense:</span><span class="sxs-lookup"><span data-stu-id="8a938-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support:</span></span>  
  
 ![Diagrama que mostra uma consulta LINQ com o IntelliSense.](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a><span data-ttu-id="8a938-114">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="8a938-114">Next Steps</span></span>  
 <span data-ttu-id="8a938-115">Para obter mais detalhes sobre o LINQ, comece se familiarizando com alguns conceitos básicos na seção de introdução [Introdução a LINQ em C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) e, em seguida, leia a documentação da tecnologia do LINQ na qual você está interessado:</span><span class="sxs-lookup"><span data-stu-id="8a938-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
-   <span data-ttu-id="8a938-116">Bancos de dados do SQL Server: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="8a938-116">SQL Server databases: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span></span>  
  
-   <span data-ttu-id="8a938-117">Documentos XML: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="8a938-117">XML documents: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="8a938-118">Conjunto de dados do ADO.NET: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="8a938-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
-   <span data-ttu-id="8a938-119">Coleções do .NET, arquivos, cadeias de caracteres e assim por diante: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="8a938-119">.NET collections, files, strings and so on: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a938-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a938-120">See also</span></span>

- [<span data-ttu-id="8a938-121">LINQ (consulta integrada à linguagem) (C#)</span><span class="sxs-lookup"><span data-stu-id="8a938-121">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
