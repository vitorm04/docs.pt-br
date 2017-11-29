---
title: "Usando tipos anuláveis (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c8a42392bbcd2e53c54ff4c13bf98c048262ae4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="1b254-102">Usando tipos anuláveis (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="1b254-102">Using Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="1b254-103">Os tipos que permitem valor nulo podem representar todos os valores de um tipo subjacente e um valor adicional [null](../../../csharp/language-reference/keywords/null.md) .</span><span class="sxs-lookup"><span data-stu-id="1b254-103">Nullable types can represent all the values of an underlying type, and an additional [null](../../../csharp/language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="1b254-104">Os tipos que permitem valor nulo são declarados em uma das duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="1b254-104">Nullable types are declared in one of two ways:</span></span>  
  
 `System.Nullable<T> variable`  
  
 <span data-ttu-id="1b254-105">-ou-</span><span class="sxs-lookup"><span data-stu-id="1b254-105">-or-</span></span>  
  
 `T? variable`  
  
 <span data-ttu-id="1b254-106">`T` é o tipo subjacente do tipo que permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="1b254-106">`T` is the underlying type of the nullable type.</span></span> <span data-ttu-id="1b254-107">`T` pode ser qualquer tipo de valor incluindo `struct`. Ele não pode ser um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="1b254-107">`T` can be any value type including `struct`; it cannot be a reference type.</span></span>  
  
 <span data-ttu-id="1b254-108">Para um exemplo de quando é possível usar um tipo que permite valor nulo, considere como uma variável booliana comum pode ter dois valores: true e false.</span><span class="sxs-lookup"><span data-stu-id="1b254-108">For an example of when you might use a nullable type, consider how an ordinary Boolean variable can have two values: true and false.</span></span> <span data-ttu-id="1b254-109">Não há nenhum valor que significa "indefinido".</span><span class="sxs-lookup"><span data-stu-id="1b254-109">There is no value that signifies "undefined".</span></span> <span data-ttu-id="1b254-110">Em muitas aplicações em programação, principalmente nas interações de banco de dados, as variáveis podem ocorrer em um estado indefinido.</span><span class="sxs-lookup"><span data-stu-id="1b254-110">In many programming applications, most notably database interactions, variables can occur in an undefined state.</span></span> <span data-ttu-id="1b254-111">Por exemplo, um campo em um banco de dados pode conter os valores true ou false, mas também pode não conter nenhum valor.</span><span class="sxs-lookup"><span data-stu-id="1b254-111">For example, a field in a database may contain the values true or false, but it may also contain no value at all.</span></span> <span data-ttu-id="1b254-112">Da mesma forma, os tipos de referência podem ser definidos como `null` para indicar que eles não estão inicializados.</span><span class="sxs-lookup"><span data-stu-id="1b254-112">Similarly, reference types can be set to `null` to indicate that they are not initialized.</span></span>  
  
 <span data-ttu-id="1b254-113">Esta disparidade pode criar trabalho extra de programação, com variáveis adicionais usadas para armazenar informações de estado, o uso de valores especiais e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="1b254-113">This disparity can create extra programming work, with additional variables used to store state information, the use of special values, and so on.</span></span> <span data-ttu-id="1b254-114">O modificador de tipo que permite valor nulo habilita o C# a criar variáveis de tipo de valor que indicam um valor indefinido.</span><span class="sxs-lookup"><span data-stu-id="1b254-114">The nullable type modifier enables C# to create value-type variables that indicate an undefined value.</span></span>  
  
## <a name="examples-of-nullable-types"></a><span data-ttu-id="1b254-115">Exemplos de tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="1b254-115">Examples of Nullable Types</span></span>  
 <span data-ttu-id="1b254-116">Qualquer tipo de valor pode ser usado como base para um tipo que permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="1b254-116">Any value type may be used as the basis for a nullable type.</span></span> <span data-ttu-id="1b254-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1b254-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## <a name="the-members-of-nullable-types"></a><span data-ttu-id="1b254-118">Os membros de tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="1b254-118">The Members of Nullable Types</span></span>  
 <span data-ttu-id="1b254-119">Cada instância de um tipo que permite valor nulo tem duas propriedades públicas somente leitura:</span><span class="sxs-lookup"><span data-stu-id="1b254-119">Each instance of a nullable type has two public read-only properties:</span></span>  
  
