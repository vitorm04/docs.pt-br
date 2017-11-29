---
title: "Variáveis locais de tipo implícito (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 26a4460acf70ff3748f12d74442f0ca568a587b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="17ec3-102">Variáveis locais de tipo implícito (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="17ec3-102">Implicitly Typed Local Variables (C# Programming Guide)</span></span>
<span data-ttu-id="17ec3-103">Variáveis locais podem ser declaradas sem fornecer um tipo explícito.</span><span class="sxs-lookup"><span data-stu-id="17ec3-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="17ec3-104">A palavra-chave `var` instrui o compilador a inferir o tipo da variável da expressão no lado direito da instrução de inicialização.</span><span class="sxs-lookup"><span data-stu-id="17ec3-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="17ec3-105">O tipo inferido pode ser um tipo interno, um tipo anônimo, um tipo definido pelo usuário ou um tipo definido na biblioteca de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="17ec3-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="17ec3-106">Para obter mais informações sobre como inicializar matrizes com `var`, consulte [Matrizes de tipo implícito](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="17ec3-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
 <span data-ttu-id="17ec3-107">Os exemplos a seguir mostram várias maneiras em que as variáveis locais podem ser declaradas com `var`:</span><span class="sxs-lookup"><span data-stu-id="17ec3-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 <span data-ttu-id="17ec3-108">É importante entender que a palavra-chave `var` não significa "variante" e não indica que a variável é vagamente tipada ou de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="17ec3-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="17ec3-109">Isso apenas significa que o compilador determina e atribui o tipo mais apropriado.</span><span class="sxs-lookup"><span data-stu-id="17ec3-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>  
  
 <span data-ttu-id="17ec3-110">A palavra-chave `var` pode ser usada nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="17ec3-110">The `var` keyword may be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="17ec3-111">Em variáveis locais (variáveis declaradas no escopo do método) conforme mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="17ec3-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>  
  
