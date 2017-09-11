---
title: "Usando tipos anuláveis (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0721d9f60abc4e158135d6b050953b3e63ab8cb5
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="bed22-102">Usando tipos anuláveis (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="bed22-102">Using Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="bed22-103">Os tipos que permitem valor nulo podem representar todos os valores de um tipo subjacente e um valor adicional [null](../../../csharp/language-reference/keywords/null.md) .</span><span class="sxs-lookup"><span data-stu-id="bed22-103">Nullable types can represent all the values of an underlying type, and an additional [null](../../../csharp/language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="bed22-104">Os tipos que permitem valor nulo são declarados em uma das duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="bed22-104">Nullable types are declared in one of two ways:</span></span>  
  
 `System.Nullable<T> variable`  
  
 <span data-ttu-id="bed22-105">-ou-</span><span class="sxs-lookup"><span data-stu-id="bed22-105">-or-</span></span>  
  
 `T? variable`  
  
 <span data-ttu-id="bed22-106">`T` é o tipo subjacente do tipo que permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bed22-106">`T` is the underlying type of the nullable type.</span></span> <span data-ttu-id="bed22-107">`T` pode ser qualquer tipo de valor incluindo `struct`. Ele não pode ser um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="bed22-107">`T` can be any value type including `struct`; it cannot be a reference type.</span></span>  
  
 <span data-ttu-id="bed22-108">Para um exemplo de quando é possível usar um tipo que permite valor nulo, considere como uma variável booliana comum pode ter dois valores: true e false.</span><span class="sxs-lookup"><span data-stu-id="bed22-108">For an example of when you might use a nullable type, consider how an ordinary Boolean variable can have two values: true and false.</span></span> <span data-ttu-id="bed22-109">Não há nenhum valor que significa "indefinido".</span><span class="sxs-lookup"><span data-stu-id="bed22-109">There is no value that signifies "undefined".</span></span> <span data-ttu-id="bed22-110">Em muitas aplicações em programação, principalmente nas interações de banco de dados, as variáveis podem ocorrer em um estado indefinido.</span><span class="sxs-lookup"><span data-stu-id="bed22-110">In many programming applications, most notably database interactions, variables can occur in an undefined state.</span></span> <span data-ttu-id="bed22-111">Por exemplo, um campo em um banco de dados pode conter os valores true ou false, mas também pode não conter nenhum valor.</span><span class="sxs-lookup"><span data-stu-id="bed22-111">For example, a field in a database may contain the values true or false, but it may also contain no value at all.</span></span> <span data-ttu-id="bed22-112">Da mesma forma, os tipos de referência podem ser definidos como `null` para indicar que eles não estão inicializados.</span><span class="sxs-lookup"><span data-stu-id="bed22-112">Similarly, reference types can be set to `null` to indicate that they are not initialized.</span></span>  
  
 <span data-ttu-id="bed22-113">Esta disparidade pode criar trabalho extra de programação, com variáveis adicionais usadas para armazenar informações de estado, o uso de valores especiais e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="bed22-113">This disparity can create extra programming work, with additional variables used to store state information, the use of special values, and so on.</span></span> <span data-ttu-id="bed22-114">O modificador de tipo que permite valor nulo habilita o C# a criar variáveis de tipo de valor que indicam um valor indefinido.</span><span class="sxs-lookup"><span data-stu-id="bed22-114">The nullable type modifier enables C# to create value-type variables that indicate an undefined value.</span></span>  
  
## <a name="examples-of-nullable-types"></a><span data-ttu-id="bed22-115">Exemplos de tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="bed22-115">Examples of Nullable Types</span></span>  
 <span data-ttu-id="bed22-116">Qualquer tipo de valor pode ser usado como base para um tipo que permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bed22-116">Any value type may be used as the basis for a nullable type.</span></span> <span data-ttu-id="bed22-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bed22-117">For example:</span></span>  
  
 <span data-ttu-id="bed22-118">[!code-cs[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="bed22-118">[!code-cs[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]</span></span>  
  
## <a name="the-members-of-nullable-types"></a><span data-ttu-id="bed22-119">Os membros de tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="bed22-119">The Members of Nullable Types</span></span>  
 <span data-ttu-id="bed22-120">Cada instância de um tipo que permite valor nulo tem duas propriedades públicas somente leitura:</span><span class="sxs-lookup"><span data-stu-id="bed22-120">Each instance of a nullable type has two public read-only properties:</span></span>  
  
-   `HasValue`  
  
     <span data-ttu-id="bed22-121">`HasValue` é do tipo `bool`.</span><span class="sxs-lookup"><span data-stu-id="bed22-121">`HasValue` is of type `bool`.</span></span> <span data-ttu-id="bed22-122">Ele é definido como `true` quando a variável contém um valor não nulo.</span><span class="sxs-lookup"><span data-stu-id="bed22-122">It is set to `true` when the variable contains a non-null value.</span></span>  
  
-   `Value`  
  
     <span data-ttu-id="bed22-123">`Value` é do mesmo tipo que o tipo subjacente.</span><span class="sxs-lookup"><span data-stu-id="bed22-123">`Value` is of the same type as the underlying type.</span></span> <span data-ttu-id="bed22-124">Se `HasValue` for `true`, `Value` conterá um valor significativo.</span><span class="sxs-lookup"><span data-stu-id="bed22-124">If `HasValue` is `true`, `Value` contains a meaningful value.</span></span> <span data-ttu-id="bed22-125">Se `HasValue` for `false`, o acesso a `Value` lançará uma <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="bed22-125">If `HasValue` is `false`, accessing `Value` will throw a <xref:System.InvalidOperationException>.</span></span>  
  
 <span data-ttu-id="bed22-126">Neste exemplo, o membro `HasValue` é usado para testar se a variável contém um valor antes de tentar exibi-la.</span><span class="sxs-lookup"><span data-stu-id="bed22-126">In this example, the `HasValue` member is used to test whether the variable contains a value before it tries to display it.</span></span>  
  
 <span data-ttu-id="bed22-127">[!code-cs[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="bed22-127">[!code-cs[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]</span></span>  
  
 <span data-ttu-id="bed22-128">O teste de um valor também pode ser feito como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="bed22-128">Testing for a value can also be done as in the following example:</span></span>  
  
 <span data-ttu-id="bed22-129">[!code-cs[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="bed22-129">[!code-cs[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]</span></span>  
  
## <a name="explicit-conversions"></a><span data-ttu-id="bed22-130">Conversões explícitas</span><span class="sxs-lookup"><span data-stu-id="bed22-130">Explicit Conversions</span></span>  
 <span data-ttu-id="bed22-131">Um tipo que permite valor nulo pode ser convertido em um tipo regular, explicitamente com uma conversão ou usando a propriedade `Value`.</span><span class="sxs-lookup"><span data-stu-id="bed22-131">A nullable type can be cast to a regular type, either explicitly with a cast, or by using the `Value` property.</span></span> <span data-ttu-id="bed22-132">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bed22-132">For example:</span></span>  
  
 <span data-ttu-id="bed22-133">[!code-cs[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="bed22-133">[!code-cs[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]</span></span>  
  
 <span data-ttu-id="bed22-134">Se uma conversão definida pelo usuário for definida entre dois tipos de dados, a mesma conversão também poderá ser usada com as versões que permitem valor nulo desses tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="bed22-134">If a user-defined conversion is defined between two data types, the same conversion can also be used with the nullable versions of these data types.</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="bed22-135">Conversões implícitas</span><span class="sxs-lookup"><span data-stu-id="bed22-135">Implicit Conversions</span></span>  
 <span data-ttu-id="bed22-136">Uma variável do tipo que permite valor nulo pode ser definida como null com a palavra-chave `null`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="bed22-136">A variable of nullable type can be set to null with the `null` keyword, as shown in the following example:</span></span>  
  
 <span data-ttu-id="bed22-137">[!code-cs[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="bed22-137">[!code-cs[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]</span></span>  
  
 <span data-ttu-id="bed22-138">A conversão de um tipo comum para um tipo que permite valor nulo, é implícita.</span><span class="sxs-lookup"><span data-stu-id="bed22-138">The conversion from an ordinary type to a nullable type, is implicit.</span></span>  
  
 <span data-ttu-id="bed22-139">[!code-cs[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="bed22-139">[!code-cs[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]</span></span>  
  
## <a name="operators"></a><span data-ttu-id="bed22-140">Operadores</span><span class="sxs-lookup"><span data-stu-id="bed22-140">Operators</span></span>  
 <span data-ttu-id="bed22-141">Os operadores unários e binários predefinidos e os operadores definidos pelo usuário que existem para tipos de valor também podem ser usados por tipos que permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bed22-141">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="bed22-142">Esses operadores produzem um valor nulo se os operandos são nulos. Caso contrário, o operador usa o valor contido para calcular o resultado.</span><span class="sxs-lookup"><span data-stu-id="bed22-142">These operators produce a null value if the operands are null; otherwise, the operator uses the contained value to calculate the result.</span></span> <span data-ttu-id="bed22-143">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bed22-143">For example:</span></span>  
  
 <span data-ttu-id="bed22-144">[!code-cs[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="bed22-144">[!code-cs[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]</span></span>  
  
 <span data-ttu-id="bed22-145">Quando você realiza comparações com tipos que permitem valor nulo, se o valor de um dos tipos que permitem valor nulo for nulo e o outro não, todas as comparações serão avaliadas como `false`, exceto `!=` (não igual).</span><span class="sxs-lookup"><span data-stu-id="bed22-145">When you perform comparisons with nullable types, if the value of one of the nullable types is null and the other is not, all comparisons evaluate to `false` except for `!=` (not equal).</span></span> <span data-ttu-id="bed22-146">É importante não presumir que porque uma comparação retorna `false`, o caso oposto retornará `true`.</span><span class="sxs-lookup"><span data-stu-id="bed22-146">It is important not to assume that because a particular comparison returns `false`, the opposite case returns `true`.</span></span> <span data-ttu-id="bed22-147">No exemplo a seguir, 10 não é maior que, menor que nem igual a null.</span><span class="sxs-lookup"><span data-stu-id="bed22-147">In the following example, 10 is not greater than, less than, nor equal to null.</span></span> <span data-ttu-id="bed22-148">Somente `num1 != num2` é avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="bed22-148">Only `num1 != num2` evaluates to `true`.</span></span>  
  
 <span data-ttu-id="bed22-149">[!code-cs[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="bed22-149">[!code-cs[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]</span></span>  
  
 <span data-ttu-id="bed22-150">Uma comparação de igualdade de dois tipos que permitem valor nulo, em que ambos são null, é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="bed22-150">An equality comparison of two nullable types that are both null evaluates to `true`.</span></span>  
  
## <a name="the--operator"></a><span data-ttu-id="bed22-151">O operador ??</span><span class="sxs-lookup"><span data-stu-id="bed22-151">The ??</span></span> <span data-ttu-id="bed22-152">Operador</span><span class="sxs-lookup"><span data-stu-id="bed22-152">Operator</span></span>  
 <span data-ttu-id="bed22-153">O operador `??` define um valor padrão que é retornado quando um tipo que permite valor nulo é atribuído a um tipo que não permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bed22-153">The `??` operator defines a default value that is returned when a nullable type is assigned to a non-nullable type.</span></span>  
  
 <span data-ttu-id="bed22-154">[!code-cs[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="bed22-154">[!code-cs[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]</span></span>  
  
 <span data-ttu-id="bed22-155">Este operador também pode ser usado com vários tipos que permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="bed22-155">This operator can also be used with multiple nullable types.</span></span> <span data-ttu-id="bed22-156">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bed22-156">For example:</span></span>  
  
 <span data-ttu-id="bed22-157">[!code-cs[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]</span><span class="sxs-lookup"><span data-stu-id="bed22-157">[!code-cs[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]</span></span>  
  
## <a name="the-bool-type"></a><span data-ttu-id="bed22-158">O tipo bool?</span><span class="sxs-lookup"><span data-stu-id="bed22-158">The bool? type</span></span>  
 <span data-ttu-id="bed22-159">O tipo que permite valor nulo `bool?` pode conter três valores diferentes: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) e [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="bed22-159">The `bool?` nullable type can contain three different values: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) and [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="bed22-160">Para obter informações sobre como converter de um bool? para um bool, consulte [Como converter bool? em bool com segurança](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span><span class="sxs-lookup"><span data-stu-id="bed22-160">For information about how to cast from a bool? to a bool, see [How to: Safely Cast from bool? to bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span></span>  
  
 <span data-ttu-id="bed22-161">Os boolianos que permitem valor nulo são como o tipo de variável booliana que é usada no SQL.</span><span class="sxs-lookup"><span data-stu-id="bed22-161">Nullable Booleans are like the Boolean variable type that is used in SQL.</span></span> <span data-ttu-id="bed22-162">Para garantir que os resultados produzidos pelos operadores `&` e `|` são consistentes com o tipo booliano de três valores no SQL, os seguintes operadores predefinidos são fornecidos:</span><span class="sxs-lookup"><span data-stu-id="bed22-162">To ensure that the results produced by the `&` and `|` operators are consistent with the three-valued Boolean type in SQL, the following predefined operators are provided:</span></span>  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
 <span data-ttu-id="bed22-163">Os resultados desses operadores estão listados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="bed22-163">The results of these operators are listed in the following table:</span></span>  
  
|<span data-ttu-id="bed22-164">X</span><span class="sxs-lookup"><span data-stu-id="bed22-164">X</span></span>|<span data-ttu-id="bed22-165">y</span><span class="sxs-lookup"><span data-stu-id="bed22-165">y</span></span>|<span data-ttu-id="bed22-166">x&y</span><span class="sxs-lookup"><span data-stu-id="bed22-166">x&y</span></span>|<span data-ttu-id="bed22-167">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="bed22-167">x&#124;y</span></span>|  
|-------|-------|---------|--------------|  
|<span data-ttu-id="bed22-168">true</span><span class="sxs-lookup"><span data-stu-id="bed22-168">true</span></span>|<span data-ttu-id="bed22-169">true</span><span class="sxs-lookup"><span data-stu-id="bed22-169">true</span></span>|<span data-ttu-id="bed22-170">true</span><span class="sxs-lookup"><span data-stu-id="bed22-170">true</span></span>|<span data-ttu-id="bed22-171">true</span><span class="sxs-lookup"><span data-stu-id="bed22-171">true</span></span>|  
|<span data-ttu-id="bed22-172">true</span><span class="sxs-lookup"><span data-stu-id="bed22-172">true</span></span>|<span data-ttu-id="bed22-173">false</span><span class="sxs-lookup"><span data-stu-id="bed22-173">false</span></span>|<span data-ttu-id="bed22-174">false</span><span class="sxs-lookup"><span data-stu-id="bed22-174">false</span></span>|<span data-ttu-id="bed22-175">true</span><span class="sxs-lookup"><span data-stu-id="bed22-175">true</span></span>|  
|<span data-ttu-id="bed22-176">true</span><span class="sxs-lookup"><span data-stu-id="bed22-176">true</span></span>|<span data-ttu-id="bed22-177">nulo</span><span class="sxs-lookup"><span data-stu-id="bed22-177">null</span></span>|<span data-ttu-id="bed22-178">nulo</span><span class="sxs-lookup"><span data-stu-id="bed22-178">null</span></span>|<span data-ttu-id="bed22-179">true</span><span class="sxs-lookup"><span data-stu-id="bed22-179">true</span></span>|  
|<span data-ttu-id="bed22-180">false</span><span class="sxs-lookup"><span data-stu-id="bed22-180">false</span></span>|<span data-ttu-id="bed22-181">true</span><span class="sxs-lookup"><span data-stu-id="bed22-181">true</span></span>|<span data-ttu-id="bed22-182">false</span><span class="sxs-lookup"><span data-stu-id="bed22-182">false</span></span>|<span data-ttu-id="bed22-183">true</span><span class="sxs-lookup"><span data-stu-id="bed22-183">true</span></span>|  
|<span data-ttu-id="bed22-184">false</span><span class="sxs-lookup"><span data-stu-id="bed22-184">false</span></span>|<span data-ttu-id="bed22-185">false</span><span class="sxs-lookup"><span data-stu-id="bed22-185">false</span></span>|<span data-ttu-id="bed22-186">false</span><span class="sxs-lookup"><span data-stu-id="bed22-186">false</span></span>|<span data-ttu-id="bed22-187">false</span><span class="sxs-lookup"><span data-stu-id="bed22-187">false</span></span>|  
|<span data-ttu-id="bed22-188">false</span><span class="sxs-lookup"><span data-stu-id="bed22-188">false</span></span>|<span data-ttu-id="bed22-189">nulo</span><span class="sxs-lookup"><span data-stu-id="bed22-189">null</span></span>|<span data-ttu-id="bed22-190">false</span><span class="sxs-lookup"><span data-stu-id="bed22-190">false</span></span>|<span data-ttu-id="bed22-191">nulo</span><span class="sxs-lookup"><span data-stu-id="bed22-191">null</span></span>|  
|<span data-ttu-id="bed22-192">nulo</span><span class="sxs-lookup"><span data-stu-id="bed22-192">null</span></span>|<span data-ttu-id="bed22-193">true</span><span class="sxs-lookup"><span data-stu-id="bed22-193">true</span></span>|<span data-ttu-id="bed22-194">nulo</span><span class="sxs-lookup"><span data-stu-id="bed22-194">null</span></span>|<span data-ttu-id="bed22-195">true</span><span class="sxs-lookup"><span data-stu-id="bed22-195">true</span></span>|  
|<span data-ttu-id="bed22-196">nulo</span><span class="sxs-lookup"><span data-stu-id="bed22-196">null</span></span>|<span data-ttu-id="bed22-197">false</span><span class="sxs-lookup"><span data-stu-id="bed22-197">false</span></span>|<span data-ttu-id="bed22-198">false</span><span class="sxs-lookup"><span data-stu-id="bed22-198">false</span></span>|<span data-ttu-id="bed22-199">nulo</span><span class="sxs-lookup"><span data-stu-id="bed22-199">null</span></span>|  
|<span data-ttu-id="bed22-200">nulo</span><span class="sxs-lookup"><span data-stu-id="bed22-200">null</span></span>|<span data-ttu-id="bed22-201">nulo</span><span class="sxs-lookup"><span data-stu-id="bed22-201">null</span></span>|<span data-ttu-id="bed22-202">nulo</span><span class="sxs-lookup"><span data-stu-id="bed22-202">null</span></span>|<span data-ttu-id="bed22-203">nulo</span><span class="sxs-lookup"><span data-stu-id="bed22-203">null</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bed22-204">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bed22-204">See Also</span></span>  
 <span data-ttu-id="bed22-205">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="bed22-205">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="bed22-206">[Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="bed22-206">[Nullable Types](../../../csharp/programming-guide/nullable-types/index.md) </span></span>  
 <span data-ttu-id="bed22-207">[Conversão boxing de tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md) </span><span class="sxs-lookup"><span data-stu-id="bed22-207">[Boxing Nullable Types](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md) </span></span>  
 [<span data-ttu-id="bed22-208">Tipos de Valor Anulável</span><span class="sxs-lookup"><span data-stu-id="bed22-208">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)

