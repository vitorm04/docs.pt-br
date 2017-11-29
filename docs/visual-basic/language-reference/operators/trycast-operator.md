---
title: Operador TryCast (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords: TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6be11b49eb3b9d98e3bf147e9b1026d4ffc860c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="5e7fa-102">Operador TryCast (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e7fa-102">TryCast Operator (Visual Basic)</span></span>
<span data-ttu-id="5e7fa-103">Apresenta uma operação de conversão de tipo que não gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5e7fa-103">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e7fa-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="5e7fa-104">Remarks</span></span>  
 <span data-ttu-id="5e7fa-105">Se uma tentativa de conversão falhar, `CType` e `DirectCast` ambos lançam um <xref:System.InvalidCastException> erro.</span><span class="sxs-lookup"><span data-stu-id="5e7fa-105">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="5e7fa-106">Isso pode afetar o desempenho do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5e7fa-106">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="5e7fa-107">`TryCast`Retorna [nada](../../../visual-basic/language-reference/nothing.md), de modo que, em vez de ter que lidar com uma possível exceção, você só precisa testar o resultado retornado em `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="5e7fa-107">`TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="5e7fa-108">Você usa o `TryCast` palavra-chave da mesma maneira que você usar o [função CType](../../../visual-basic/language-reference/functions/ctype-function.md) e [operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="5e7fa-108">You use the `TryCast` keyword the same way you use the [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) and the [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) keyword.</span></span> <span data-ttu-id="5e7fa-109">Você fornece uma expressão como o primeiro argumento e um tipo para convertê-lo para o segundo argumento.</span><span class="sxs-lookup"><span data-stu-id="5e7fa-109">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="5e7fa-110">`TryCast`funciona apenas em tipos de referência, como classes e interfaces.</span><span class="sxs-lookup"><span data-stu-id="5e7fa-110">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="5e7fa-111">Ele requer uma relação de herança ou implementação entre os dois tipos.</span><span class="sxs-lookup"><span data-stu-id="5e7fa-111">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="5e7fa-112">Isso significa que um tipo deve herdar de ou implementar o outro.</span><span class="sxs-lookup"><span data-stu-id="5e7fa-112">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="5e7fa-113">Erros e falhas</span><span class="sxs-lookup"><span data-stu-id="5e7fa-113">Errors and Failures</span></span>  
 <span data-ttu-id="5e7fa-114">`TryCast`gera um erro do compilador se ele detecta que não existe nenhuma relação de herança ou implementação.</span><span class="sxs-lookup"><span data-stu-id="5e7fa-114">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="5e7fa-115">Mas a falta de um erro do compilador não garante uma conversão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="5e7fa-115">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="5e7fa-116">Se a conversão desejada é de restrição, ele poderá falhar em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5e7fa-116">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="5e7fa-117">Se isso acontecer, `TryCast` retorna [nada](../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="5e7fa-117">If this happens, `TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="5e7fa-118">Palavras-chave de conversão</span><span class="sxs-lookup"><span data-stu-id="5e7fa-118">Conversion Keywords</span></span>  
 <span data-ttu-id="5e7fa-119">Uma comparação entre as palavras-chave de conversão de tipo é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="5e7fa-119">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="5e7fa-120">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="5e7fa-120">Keyword</span></span>|<span data-ttu-id="5e7fa-121">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="5e7fa-121">Data types</span></span>|<span data-ttu-id="5e7fa-122">Relacionamento de argumento</span><span class="sxs-lookup"><span data-stu-id="5e7fa-122">Argument relationship</span></span>|<span data-ttu-id="5e7fa-123">Falha de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5e7fa-123">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="5e7fa-124">Função CType</span><span class="sxs-lookup"><span data-stu-id="5e7fa-124">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)|<span data-ttu-id="5e7fa-125">Quaisquer tipos de dados</span><span class="sxs-lookup"><span data-stu-id="5e7fa-125">Any data types</span></span>|<span data-ttu-id="5e7fa-126">Widening ou conversão de estreitamento deve ser definido entre os dois tipos de dados</span><span class="sxs-lookup"><span data-stu-id="5e7fa-126">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="5e7fa-127">Lança<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="5e7fa-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="5e7fa-128">Operador DirectCast</span><span class="sxs-lookup"><span data-stu-id="5e7fa-128">DirectCast Operator</span></span>](../../../visual-basic/language-reference/operators/directcast-operator.md)|<span data-ttu-id="5e7fa-129">Quaisquer tipos de dados</span><span class="sxs-lookup"><span data-stu-id="5e7fa-129">Any data types</span></span>|<span data-ttu-id="5e7fa-130">Um tipo deve herdar de ou implementar o outro tipo</span><span class="sxs-lookup"><span data-stu-id="5e7fa-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="5e7fa-131">Lança<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="5e7fa-131">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="5e7fa-132">Somente tipos de referência</span><span class="sxs-lookup"><span data-stu-id="5e7fa-132">Reference types only</span></span>|<span data-ttu-id="5e7fa-133">Um tipo deve herdar de ou implementar o outro tipo</span><span class="sxs-lookup"><span data-stu-id="5e7fa-133">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="5e7fa-134">Retorna [nada](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="5e7fa-134">Returns [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5e7fa-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5e7fa-135">Example</span></span>  
 <span data-ttu-id="5e7fa-136">O exemplo a seguir mostra como usar `TryCast`.</span><span class="sxs-lookup"><span data-stu-id="5e7fa-136">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](../../../visual-basic/language-reference/codesnippet/VisualBasic/trycast-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5e7fa-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e7fa-137">See Also</span></span>  
 [<span data-ttu-id="5e7fa-138">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="5e7fa-138">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="5e7fa-139">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="5e7fa-139">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
