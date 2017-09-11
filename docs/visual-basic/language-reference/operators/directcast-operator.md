---
title: Operador DirectCast (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.directCast
- directCast
dev_langs:
- VB
helpviewer_keywords:
- DirectCast keyword
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4fafebbfe317cbd57a0c73a6564c44d82665fb5b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="directcast-operator-visual-basic"></a><span data-ttu-id="b3b56-102">Operador DirectCast (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3b56-102">DirectCast Operator (Visual Basic)</span></span>
<span data-ttu-id="b3b56-103">Introduz uma operação de conversão de tipo com base em herança ou implementação.</span><span class="sxs-lookup"><span data-stu-id="b3b56-103">Introduces a type conversion operation based on inheritance or implementation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3b56-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="b3b56-104">Remarks</span></span>  
 <span data-ttu-id="b3b56-105">`DirectCast`Não use o Visual Basic rotinas auxiliares de tempo de execução para conversão, para que possa fornecer um pouco melhor desempenho do que `CType` durante a conversão para e do tipo de dados `Object`.</span><span class="sxs-lookup"><span data-stu-id="b3b56-105">`DirectCast` does not use the Visual Basic run-time helper routines for conversion, so it can provide somewhat better performance than `CType` when converting to and from data type `Object`.</span></span>  
  
 <span data-ttu-id="b3b56-106">Você usa o `DirectCast` palavra-chave semelhante à maneira como você usa o [função CType](../../../visual-basic/language-reference/functions/ctype-function.md) e [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b3b56-106">You use the `DirectCast` keyword similar to the way you use the [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) and the [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) keyword.</span></span> <span data-ttu-id="b3b56-107">Forneça uma expressão como o primeiro argumento e um tipo que será convertido como o segundo argumento.</span><span class="sxs-lookup"><span data-stu-id="b3b56-107">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="b3b56-108">`DirectCast`requer uma relação de herança ou implementação entre os tipos de dados dos dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="b3b56-108">`DirectCast` requires an inheritance or implementation relationship between the data types of the two arguments.</span></span> <span data-ttu-id="b3b56-109">Isso significa que um tipo deve herdar de ou implementar o outro.</span><span class="sxs-lookup"><span data-stu-id="b3b56-109">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="b3b56-110">Erros e falhas</span><span class="sxs-lookup"><span data-stu-id="b3b56-110">Errors and Failures</span></span>  
 <span data-ttu-id="b3b56-111">`DirectCast`gera um erro do compilador se ele detectar que nenhuma relação de herança ou implementação existe.</span><span class="sxs-lookup"><span data-stu-id="b3b56-111">`DirectCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="b3b56-112">Mas a falta de um erro do compilador não garante uma conversão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="b3b56-112">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="b3b56-113">Se a conversão desejada é de restrição, ele pode falhar em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b3b56-113">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="b3b56-114">Se isso acontecer, o tempo de execução gera uma <xref:System.InvalidCastException>erro.</xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="b3b56-114">If this happens, the runtime throws an <xref:System.InvalidCastException> error.</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="b3b56-115">Palavras-chave de conversão</span><span class="sxs-lookup"><span data-stu-id="b3b56-115">Conversion Keywords</span></span>  
 <span data-ttu-id="b3b56-116">Uma comparação entre as palavras-chave de conversão de tipo é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="b3b56-116">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="b3b56-117">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="b3b56-117">Keyword</span></span>|<span data-ttu-id="b3b56-118">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="b3b56-118">Data types</span></span>|<span data-ttu-id="b3b56-119">Relacionamento de argumento</span><span class="sxs-lookup"><span data-stu-id="b3b56-119">Argument relationship</span></span>|<span data-ttu-id="b3b56-120">Falha de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="b3b56-120">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="b3b56-121">Função CType</span><span class="sxs-lookup"><span data-stu-id="b3b56-121">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)|<span data-ttu-id="b3b56-122">Quaisquer tipos de dados</span><span class="sxs-lookup"><span data-stu-id="b3b56-122">Any data types</span></span>|<span data-ttu-id="b3b56-123">Ampliação ou restringir a conversão deve ser definido entre os dois tipos de dados</span><span class="sxs-lookup"><span data-stu-id="b3b56-123">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="b3b56-124">Lança<xref:System.InvalidCastException></xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="b3b56-124">Throws <xref:System.InvalidCastException></span></span>|  
|`DirectCast`|<span data-ttu-id="b3b56-125">Quaisquer tipos de dados</span><span class="sxs-lookup"><span data-stu-id="b3b56-125">Any data types</span></span>|<span data-ttu-id="b3b56-126">Um tipo deve herdar de ou implementar o outro tipo</span><span class="sxs-lookup"><span data-stu-id="b3b56-126">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="b3b56-127">Lança<xref:System.InvalidCastException></xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="b3b56-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="b3b56-128">Operador TryCast</span><span class="sxs-lookup"><span data-stu-id="b3b56-128">TryCast Operator</span></span>](../../../visual-basic/language-reference/operators/trycast-operator.md)|<span data-ttu-id="b3b56-129">Somente tipos de referência</span><span class="sxs-lookup"><span data-stu-id="b3b56-129">Reference types only</span></span>|<span data-ttu-id="b3b56-130">Um tipo deve herdar de ou implementar o outro tipo</span><span class="sxs-lookup"><span data-stu-id="b3b56-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="b3b56-131">Retorna [nada](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="b3b56-131">Returns [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b3b56-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3b56-132">Example</span></span>  
 <span data-ttu-id="b3b56-133">O exemplo a seguir demonstra dois usos do `DirectCast`, um que falha em tempo de execução e um deles tenha êxito.</span><span class="sxs-lookup"><span data-stu-id="b3b56-133">The following example demonstrates two uses of `DirectCast`, one that fails at run time and one that succeeds.</span></span>  
  
 <span data-ttu-id="b3b56-134">[!code-vb[VbVbalrKeywords n º&1;](../../../visual-basic/language-reference/codesnippet/VisualBasic/directcast-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b3b56-134">[!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/VisualBasic/directcast-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="b3b56-135">No exemplo anterior, o tempo de execução do tipo de `q` é `Double`.</span><span class="sxs-lookup"><span data-stu-id="b3b56-135">In the preceding example, the run-time type of `q` is `Double`.</span></span> <span data-ttu-id="b3b56-136">`CType`é bem-sucedida pois `Double` pode ser convertido em `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b3b56-136">`CType` succeeds because `Double` can be converted to `Integer`.</span></span> <span data-ttu-id="b3b56-137">No entanto, o primeiro `DirectCast` falha em tempo de execução porque o tipo de tempo de execução de `Double` não tem nenhuma relação de herança com `Integer`, mesmo que exista uma conversão.</span><span class="sxs-lookup"><span data-stu-id="b3b56-137">However, the first `DirectCast` fails at run time because the run-time type of `Double` has no inheritance relationship with `Integer`, even though a conversion exists.</span></span> <span data-ttu-id="b3b56-138">A segunda `DirectCast` é bem-sucedida pois ele converte do tipo <xref:System.Windows.Forms.Form>digitar <xref:System.Windows.Forms.Control>, do qual <xref:System.Windows.Forms.Form>herda.</xref:System.Windows.Forms.Form> </xref:System.Windows.Forms.Control> </xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="b3b56-138">The second `DirectCast` succeeds because it converts from type <xref:System.Windows.Forms.Form> to type <xref:System.Windows.Forms.Control>, from which <xref:System.Windows.Forms.Form> inherits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b56-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3b56-139">See Also</span></span>  
 <span data-ttu-id="b3b56-140"><xref:System.Convert.ChangeType%2A?displayProperty=fullName></xref:System.Convert.ChangeType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b3b56-140"><xref:System.Convert.ChangeType%2A?displayProperty=fullName></span></span>   
<span data-ttu-id="b3b56-141"> [Conversões entre](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="b3b56-141"> [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span></span>  
<span data-ttu-id="b3b56-142"> [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="b3b56-142"> [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)</span></span>
