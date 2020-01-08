---
title: Como usar árvores de expressão para criar consultas dinâmicasC#()
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 6114ec13dd43a7df146b87dda00fba06d6eb870c
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635893"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a><span data-ttu-id="03634-102">Como usar árvores de expressão para criar consultas dinâmicasC#()</span><span class="sxs-lookup"><span data-stu-id="03634-102">How to use expression trees to build dynamic queries (C#)</span></span>
<span data-ttu-id="03634-103">No LINQ, as árvores de expressão são usadas para representar consultas estruturadas que se destinam a fontes de dados que implementam <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="03634-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="03634-104">Por exemplo, o provedor LINQ implementa a interface <xref:System.Linq.IQueryable%601> para consultar repositórios de dados relacionais.</span><span class="sxs-lookup"><span data-stu-id="03634-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="03634-105">O compilador do C# compila as consultas que se destinam a essas fontes de dados, no código que cria uma árvore de expressão em runtime.</span><span class="sxs-lookup"><span data-stu-id="03634-105">The C# compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="03634-106">O provedor de consultas pode percorrer a estrutura de dados da árvore de expressão e convertê-la em uma linguagem de consulta apropriada para a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="03634-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="03634-107">As árvores de expressão também são usadas no LINQ para representar expressões lambda que são atribuídas a variáveis do tipo <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="03634-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="03634-108">Este tópico descreve como usar árvores de expressão para criar consultas LINQ dinâmicas.</span><span class="sxs-lookup"><span data-stu-id="03634-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="03634-109">As consultas dinâmicas são úteis quando as especificações de uma consulta não são conhecidas em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="03634-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="03634-110">Por exemplo, um aplicativo pode fornecer uma interface do usuário que permite ao usuário final especificar um ou mais predicados para filtrar os dados.</span><span class="sxs-lookup"><span data-stu-id="03634-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="03634-111">Para usar a LINQ para a consulta, esse tipo de aplicativo deve usar árvores de expressão para criar a consulta LINQ em runtime.</span><span class="sxs-lookup"><span data-stu-id="03634-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03634-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="03634-112">Example</span></span>  
 <span data-ttu-id="03634-113">O exemplo a seguir mostra como usar árvores de expressão para construir uma consulta em uma fonte de dados `IQueryable` e, em seguida, executá-la.</span><span class="sxs-lookup"><span data-stu-id="03634-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="03634-114">O código compila uma árvore de expressão para representar a consulta a seguir:</span><span class="sxs-lookup"><span data-stu-id="03634-114">The code builds an expression tree to represent the following query:</span></span>  
  
 ```csharp
 companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))
          .OrderBy(company => company)
 ```
  
 <span data-ttu-id="03634-115">Os métodos de fábrica no namespace <xref:System.Linq.Expressions> são usados para criar árvores de expressão que representam as expressões que compõem a consulta geral.</span><span class="sxs-lookup"><span data-stu-id="03634-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="03634-116">As expressões que representam as chamadas aos métodos do operador de consulta padrão, referem-se às implementações <xref:System.Linq.Queryable> dos métodos a seguir.</span><span class="sxs-lookup"><span data-stu-id="03634-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="03634-117">A árvore de expressão final é passada para a implementação de <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> do provedor da fonte de dados `IQueryable` para criar uma consulta executável do tipo `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="03634-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="03634-118">Os resultados são obtidos ao enumerar essa variável de consulta.</span><span class="sxs-lookup"><span data-stu-id="03634-118">The results are obtained by enumerating that query variable.</span></span>  
  
```csharp  
// Add a using directive for System.Linq.Expressions.  
  
string[] companies = { "Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",  
                   "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",  
                   "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",  
                   "Blue Yonder Airlines", "Trey Research", "The Phone Company",  
                   "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee" };  
  
// The IQueryable data to query.  
IQueryable<String> queryableData = companies.AsQueryable<string>();  
  
// Compose the expression tree that represents the parameter to the predicate.  
ParameterExpression pe = Expression.Parameter(typeof(string), "company");  
  
// ***** Where(company => (company.ToLower() == "coho winery" || company.Length > 16)) *****  
// Create an expression tree that represents the expression 'company.ToLower() == "coho winery"'.  
Expression left = Expression.Call(pe, typeof(string).GetMethod("ToLower", System.Type.EmptyTypes));  
Expression right = Expression.Constant("coho winery");  
Expression e1 = Expression.Equal(left, right);  
  
// Create an expression tree that represents the expression 'company.Length > 16'.  
left = Expression.Property(pe, typeof(string).GetProperty("Length"));  
right = Expression.Constant(16, typeof(int));  
Expression e2 = Expression.GreaterThan(left, right);  
  
// Combine the expression trees to create an expression tree that represents the  
// expression '(company.ToLower() == "coho winery" || company.Length > 16)'.  
Expression predicateBody = Expression.OrElse(e1, e2);  
  
// Create an expression tree that represents the expression  
// 'queryableData.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))'  
MethodCallExpression whereCallExpression = Expression.Call(  
    typeof(Queryable),  
    "Where",  
    new Type[] { queryableData.ElementType },  
    queryableData.Expression,  
    Expression.Lambda<Func<string, bool>>(predicateBody, new ParameterExpression[] { pe }));  
// ***** End Where *****  
  
// ***** OrderBy(company => company) *****  
// Create an expression tree that represents the expression  
// 'whereCallExpression.OrderBy(company => company)'  
MethodCallExpression orderByCallExpression = Expression.Call(  
    typeof(Queryable),  
    "OrderBy",  
    new Type[] { queryableData.ElementType, queryableData.ElementType },  
    whereCallExpression,  
    Expression.Lambda<Func<string, string>>(pe, new ParameterExpression[] { pe }));  
// ***** End OrderBy *****  
  
// Create an executable query from the expression tree.  
IQueryable<string> results = queryableData.Provider.CreateQuery<string>(orderByCallExpression);  
  
// Enumerate the results.  
foreach (string company in results)  
    Console.WriteLine(company);  
  
/*  This code produces the following output:  
  
    Blue Yonder Airlines  
    City Power & Light  
    Coho Winery  
    Consolidated Messenger  
    Graphic Design Institute  
    Humongous Insurance  
    Lucerne Publishing  
    Northwind Traders  
    The Phone Company  
    Wide World Importers  
*/  
```  
  
 <span data-ttu-id="03634-119">Esse código usa um número fixo de expressões no predicado que é passado para o método `Queryable.Where`.</span><span class="sxs-lookup"><span data-stu-id="03634-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="03634-120">No entanto, você pode escrever um aplicativo que combina um número variável de expressões de predicado que dependam da entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="03634-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="03634-121">Você também pode variar os operadores de consulta padrão que são chamados na consulta, dependendo da entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="03634-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="03634-122">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="03634-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="03634-123">Inclua o namespace System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="03634-123">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03634-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="03634-124">See also</span></span>

- [<span data-ttu-id="03634-125">Árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="03634-125">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="03634-126">Como executar árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="03634-126">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="03634-127">Especificar filtros predicados dinamicamente em runtime</span><span class="sxs-lookup"><span data-stu-id="03634-127">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
