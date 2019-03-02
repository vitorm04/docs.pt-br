---
title: Função CType (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: dbf01263723a9e2890dab57d5ffc3d467ed250fc
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212047"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="30829-102">Função CType (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30829-102">CType Function (Visual Basic)</span></span>

<span data-ttu-id="30829-103">Retorna o resultado da conversão explícita de uma expressão para um tipo de dados especificado, objeto, estrutura, classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="30829-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="30829-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30829-104">Syntax</span></span>

```
CType(expression, typename)
```

## <a name="parts"></a><span data-ttu-id="30829-105">Partes</span><span class="sxs-lookup"><span data-stu-id="30829-105">Parts</span></span>

<span data-ttu-id="30829-106">`expression` Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="30829-106">`expression` Any valid expression.</span></span> <span data-ttu-id="30829-107">Se o valor de `expression` está fora do intervalo permitido por `typename`, Visual Basic gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="30829-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>

<span data-ttu-id="30829-108">`typename` Qualquer expressão que é legal em um `As` cláusula em uma `Dim` instrução, ou seja, o nome de qualquer tipo de dados, objeto, estrutura, classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="30829-108">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>

## <a name="remarks"></a><span data-ttu-id="30829-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="30829-109">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="30829-110">Você também pode usar as funções a seguir para executar uma conversão de tipo:</span><span class="sxs-lookup"><span data-stu-id="30829-110">You can also use the following functions to perform a type conversion:</span></span>
>
> - <span data-ttu-id="30829-111">Funções de conversão de tipo, como `CByte`, `CDbl`, e `CInt` que executa uma conversão para um tipo de dados específico.</span><span class="sxs-lookup"><span data-stu-id="30829-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="30829-112">Para obter mais informações, consulte [funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="30829-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>
> - <span data-ttu-id="30829-113">[Operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="30829-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span> <span data-ttu-id="30829-114">Esses operadores exigem que um tipo herda de ou implementa o outro tipo.</span><span class="sxs-lookup"><span data-stu-id="30829-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="30829-115">Eles podem fornecer desempenho um pouco melhor do que `CType` durante a conversão de e para o `Object` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="30829-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>

<span data-ttu-id="30829-116">`CType` é compilado embutido, o que significa que o código de conversão é parte do código que avalia a expressão.</span><span class="sxs-lookup"><span data-stu-id="30829-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="30829-117">Em alguns casos, o código é executado mais rapidamente porque nenhum procedimento é chamado para executar a conversão.</span><span class="sxs-lookup"><span data-stu-id="30829-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>

<span data-ttu-id="30829-118">Se nenhuma conversão é definida de `expression` à `typename` (por exemplo, do `Integer` para `Date`), Visual Basic exibe uma mensagem de erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="30829-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>

<span data-ttu-id="30829-119">Se uma conversão falhar em tempo de execução, a exceção apropriada é lançada.</span><span class="sxs-lookup"><span data-stu-id="30829-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="30829-120">Se uma conversão de redução falhar, um <xref:System.OverflowException> é o resultado mais comum.</span><span class="sxs-lookup"><span data-stu-id="30829-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="30829-121">Se a conversão é indefinida, um <xref:System.InvalidCastException> gerada.</span><span class="sxs-lookup"><span data-stu-id="30829-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="30829-122">Por exemplo, isso pode acontecer se `expression` é do tipo `Object` e seu tipo de tempo de execução não tiver nenhuma conversão para `typename`.</span><span class="sxs-lookup"><span data-stu-id="30829-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>

<span data-ttu-id="30829-123">Se o tipo de dados `expression` ou `typename` é uma classe ou estrutura que você definiu, você pode definir `CType` nessa classe ou estrutura como um operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="30829-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="30829-124">Isso torna `CType` atuar como um *operador sobrecarregado*.</span><span class="sxs-lookup"><span data-stu-id="30829-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="30829-125">Se você fizer isso, você pode controlar o comportamento de conversões para e de sua classe ou estrutura, incluindo as exceções que podem ser lançadas.</span><span class="sxs-lookup"><span data-stu-id="30829-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>

## <a name="overloading"></a><span data-ttu-id="30829-126">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="30829-126">Overloading</span></span>

<span data-ttu-id="30829-127">O `CType` operador também pode ser sobrecarregado em uma classe ou estrutura definida fora de seu código.</span><span class="sxs-lookup"><span data-stu-id="30829-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="30829-128">Se seu código converte para ou de uma classe ou estrutura, certifique-se de entender o comportamento do seu `CType` operador.</span><span class="sxs-lookup"><span data-stu-id="30829-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="30829-129">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="30829-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="converting-dynamic-objects"></a><span data-ttu-id="30829-130">Convertendo objetos dinâmicos</span><span class="sxs-lookup"><span data-stu-id="30829-130">Converting Dynamic Objects</span></span>

<span data-ttu-id="30829-131">Conversões de tipos de objetos dinâmicos são executadas pela conversões dinâmicas definidas pelo usuário que usam o <xref:System.Dynamic.DynamicObject.TryConvert%2A> ou <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> métodos.</span><span class="sxs-lookup"><span data-stu-id="30829-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="30829-132">Se você estiver trabalhando com objetos dinâmicos, use o <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> método para converter o objeto dinâmico.</span><span class="sxs-lookup"><span data-stu-id="30829-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>

## <a name="example"></a><span data-ttu-id="30829-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30829-133">Example</span></span>

<span data-ttu-id="30829-134">O exemplo a seguir usa o `CType` função para converter uma expressão para o `Single` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="30829-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

<span data-ttu-id="30829-135">Para obter exemplos adicionais, consulte [conversões implícitas e explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="30829-135">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="30829-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30829-136">See also</span></span>

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="30829-137">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="30829-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="30829-138">Funções de Conversão</span><span class="sxs-lookup"><span data-stu-id="30829-138">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="30829-139">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="30829-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="30829-140">Como: Definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="30829-140">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="30829-141">Conversão de tipos no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="30829-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
