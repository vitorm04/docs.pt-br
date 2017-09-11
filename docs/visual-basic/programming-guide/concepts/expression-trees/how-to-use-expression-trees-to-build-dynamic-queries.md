---
title: "Como: usar árvores de expressão para compilar consultas dinâmicas (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8d69be78a9f3568535dffe54e21af80c6eb12f70
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="a5a13-102">Como: usar árvores de expressão para compilar consultas dinâmicas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5a13-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>
<span data-ttu-id="a5a13-103">Em LINQ, árvores de expressão são usados para representar consultas estruturadas que fontes de destino de dados que implementam <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601></span><span class="sxs-lookup"><span data-stu-id="a5a13-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="a5a13-104">Por exemplo, o provedor LINQ implementa o <xref:System.Linq.IQueryable%601>interface para consultar armazenamentos de dados relacionais.</xref:System.Linq.IQueryable%601></span><span class="sxs-lookup"><span data-stu-id="a5a13-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="a5a13-105">O compilador do Visual Basic compila as consultas que essas fontes de dados de destino no código que cria uma árvore de expressão em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a5a13-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="a5a13-106">O provedor de consultas pode percorrer a estrutura de dados de árvore de expressão e convertê-la em uma linguagem de consulta apropriada para a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="a5a13-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="a5a13-107">Árvores de expressão também são usados em LINQ para representar as expressões lambda são atribuídas a variáveis do tipo <xref:System.Linq.Expressions.Expression%601>.</xref:System.Linq.Expressions.Expression%601></span><span class="sxs-lookup"><span data-stu-id="a5a13-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="a5a13-108">Este tópico descreve como usar árvores de expressão para criar consultas LINQ dinâmicas.</span><span class="sxs-lookup"><span data-stu-id="a5a13-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="a5a13-109">Consultas dinâmicas são úteis quando as especificações de uma consulta não são conhecidas em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="a5a13-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="a5a13-110">Por exemplo, um aplicativo pode fornecer uma interface de usuário que permite ao usuário final especificar um ou mais predicados para filtrar os dados.</span><span class="sxs-lookup"><span data-stu-id="a5a13-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="a5a13-111">Para usar LINQ para consultar, esse tipo de aplicativo deve usar árvores de expressão para criar a consulta LINQ em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a5a13-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5a13-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5a13-112">Example</span></span>  
 <span data-ttu-id="a5a13-113">O exemplo a seguir mostra como usar árvores de expressão para construir uma consulta em relação a um `IQueryable` fonte de dados e, em seguida, executá-lo.</span><span class="sxs-lookup"><span data-stu-id="a5a13-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="a5a13-114">O código cria uma árvore de expressão para representar a consulta a seguir:</span><span class="sxs-lookup"><span data-stu-id="a5a13-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 <span data-ttu-id="a5a13-115">Os métodos de fábrica no <xref:System.Linq.Expressions>namespace são usados para criar árvores de expressão que representam as expressões que compõem a consulta geral.</xref:System.Linq.Expressions></span><span class="sxs-lookup"><span data-stu-id="a5a13-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="a5a13-116">As expressões que representam as chamadas para os métodos de operador de consulta padrão se referem a <xref:System.Linq.Queryable>implementações dos métodos a seguir.</xref:System.Linq.Queryable></span><span class="sxs-lookup"><span data-stu-id="a5a13-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="a5a13-117">A árvore de expressão final é passada para o <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29>implementação do provedor do `IQueryable` fonte de dados para criar uma consulta executável do tipo `IQueryable`.</xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29></span><span class="sxs-lookup"><span data-stu-id="a5a13-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="a5a13-118">Os resultados são obtidos, enumerando essa variável de consulta.</span><span class="sxs-lookup"><span data-stu-id="a5a13-118">The results are obtained by enumerating that query variable.</span></span>  
  
<span data-ttu-id="a5a13-119"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="a5a13-119"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="a5a13-120">Esse código usa um número fixo de expressões no predicado que é passado para o `Queryable.Where` método.</span><span class="sxs-lookup"><span data-stu-id="a5a13-120">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="a5a13-121">No entanto, você pode escrever um aplicativo que combina um número variável de expressões de predicado que depende da entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="a5a13-121">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="a5a13-122">Você também pode variar os operadores de consulta padrão que são chamados na consulta, dependendo da entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="a5a13-122">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a5a13-123">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a5a13-123">Compiling the Code</span></span>  
  
-   <span data-ttu-id="a5a13-124">Criar um novo **aplicativo de Console** projeto.</span><span class="sxs-lookup"><span data-stu-id="a5a13-124">Create a new **Console Application** project.</span></span>  
  
-   <span data-ttu-id="a5a13-125">Adicione uma referência a System.Core.dll se já não está referenciado.</span><span class="sxs-lookup"><span data-stu-id="a5a13-125">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="a5a13-126">Inclua o namespace System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="a5a13-126">Include the System.Linq.Expressions namespace.</span></span>  
  
-   <span data-ttu-id="a5a13-127">Copie o código do exemplo e cole-a na `Main` `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="a5a13-127">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a13-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5a13-128">See Also</span></span>  
 <span data-ttu-id="a5a13-129">[Árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span><span class="sxs-lookup"><span data-stu-id="a5a13-129">[Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span></span>  
<span data-ttu-id="a5a13-130"> [Como: executar árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)</span><span class="sxs-lookup"><span data-stu-id="a5a13-130"> [How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)</span></span>
