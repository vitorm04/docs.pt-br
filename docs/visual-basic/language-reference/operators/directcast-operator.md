---
title: Operador DirectCast
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 7b070b8eba240440821f7984a9336c2ecaf61706
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867087"
---
# <a name="directcast-operator-visual-basic"></a><span data-ttu-id="f209c-102">Operador DirectCast (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f209c-102">DirectCast Operator (Visual Basic)</span></span>

<span data-ttu-id="f209c-103">Apresenta uma operação de conversão de tipo baseada na herança ou implementação.</span><span class="sxs-lookup"><span data-stu-id="f209c-103">Introduces a type conversion operation based on inheritance or implementation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f209c-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="f209c-104">Remarks</span></span>  

 <span data-ttu-id="f209c-105">`DirectCast` o não usa as rotinas auxiliares de tempo de execução Visual Basic para conversão, para que possa fornecer um desempenho um pouco melhor do que `CType` ao converter de e para o tipo de dados `Object` .</span><span class="sxs-lookup"><span data-stu-id="f209c-105">`DirectCast` does not use the Visual Basic run-time helper routines for conversion, so it can provide somewhat better performance than `CType` when converting to and from data type `Object`.</span></span>  
  
 <span data-ttu-id="f209c-106">Você usa a `DirectCast` palavra-chave semelhante à maneira como usa a [função CType](../functions/ctype-function.md) e a palavra-chave do [Operador TryCast](trycast-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="f209c-106">You use the `DirectCast` keyword similar to the way you use the [CType Function](../functions/ctype-function.md) and the [TryCast Operator](trycast-operator.md) keyword.</span></span> <span data-ttu-id="f209c-107">Você fornece uma expressão como o primeiro argumento e um tipo para convertê-lo como o segundo argumento.</span><span class="sxs-lookup"><span data-stu-id="f209c-107">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="f209c-108">`DirectCast` requer uma relação de herança ou de implementação entre os tipos de dados dos dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="f209c-108">`DirectCast` requires an inheritance or implementation relationship between the data types of the two arguments.</span></span> <span data-ttu-id="f209c-109">Isso significa que um tipo deve herdar ou implementar o outro.</span><span class="sxs-lookup"><span data-stu-id="f209c-109">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="f209c-110">Erros e falhas</span><span class="sxs-lookup"><span data-stu-id="f209c-110">Errors and Failures</span></span>  

 <span data-ttu-id="f209c-111">`DirectCast` gera um erro do compilador se detectar que não existe nenhuma relação de herança ou implementação.</span><span class="sxs-lookup"><span data-stu-id="f209c-111">`DirectCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="f209c-112">Mas a falta de um erro do compilador não garante uma conversão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="f209c-112">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="f209c-113">Se a conversão desejada for restrita, ela poderá falhar em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f209c-113">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="f209c-114">Se isso acontecer, o tempo de execução gera um <xref:System.InvalidCastException> erro.</span><span class="sxs-lookup"><span data-stu-id="f209c-114">If this happens, the runtime throws an <xref:System.InvalidCastException> error.</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="f209c-115">Palavras-chave de conversão</span><span class="sxs-lookup"><span data-stu-id="f209c-115">Conversion Keywords</span></span>  

 <span data-ttu-id="f209c-116">Uma comparação das palavras-chave de conversão de tipo é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="f209c-116">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="f209c-117">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="f209c-117">Keyword</span></span>|<span data-ttu-id="f209c-118">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="f209c-118">Data types</span></span>|<span data-ttu-id="f209c-119">Relação de argumento</span><span class="sxs-lookup"><span data-stu-id="f209c-119">Argument relationship</span></span>|<span data-ttu-id="f209c-120">Falha de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="f209c-120">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="f209c-121">Função CType</span><span class="sxs-lookup"><span data-stu-id="f209c-121">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="f209c-122">Quaisquer tipos de dados</span><span class="sxs-lookup"><span data-stu-id="f209c-122">Any data types</span></span>|<span data-ttu-id="f209c-123">A conversão de alargamento ou de estreitamento deve ser definida entre os dois tipos de dados</span><span class="sxs-lookup"><span data-stu-id="f209c-123">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="f209c-124">Emite <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="f209c-124">Throws <xref:System.InvalidCastException></span></span>|  
|`DirectCast`|<span data-ttu-id="f209c-125">Quaisquer tipos de dados</span><span class="sxs-lookup"><span data-stu-id="f209c-125">Any data types</span></span>|<span data-ttu-id="f209c-126">Um tipo deve herdar ou implementar o outro tipo</span><span class="sxs-lookup"><span data-stu-id="f209c-126">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="f209c-127">Emite <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="f209c-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="f209c-128">Operador TryCast</span><span class="sxs-lookup"><span data-stu-id="f209c-128">TryCast Operator</span></span>](trycast-operator.md)|<span data-ttu-id="f209c-129">Somente tipos de referência</span><span class="sxs-lookup"><span data-stu-id="f209c-129">Reference types only</span></span>|<span data-ttu-id="f209c-130">Um tipo deve herdar ou implementar o outro tipo</span><span class="sxs-lookup"><span data-stu-id="f209c-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="f209c-131">Não retorna [nada](../nothing.md)</span><span class="sxs-lookup"><span data-stu-id="f209c-131">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f209c-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f209c-132">Example</span></span>  

 <span data-ttu-id="f209c-133">O exemplo a seguir demonstra dois usos de `DirectCast` , um que falha em tempo de execução e um que é bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="f209c-133">The following example demonstrates two uses of `DirectCast`, one that fails at run time and one that succeeds.</span></span>  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 <span data-ttu-id="f209c-134">No exemplo anterior, o tipo de tempo de execução de `q` é `Double` .</span><span class="sxs-lookup"><span data-stu-id="f209c-134">In the preceding example, the run-time type of `q` is `Double`.</span></span> <span data-ttu-id="f209c-135">`CType` tem sucesso porque `Double` pode ser convertido em `Integer` .</span><span class="sxs-lookup"><span data-stu-id="f209c-135">`CType` succeeds because `Double` can be converted to `Integer`.</span></span> <span data-ttu-id="f209c-136">No entanto, a primeira `DirectCast` falha em tempo de execução porque o tipo de tempo de execução de `Double` não tem nenhuma relação de herança com `Integer` , embora exista uma conversão.</span><span class="sxs-lookup"><span data-stu-id="f209c-136">However, the first `DirectCast` fails at run time because the run-time type of `Double` has no inheritance relationship with `Integer`, even though a conversion exists.</span></span> <span data-ttu-id="f209c-137">O segundo `DirectCast` é executado com sucesso porque converte de tipo <xref:System.Windows.Forms.Form> para tipo <xref:System.Windows.Forms.Control> , do qual <xref:System.Windows.Forms.Form> herda.</span><span class="sxs-lookup"><span data-stu-id="f209c-137">The second `DirectCast` succeeds because it converts from type <xref:System.Windows.Forms.Form> to type <xref:System.Windows.Forms.Control>, from which <xref:System.Windows.Forms.Form> inherits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f209c-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="f209c-138">See also</span></span>

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f209c-139">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="f209c-139">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="f209c-140">Conversões implícitas e explícitas</span><span class="sxs-lookup"><span data-stu-id="f209c-140">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