-   <span data-ttu-id="17ec3-112">Em uma instrução de inicialização [for](../../../csharp/language-reference/keywords/for.md).</span><span class="sxs-lookup"><span data-stu-id="17ec3-112">In a [for](../../../csharp/language-reference/keywords/for.md) initialization statement.</span></span>  
  
    ```  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   <span data-ttu-id="17ec3-113">Em uma instrução de inicialização [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="17ec3-113">In a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) initialization statement.</span></span>  
  
    ```  
    foreach(var item in list){...}  
    ```  
  
-   <span data-ttu-id="17ec3-114">Em uma instrução [using](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="17ec3-114">In a [using](../../../csharp/language-reference/keywords/using-statement.md) statement.</span></span>  
  
    ```  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 <span data-ttu-id="17ec3-115">Para obter mais informações, consulte [Como usar matrizes e variáveis locais de tipo implícito em uma expressão de consulta](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="17ec3-115">For more information, see [How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>  
  
## <a name="var-and-anonymous-types"></a><span data-ttu-id="17ec3-116">var e tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="17ec3-116">var and Anonymous Types</span></span>  
 <span data-ttu-id="17ec3-117">Em muitos casos, o uso de `var` é opcional e é apenas uma conveniência sintática.</span><span class="sxs-lookup"><span data-stu-id="17ec3-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="17ec3-118">No entanto, quando uma variável é inicializada com um tipo anônimo você deve declarar a variável como `var` se precisar acessar as propriedades do objeto em um momento posterior.</span><span class="sxs-lookup"><span data-stu-id="17ec3-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="17ec3-119">Esse é um cenário comum em expressões de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="17ec3-119">This is a common scenario in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="17ec3-120">Para obter mais informações, consulte [Tipos Anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="17ec3-120">For more information, see [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
 <span data-ttu-id="17ec3-121">Da perspectiva do código-fonte, um tipo anônimo não tem nome.</span><span class="sxs-lookup"><span data-stu-id="17ec3-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="17ec3-122">Portanto, se uma variável de consulta tiver sido inicializada com `var`, a única maneira de acessar as propriedades na sequência retornada será usar `var` como o tipo da variável de iteração na instrução `foreach`.</span><span class="sxs-lookup"><span data-stu-id="17ec3-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="17ec3-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="17ec3-123">Remarks</span></span>  
 <span data-ttu-id="17ec3-124">As seguintes restrições se aplicam às declarações de variável de tipo implícito:</span><span class="sxs-lookup"><span data-stu-id="17ec3-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>  
  
-   <span data-ttu-id="17ec3-125">`var` pode ser usado apenas quando uma variável local é declarada e inicializada na mesma instrução, a variável não pode ser inicializada como nula, um grupo de métodos ou uma função anônima.</span><span class="sxs-lookup"><span data-stu-id="17ec3-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>  
  
-   <span data-ttu-id="17ec3-126">`var` não pode ser usado em campos no escopo da classe.</span><span class="sxs-lookup"><span data-stu-id="17ec3-126">`var` cannot be used on fields at class scope.</span></span>  
  
-   <span data-ttu-id="17ec3-127">Variáveis declaradas usando `var` não podem ser usadas na expressão de inicialização.</span><span class="sxs-lookup"><span data-stu-id="17ec3-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="17ec3-128">Em outras palavras, essa expressão é válida `: int i = (i = 20);`, mas essa expressão gera um erro em tempo de compilação: `var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="17ec3-128">In other words, this expression is legal`: int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>  
  
-   <span data-ttu-id="17ec3-129">Diversas variáveis de tipo implícito não podem ser inicializadas na mesma instrução.</span><span class="sxs-lookup"><span data-stu-id="17ec3-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>  
  
-   <span data-ttu-id="17ec3-130">Se um tipo nomeado `var` estiver no escopo, a palavra-chave `var` será resolvida para esse nome de tipo e não será tratada como parte de uma declaração de variável local de tipo implícito.</span><span class="sxs-lookup"><span data-stu-id="17ec3-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>  
  
 <span data-ttu-id="17ec3-131">Você pode descobrir que `var` também pode ser útil com expressões de consulta em que o tipo construído exato da variável de consulta é difícil de ser determinado.</span><span class="sxs-lookup"><span data-stu-id="17ec3-131">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="17ec3-132">Isso pode ocorrer com operações de agrupamento e classificação.</span><span class="sxs-lookup"><span data-stu-id="17ec3-132">This can occur with grouping and ordering operations.</span></span>  
  
 <span data-ttu-id="17ec3-133">A palavra-chave `var` também pode ser útil quando o tipo específico da variável é enfadonho de digitar no teclado, é óbvio ou não acrescenta à legibilidade do código.</span><span class="sxs-lookup"><span data-stu-id="17ec3-133">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="17ec3-134">Um exemplo em que `var` é útil dessa maneira é com os tipos genéricos aninhados, como os usados com operações de grupo.</span><span class="sxs-lookup"><span data-stu-id="17ec3-134">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="17ec3-135">Na consulta a seguir, o tipo da variável de consulta é `IEnumerable<IGrouping<string, Student>>`.</span><span class="sxs-lookup"><span data-stu-id="17ec3-135">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="17ec3-136">Contanto que você e as outras pessoas que devem manter o código entendam isso, não há problema em usar a tipagem implícita por questões de conveniência e brevidade.</span><span class="sxs-lookup"><span data-stu-id="17ec3-136">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 <span data-ttu-id="17ec3-137">No entanto, o uso de `var` tem pelo menos o potencial de tornar seu código mais difícil de entender para outros desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="17ec3-137">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="17ec3-138">Por esse motivo, a documentação do C# geralmente usa `var` somente quando é necessário.</span><span class="sxs-lookup"><span data-stu-id="17ec3-138">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17ec3-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17ec3-139">See Also</span></span>  
 [<span data-ttu-id="17ec3-140">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="17ec3-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="17ec3-141">Matrizes de tipo implícito</span><span class="sxs-lookup"><span data-stu-id="17ec3-141">Implicitly Typed Arrays</span></span>](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)  
 [<span data-ttu-id="17ec3-142">Como usar matrizes e variáveis locais de tipo implícito em uma expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="17ec3-142">How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)  
 [<span data-ttu-id="17ec3-143">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="17ec3-143">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="17ec3-144">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="17ec3-144">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="17ec3-145">var</span><span class="sxs-lookup"><span data-stu-id="17ec3-145">var</span></span>](../../../csharp/language-reference/keywords/var.md)  
 [<span data-ttu-id="17ec3-146">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="17ec3-146">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="17ec3-147">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="17ec3-147">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="17ec3-148">for</span><span class="sxs-lookup"><span data-stu-id="17ec3-148">for</span></span>](../../../csharp/language-reference/keywords/for.md)  
 [<span data-ttu-id="17ec3-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="17ec3-149">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="17ec3-150">Instrução using</span><span class="sxs-lookup"><span data-stu-id="17ec3-150">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
