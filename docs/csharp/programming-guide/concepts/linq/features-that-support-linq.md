---
title: "funcionalidades do C# que dão suporte a LINQ"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 01db44482ee3230d15af5ce8e0373fb15a769609
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="1124c-102">funcionalidades do C# que dão suporte a LINQ</span><span class="sxs-lookup"><span data-stu-id="1124c-102">C# Features That Support LINQ</span></span>
<span data-ttu-id="1124c-103">A seção a seguir apresenta os novos constructos de linguagem introduzidos no C# 3.0.</span><span class="sxs-lookup"><span data-stu-id="1124c-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="1124c-104">Embora esses novos recursos tenham algum grau de utilização com consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], eles não estão limitados a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] e podem ser usados em qualquer contexto em que sejam úteis.</span><span class="sxs-lookup"><span data-stu-id="1124c-104">Although these new features are all used to a degree with [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, they are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] and can be used in any context where you find them useful.</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="1124c-105">Expressões de consulta</span><span class="sxs-lookup"><span data-stu-id="1124c-105">Query Expressions</span></span>  
 <span data-ttu-id="1124c-106">As expressões de consultas usam uma sintaxe declarativa semelhante ao SQL ou XQuery para consultar em coleções IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="1124c-106">Queries expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="1124c-107">Em tempo de compilação, a sintaxe de consulta é convertida em chamadas de método a uma implementação da [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dos métodos de extensão do operador de consulta padrão do provedor.</span><span class="sxs-lookup"><span data-stu-id="1124c-107">At compile time query syntax is converted to method calls to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="1124c-108">Os aplicativos controlam os operadores de consulta padrão que estão no escopo, especificando o namespace apropriado com uma diretiva `using`.</span><span class="sxs-lookup"><span data-stu-id="1124c-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="1124c-109">A expressão de consulta a seguir pega uma matriz de cadeias de caracteres, agrupa-os de acordo com o primeiro caractere da cadeia de caracteres e ordena os grupos.</span><span class="sxs-lookup"><span data-stu-id="1124c-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 <span data-ttu-id="1124c-110">Para obter mais informações, consulte [Expressões de Consulta LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span><span class="sxs-lookup"><span data-stu-id="1124c-110">For more information, see [LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span></span>  
  
## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="1124c-111">Variáveis tipadas implicitamente (var)</span><span class="sxs-lookup"><span data-stu-id="1124c-111">Implicitly Typed Variables (var)</span></span>  
 <span data-ttu-id="1124c-112">Em vez de especificar explicitamente um tipo ao declarar e inicializar uma variável, você pode usar o modificador [var](../../../../csharp/language-reference/keywords/var.md) para instruir o compilador a inferir e atribuir o tipo, conforme mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="1124c-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../../csharp/language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 <span data-ttu-id="1124c-113">As variáveis declaradas como `var` são tão fortemente tipadas quanto as variáveis cujo tipo você especifica explicitamente.</span><span class="sxs-lookup"><span data-stu-id="1124c-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="1124c-114">O uso de `var` possibilita a criação de tipos anônimos, mas ele pode ser usado para qualquer variável local.</span><span class="sxs-lookup"><span data-stu-id="1124c-114">The use of `var` makes it possible to create anonymous types, but it can be used for any local variable.</span></span> <span data-ttu-id="1124c-115">As matrizes também podem ser declaradas com tipagem implícita.</span><span class="sxs-lookup"><span data-stu-id="1124c-115">Arrays can also be declared with implicit typing.</span></span>  
  
 <span data-ttu-id="1124c-116">Para obter mais informações, consulte [Variáveis Locais de Tipo Implícito](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="1124c-116">For more information, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="object-and-collection-initializers"></a><span data-ttu-id="1124c-117">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="1124c-117">Object and Collection Initializers</span></span>  
 <span data-ttu-id="1124c-118">Os inicializadores de objeto e de coleção possibilitam a inicialização de objetos sem chamar explicitamente um construtor para o objeto.</span><span class="sxs-lookup"><span data-stu-id="1124c-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="1124c-119">Os inicializadores normalmente são usados em expressões de consulta quando projetam os dados de origem em um novo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="1124c-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="1124c-120">Supondo uma classe chamada `Customer` com propriedades públicas `Name` e `Phone`, o inicializador de objeto pode ser usado como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="1124c-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 <span data-ttu-id="1124c-121">Para obter mais informações, consulte [Inicializadores de coleção e objeto](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="1124c-121">For more information, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="1124c-122">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="1124c-122">Anonymous Types</span></span>  
 <span data-ttu-id="1124c-123">Um tipo anônimo é construído pelo compilador e o nome do tipo só fica disponível para o compilador.</span><span class="sxs-lookup"><span data-stu-id="1124c-123">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="1124c-124">Os tipos anônimos fornecem uma maneira conveniente de agrupar um conjunto de propriedades temporariamente em um resultado de consulta, sem a necessidade de definir um tipo nomeado separado.</span><span class="sxs-lookup"><span data-stu-id="1124c-124">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="1124c-125">Os tipos anônimos são inicializados com uma nova expressão e um inicializador de objeto, como mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="1124c-125">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 <span data-ttu-id="1124c-126">Para obter mais informações, consulte [Tipos Anônimos](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="1124c-126">For more information, see [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="1124c-127">Métodos de extensão</span><span class="sxs-lookup"><span data-stu-id="1124c-127">Extension Methods</span></span>  
 <span data-ttu-id="1124c-128">Um método de extensão é um método estático que pode ser associado a um tipo, para que ele possa ser chamado como se fosse um método de instância no tipo.</span><span class="sxs-lookup"><span data-stu-id="1124c-128">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="1124c-129">Esse recurso permite que você, na verdade, "adicione" novos métodos a tipos existentes sem realmente modificá-los.</span><span class="sxs-lookup"><span data-stu-id="1124c-129">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="1124c-130">Os operadores de consulta padrão são um conjunto de métodos de extensão que fornecem a funcionalidade de consulta da [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para qualquer tipo que implementa a <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="1124c-130">The standard query operators are a set of extension methods that provide [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="1124c-131">Para obter mais informações, consulte [Métodos de extensão](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="1124c-131">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="1124c-132">Expressões lambda</span><span class="sxs-lookup"><span data-stu-id="1124c-132">Lambda Expressions</span></span>  
 <span data-ttu-id="1124c-133">Uma expressão lambda é uma função embutida que usa o operador => para separar os parâmetros de entrada do corpo da função e podem ser convertidos em um delegado ou uma árvore de expressão, em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="1124c-133">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="1124c-134">Na programação [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], você encontrará as expressões lambda ao fazer chamadas de método diretas aos operadores de consulta padrão.</span><span class="sxs-lookup"><span data-stu-id="1124c-134">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>  
  
 <span data-ttu-id="1124c-135">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="1124c-135">For more information, see:</span></span>  
  
-   [<span data-ttu-id="1124c-136">Funções Anônimas</span><span class="sxs-lookup"><span data-stu-id="1124c-136">Anonymous Functions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [<span data-ttu-id="1124c-137">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="1124c-137">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [<span data-ttu-id="1124c-138">Árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="1124c-138">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
  
## <a name="auto-implemented-properties"></a><span data-ttu-id="1124c-139">Propriedades autoimplementadas</span><span class="sxs-lookup"><span data-stu-id="1124c-139">Auto-Implemented Properties</span></span>  
 <span data-ttu-id="1124c-140">As propriedades autoimplementadas tornam a declaração de propriedade mais concisa.</span><span class="sxs-lookup"><span data-stu-id="1124c-140">Auto-implemented properties make property-declaration more concise.</span></span> <span data-ttu-id="1124c-141">Quando você declarar uma propriedade, conforme mostrado no exemplo a seguir, o compilador criará um campo de suporte particular e anônimo que não é acessível, a não ser por meio das propriedades getter e setter.</span><span class="sxs-lookup"><span data-stu-id="1124c-141">When you declare a property as shown in the following example, the compiler will create a private, anonymous backing field that is not accessible except through the property getter and setter.</span></span>  
  
```  
public string Name {get; set;}  
```  
  
 <span data-ttu-id="1124c-142">Para obter mais informações, consulte [Propriedades autoimplementadas](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="1124c-142">For more information, see [Auto-Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1124c-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1124c-143">See Also</span></span>  
 [<span data-ttu-id="1124c-144">LINQ (Consulta Integrada à Linguagem) (C#)</span><span class="sxs-lookup"><span data-stu-id="1124c-144">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)

