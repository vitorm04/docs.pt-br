---
title: Conversões boxing e unboxing – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: da4aabbd0529ee239dacd2dff7c7825d41110b44
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835161"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="a4efb-102">Conversões boxing e unboxing (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="a4efb-102">Boxing and Unboxing (C# Programming Guide)</span></span>
<span data-ttu-id="a4efb-103">Conversão boxing é o processo de conversão de um [tipo de valor](../../../csharp/language-reference/keywords/value-types.md) para o tipo `object` ou para qualquer tipo de interface implementada por esse tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="a4efb-103">Boxing is the process of converting a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="a4efb-104">Quando o CLR realiza a conversão boxing de um tipo de valor, ele encapsula o valor dentro de System.Object e o armazena no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a4efb-104">When the CLR boxes a value type, it wraps the value inside a System.Object and stores it on the managed heap.</span></span> <span data-ttu-id="a4efb-105">A conversão unboxing extrai o tipo de valor do objeto.</span><span class="sxs-lookup"><span data-stu-id="a4efb-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="a4efb-106">A conversão boxing é implícita, a conversão unboxing é explícita.</span><span class="sxs-lookup"><span data-stu-id="a4efb-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="a4efb-107">O conceito de conversões boxing e unboxing serve como base para a exibição unificada de C# do sistema de tipos em que um valor de qualquer tipo pode ser tratado como um objeto.</span><span class="sxs-lookup"><span data-stu-id="a4efb-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>  
  
 <span data-ttu-id="a4efb-108">No exemplo a seguir, a variável de inteiro `i` é submetida à *conversão boxing* e atribuída ao objeto `o`.</span><span class="sxs-lookup"><span data-stu-id="a4efb-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]  
  
 <span data-ttu-id="a4efb-109">O objeto `o` pode ser submetido à conversão unboxing e atribuído à variável de inteiro `i`:</span><span class="sxs-lookup"><span data-stu-id="a4efb-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]  
  
 <span data-ttu-id="a4efb-110">Os exemplos a seguir ilustram como a conversão boxing é usada em C#.</span><span class="sxs-lookup"><span data-stu-id="a4efb-110">The following examples illustrate how boxing is used in C#.</span></span>  
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="performance"></a><span data-ttu-id="a4efb-111">Desempenho</span><span class="sxs-lookup"><span data-stu-id="a4efb-111">Performance</span></span>  
 <span data-ttu-id="a4efb-112">Em relação às atribuições simples, as conversões boxing e unboxing são processos computacionalmente dispendiosos.</span><span class="sxs-lookup"><span data-stu-id="a4efb-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="a4efb-113">Quando um tipo de valor é submetido à conversão boxing, um novo objeto deve ser alocado e construído.</span><span class="sxs-lookup"><span data-stu-id="a4efb-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="a4efb-114">A um grau menor, a conversão necessária para a conversão unboxing também é computacionalmente dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="a4efb-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="a4efb-115">Para obter mais informações, consulte [Desempenho](../../../../docs/framework/performance/performance-tips.md).</span><span class="sxs-lookup"><span data-stu-id="a4efb-115">For more information, see [Performance](../../../../docs/framework/performance/performance-tips.md).</span></span>  
  
## <a name="boxing"></a><span data-ttu-id="a4efb-116">Boxing</span><span class="sxs-lookup"><span data-stu-id="a4efb-116">Boxing</span></span>  
 <span data-ttu-id="a4efb-117">A conversão boxing é usada para armazenar tipos de valor no heap coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="a4efb-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="a4efb-118">A conversão boxing é uma conversão implícita de um [tipo de valor](../../../csharp/language-reference/keywords/value-types.md) para o tipo `object` ou para qualquer tipo de interface implementada por esse tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="a4efb-118">Boxing is an implicit conversion of a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="a4efb-119">A conversão boxing de um tipo de valor aloca uma instância de objeto no heap e copia o valor no novo objeto.</span><span class="sxs-lookup"><span data-stu-id="a4efb-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>  
  
 <span data-ttu-id="a4efb-120">Considere a seguinte declaração de uma variável de tipo de valor:</span><span class="sxs-lookup"><span data-stu-id="a4efb-120">Consider the following declaration of a value-type variable:</span></span>  
  
 [!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]  
  
 <span data-ttu-id="a4efb-121">A instrução a seguir aplica implicitamente a operação de conversão boxing na variável `i`:</span><span class="sxs-lookup"><span data-stu-id="a4efb-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]  
  
 <span data-ttu-id="a4efb-122">O resultado dessa instrução é a criação de uma referência de objeto `o`, na pilha, que faz referência a um valor do tipo `int`, no heap.</span><span class="sxs-lookup"><span data-stu-id="a4efb-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="a4efb-123">Esse valor é uma cópia do valor do tipo de valor atribuído à variável `i`.</span><span class="sxs-lookup"><span data-stu-id="a4efb-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="a4efb-124">A diferença entre as duas variáveis, `i` e `o`, é ilustrada na figura de conversão boxing a seguir:</span><span class="sxs-lookup"><span data-stu-id="a4efb-124">The difference between the two variables, `i` and `o`, is illustrated in the following image of boxing conversion:</span></span>  
  
 ![Gráfico mostrando a diferença entre variáveis i e o.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)    
  
 <span data-ttu-id="a4efb-126">Também é possível executar a conversão boxing explicitamente como no exemplo a seguir, mas a conversão boxing explícita nunca é necessária:</span><span class="sxs-lookup"><span data-stu-id="a4efb-126">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>  
  
 [!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]  
  
