---
title: "Conversões boxing e unboxing (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.boxing
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
caps.latest.revision: 34
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
ms.openlocfilehash: c783ac60735ba25db2736bd9469063c0897be22f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="2e03c-102">Conversões boxing e unboxing (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="2e03c-102">Boxing and Unboxing (C# Programming Guide)</span></span>
<span data-ttu-id="2e03c-103">Conversão boxing é o processo de conversão de um [tipo de valor](../../../csharp/language-reference/keywords/value-types.md) para o tipo `object` ou para qualquer tipo de interface implementada por esse tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="2e03c-103">Boxing is the process of converting a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="2e03c-104">Quando o CLR realiza a conversão boxing de um tipo de valor, ele encapsula o valor dentro de System.Object e o armazena no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2e03c-104">When the CLR boxes a value type, it wraps the value inside a System.Object and stores it on the managed heap.</span></span> <span data-ttu-id="2e03c-105">A conversão unboxing extrai o tipo de valor do objeto.</span><span class="sxs-lookup"><span data-stu-id="2e03c-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="2e03c-106">A conversão boxing é implícita, a conversão unboxing é explícita.</span><span class="sxs-lookup"><span data-stu-id="2e03c-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="2e03c-107">O conceito de conversões boxing e unboxing serve como base para a exibição unificada de C# do sistema de tipos em que um valor de qualquer tipo pode ser tratado como um objeto.</span><span class="sxs-lookup"><span data-stu-id="2e03c-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>  
  
 <span data-ttu-id="2e03c-108">No exemplo a seguir, a variável de inteiro `i` é submetida à *conversão boxing* e atribuída ao objeto `o`.</span><span class="sxs-lookup"><span data-stu-id="2e03c-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>  
  
 <span data-ttu-id="2e03c-109">[!code-cs[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2e03c-109">[!code-cs[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]</span></span>  
  
 <span data-ttu-id="2e03c-110">O objeto `o` pode ser submetido à conversão unboxing e atribuído à variável de inteiro `i`:</span><span class="sxs-lookup"><span data-stu-id="2e03c-110">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>  
  
 <span data-ttu-id="2e03c-111">[!code-cs[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="2e03c-111">[!code-cs[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]</span></span>  
  
 <span data-ttu-id="2e03c-112">Os exemplos a seguir ilustram como a conversão boxing é usada em C#.</span><span class="sxs-lookup"><span data-stu-id="2e03c-112">The following examples illustrate how boxing is used in C#.</span></span>  
  
 <span data-ttu-id="2e03c-113">[!code-cs[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="2e03c-113">[!code-cs[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]</span></span>  
  
## <a name="performance"></a><span data-ttu-id="2e03c-114">Desempenho</span><span class="sxs-lookup"><span data-stu-id="2e03c-114">Performance</span></span>  
 <span data-ttu-id="2e03c-115">Em relação às atribuições simples, as conversões boxing e unboxing são processos computacionalmente dispendiosos.</span><span class="sxs-lookup"><span data-stu-id="2e03c-115">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="2e03c-116">Quando um tipo de valor é submetido à conversão boxing, um novo objeto deve ser alocado e construído.</span><span class="sxs-lookup"><span data-stu-id="2e03c-116">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="2e03c-117">A um grau menor, a conversão necessária para a conversão unboxing também é computacionalmente dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="2e03c-117">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="2e03c-118">Para obter mais informações, consulte [Desempenho](https://msdn.microsoft.com/library/ms173196(VS.110).aspx).</span><span class="sxs-lookup"><span data-stu-id="2e03c-118">For more information, see [Performance](https://msdn.microsoft.com/library/ms173196(VS.110).aspx).</span></span>  
  
## <a name="boxing"></a><span data-ttu-id="2e03c-119">Boxing</span><span class="sxs-lookup"><span data-stu-id="2e03c-119">Boxing</span></span>  
 <span data-ttu-id="2e03c-120">A conversão boxing é usada para armazenar tipos de valor no heap coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="2e03c-120">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="2e03c-121">A conversão boxing é uma conversão implícita de um [tipo de valor](../../../csharp/language-reference/keywords/value-types.md) para o tipo `object` ou para qualquer tipo de interface implementada por esse tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="2e03c-121">Boxing is an implicit conversion of a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="2e03c-122">A conversão boxing de um tipo de valor aloca uma instância de objeto no heap e copia o valor no novo objeto.</span><span class="sxs-lookup"><span data-stu-id="2e03c-122">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>  
  
 <span data-ttu-id="2e03c-123">Considere a seguinte declaração de uma variável de tipo de valor:</span><span class="sxs-lookup"><span data-stu-id="2e03c-123">Consider the following declaration of a value-type variable:</span></span>  
  
 <span data-ttu-id="2e03c-124">[!code-cs[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="2e03c-124">[!code-cs[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]</span></span>  
  
 <span data-ttu-id="2e03c-125">A instrução a seguir aplica implicitamente a operação de conversão boxing na variável `i`:</span><span class="sxs-lookup"><span data-stu-id="2e03c-125">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>  
  
 <span data-ttu-id="2e03c-126">[!code-cs[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="2e03c-126">[!code-cs[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]</span></span>  
  
 <span data-ttu-id="2e03c-127">O resultado dessa instrução é a criação de uma referência de objeto `o`, na pilha, que faz referência a um valor do tipo `int`, no heap.</span><span class="sxs-lookup"><span data-stu-id="2e03c-127">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="2e03c-128">Esse valor é uma cópia do valor do tipo de valor atribuído à variável `i`.</span><span class="sxs-lookup"><span data-stu-id="2e03c-128">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="2e03c-129">A diferença entre as duas variáveis, `i` e `o`, é ilustrada na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="2e03c-129">The difference between the two variables, `i` and `o`, is illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="2e03c-130">![Gráfico de Conversão Boxing](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="2e03c-130">![BoxingConversion graphic](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span></span>  
<span data-ttu-id="2e03c-131">Conversão boxing</span><span class="sxs-lookup"><span data-stu-id="2e03c-131">Boxing Conversion</span></span>  
  
 <span data-ttu-id="2e03c-132">Também é possível executar a conversão boxing explicitamente como no exemplo a seguir, mas a conversão boxing explícita nunca é necessária:</span><span class="sxs-lookup"><span data-stu-id="2e03c-132">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>  
  
 <span data-ttu-id="2e03c-133">[!code-cs[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="2e03c-133">[!code-cs[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]</span></span>  
  
## <a name="description"></a><span data-ttu-id="2e03c-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e03c-134">Description</span></span>  
 <span data-ttu-id="2e03c-135">Este exemplo converte uma variável de inteiro `i` em um objeto `o` usando a conversão boxing.</span><span class="sxs-lookup"><span data-stu-id="2e03c-135">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="2e03c-136">Em seguida, o valor armazenado na variável `i` é alterado de `123` para `456`.</span><span class="sxs-lookup"><span data-stu-id="2e03c-136">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="2e03c-137">O exemplo mostra que o tipo do valor original e o objeto submetido à conversão boxing usa locais de memória separados e, portanto, pode armazenar valores diferentes.</span><span class="sxs-lookup"><span data-stu-id="2e03c-137">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e03c-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2e03c-138">Example</span></span>  
 <span data-ttu-id="2e03c-139">[!code-cs[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="2e03c-139">[!code-cs[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]</span></span>  
  
## <a name="unboxing"></a><span data-ttu-id="2e03c-140">Unboxing</span><span class="sxs-lookup"><span data-stu-id="2e03c-140">Unboxing</span></span>  
 <span data-ttu-id="2e03c-141">A conversão unboxing é uma conversão explícita do tipo `object` para um [tipo de valor](../../../csharp/language-reference/keywords/value-types.md) ou de um tipo de interface para um tipo de valor que implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="2e03c-141">Unboxing is an explicit conversion from the type `object` to a [value type](../../../csharp/language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="2e03c-142">Uma operação de conversão unboxing consiste em:</span><span class="sxs-lookup"><span data-stu-id="2e03c-142">An unboxing operation consists of:</span></span>  
  
-   <span data-ttu-id="2e03c-143">Verificar a instância do objeto para garantir que ele é um valor da conversão boxing de um determinado tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="2e03c-143">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>  
  
-   <span data-ttu-id="2e03c-144">Copiar o valor da instância para a variável de tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="2e03c-144">Copying the value from the instance into the value-type variable.</span></span>  
  
 <span data-ttu-id="2e03c-145">As instruções a seguir demonstram operações conversão boxing e unboxing:</span><span class="sxs-lookup"><span data-stu-id="2e03c-145">The following statements demonstrate both boxing and unboxing operations:</span></span>  
  
 <span data-ttu-id="2e03c-146">[!code-cs[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="2e03c-146">[!code-cs[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]</span></span>  
  
 <span data-ttu-id="2e03c-147">A figura a seguir demonstra o resultado das instruções anteriores.</span><span class="sxs-lookup"><span data-stu-id="2e03c-147">The following figure demonstrates the result of the previous statements.</span></span>  
  
 <span data-ttu-id="2e03c-148">![Gráfico de Conversão UnBoxing](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="2e03c-148">![UnBoxing Conversion graphic](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span></span>  
<span data-ttu-id="2e03c-149">Conversão unboxing</span><span class="sxs-lookup"><span data-stu-id="2e03c-149">Unboxing Conversion</span></span>  
  
 <span data-ttu-id="2e03c-150">Para a conversão unboxing de tipos de valor ter êxito em tempo de execução, o item sendo submetido à conversão unboxing deve ser uma referência para um objeto que foi criado anteriormente ao realizar a conversão boxing de uma instância desse tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="2e03c-150">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="2e03c-151">Tentar realizar a conversão unboxing de `null` causa uma <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="2e03c-151">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="2e03c-152">Tentar realizar a conversão unboxing de uma referência para um tipo de valor incompatível causa uma <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="2e03c-152">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e03c-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2e03c-153">Example</span></span>  
 <span data-ttu-id="2e03c-154">O exemplo a seguir demonstra um caso de conversão unboxing inválida e o `InvalidCastException` resultante.</span><span class="sxs-lookup"><span data-stu-id="2e03c-154">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="2e03c-155">Usando `try` e `catch`, uma mensagem de erro é exibida quando o erro ocorre.</span><span class="sxs-lookup"><span data-stu-id="2e03c-155">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>  
  
 <span data-ttu-id="2e03c-156">[!code-cs[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="2e03c-156">[!code-cs[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]</span></span>  
  
 <span data-ttu-id="2e03c-157">Este programa produz:</span><span class="sxs-lookup"><span data-stu-id="2e03c-157">This program outputs:</span></span>  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 <span data-ttu-id="2e03c-158">Se você alterar a instrução:</span><span class="sxs-lookup"><span data-stu-id="2e03c-158">If you change the statement:</span></span>  
  
```  
int j = (short) o;  
```  
  
 <span data-ttu-id="2e03c-159">para:</span><span class="sxs-lookup"><span data-stu-id="2e03c-159">to:</span></span>  
  
```  
int j = (int) o;  
```  
  
 <span data-ttu-id="2e03c-160">a conversão será executada e você receberá a saída:</span><span class="sxs-lookup"><span data-stu-id="2e03c-160">the conversion will be performed, and you will get the output:</span></span>  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="2e03c-161">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="2e03c-161">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a><span data-ttu-id="2e03c-162">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="2e03c-162">Related Sections</span></span>  
 <span data-ttu-id="2e03c-163">Para saber mais:</span><span class="sxs-lookup"><span data-stu-id="2e03c-163">For more information:</span></span>  
  
-   [<span data-ttu-id="2e03c-164">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="2e03c-164">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="2e03c-165">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="2e03c-165">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="2e03c-166">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="2e03c-166">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2e03c-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e03c-167">See Also</span></span>  
 [<span data-ttu-id="2e03c-168">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="2e03c-168">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

