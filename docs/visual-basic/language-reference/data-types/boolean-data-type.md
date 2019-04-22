---
title: Tipo de dados booliano (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 7b64302d801a08f976de0ec969983c821f7a8471
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841207"
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="e72a1-102">Tipo de dados booliano (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e72a1-102">Boolean Data Type (Visual Basic)</span></span>
<span data-ttu-id="e72a1-103">Contém valores que podem ser apenas `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="e72a1-103">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="e72a1-104">As palavras-chave `True` e `False` correspondem aos dois estados de `Boolean` variáveis.</span><span class="sxs-lookup"><span data-stu-id="e72a1-104">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e72a1-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="e72a1-105">Remarks</span></span>  
 <span data-ttu-id="e72a1-106">Use o [(Visual Basic) do tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) para conter os valores de dois estados, como verdadeiro/falso, Sim/não ou ativado/desativado.</span><span class="sxs-lookup"><span data-stu-id="e72a1-106">Use the [Boolean Data Type (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="e72a1-107">O valor padrão de `Boolean` é `False`.</span><span class="sxs-lookup"><span data-stu-id="e72a1-107">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="e72a1-108">`Boolean` valores não são armazenados como números e os valores armazenados não pretendem ser equivalentes aos números.</span><span class="sxs-lookup"><span data-stu-id="e72a1-108">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="e72a1-109">Você nunca deve gravar códigos que contem com valores numéricos equivalentes para `True` e `False`.</span><span class="sxs-lookup"><span data-stu-id="e72a1-109">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="e72a1-110">Sempre que possível, você deve restringir o uso de `Boolean` variáveis para os valores lógicos para que elas são criadas.</span><span class="sxs-lookup"><span data-stu-id="e72a1-110">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="e72a1-111">Conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="e72a1-111">Type Conversions</span></span>  
 <span data-ttu-id="e72a1-112">Quando o Visual Basic converte valores de tipo de dados numéricos para `Boolean`, 0 se torna `False` e todos os outros valores se tornam `True`.</span><span class="sxs-lookup"><span data-stu-id="e72a1-112">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="e72a1-113">Quando o Visual Basic converte `Boolean` valores em tipos numéricos, `False` se torna 0 e `True` torna-se -1.</span><span class="sxs-lookup"><span data-stu-id="e72a1-113">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="e72a1-114">Ao converter entre `Boolean` valores e tipos de dados numéricos, tenha em mente que os métodos de conversão do .NET Framework nem sempre produzem os mesmos resultados que as palavras-chave de conversão do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e72a1-114">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="e72a1-115">Isso ocorre porque a conversão do Visual Basic retém o comportamento compatível com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="e72a1-115">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="e72a1-116">Para obter mais informações, consulte "Tipo booliano não converter para tipo numérico com precisão" em [solução de problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="e72a1-116">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="e72a1-117">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="e72a1-117">Programming Tips</span></span>  
  
-   <span data-ttu-id="e72a1-118">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="e72a1-118">**Negative Numbers.**</span></span> <span data-ttu-id="e72a1-119">`Boolean` não é um tipo numérico e não pode representar um valor negativo.</span><span class="sxs-lookup"><span data-stu-id="e72a1-119">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="e72a1-120">Em qualquer caso, você não deve usar `Boolean` para armazenar valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="e72a1-120">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="e72a1-121">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="e72a1-121">**Type Characters.**</span></span> <span data-ttu-id="e72a1-122">`Boolean` não tem nenhum caractere de tipo literal ou um caractere de tipo identificador.</span><span class="sxs-lookup"><span data-stu-id="e72a1-122">`Boolean` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="e72a1-123">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="e72a1-123">**Framework Type.**</span></span> <span data-ttu-id="e72a1-124">O tipo correspondente no .NET Framework é a estrutura <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e72a1-124">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e72a1-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e72a1-125">Example</span></span>  
 <span data-ttu-id="e72a1-126">No exemplo a seguir `runningVB` é um `Boolean` variável, que armazena um simples configuração Sim/não.</span><span class="sxs-lookup"><span data-stu-id="e72a1-126">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="e72a1-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e72a1-127">See also</span></span>

- <xref:System.Boolean?displayProperty=nameWithType>
- [<span data-ttu-id="e72a1-128">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="e72a1-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="e72a1-129">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="e72a1-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="e72a1-130">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="e72a1-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="e72a1-131">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="e72a1-131">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="e72a1-132">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="e72a1-132">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="e72a1-133">Função CType</span><span class="sxs-lookup"><span data-stu-id="e72a1-133">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
