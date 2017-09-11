---
title: Operador TryCast (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.trycast
- trycast
dev_langs:
- VB
helpviewer_keywords:
- TryCast keyword
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
caps.latest.revision: 17
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
ms.openlocfilehash: 8df8035d1763ccf520e4dccd244dbf55b9817ac4
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="63288-102">Operador TryCast (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63288-102">TryCast Operator (Visual Basic)</span></span>
<span data-ttu-id="63288-103">Introduz uma operação de conversão de tipo que não gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="63288-103">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63288-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="63288-104">Remarks</span></span>  
 <span data-ttu-id="63288-105">Se uma tentativa de conversão falhar, `CType` e `DirectCast` ambos lançar um <xref:System.InvalidCastException>erro.</xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="63288-105">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="63288-106">Isso pode afetar negativamente o desempenho do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="63288-106">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="63288-107">`TryCast`Retorna [nada](../../../visual-basic/language-reference/nothing.md), de modo que, em vez de ter que lidar com uma possível exceção, você só precisa testar o resultado em `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="63288-107">`TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="63288-108">Você usa o `TryCast` palavra-chave da mesma maneira que você use o [função CType](../../../visual-basic/language-reference/functions/ctype-function.md) e [operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="63288-108">You use the `TryCast` keyword the same way you use the [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) and the [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) keyword.</span></span> <span data-ttu-id="63288-109">Forneça uma expressão como o primeiro argumento e um tipo que será convertido como o segundo argumento.</span><span class="sxs-lookup"><span data-stu-id="63288-109">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="63288-110">`TryCast`funciona somente em tipos de referência, como classes e interfaces.</span><span class="sxs-lookup"><span data-stu-id="63288-110">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="63288-111">Ele requer uma relação de herança ou implementação entre os dois tipos.</span><span class="sxs-lookup"><span data-stu-id="63288-111">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="63288-112">Isso significa que um tipo deve herdar de ou implementar o outro.</span><span class="sxs-lookup"><span data-stu-id="63288-112">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="63288-113">Erros e falhas</span><span class="sxs-lookup"><span data-stu-id="63288-113">Errors and Failures</span></span>  
 <span data-ttu-id="63288-114">`TryCast`gera um erro do compilador se ele detectar que nenhuma relação de herança ou implementação existe.</span><span class="sxs-lookup"><span data-stu-id="63288-114">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="63288-115">Mas a falta de um erro do compilador não garante uma conversão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="63288-115">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="63288-116">Se a conversão desejada é de restrição, ele pode falhar em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="63288-116">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="63288-117">Se isso acontecer, `TryCast` retorna [nada](../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="63288-117">If this happens, `TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="63288-118">Palavras-chave de conversão</span><span class="sxs-lookup"><span data-stu-id="63288-118">Conversion Keywords</span></span>  
 <span data-ttu-id="63288-119">Uma comparação entre as palavras-chave de conversão de tipo é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="63288-119">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="63288-120">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="63288-120">Keyword</span></span>|<span data-ttu-id="63288-121">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="63288-121">Data types</span></span>|<span data-ttu-id="63288-122">Relacionamento de argumento</span><span class="sxs-lookup"><span data-stu-id="63288-122">Argument relationship</span></span>|<span data-ttu-id="63288-123">Falha de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="63288-123">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="63288-124">Função CType</span><span class="sxs-lookup"><span data-stu-id="63288-124">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)|<span data-ttu-id="63288-125">Quaisquer tipos de dados</span><span class="sxs-lookup"><span data-stu-id="63288-125">Any data types</span></span>|<span data-ttu-id="63288-126">Ampliação ou restringir a conversão deve ser definido entre os dois tipos de dados</span><span class="sxs-lookup"><span data-stu-id="63288-126">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="63288-127">Lança<xref:System.InvalidCastException></xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="63288-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="63288-128">Operador DirectCast</span><span class="sxs-lookup"><span data-stu-id="63288-128">DirectCast Operator</span></span>](../../../visual-basic/language-reference/operators/directcast-operator.md)|<span data-ttu-id="63288-129">Quaisquer tipos de dados</span><span class="sxs-lookup"><span data-stu-id="63288-129">Any data types</span></span>|<span data-ttu-id="63288-130">Um tipo deve herdar de ou implementar o outro tipo</span><span class="sxs-lookup"><span data-stu-id="63288-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="63288-131">Lança<xref:System.InvalidCastException></xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="63288-131">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="63288-132">Somente tipos de referência</span><span class="sxs-lookup"><span data-stu-id="63288-132">Reference types only</span></span>|<span data-ttu-id="63288-133">Um tipo deve herdar de ou implementar o outro tipo</span><span class="sxs-lookup"><span data-stu-id="63288-133">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="63288-134">Retorna [nada](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="63288-134">Returns [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="63288-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="63288-135">Example</span></span>  
 <span data-ttu-id="63288-136">O exemplo a seguir mostra como usar `TryCast`.</span><span class="sxs-lookup"><span data-stu-id="63288-136">The following example shows how to use `TryCast`.</span></span>  
  
 <span data-ttu-id="63288-137">[!code-vb[VbVbalrKeywords n º&6;](../../../visual-basic/language-reference/codesnippet/VisualBasic/trycast-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="63288-137">[!code-vb[VbVbalrKeywords#6](../../../visual-basic/language-reference/codesnippet/VisualBasic/trycast-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63288-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63288-138">See Also</span></span>  
 <span data-ttu-id="63288-139">[Conversões entre](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="63288-139">[Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span></span>  
<span data-ttu-id="63288-140"> [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="63288-140"> [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)</span></span>