-   `HasValue`  
  
     <span data-ttu-id="1b254-120">`HasValue` é do tipo `bool`.</span><span class="sxs-lookup"><span data-stu-id="1b254-120">`HasValue` is of type `bool`.</span></span> <span data-ttu-id="1b254-121">Ele é definido como `true` quando a variável contém um valor não nulo.</span><span class="sxs-lookup"><span data-stu-id="1b254-121">It is set to `true` when the variable contains a non-null value.</span></span>  
  
-   `Value`  
  
     <span data-ttu-id="1b254-122">`Value` é do mesmo tipo que o tipo subjacente.</span><span class="sxs-lookup"><span data-stu-id="1b254-122">`Value` is of the same type as the underlying type.</span></span> <span data-ttu-id="1b254-123">Se `HasValue` for `true`, `Value` conterá um valor significativo.</span><span class="sxs-lookup"><span data-stu-id="1b254-123">If `HasValue` is `true`, `Value` contains a meaningful value.</span></span> <span data-ttu-id="1b254-124">Se `HasValue` for `false`, o acesso a `Value` lançará uma <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="1b254-124">If `HasValue` is `false`, accessing `Value` will throw a <xref:System.InvalidOperationException>.</span></span>  
  
 <span data-ttu-id="1b254-125">Neste exemplo, o membro `HasValue` é usado para testar se a variável contém um valor antes de tentar exibi-la.</span><span class="sxs-lookup"><span data-stu-id="1b254-125">In this example, the `HasValue` member is used to test whether the variable contains a value before it tries to display it.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 <span data-ttu-id="1b254-126">O teste de um valor também pode ser feito como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1b254-126">Testing for a value can also be done as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## <a name="explicit-conversions"></a><span data-ttu-id="1b254-127">Conversões explícitas</span><span class="sxs-lookup"><span data-stu-id="1b254-127">Explicit Conversions</span></span>  
 <span data-ttu-id="1b254-128">Um tipo que permite valor nulo pode ser convertido em um tipo regular, explicitamente com uma conversão ou usando a propriedade `Value`.</span><span class="sxs-lookup"><span data-stu-id="1b254-128">A nullable type can be cast to a regular type, either explicitly with a cast, or by using the `Value` property.</span></span> <span data-ttu-id="1b254-129">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1b254-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 <span data-ttu-id="1b254-130">Se uma conversão definida pelo usuário for definida entre dois tipos de dados, a mesma conversão também poderá ser usada com as versões que permitem valor nulo desses tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="1b254-130">If a user-defined conversion is defined between two data types, the same conversion can also be used with the nullable versions of these data types.</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="1b254-131">Conversões implícitas</span><span class="sxs-lookup"><span data-stu-id="1b254-131">Implicit Conversions</span></span>  
 <span data-ttu-id="1b254-132">Uma variável do tipo que permite valor nulo pode ser definida como null com a palavra-chave `null`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1b254-132">A variable of nullable type can be set to null with the `null` keyword, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 <span data-ttu-id="1b254-133">A conversão de um tipo comum para um tipo que permite valor nulo, é implícita.</span><span class="sxs-lookup"><span data-stu-id="1b254-133">The conversion from an ordinary type to a nullable type, is implicit.</span></span>  
  
 [!code-csharp[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## <a name="operators"></a><span data-ttu-id="1b254-134">Operadores</span><span class="sxs-lookup"><span data-stu-id="1b254-134">Operators</span></span>  
 <span data-ttu-id="1b254-135">Os operadores unários e binários predefinidos e os operadores definidos pelo usuário que existem para tipos de valor também podem ser usados por tipos que permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="1b254-135">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="1b254-136">Esses operadores produzem um valor nulo se os operandos são nulos. Caso contrário, o operador usa o valor contido para calcular o resultado.</span><span class="sxs-lookup"><span data-stu-id="1b254-136">These operators produce a null value if the operands are null; otherwise, the operator uses the contained value to calculate the result.</span></span> <span data-ttu-id="1b254-137">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1b254-137">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 <span data-ttu-id="1b254-138">Quando você realiza comparações com tipos que permitem valor nulo, se o valor de um dos tipos que permitem valor nulo for nulo e o outro não, todas as comparações serão avaliadas como `false`, exceto `!=` (não igual).</span><span class="sxs-lookup"><span data-stu-id="1b254-138">When you perform comparisons with nullable types, if the value of one of the nullable types is null and the other is not, all comparisons evaluate to `false` except for `!=` (not equal).</span></span> <span data-ttu-id="1b254-139">É importante não presumir que porque uma comparação retorna `false`, o caso oposto retornará `true`.</span><span class="sxs-lookup"><span data-stu-id="1b254-139">It is important not to assume that because a particular comparison returns `false`, the opposite case returns `true`.</span></span> <span data-ttu-id="1b254-140">No exemplo a seguir, 10 não é maior que, menor que nem igual a null.</span><span class="sxs-lookup"><span data-stu-id="1b254-140">In the following example, 10 is not greater than, less than, nor equal to null.</span></span> <span data-ttu-id="1b254-141">Somente `num1 != num2` é avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="1b254-141">Only `num1 != num2` evaluates to `true`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 <span data-ttu-id="1b254-142">Uma comparação de igualdade de dois tipos que permitem valor nulo, em que ambos são null, é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="1b254-142">An equality comparison of two nullable types that are both null evaluates to `true`.</span></span>  
  
## <a name="the--operator"></a><span data-ttu-id="1b254-143">O operador ??</span><span class="sxs-lookup"><span data-stu-id="1b254-143">The ??</span></span> <span data-ttu-id="1b254-144">Operador</span><span class="sxs-lookup"><span data-stu-id="1b254-144">Operator</span></span>  
 <span data-ttu-id="1b254-145">O operador `??` define um valor padrão que é retornado quando um tipo que permite valor nulo é atribuído a um tipo que não permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="1b254-145">The `??` operator defines a default value that is returned when a nullable type is assigned to a non-nullable type.</span></span>  
  
 [!code-csharp[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 <span data-ttu-id="1b254-146">Este operador também pode ser usado com vários tipos que permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="1b254-146">This operator can also be used with multiple nullable types.</span></span> <span data-ttu-id="1b254-147">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1b254-147">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## <a name="the-bool-type"></a><span data-ttu-id="1b254-148">O tipo bool?</span><span class="sxs-lookup"><span data-stu-id="1b254-148">The bool? type</span></span>  
 <span data-ttu-id="1b254-149">O tipo que permite valor nulo `bool?` pode conter três valores diferentes: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) e [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="1b254-149">The `bool?` nullable type can contain three different values: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) and [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="1b254-150">Para obter informações sobre como converter de um bool? para um bool, consulte [Como converter bool? em bool com segurança](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span><span class="sxs-lookup"><span data-stu-id="1b254-150">For information about how to cast from a bool? to a bool, see [How to: Safely Cast from bool? to bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span></span>  
  
 <span data-ttu-id="1b254-151">Os boolianos que permitem valor nulo são como o tipo de variável booliana que é usada no SQL.</span><span class="sxs-lookup"><span data-stu-id="1b254-151">Nullable Booleans are like the Boolean variable type that is used in SQL.</span></span> <span data-ttu-id="1b254-152">Para garantir que os resultados produzidos pelos operadores `&` e `|` são consistentes com o tipo booliano de três valores no SQL, os seguintes operadores predefinidos são fornecidos:</span><span class="sxs-lookup"><span data-stu-id="1b254-152">To ensure that the results produced by the `&` and `|` operators are consistent with the three-valued Boolean type in SQL, the following predefined operators are provided:</span></span>  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
 <span data-ttu-id="1b254-153">Os resultados desses operadores estão listados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="1b254-153">The results of these operators are listed in the following table:</span></span>  
  
|<span data-ttu-id="1b254-154">X</span><span class="sxs-lookup"><span data-stu-id="1b254-154">X</span></span>|<span data-ttu-id="1b254-155">y</span><span class="sxs-lookup"><span data-stu-id="1b254-155">y</span></span>|<span data-ttu-id="1b254-156">x&y</span><span class="sxs-lookup"><span data-stu-id="1b254-156">x&y</span></span>|<span data-ttu-id="1b254-157">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="1b254-157">x&#124;y</span></span>|  
|-------|-------|---------|--------------|  
|<span data-ttu-id="1b254-158">true</span><span class="sxs-lookup"><span data-stu-id="1b254-158">true</span></span>|<span data-ttu-id="1b254-159">true</span><span class="sxs-lookup"><span data-stu-id="1b254-159">true</span></span>|<span data-ttu-id="1b254-160">true</span><span class="sxs-lookup"><span data-stu-id="1b254-160">true</span></span>|<span data-ttu-id="1b254-161">true</span><span class="sxs-lookup"><span data-stu-id="1b254-161">true</span></span>|  
|<span data-ttu-id="1b254-162">true</span><span class="sxs-lookup"><span data-stu-id="1b254-162">true</span></span>|<span data-ttu-id="1b254-163">false</span><span class="sxs-lookup"><span data-stu-id="1b254-163">false</span></span>|<span data-ttu-id="1b254-164">false</span><span class="sxs-lookup"><span data-stu-id="1b254-164">false</span></span>|<span data-ttu-id="1b254-165">true</span><span class="sxs-lookup"><span data-stu-id="1b254-165">true</span></span>|  
|<span data-ttu-id="1b254-166">true</span><span class="sxs-lookup"><span data-stu-id="1b254-166">true</span></span>|<span data-ttu-id="1b254-167">nulo</span><span class="sxs-lookup"><span data-stu-id="1b254-167">null</span></span>|<span data-ttu-id="1b254-168">nulo</span><span class="sxs-lookup"><span data-stu-id="1b254-168">null</span></span>|<span data-ttu-id="1b254-169">true</span><span class="sxs-lookup"><span data-stu-id="1b254-169">true</span></span>|  
|<span data-ttu-id="1b254-170">false</span><span class="sxs-lookup"><span data-stu-id="1b254-170">false</span></span>|<span data-ttu-id="1b254-171">true</span><span class="sxs-lookup"><span data-stu-id="1b254-171">true</span></span>|<span data-ttu-id="1b254-172">false</span><span class="sxs-lookup"><span data-stu-id="1b254-172">false</span></span>|<span data-ttu-id="1b254-173">true</span><span class="sxs-lookup"><span data-stu-id="1b254-173">true</span></span>|  
|<span data-ttu-id="1b254-174">false</span><span class="sxs-lookup"><span data-stu-id="1b254-174">false</span></span>|<span data-ttu-id="1b254-175">false</span><span class="sxs-lookup"><span data-stu-id="1b254-175">false</span></span>|<span data-ttu-id="1b254-176">false</span><span class="sxs-lookup"><span data-stu-id="1b254-176">false</span></span>|<span data-ttu-id="1b254-177">false</span><span class="sxs-lookup"><span data-stu-id="1b254-177">false</span></span>|  
|<span data-ttu-id="1b254-178">false</span><span class="sxs-lookup"><span data-stu-id="1b254-178">false</span></span>|<span data-ttu-id="1b254-179">nulo</span><span class="sxs-lookup"><span data-stu-id="1b254-179">null</span></span>|<span data-ttu-id="1b254-180">false</span><span class="sxs-lookup"><span data-stu-id="1b254-180">false</span></span>|<span data-ttu-id="1b254-181">nulo</span><span class="sxs-lookup"><span data-stu-id="1b254-181">null</span></span>|  
|<span data-ttu-id="1b254-182">nulo</span><span class="sxs-lookup"><span data-stu-id="1b254-182">null</span></span>|<span data-ttu-id="1b254-183">true</span><span class="sxs-lookup"><span data-stu-id="1b254-183">true</span></span>|<span data-ttu-id="1b254-184">nulo</span><span class="sxs-lookup"><span data-stu-id="1b254-184">null</span></span>|<span data-ttu-id="1b254-185">true</span><span class="sxs-lookup"><span data-stu-id="1b254-185">true</span></span>|  
|<span data-ttu-id="1b254-186">nulo</span><span class="sxs-lookup"><span data-stu-id="1b254-186">null</span></span>|<span data-ttu-id="1b254-187">false</span><span class="sxs-lookup"><span data-stu-id="1b254-187">false</span></span>|<span data-ttu-id="1b254-188">false</span><span class="sxs-lookup"><span data-stu-id="1b254-188">false</span></span>|<span data-ttu-id="1b254-189">nulo</span><span class="sxs-lookup"><span data-stu-id="1b254-189">null</span></span>|  
|<span data-ttu-id="1b254-190">nulo</span><span class="sxs-lookup"><span data-stu-id="1b254-190">null</span></span>|<span data-ttu-id="1b254-191">nulo</span><span class="sxs-lookup"><span data-stu-id="1b254-191">null</span></span>|<span data-ttu-id="1b254-192">nulo</span><span class="sxs-lookup"><span data-stu-id="1b254-192">null</span></span>|<span data-ttu-id="1b254-193">nulo</span><span class="sxs-lookup"><span data-stu-id="1b254-193">null</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1b254-194">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b254-194">See Also</span></span>  
 [<span data-ttu-id="1b254-195">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1b254-195">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1b254-196">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="1b254-196">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="1b254-197">Conversão boxing de tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="1b254-197">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
 [<span data-ttu-id="1b254-198">Tipos de Valor Anulável</span><span class="sxs-lookup"><span data-stu-id="1b254-198">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
