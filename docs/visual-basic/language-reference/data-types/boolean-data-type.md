---
title: Tipo de dados booliano (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bdc106f1ec874c1a2165df069d5f3485fe5b2e43
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="4a5b5-102">Tipo de dados booliano (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a5b5-102">Boolean Data Type (Visual Basic)</span></span>
<span data-ttu-id="4a5b5-103">Contém valores que podem ser apenas `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-103">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="4a5b5-104">As palavras-chave `True` e `False` correspondem aos dois estados de `Boolean` variáveis.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-104">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a5b5-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a5b5-105">Remarks</span></span>  
 <span data-ttu-id="4a5b5-106">Use o [(Visual Basic) do tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) conter valores de dois estados, como verdadeiro/falso, Sim/Não, ou ativado/desativado.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-106">Use the [Boolean Data Type (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="4a5b5-107">O valor padrão de `Boolean` é `False`.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-107">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="4a5b5-108">`Boolean`valores não são armazenados como números, e os valores armazenados não devem ser equivalentes a números.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-108">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="4a5b5-109">Você nunca deve gravar códigos que contem com valores numéricos equivalentes para `True` e `False`.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-109">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="4a5b5-110">Sempre que possível, você deve restringir o uso de `Boolean` variáveis para os valores lógicos para os quais eles são criados.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-110">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="4a5b5-111">Conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="4a5b5-111">Type Conversions</span></span>  
 <span data-ttu-id="4a5b5-112">Quando o Visual Basic converte valores de tipo de dados numéricos para `Boolean`, 0 se torna `False` e todos os outros valores tornam-se `True`.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-112">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="4a5b5-113">Quando o Visual Basic converte `Boolean` valores para tipos numéricos, `False` se torna 0 e `True` torna-se -1.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-113">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="4a5b5-114">Ao converter entre `Boolean` valores e tipos de dados numéricos, tenha em mente que os métodos de conversão do .NET Framework nem sempre produzem os mesmos resultados que as palavras-chave de conversão do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-114">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="4a5b5-115">Isso ocorre porque a conversão do Visual Basic retém o comportamento compatível com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-115">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="4a5b5-116">Para obter mais informações, consulte "Tipo booleano não converter para tipo numérico com precisão" em [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="4a5b5-116">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="4a5b5-117">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="4a5b5-117">Programming Tips</span></span>  
  
-   <span data-ttu-id="4a5b5-118">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="4a5b5-118">**Negative Numbers.**</span></span> <span data-ttu-id="4a5b5-119">`Boolean`não é um tipo numérico e não pode representar um valor negativo.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-119">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="4a5b5-120">Em qualquer caso, você não deve usar `Boolean` para armazenar valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-120">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="4a5b5-121">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="4a5b5-121">**Type Characters.**</span></span> <span data-ttu-id="4a5b5-122">`Boolean`não tem o caractere de tipo literal ou caractere de tipo identificador.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-122">`Boolean` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="4a5b5-123">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="4a5b5-123">**Framework Type.**</span></span> <span data-ttu-id="4a5b5-124">O tipo correspondente no .NET Framework é a estrutura <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-124">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a5b5-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4a5b5-125">Example</span></span>  
 <span data-ttu-id="4a5b5-126">No exemplo a seguir, `runningVB` é um `Boolean` variável, que armazena um simples configuração Sim/não.</span><span class="sxs-lookup"><span data-stu-id="4a5b5-126">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a5b5-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a5b5-127">See Also</span></span>  
 <xref:System.Boolean?displayProperty=nameWithType>  
 [<span data-ttu-id="4a5b5-128">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="4a5b5-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="4a5b5-129">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="4a5b5-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="4a5b5-130">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="4a5b5-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="4a5b5-131">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="4a5b5-131">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="4a5b5-132">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="4a5b5-132">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="4a5b5-133">Função CType</span><span class="sxs-lookup"><span data-stu-id="4a5b5-133">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
