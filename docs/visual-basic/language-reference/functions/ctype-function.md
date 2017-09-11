---
title: "Função CType (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.CType
dev_langs:
- VB
helpviewer_keywords:
- expression conversion results
- explicit data type conversions
- CType function
- conversions, expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1c3691f56485eacff44b8fbdcf9cbc8f69889f6f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="3e46e-102">Função CType (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e46e-102">CType Function (Visual Basic)</span></span>
<span data-ttu-id="3e46e-103">Retorna o resultado da conversão explícita de uma expressão para um tipo de dados especificado, objeto, estrutura, classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="3e46e-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e46e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e46e-104">Syntax</span></span>  
  
```  
CType(expression, typename)  
```  
  
## <a name="parts"></a><span data-ttu-id="3e46e-105">Partes</span><span class="sxs-lookup"><span data-stu-id="3e46e-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="3e46e-106">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="3e46e-106">Any valid expression.</span></span> <span data-ttu-id="3e46e-107">Se o valor de `expression` está fora do intervalo permitido por `typename`, Visual Basic gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="3e46e-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>  
  
 `typename`  
 <span data-ttu-id="3e46e-108">Qualquer expressão que seja legal em um `As` cláusula em uma `Dim` instrução, ou seja, o nome de qualquer tipo de dados, objeto, estrutura, classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="3e46e-108">Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e46e-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e46e-109">Remarks</span></span>  
  
> [!TIP]
>  <span data-ttu-id="3e46e-110">Você também pode usar as funções a seguir para executar uma conversão de tipo:</span><span class="sxs-lookup"><span data-stu-id="3e46e-110">You can also use the following functions to perform a type conversion:</span></span>  
>   
>  -   <span data-ttu-id="3e46e-111">Funções de conversão de tipo como `CByte`, `CDbl`, e `CInt` que executar uma conversão para um tipo de dados específico.</span><span class="sxs-lookup"><span data-stu-id="3e46e-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="3e46e-112">Para obter mais informações, consulte [funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="3e46e-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
> -   <span data-ttu-id="3e46e-113">[Operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="3e46e-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span> <span data-ttu-id="3e46e-114">Esses operadores exigem que um tipo de herdar de ou implementar o outro tipo.</span><span class="sxs-lookup"><span data-stu-id="3e46e-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="3e46e-115">Podem fornecer desempenho um pouco melhor do que `CType` durante a conversão de e para o `Object` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="3e46e-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>  
  
 <span data-ttu-id="3e46e-116">`CType`é embutido compilado, o que significa que o código de conversão faz parte do código que avalia a expressão.</span><span class="sxs-lookup"><span data-stu-id="3e46e-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="3e46e-117">Em alguns casos, o código é executado mais rápido porque não há procedimentos são chamados para executar a conversão.</span><span class="sxs-lookup"><span data-stu-id="3e46e-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>  
  
 <span data-ttu-id="3e46e-118">Se nenhuma conversão é definida de `expression` para `typename` (por exemplo, de `Integer` para `Date`), do Visual Basic exibe uma mensagem de erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="3e46e-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>  
  
 <span data-ttu-id="3e46e-119">Se uma conversão falhar em tempo de execução, a exceção apropriada é gerada.</span><span class="sxs-lookup"><span data-stu-id="3e46e-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="3e46e-120">Se uma conversão de redução falhar, um <xref:System.OverflowException>é o resultado mais comum.</xref:System.OverflowException></span><span class="sxs-lookup"><span data-stu-id="3e46e-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="3e46e-121">Se a conversão for indefinida, uma <xref:System.InvalidCastException>em gerada.</xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="3e46e-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="3e46e-122">Por exemplo, isso pode acontecer se `expression` é do tipo `Object` e seu tipo de tempo de execução não tem nenhuma conversão em `typename`.</span><span class="sxs-lookup"><span data-stu-id="3e46e-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>  
  
 <span data-ttu-id="3e46e-123">Se o tipo de dados `expression` ou `typename` é uma classe ou estrutura que você definiu, você pode definir `CType` na classe ou estrutura como um operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="3e46e-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="3e46e-124">Isso torna `CType` atuar como um *sobrecarregado operador*.</span><span class="sxs-lookup"><span data-stu-id="3e46e-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="3e46e-125">Se você fizer isso, você pode controlar o comportamento de conversões para e de sua classe ou estrutura, incluindo as exceções que podem ser geradas.</span><span class="sxs-lookup"><span data-stu-id="3e46e-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="3e46e-126">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="3e46e-126">Overloading</span></span>  
 <span data-ttu-id="3e46e-127">O `CType` também pode ser sobrecarregado operador em uma classe ou estrutura definida fora de seu código.</span><span class="sxs-lookup"><span data-stu-id="3e46e-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="3e46e-128">Se o código a seguir converte para ou de uma classe ou estrutura, certifique-se de entender o comportamento do seu `CType` operador.</span><span class="sxs-lookup"><span data-stu-id="3e46e-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="3e46e-129">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3e46e-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="converting-dynamic-objects"></a><span data-ttu-id="3e46e-130">Convertendo objetos dinâmicos</span><span class="sxs-lookup"><span data-stu-id="3e46e-130">Converting Dynamic Objects</span></span>  
 <span data-ttu-id="3e46e-131">Conversões de tipo de objetos dinâmicos são executadas por conversões dinâmicas definido pelo usuário que usam o <xref:System.Dynamic.DynamicObject.TryConvert%2A>ou <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A>métodos.</xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> </xref:System.Dynamic.DynamicObject.TryConvert%2A></span><span class="sxs-lookup"><span data-stu-id="3e46e-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="3e46e-132">Se você estiver trabalhando com objetos dinâmicos, use o <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A>método para converter o objeto dinâmico.</xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A></span><span class="sxs-lookup"><span data-stu-id="3e46e-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e46e-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e46e-133">Example</span></span>  
 <span data-ttu-id="3e46e-134">O exemplo a seguir usa o `CType` função para converter uma expressão para o `Single` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="3e46e-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>  
  
 <span data-ttu-id="3e46e-135">[!code-vb[VbVbalrFunctions&#24;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/ctype-function_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="3e46e-135">[!code-vb[VbVbalrFunctions#24](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/ctype-function_1.vb)]</span></span>  
  
 <span data-ttu-id="3e46e-136">Para obter exemplos adicionais, consulte [conversões explícitas e implícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="3e46e-136">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e46e-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e46e-137">See Also</span></span>  
 <span data-ttu-id="3e46e-138"><xref:System.OverflowException></xref:System.OverflowException></span><span class="sxs-lookup"><span data-stu-id="3e46e-138"><xref:System.OverflowException></span></span>   
 <span data-ttu-id="3e46e-139"><xref:System.InvalidCastException></xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="3e46e-139"><xref:System.InvalidCastException></span></span>   
<span data-ttu-id="3e46e-140"> [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="3e46e-140"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="3e46e-141"> [Funções de conversão](../../../visual-basic/language-reference/functions/conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="3e46e-141"> [Conversion Functions](../../../visual-basic/language-reference/functions/conversion-functions.md) </span></span>  
<span data-ttu-id="3e46e-142"> [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md) </span><span class="sxs-lookup"><span data-stu-id="3e46e-142"> [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md) </span></span>  
<span data-ttu-id="3e46e-143"> [Como: definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md) </span><span class="sxs-lookup"><span data-stu-id="3e46e-143"> [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md) </span></span>  
<span data-ttu-id="3e46e-144"> [Conversão de tipo no .NET Framework](http://msdn.microsoft.com/library/ba36154f-064c-47d3-9f05-72f93a7ca96d)</span><span class="sxs-lookup"><span data-stu-id="3e46e-144"> [Type Conversion in the .NET Framework](http://msdn.microsoft.com/library/ba36154f-064c-47d3-9f05-72f93a7ca96d)</span></span>
