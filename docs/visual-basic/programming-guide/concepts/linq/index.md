---
title: "LINQ (consulta integrada à linguagem) (Visual Basic)"
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
ms.assetid: a99371f7-097c-49a0-b62b-0e31c34aad0e
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eca96e5d9be109bf5b8a9eff1bdf289b5b16ac06
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="language-integrated-query-linq-visual-basic"></a><span data-ttu-id="10b2a-102">LINQ (consulta integrada à linguagem) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10b2a-102">Language-Integrated Query (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="10b2a-103">O LINQ é um conjunto de recursos que estende os recursos avançados de consulta à sintaxe das linguagens do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="10b2a-103">LINQ is a set of features that extends powerful query capabilities to the language syntax of Visual Basic.</span></span> <span data-ttu-id="10b2a-104">O LINQ apresenta padrões com aprendizado facilitado para consultar e atualizar dados, e a tecnologia pode ser estendida para dar suporte a, potencialmente, qualquer tipo de armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="10b2a-104">LINQ introduces standard, easily-learned patterns for querying and updating data, and the technology can be extended to support potentially any kind of data store.</span></span>  <span data-ttu-id="10b2a-105">O NET Framework inclui assemblies de provedor LINQ que permitem o uso do LINQ com coleções do .NET Framework, bancos de dados do SQL Server, conjuntos de dados ADO.NET e documentos XML.</span><span class="sxs-lookup"><span data-stu-id="10b2a-105">The .NET Framework includes LINQ provider assemblies that enable the use of LINQ with .NET Framework collections, SQL Server databases, ADO.NET Datasets, and XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="10b2a-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="10b2a-106">In This Section</span></span>  
 [<span data-ttu-id="10b2a-107">Introdução ao LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10b2a-107">Introduction to LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 <span data-ttu-id="10b2a-108">Fornece uma introdução geral dos tipos de aplicativos que você pode escrever e dos tipos de problemas que você pode resolver com consultas do LINQ.</span><span class="sxs-lookup"><span data-stu-id="10b2a-108">Provides a general introduction to the kinds of applications that you can write and the kinds of problems that you can solve with LINQ queries.</span></span>  
  
 [<span data-ttu-id="10b2a-109">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10b2a-109">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 <span data-ttu-id="10b2a-110">Descreve os fatos básicos que você deve saber para entender a documentação do Visual Basic e exemplos.</span><span class="sxs-lookup"><span data-stu-id="10b2a-110">Describes the basic facts you should know in order to understand the Visual Basic documentation and samples.</span></span>  
  
 [<span data-ttu-id="10b2a-111">Suporte do Visual Studio IDE e ferramentas para LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10b2a-111">Visual Studio IDE and Tools Support for LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/visual-studio-ide-and-tools-support-for-linq.md)  
 <span data-ttu-id="10b2a-112">Descreve o Object Relational Designer do Visual Studio, suporte do depurador para consultas e outros recursos do IDE relacionados ao LINQ.</span><span class="sxs-lookup"><span data-stu-id="10b2a-112">Describes Visual Studio's Object Relational Designer, debugger support for queries, and other IDE features related to LINQ.</span></span>  
  
 [<span data-ttu-id="10b2a-113">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10b2a-113">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="10b2a-114">Fornece uma introdução aos operadores de consulta padrão.</span><span class="sxs-lookup"><span data-stu-id="10b2a-114">Provides an introduction to the standard query operators.</span></span> <span data-ttu-id="10b2a-115">Ele também fornece links para tópicos que contêm mais informações sobre cada tipo de operação de consulta.</span><span class="sxs-lookup"><span data-stu-id="10b2a-115">It also provides links to topics that have more information about each type of query operation.</span></span>  
  
 [<span data-ttu-id="10b2a-116">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10b2a-116">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 <span data-ttu-id="10b2a-117">Inclui links para tópicos que explicam como usar o LINQ to Objects para acessar estruturas de dados na memória.</span><span class="sxs-lookup"><span data-stu-id="10b2a-117">Includes links to topics that explain how to use LINQ to Objects to access in-memory data structures,</span></span>  
  
 [<span data-ttu-id="10b2a-118">LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10b2a-118">LINQ to XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
 <span data-ttu-id="10b2a-119">Inclui links para tópicos que explicam como usar o LINQ to XML, o qual fornece os recursos de modificação de documentos na memória do DOM (Modelo de Objeto do Documento) e dão suporte a expressões de consulta do LINQ.</span><span class="sxs-lookup"><span data-stu-id="10b2a-119">Includes links to topics that explain how to use LINQ to XML, which provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports LINQ query expressions.</span></span>  
  
 [<span data-ttu-id="10b2a-120">LINQ to ADO.NET (página do portal)</span><span class="sxs-lookup"><span data-stu-id="10b2a-120">LINQ to ADO.NET (Portal Page)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-adonet-portal-page.md)  
 <span data-ttu-id="10b2a-121">Fornece um ponto de entrada para a documentação sobre LINQ to DataSet, LINQ to SQL e LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="10b2a-121">Provides an entry point for documentation about LINQ to DataSet, LINQ to SQL, and LINQ to Entities.</span></span> <span data-ttu-id="10b2a-122">O LINQ to DataSet permite que você crie recursos mais sofisticados de consulta no <xref:System.Data.DataSet> usando a mesma funcionalidade de consultas que está disponível para outras fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="10b2a-122">LINQ to DataSet enables you to build richer query capabilities into <xref:System.Data.DataSet> by using the same query functionality that is available for other data sources.</span></span> <span data-ttu-id="10b2a-123">O LINQ to SQL fornece uma infraestrutura em tempo de execução para gerenciar dados relacionais como objetos.</span><span class="sxs-lookup"><span data-stu-id="10b2a-123">LINQ to SQL provides a run-time infrastructure for managing relational data as objects.</span></span> <span data-ttu-id="10b2a-124">O LINQ to Entities permite que os desenvolvedores escrevam consultas no modelo conceitual de Entity Framework usando C #.</span><span class="sxs-lookup"><span data-stu-id="10b2a-124">LINQ to Entities enables developers to write queries against the Entity Framework conceptual model by using C#.</span></span>  
  
 [<span data-ttu-id="10b2a-125">Habilitando uma fonte de dados para consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="10b2a-125">Enabling a Data Source for LINQ Querying</span></span>](../../../../visual-basic/programming-guide/concepts/linq/enabling-a-data-source-for-linq-querying.md)  
 <span data-ttu-id="10b2a-126">Fornece uma introdução aos provedores LINQ personalizados, a árvores de expressões de LINQ e a outras formas de estender o LINQ.</span><span class="sxs-lookup"><span data-stu-id="10b2a-126">Provides an introduction to custom LINQ providers, LINQ expression trees, and other ways to extend LINQ.</span></span>

