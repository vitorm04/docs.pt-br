---
title: funcionalidades do C# que dão suporte a LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: af7bf487ff4ed250025b946f0948c269fcc5bf09
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418570"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="66e99-102">funcionalidades do C# que dão suporte a LINQ</span><span class="sxs-lookup"><span data-stu-id="66e99-102">C# Features That Support LINQ</span></span>

<span data-ttu-id="66e99-103">A seção a seguir apresenta os novos constructos de linguagem introduzidos no C# 3.0.</span><span class="sxs-lookup"><span data-stu-id="66e99-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="66e99-104">Embora esses novos recursos tenham algum grau de utilização com consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], eles não estão limitados a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] e podem ser usados em qualquer contexto em que sejam úteis.</span><span class="sxs-lookup"><span data-stu-id="66e99-104">Although these new features are all used to a degree with [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, they are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] and can be used in any context where you find them useful.</span></span>

## <a name="query-expressions"></a><span data-ttu-id="66e99-105">Expressões de consulta</span><span class="sxs-lookup"><span data-stu-id="66e99-105">Query Expressions</span></span>

<span data-ttu-id="66e99-106">As expressões de consulta usam uma sintaxe declarativa semelhante ao SQL ou XQuery para consultar em coleções IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="66e99-106">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="66e99-107">Em tempo de compilação, a sintaxe de consulta é convertida em chamadas de método a uma implementação da [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dos métodos de extensão do operador de consulta padrão do provedor.</span><span class="sxs-lookup"><span data-stu-id="66e99-107">At compile time query syntax is converted to method calls to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="66e99-108">Os aplicativos controlam os operadores de consulta padrão que estão no escopo, especificando o namespace apropriado com uma diretiva `using`.</span><span class="sxs-lookup"><span data-stu-id="66e99-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="66e99-109">A expressão de consulta a seguir pega uma matriz de cadeias de caracteres, agrupa-os de acordo com o primeiro caractere da cadeia de caracteres e ordena os grupos.</span><span class="sxs-lookup"><span data-stu-id="66e99-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

<span data-ttu-id="66e99-110">Para obter mais informações, consulte [Expressões de Consulta LINQ](../../../linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="66e99-110">For more information, see [LINQ Query Expressions](../../../linq/index.md).</span></span>

## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="66e99-111">Variáveis tipadas implicitamente (var)</span><span class="sxs-lookup"><span data-stu-id="66e99-111">Implicitly Typed Variables (var)</span></span>

<span data-ttu-id="66e99-112">Em vez de especificar explicitamente um tipo ao declarar e inicializar uma variável, você pode usar o modificador [var](../../../language-reference/keywords/var.md) para instruir o compilador a inferir e atribuir o tipo, conforme mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="66e99-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

<span data-ttu-id="66e99-113">As variáveis declaradas como `var` são tão fortemente tipadas quanto as variáveis cujo tipo você especifica explicitamente.</span><span class="sxs-lookup"><span data-stu-id="66e99-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="66e99-114">O uso de `var` possibilita a criação de tipos anônimos, mas ele pode ser usado para quaisquer variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="66e99-114">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="66e99-115">As matrizes também podem ser declaradas com tipagem implícita.</span><span class="sxs-lookup"><span data-stu-id="66e99-115">Arrays can also be declared with implicit typing.</span></span>

<span data-ttu-id="66e99-116">Para obter mais informações, consulte [Variáveis locais de tipo implícito](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="66e99-116">For more information, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

## <a name="object-and-collection-initializers"></a><span data-ttu-id="66e99-117">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="66e99-117">Object and Collection Initializers</span></span>

<span data-ttu-id="66e99-118">Os inicializadores de objeto e de coleção possibilitam a inicialização de objetos sem chamar explicitamente um construtor para o objeto.</span><span class="sxs-lookup"><span data-stu-id="66e99-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="66e99-119">Os inicializadores normalmente são usados em expressões de consulta quando projetam os dados de origem em um novo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="66e99-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="66e99-120">Supondo uma classe chamada `Customer` com propriedades públicas `Name` e `Phone`, o inicializador de objeto pode ser usado como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="66e99-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

<span data-ttu-id="66e99-121">Continuando com a nossa classe `Customer`, suponha que haja uma fonte de dados chamada `IncomingOrders` e que, para cada ordem com um grande `OrderSize`, desejamos criar um novo `Customer` com base fora dessa ordem.</span><span class="sxs-lookup"><span data-stu-id="66e99-121">Continuing with our `Customer` class, assume that there is a data source called `IncomingOrders`, and that for each order with a large `OrderSize`, we would like to create a new `Customer` based off of that order.</span></span> <span data-ttu-id="66e99-122">Uma consulta LINQ pode ser executada nessa fonte de dados e usar a inicialização do objeto para preencher uma coleção:</span><span class="sxs-lookup"><span data-stu-id="66e99-122">A LINQ query can be executed on this data source and use object initialization to fill a collection:</span></span>

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

<span data-ttu-id="66e99-123">A fonte de dados pode ter mais propriedades escondidas do que a classe `Customer`, como `OrderSize`, mas com a inicialização do objeto, os dados retornados da consulta são moldados no tipo de dados desejado; escolhemos os dados que são relevantes para nossa classe.</span><span class="sxs-lookup"><span data-stu-id="66e99-123">The data source may have more properties lying under the hood than the `Customer` class such as `OrderSize`, but with object initialization, the data returned from the query is molded into the desired data type; we choose the data that is relevant to our class.</span></span> <span data-ttu-id="66e99-124">Consequentemente, agora temos um `IEnumerable` preenchido com os novos `Customer`s que queríamos.</span><span class="sxs-lookup"><span data-stu-id="66e99-124">As a result, we now have an `IEnumerable` filled with the new `Customer`s we wanted.</span></span> <span data-ttu-id="66e99-125">O trecho acima também pode ser escrito na sintaxe de método do LINQ:</span><span class="sxs-lookup"><span data-stu-id="66e99-125">The above can also be written in LINQ's method syntax:</span></span>

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

<span data-ttu-id="66e99-126">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="66e99-126">For more information, see:</span></span>

- [<span data-ttu-id="66e99-127">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="66e99-127">Object and Collection Initializers</span></span>](../../classes-and-structs/object-and-collection-initializers.md)

- [<span data-ttu-id="66e99-128">Sintaxe de Expressão de Consulta para Operadores de Consulta Padrão</span><span class="sxs-lookup"><span data-stu-id="66e99-128">Query Expression Syntax for Standard Query Operators</span></span>](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a><span data-ttu-id="66e99-129">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="66e99-129">Anonymous Types</span></span>

<span data-ttu-id="66e99-130">Um tipo anônimo é construído pelo compilador e o nome do tipo só fica disponível para o compilador.</span><span class="sxs-lookup"><span data-stu-id="66e99-130">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="66e99-131">Os tipos anônimos fornecem uma maneira conveniente de agrupar um conjunto de propriedades temporariamente em um resultado de consulta, sem a necessidade de definir um tipo nomeado separado.</span><span class="sxs-lookup"><span data-stu-id="66e99-131">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="66e99-132">Os tipos anônimos são inicializados com uma nova expressão e um inicializador de objeto, como mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="66e99-132">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

<span data-ttu-id="66e99-133">Para obter mais informações, consulte [Tipos anônimos](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="66e99-133">For more information, see [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>

## <a name="extension-methods"></a><span data-ttu-id="66e99-134">Métodos de extensão</span><span class="sxs-lookup"><span data-stu-id="66e99-134">Extension Methods</span></span>

<span data-ttu-id="66e99-135">Um método de extensão é um método estático que pode ser associado a um tipo, para que ele possa ser chamado como se fosse um método de instância no tipo.</span><span class="sxs-lookup"><span data-stu-id="66e99-135">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="66e99-136">Esse recurso permite que você, na verdade, "adicione" novos métodos a tipos existentes sem realmente modificá-los.</span><span class="sxs-lookup"><span data-stu-id="66e99-136">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="66e99-137">Os operadores de consulta padrão são um conjunto de métodos de extensão que fornecem a funcionalidade de consulta da [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para qualquer tipo que implementa a <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="66e99-137">The standard query operators are a set of extension methods that provide [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

<span data-ttu-id="66e99-138">Para obter mais informações, consulte [Métodos de extensão](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="66e99-138">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="66e99-139">Expressões lambda</span><span class="sxs-lookup"><span data-stu-id="66e99-139">Lambda Expressions</span></span>

<span data-ttu-id="66e99-140">Uma expressão lambda é uma função embutida que usa o operador => para separar os parâmetros de entrada do corpo da função e podem ser convertidos em um delegado ou uma árvore de expressão, em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="66e99-140">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="66e99-141">Na programação [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], você encontrará as expressões lambda ao fazer chamadas de método diretas aos operadores de consulta padrão.</span><span class="sxs-lookup"><span data-stu-id="66e99-141">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>

<span data-ttu-id="66e99-142">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="66e99-142">For more information, see:</span></span>

- [<span data-ttu-id="66e99-143">Funções Anônimas</span><span class="sxs-lookup"><span data-stu-id="66e99-143">Anonymous Functions</span></span>](../../statements-expressions-operators/anonymous-functions.md)

- [<span data-ttu-id="66e99-144">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="66e99-144">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)

- [<span data-ttu-id="66e99-145">Árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="66e99-145">Expression Trees (C#)</span></span>](../expression-trees/index.md)

## <a name="see-also"></a><span data-ttu-id="66e99-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66e99-146">See also</span></span>

- [<span data-ttu-id="66e99-147">LINQ (consulta integrada à linguagem) (C#)</span><span class="sxs-lookup"><span data-stu-id="66e99-147">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
