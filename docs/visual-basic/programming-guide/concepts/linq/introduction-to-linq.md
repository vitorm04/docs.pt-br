---
title: Introdução ao LINQ (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: 2900cade8bc4166cccb62baf4381cb926cdff5f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822256"
---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="f43f8-102">Introdução ao LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f43f8-102">Introduction to LINQ (Visual Basic)</span></span>
<span data-ttu-id="f43f8-103">O LINQ (consulta integrada à linguagem) é uma inovação introduzida no .NET Framework versão 3.5 que preenche a lacuna entre o mundo dos objetos e o mundo dos dados.</span><span class="sxs-lookup"><span data-stu-id="f43f8-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="f43f8-104">Tradicionalmente, consultas em dados são expressas como cadeias de caracteres simples sem verificação de tipo no tempo de compilação ou no suporte a IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="f43f8-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="f43f8-105">Além disso, você precisará aprender uma linguagem de consulta diferente para cada tipo de fonte de dados: Bancos de dados SQL, documentos XML, vários serviços Web e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="f43f8-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="f43f8-106">LINQ faz uma *consulta* uma construção de linguagem de primeira classe no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f43f8-106">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="f43f8-107">Você escreve consultas em coleções fortemente tipadas de objetos usando palavras-chave da linguagem e operadores familiares.</span><span class="sxs-lookup"><span data-stu-id="f43f8-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="f43f8-108">Você pode escrever consultas LINQ no Visual Basic para bancos de dados do SQL Server, documentos XML, conjuntos de dados ADO.NET e qualquer coleção de objetos que dá suporte a <xref:System.Collections.IEnumerable> ou o genérico <xref:System.Collections.Generic.IEnumerable%601> interface.</span><span class="sxs-lookup"><span data-stu-id="f43f8-108">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="f43f8-109">O suporte ao LINQ também é fornecido por terceiros para muitos serviços Web e outras implementações de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f43f8-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="f43f8-110">É possível usar consultas do LINQ em novos projetos ou em conjunto com consultas que não são do LINQ em projetos existentes.</span><span class="sxs-lookup"><span data-stu-id="f43f8-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="f43f8-111">O único requisito é que o projeto tenha como alvo o .NET Framework 3.5 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="f43f8-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="f43f8-112">A ilustração a seguir do Visual Studio mostra uma consulta do LINQ parcialmente concluída em um banco de dados do SQL Server no C# e no Visual Basic, com verificação de tipo completa e suporte a IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="f43f8-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 ![Diagrama que shwos uma consulta LINQ com Intellisense.](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a><span data-ttu-id="f43f8-114">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="f43f8-114">Next Steps</span></span>  
 <span data-ttu-id="f43f8-115">Para obter mais detalhes sobre o LINQ, comece se familiarizando com alguns conceitos básicos na seção de Introdução [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), e, em seguida, leia a documentação para a tecnologia LINQ na qual você está está interessado:</span><span class="sxs-lookup"><span data-stu-id="f43f8-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
-   <span data-ttu-id="f43f8-116">Bancos de dados do SQL Server: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="f43f8-116">SQL Server databases: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span></span>  
  
-   <span data-ttu-id="f43f8-117">Documentos XML: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="f43f8-117">XML documents: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="f43f8-118">Conjunto de dados do ADO.NET: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="f43f8-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
-   <span data-ttu-id="f43f8-119">Coleções do .NET, arquivos, cadeias de caracteres e assim por diante: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="f43f8-119">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f43f8-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f43f8-120">See also</span></span>

- [<span data-ttu-id="f43f8-121">LINQ (consulta integrada à linguagem) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f43f8-121">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