## <a name="description"></a><span data-ttu-id="a4efb-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4efb-127">Description</span></span>  
 <span data-ttu-id="a4efb-128">Este exemplo converte uma variável de inteiro `i` em um objeto `o` usando a conversão boxing.</span><span class="sxs-lookup"><span data-stu-id="a4efb-128">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="a4efb-129">Em seguida, o valor armazenado na variável `i` é alterado de `123` para `456`.</span><span class="sxs-lookup"><span data-stu-id="a4efb-129">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="a4efb-130">O exemplo mostra que o tipo do valor original e o objeto submetido à conversão boxing usa locais de memória separados e, portanto, pode armazenar valores diferentes.</span><span class="sxs-lookup"><span data-stu-id="a4efb-130">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4efb-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a4efb-131">Example</span></span>  
 [!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]  
  
## <a name="unboxing"></a><span data-ttu-id="a4efb-132">Unboxing</span><span class="sxs-lookup"><span data-stu-id="a4efb-132">Unboxing</span></span>  
 <span data-ttu-id="a4efb-133">A conversão unboxing é uma conversão explícita do tipo `object` para um [tipo de valor](../../../csharp/language-reference/keywords/value-types.md) ou de um tipo de interface para um tipo de valor que implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="a4efb-133">Unboxing is an explicit conversion from the type `object` to a [value type](../../../csharp/language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="a4efb-134">Uma operação de conversão unboxing consiste em:</span><span class="sxs-lookup"><span data-stu-id="a4efb-134">An unboxing operation consists of:</span></span>  
  
-   <span data-ttu-id="a4efb-135">Verificar a instância do objeto para garantir que ele é um valor da conversão boxing de um determinado tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="a4efb-135">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>  
  
-   <span data-ttu-id="a4efb-136">Copiar o valor da instância para a variável de tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="a4efb-136">Copying the value from the instance into the value-type variable.</span></span>  
  
 <span data-ttu-id="a4efb-137">As instruções a seguir demonstram operações conversão boxing e unboxing:</span><span class="sxs-lookup"><span data-stu-id="a4efb-137">The following statements demonstrate both boxing and unboxing operations:</span></span>  
  
 [!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]  
  
 <span data-ttu-id="a4efb-138">A figura a seguir demonstra o resultado das instruções anteriores:</span><span class="sxs-lookup"><span data-stu-id="a4efb-138">The following figure demonstrates the result of the previous statements:</span></span> 
  
 ![Gráfico mostrando uma conversão unboxing.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)
  
 <span data-ttu-id="a4efb-140">Para a conversão unboxing de tipos de valor ter êxito em tempo de execução, o item sendo submetido à conversão unboxing deve ser uma referência para um objeto que foi criado anteriormente ao realizar a conversão boxing de uma instância desse tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="a4efb-140">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="a4efb-141">Tentar realizar a conversão unboxing de `null` causa uma <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="a4efb-141">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="a4efb-142">Tentar realizar a conversão unboxing de uma referência para um tipo de valor incompatível causa uma <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="a4efb-142">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4efb-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a4efb-143">Example</span></span>  
 <span data-ttu-id="a4efb-144">O exemplo a seguir demonstra um caso de conversão unboxing inválida e o `InvalidCastException` resultante.</span><span class="sxs-lookup"><span data-stu-id="a4efb-144">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="a4efb-145">Usando `try` e `catch`, uma mensagem de erro é exibida quando o erro ocorre.</span><span class="sxs-lookup"><span data-stu-id="a4efb-145">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>  
  
 [!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]  
  
 <span data-ttu-id="a4efb-146">Este programa produz:</span><span class="sxs-lookup"><span data-stu-id="a4efb-146">This program outputs:</span></span>  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 <span data-ttu-id="a4efb-147">Se você alterar a instrução:</span><span class="sxs-lookup"><span data-stu-id="a4efb-147">If you change the statement:</span></span>  
  
```csharp
int j = (short) o;  
```  
  
 <span data-ttu-id="a4efb-148">para:</span><span class="sxs-lookup"><span data-stu-id="a4efb-148">to:</span></span>  
  
```csharp
int j = (int) o;  
```  
  
 <span data-ttu-id="a4efb-149">a conversão será executada e você receberá a saída:</span><span class="sxs-lookup"><span data-stu-id="a4efb-149">the conversion will be performed, and you will get the output:</span></span>  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="a4efb-150">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="a4efb-150">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a><span data-ttu-id="a4efb-151">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="a4efb-151">Related Sections</span></span>  
 <span data-ttu-id="a4efb-152">Para saber mais:</span><span class="sxs-lookup"><span data-stu-id="a4efb-152">For more information:</span></span>  
  
-   [<span data-ttu-id="a4efb-153">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="a4efb-153">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="a4efb-154">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="a4efb-154">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a><span data-ttu-id="a4efb-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4efb-155">See also</span></span>

- [<span data-ttu-id="a4efb-156">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a4efb-156">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
