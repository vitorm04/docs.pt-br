---
title: 'Como: Usar árvores de expressão para compilar consultas dinâmicas (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: 2f91d95f888ab98902cc300afb61c41b62e64050
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966212"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="52304-102">Como: Usar árvores de expressão para compilar consultas dinâmicas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52304-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>
<span data-ttu-id="52304-103">No LINQ, as árvores de expressão são usadas para representar consultas estruturadas que se destinam a fontes de dados que implementam <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="52304-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="52304-104">Por exemplo, o provedor LINQ implementa a interface <xref:System.Linq.IQueryable%601> para consultar repositórios de dados relacionais.</span><span class="sxs-lookup"><span data-stu-id="52304-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="52304-105">O compilador do Visual Basic compila as consultas que se destinam a essas fontes de dados no código que cria uma árvore de expressão em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="52304-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="52304-106">O provedor de consultas pode percorrer a estrutura de dados da árvore de expressão e convertê-la em uma linguagem de consulta apropriada para a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="52304-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="52304-107">As árvores de expressão também são usadas no LINQ para representar expressões lambda que são atribuídas a variáveis do tipo <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="52304-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="52304-108">Este tópico descreve como usar árvores de expressão para criar consultas LINQ dinâmicas.</span><span class="sxs-lookup"><span data-stu-id="52304-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="52304-109">As consultas dinâmicas são úteis quando as especificações de uma consulta não são conhecidas em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="52304-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="52304-110">Por exemplo, um aplicativo pode fornecer uma interface do usuário que permite ao usuário final especificar um ou mais predicados para filtrar os dados.</span><span class="sxs-lookup"><span data-stu-id="52304-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="52304-111">Para usar a LINQ para a consulta, esse tipo de aplicativo deve usar árvores de expressão para criar a consulta LINQ em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="52304-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52304-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="52304-112">Example</span></span>  
 <span data-ttu-id="52304-113">O exemplo a seguir mostra como usar árvores de expressão para construir uma consulta em uma fonte de dados `IQueryable` e, em seguida, executá-la.</span><span class="sxs-lookup"><span data-stu-id="52304-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="52304-114">O código compila uma árvore de expressão para representar a consulta a seguir:</span><span class="sxs-lookup"><span data-stu-id="52304-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 <span data-ttu-id="52304-115">Os métodos de fábrica no namespace <xref:System.Linq.Expressions> são usados para criar árvores de expressão que representam as expressões que compõem a consulta geral.</span><span class="sxs-lookup"><span data-stu-id="52304-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="52304-116">As expressões que representam as chamadas aos métodos do operador de consulta padrão, referem-se às implementações <xref:System.Linq.Queryable> dos métodos a seguir.</span><span class="sxs-lookup"><span data-stu-id="52304-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="52304-117">A árvore de expressão final é passada para a implementação de <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> do provedor da fonte de dados `IQueryable` para criar uma consulta executável do tipo `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="52304-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="52304-118">Os resultados são obtidos ao enumerar essa variável de consulta.</span><span class="sxs-lookup"><span data-stu-id="52304-118">The results are obtained by enumerating that query variable.</span></span>  
  
```vb  
' Add an Imports statement for System.Linq.Expressions.  
  
Dim companies =   
    {"Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",   
     "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",   
     "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",   
     "Blue Yonder Airlines", "Trey Research", "The Phone Company",   
     "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee"}  
  
' The IQueryable data to query.  
Dim queryableData As IQueryable(Of String) = companies.AsQueryable()  
  
' Compose the expression tree that represents the parameter to the predicate.  
Dim pe As ParameterExpression = Expression.Parameter(GetType(String), "company")  
  
' ***** Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16) *****  
' Create an expression tree that represents the expression: company.ToLower() = "coho winery".  
Dim left As Expression = Expression.Call(pe, GetType(String).GetMethod("ToLower", System.Type.EmptyTypes))  
Dim right As Expression = Expression.Constant("coho winery")  
Dim e1 As Expression = Expression.Equal(left, right)  
  
' Create an expression tree that represents the expression: company.Length > 16.  
left = Expression.Property(pe, GetType(String).GetProperty("Length"))  
right = Expression.Constant(16, GetType(Integer))  
Dim e2 As Expression = Expression.GreaterThan(left, right)  
  
' Combine the expressions to create an expression tree that represents the  
' expression: company.ToLower() = "coho winery" OrElse company.Length > 16).  
Dim predicateBody As Expression = Expression.OrElse(e1, e2)  
  
' Create an expression tree that represents the expression:  
' queryableData.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16)  
Dim whereCallExpression As MethodCallExpression = Expression.Call(   
        GetType(Queryable),   
        "Where",   
        New Type() {queryableData.ElementType},   
        queryableData.Expression,   
        Expression.Lambda(Of Func(Of String, Boolean))(predicateBody, New ParameterExpression() {pe}))  
' ***** End Where *****  
  
' ***** OrderBy(Function(company) company) *****  
' Create an expression tree that represents the expression:  
' whereCallExpression.OrderBy(Function(company) company)  
Dim orderByCallExpression As MethodCallExpression = Expression.Call(   
        GetType(Queryable),   
        "OrderBy",   
        New Type() {queryableData.ElementType, queryableData.ElementType},   
        whereCallExpression,   
        Expression.Lambda(Of Func(Of String, String))(pe, New ParameterExpression() {pe}))  
' ***** End OrderBy *****  
  
' Create an executable query from the expression tree.  
Dim results As IQueryable(Of String) = queryableData.Provider.CreateQuery(Of String)(orderByCallExpression)  
  
' Enumerate the results.  
For Each company As String In results  
    Console.WriteLine(company)  
Next  
  
' This code produces the following output:  
'  
' Blue Yonder Airlines  
' City Power & Light  
' Coho Winery  
' Consolidated Messenger  
' Graphic Design Institute  
' Humongous Insurance  
' Lucerne Publishing  
' Northwind Traders  
' The Phone Company  
' Wide World Importers  
```  
  
 <span data-ttu-id="52304-119">Esse código usa um número fixo de expressões no predicado que é passado para o método `Queryable.Where`.</span><span class="sxs-lookup"><span data-stu-id="52304-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="52304-120">No entanto, você pode escrever um aplicativo que combina um número variável de expressões de predicado que dependam da entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="52304-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="52304-121">Você também pode variar os operadores de consulta padrão que são chamados na consulta, dependendo da entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="52304-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="52304-122">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="52304-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="52304-123">Crie um novo projeto de **Aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="52304-123">Create a new **Console Application** project.</span></span>  
  
- <span data-ttu-id="52304-124">Adicione uma referência à System.Core.dll, se ainda não foi referenciada.</span><span class="sxs-lookup"><span data-stu-id="52304-124">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
- <span data-ttu-id="52304-125">Inclua o namespace System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="52304-125">Include the System.Linq.Expressions namespace.</span></span>  
  
- <span data-ttu-id="52304-126">Copie o código do exemplo e cole-o na `Main` `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="52304-126">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52304-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52304-127">See also</span></span>

- [<span data-ttu-id="52304-128">Árvores de expressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52304-128">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="52304-129">Como: Executar árvores de expressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52304-129">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
