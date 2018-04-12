---
title: Operador DirectCast (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d9b81abea364e328b831ee98c3b847161c3f7dd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="directcast-operator-visual-basic"></a><span data-ttu-id="b7fcb-102">Operador DirectCast (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7fcb-102">DirectCast Operator (Visual Basic)</span></span>
<span data-ttu-id="b7fcb-103">Apresenta uma operação de conversão de tipo com base em herança ou implementação.</span><span class="sxs-lookup"><span data-stu-id="b7fcb-103">Introduces a type conversion operation based on inheritance or implementation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7fcb-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7fcb-104">Remarks</span></span>  
 <span data-ttu-id="b7fcb-105">`DirectCast`Não use o Visual Basic rotinas auxiliares de tempo de execução para a conversão, para que possa fornecer um pouco melhor desempenho do que `CType` durante a conversão para e do tipo de dados `Object`.</span><span class="sxs-lookup"><span data-stu-id="b7fcb-105">`DirectCast` does not use the Visual Basic run-time helper routines for conversion, so it can provide somewhat better performance than `CType` when converting to and from data type `Object`.</span></span>  
  
 <span data-ttu-id="b7fcb-106">Você usa o `DirectCast` palavra-chave semelhante à forma como você usa o [função CType](../../../visual-basic/language-reference/functions/ctype-function.md) e [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b7fcb-106">You use the `DirectCast` keyword similar to the way you use the [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) and the [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) keyword.</span></span> <span data-ttu-id="b7fcb-107">Você fornece uma expressão como o primeiro argumento e um tipo para convertê-lo para o segundo argumento.</span><span class="sxs-lookup"><span data-stu-id="b7fcb-107">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="b7fcb-108">`DirectCast`requer uma relação de herança ou implementação entre os tipos de dados dos dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="b7fcb-108">`DirectCast` requires an inheritance or implementation relationship between the data types of the two arguments.</span></span> <span data-ttu-id="b7fcb-109">Isso significa que um tipo deve herdar de ou implementar o outro.</span><span class="sxs-lookup"><span data-stu-id="b7fcb-109">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="b7fcb-110">Erros e falhas</span><span class="sxs-lookup"><span data-stu-id="b7fcb-110">Errors and Failures</span></span>  
 <span data-ttu-id="b7fcb-111">`DirectCast`gera um erro do compilador se ele detecta que não existe nenhuma relação de herança ou implementação.</span><span class="sxs-lookup"><span data-stu-id="b7fcb-111">`DirectCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="b7fcb-112">Mas a falta de um erro do compilador não garante uma conversão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="b7fcb-112">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="b7fcb-113">Se a conversão desejada é de restrição, ele poderá falhar em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b7fcb-113">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="b7fcb-114">Se isso acontecer, o tempo de execução gera um <xref:System.InvalidCastException> erro.</span><span class="sxs-lookup"><span data-stu-id="b7fcb-114">If this happens, the runtime throws an <xref:System.InvalidCastException> error.</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="b7fcb-115">Palavras-chave de conversão</span><span class="sxs-lookup"><span data-stu-id="b7fcb-115">Conversion Keywords</span></span>  
 <span data-ttu-id="b7fcb-116">Uma comparação entre as palavras-chave de conversão de tipo é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="b7fcb-116">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="b7fcb-117">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="b7fcb-117">Keyword</span></span>|<span data-ttu-id="b7fcb-118">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="b7fcb-118">Data types</span></span>|<span data-ttu-id="b7fcb-119">Relacionamento de argumento</span><span class="sxs-lookup"><span data-stu-id="b7fcb-119">Argument relationship</span></span>|<span data-ttu-id="b7fcb-120">Falha de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="b7fcb-120">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="b7fcb-121">Função CType</span><span class="sxs-lookup"><span data-stu-id="b7fcb-121">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)|<span data-ttu-id="b7fcb-122">Quaisquer tipos de dados</span><span class="sxs-lookup"><span data-stu-id="b7fcb-122">Any data types</span></span>|<span data-ttu-id="b7fcb-123">Widening ou conversão de estreitamento deve ser definido entre os dois tipos de dados</span><span class="sxs-lookup"><span data-stu-id="b7fcb-123">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="b7fcb-124">Lança<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="b7fcb-124">Throws <xref:System.InvalidCastException></span></span>|  
|`DirectCast`|<span data-ttu-id="b7fcb-125">Quaisquer tipos de dados</span><span class="sxs-lookup"><span data-stu-id="b7fcb-125">Any data types</span></span>|<span data-ttu-id="b7fcb-126">Um tipo deve herdar de ou implementar o outro tipo</span><span class="sxs-lookup"><span data-stu-id="b7fcb-126">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="b7fcb-127">Lança<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="b7fcb-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="b7fcb-128">Operador TryCast</span><span class="sxs-lookup"><span data-stu-id="b7fcb-128">TryCast Operator</span></span>](../../../visual-basic/language-reference/operators/trycast-operator.md)|<span data-ttu-id="b7fcb-129">Somente tipos de referência</span><span class="sxs-lookup"><span data-stu-id="b7fcb-129">Reference types only</span></span>|<span data-ttu-id="b7fcb-130">Um tipo deve herdar de ou implementar o outro tipo</span><span class="sxs-lookup"><span data-stu-id="b7fcb-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="b7fcb-131">Retorna [nada](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="b7fcb-131">Returns [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b7fcb-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7fcb-132">Example</span></span>  
 <span data-ttu-id="b7fcb-133">O exemplo a seguir demonstra dois usos do `DirectCast`, um que falha em tempo de execução e um deles tenha êxito.</span><span class="sxs-lookup"><span data-stu-id="b7fcb-133">The following example demonstrates two uses of `DirectCast`, one that fails at run time and one that succeeds.</span></span>  
  
 [!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/VisualBasic/directcast-operator_1.vb)]  
  
 <span data-ttu-id="b7fcb-134">No exemplo anterior, o tempo de execução do tipo de `q` é `Double`.</span><span class="sxs-lookup"><span data-stu-id="b7fcb-134">In the preceding example, the run-time type of `q` is `Double`.</span></span> <span data-ttu-id="b7fcb-135">`CType`é bem-sucedido porque `Double` pode ser convertido em `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b7fcb-135">`CType` succeeds because `Double` can be converted to `Integer`.</span></span> <span data-ttu-id="b7fcb-136">No entanto, o primeiro `DirectCast` falhar em tempo de execução porque o tempo de execução do tipo de `Double` não tem nenhuma relação de herança com `Integer`, mesmo que exista uma conversão.</span><span class="sxs-lookup"><span data-stu-id="b7fcb-136">However, the first `DirectCast` fails at run time because the run-time type of `Double` has no inheritance relationship with `Integer`, even though a conversion exists.</span></span> <span data-ttu-id="b7fcb-137">A segunda `DirectCast` é bem-sucedido porque ele converte do tipo <xref:System.Windows.Forms.Form> digitar <xref:System.Windows.Forms.Control>, do qual <xref:System.Windows.Forms.Form> herda.</span><span class="sxs-lookup"><span data-stu-id="b7fcb-137">The second `DirectCast` succeeds because it converts from type <xref:System.Windows.Forms.Form> to type <xref:System.Windows.Forms.Control>, from which <xref:System.Windows.Forms.Form> inherits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7fcb-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7fcb-138">See Also</span></span>  
 <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="b7fcb-139">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="b7fcb-139">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="b7fcb-140">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="b7fcb-140">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
