---
title: Operador TryCast
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: dc4807781f9e1aaf894016952911bd7b32c42948
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875318"
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="ce790-102">Operador TryCast (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce790-102">TryCast Operator (Visual Basic)</span></span>

<span data-ttu-id="ce790-103">Apresenta uma operação de conversão de tipo que não gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="ce790-103">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce790-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="ce790-104">Remarks</span></span>  

 <span data-ttu-id="ce790-105">Se uma tentativa de conversão falhar, `CType` e `DirectCast` os dois geram um <xref:System.InvalidCastException> erro.</span><span class="sxs-lookup"><span data-stu-id="ce790-105">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="ce790-106">Isso pode afetar negativamente o desempenho do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce790-106">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="ce790-107">`TryCast` Não retorna [nada](../nothing.md), de modo que, em vez de ter que lidar com uma possível exceção, você só precisa testar o resultado retornado `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="ce790-107">`TryCast` returns [Nothing](../nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="ce790-108">Você usa a `TryCast` palavra-chave da mesma maneira que usa a [função CType](../functions/ctype-function.md) e a palavra-chave [DirectCast Operator](directcast-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="ce790-108">You use the `TryCast` keyword the same way you use the [CType Function](../functions/ctype-function.md) and the [DirectCast Operator](directcast-operator.md) keyword.</span></span> <span data-ttu-id="ce790-109">Você fornece uma expressão como o primeiro argumento e um tipo para convertê-lo como o segundo argumento.</span><span class="sxs-lookup"><span data-stu-id="ce790-109">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="ce790-110">`TryCast` funciona somente em tipos de referência, como classes e interfaces.</span><span class="sxs-lookup"><span data-stu-id="ce790-110">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="ce790-111">Ele requer uma relação de herança ou de implementação entre os dois tipos.</span><span class="sxs-lookup"><span data-stu-id="ce790-111">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="ce790-112">Isso significa que um tipo deve herdar ou implementar o outro.</span><span class="sxs-lookup"><span data-stu-id="ce790-112">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="ce790-113">Erros e falhas</span><span class="sxs-lookup"><span data-stu-id="ce790-113">Errors and Failures</span></span>  

 <span data-ttu-id="ce790-114">`TryCast` gera um erro do compilador se detectar que não existe nenhuma relação de herança ou implementação.</span><span class="sxs-lookup"><span data-stu-id="ce790-114">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="ce790-115">Mas a falta de um erro do compilador não garante uma conversão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="ce790-115">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="ce790-116">Se a conversão desejada for restrita, ela poderá falhar em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ce790-116">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="ce790-117">Se isso acontecer, o não `TryCast` retornará [nada](../nothing.md).</span><span class="sxs-lookup"><span data-stu-id="ce790-117">If this happens, `TryCast` returns [Nothing](../nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="ce790-118">Palavras-chave de conversão</span><span class="sxs-lookup"><span data-stu-id="ce790-118">Conversion Keywords</span></span>  

 <span data-ttu-id="ce790-119">Uma comparação das palavras-chave de conversão de tipo é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="ce790-119">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="ce790-120">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="ce790-120">Keyword</span></span>|<span data-ttu-id="ce790-121">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="ce790-121">Data types</span></span>|<span data-ttu-id="ce790-122">Relação de argumento</span><span class="sxs-lookup"><span data-stu-id="ce790-122">Argument relationship</span></span>|<span data-ttu-id="ce790-123">Falha de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="ce790-123">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="ce790-124">Função CType</span><span class="sxs-lookup"><span data-stu-id="ce790-124">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="ce790-125">Quaisquer tipos de dados</span><span class="sxs-lookup"><span data-stu-id="ce790-125">Any data types</span></span>|<span data-ttu-id="ce790-126">A conversão de alargamento ou de estreitamento deve ser definida entre os dois tipos de dados</span><span class="sxs-lookup"><span data-stu-id="ce790-126">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="ce790-127">Emite <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="ce790-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="ce790-128">Operador DirectCast</span><span class="sxs-lookup"><span data-stu-id="ce790-128">DirectCast Operator</span></span>](directcast-operator.md)|<span data-ttu-id="ce790-129">Quaisquer tipos de dados</span><span class="sxs-lookup"><span data-stu-id="ce790-129">Any data types</span></span>|<span data-ttu-id="ce790-130">Um tipo deve herdar ou implementar o outro tipo</span><span class="sxs-lookup"><span data-stu-id="ce790-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="ce790-131">Emite <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="ce790-131">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="ce790-132">Somente tipos de referência</span><span class="sxs-lookup"><span data-stu-id="ce790-132">Reference types only</span></span>|<span data-ttu-id="ce790-133">Um tipo deve herdar ou implementar o outro tipo</span><span class="sxs-lookup"><span data-stu-id="ce790-133">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="ce790-134">Não retorna [nada](../nothing.md)</span><span class="sxs-lookup"><span data-stu-id="ce790-134">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ce790-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ce790-135">Example</span></span>  

 <span data-ttu-id="ce790-136">O exemplo a seguir mostra como usar `TryCast`.</span><span class="sxs-lookup"><span data-stu-id="ce790-136">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="ce790-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="ce790-137">See also</span></span>

- [<span data-ttu-id="ce790-138">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="ce790-138">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="ce790-139">Conversões implícitas e explícitas</span><span class="sxs-lookup"><span data-stu-id="ce790-139">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
