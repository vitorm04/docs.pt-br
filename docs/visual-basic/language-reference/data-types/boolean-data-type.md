---
title: Tipo de dados booliano
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
ms.openlocfilehash: 851c524a83c5f24b77a151634a96798249c5905e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374415"
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="386ec-102">Tipo de dados booliano (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="386ec-102">Boolean Data Type (Visual Basic)</span></span>

<span data-ttu-id="386ec-103">Contém valores que podem ser apenas `True` ou `False` .</span><span class="sxs-lookup"><span data-stu-id="386ec-103">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="386ec-104">As palavras-chave `True` e `False` correspondem aos dois Estados de `Boolean` variáveis.</span><span class="sxs-lookup"><span data-stu-id="386ec-104">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="386ec-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="386ec-105">Remarks</span></span>  

 <span data-ttu-id="386ec-106">Use o [tipo de dados booliano (Visual Basic)](boolean-data-type.md) para conter valores de dois Estados, como true/false, yes/no ou on/off.</span><span class="sxs-lookup"><span data-stu-id="386ec-106">Use the [Boolean Data Type (Visual Basic)](boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="386ec-107">O valor padrão de `Boolean` é `False`.</span><span class="sxs-lookup"><span data-stu-id="386ec-107">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="386ec-108">`Boolean`os valores não são armazenados como números e os valores armazenados não devem ser equivalentes aos números.</span><span class="sxs-lookup"><span data-stu-id="386ec-108">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="386ec-109">Você nunca deve escrever código que dependa de valores numéricos equivalentes para `True` e `False` .</span><span class="sxs-lookup"><span data-stu-id="386ec-109">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="386ec-110">Sempre que possível, você deve restringir o uso de `Boolean` variáveis para os valores lógicos para os quais elas foram projetadas.</span><span class="sxs-lookup"><span data-stu-id="386ec-110">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="386ec-111">Conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="386ec-111">Type Conversions</span></span>  

 <span data-ttu-id="386ec-112">Quando Visual Basic converte valores de tipo de dados numéricos para `Boolean` , 0 se torna `False` e todos os outros valores se tornam `True` .</span><span class="sxs-lookup"><span data-stu-id="386ec-112">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="386ec-113">Quando Visual Basic converte `Boolean` valores em tipos numéricos, `False` torna-se 0 e `True` se torna-1.</span><span class="sxs-lookup"><span data-stu-id="386ec-113">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="386ec-114">Ao converter entre `Boolean` valores e tipos de dados numéricos, tenha em mente que os métodos de conversão de .NET Framework nem sempre produzem os mesmos resultados que as palavras-chave de conversão de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="386ec-114">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="386ec-115">Isso ocorre porque a conversão de Visual Basic retém o comportamento compatível com as versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="386ec-115">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="386ec-116">Para obter mais informações, consulte "o tipo booliano não converte em tipo numérico com precisão" em [tipos de dados de solução de problemas](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="386ec-116">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="386ec-117">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="386ec-117">Programming Tips</span></span>  
  
- <span data-ttu-id="386ec-118">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="386ec-118">**Negative Numbers.**</span></span> <span data-ttu-id="386ec-119">`Boolean`Não é um tipo numérico e não pode representar um valor negativo.</span><span class="sxs-lookup"><span data-stu-id="386ec-119">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="386ec-120">Em qualquer caso, você não deve usar `Boolean` para armazenar valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="386ec-120">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
- <span data-ttu-id="386ec-121">**Digite os caracteres.**</span><span class="sxs-lookup"><span data-stu-id="386ec-121">**Type Characters.**</span></span> <span data-ttu-id="386ec-122">`Boolean`Não tem caractere de tipo literal ou caractere de tipo de identificador.</span><span class="sxs-lookup"><span data-stu-id="386ec-122">`Boolean` has no literal type character or identifier type character.</span></span>  
  
- <span data-ttu-id="386ec-123">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="386ec-123">**Framework Type.**</span></span> <span data-ttu-id="386ec-124">O tipo correspondente no .NET Framework é a estrutura <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="386ec-124">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="386ec-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="386ec-125">Example</span></span>  

 <span data-ttu-id="386ec-126">No exemplo a seguir, `runningVB` é uma `Boolean` variável, que armazena uma configuração Sim/não simples.</span><span class="sxs-lookup"><span data-stu-id="386ec-126">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="386ec-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="386ec-127">See also</span></span>

- <xref:System.Boolean?displayProperty=nameWithType>
- [<span data-ttu-id="386ec-128">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="386ec-128">Data Types</span></span>](index.md)
- [<span data-ttu-id="386ec-129">Funções de conversão do tipo</span><span class="sxs-lookup"><span data-stu-id="386ec-129">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="386ec-130">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="386ec-130">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="386ec-131">Uso eficiente de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="386ec-131">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="386ec-132">Solução de problemas de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="386ec-132">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="386ec-133">Função CType</span><span class="sxs-lookup"><span data-stu-id="386ec-133">CType Function</span></span>](../functions/ctype-function.md)
