---
title: Tipo de dados UShort
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: 7cdbd5fb192fd5cc1be6260dcdcdb1f30cf3f865
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343860"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="cca92-102">Tipo de dados UShort (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cca92-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="cca92-103">Mantém inteiros de 16 bits (2 bytes) não assinados, variando no valor de 0 a 65.535.</span><span class="sxs-lookup"><span data-stu-id="cca92-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cca92-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="cca92-104">Remarks</span></span>

 <span data-ttu-id="cca92-105">Use o tipo de dados `UShort` para conter dados binários muito grandes para `Byte`.</span><span class="sxs-lookup"><span data-stu-id="cca92-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="cca92-106">O valor padrão de `UShort` é 0.</span><span class="sxs-lookup"><span data-stu-id="cca92-106">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="cca92-107">Atribuições de literal</span><span class="sxs-lookup"><span data-stu-id="cca92-107">Literal assignments</span></span>

<span data-ttu-id="cca92-108">Você pode declarar e inicializar uma variável `UShort` atribuindo-lhe um literal decimal, um literal hexadecimal, um literal octal ou (começando com Visual Basic 2017) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="cca92-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="cca92-109">Se o literal inteiro estiver fora do intervalo de `UShort` (ou seja, se for menor que <xref:System.UInt16.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="cca92-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="cca92-110">No exemplo a seguir, números inteiros iguais a 65.034 que são representados como decimais, hexadecimais e literais binários são atribuídos a `UShort` valores.</span><span class="sxs-lookup"><span data-stu-id="cca92-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="cca92-111">Você usa o prefixo `&h` ou `&H` para indicar um literal hexadecimal, o prefixo `&b` ou `&B` para denotar um literal binário e o prefixo `&o` ou `&O` para indicar um literal octal.</span><span class="sxs-lookup"><span data-stu-id="cca92-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="cca92-112">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="cca92-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="cca92-113">A partir do Visual Basic 2017, você também pode usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="cca92-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="cca92-114">A partir do Visual Basic 15,5, você também pode usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos hexadecimal, binário ou octal.</span><span class="sxs-lookup"><span data-stu-id="cca92-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="cca92-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="cca92-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="cca92-116">Os literais numéricos também podem incluir o `US` ou `us` [caractere de tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar o tipo de dados `UShort`, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="cca92-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="cca92-117">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="cca92-117">Programming tips</span></span>
  
- <span data-ttu-id="cca92-118">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="cca92-118">**Negative Numbers.**</span></span> <span data-ttu-id="cca92-119">Como `UShort` é um tipo não assinado, ele não pode representar um número negativo.</span><span class="sxs-lookup"><span data-stu-id="cca92-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="cca92-120">Se você usar o operador menos unário (`-`) em uma expressão avaliada como tipo `UShort`, Visual Basic converterá a expressão para `Integer` primeiro.</span><span class="sxs-lookup"><span data-stu-id="cca92-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="cca92-121">**Conformidade com CLS.**</span><span class="sxs-lookup"><span data-stu-id="cca92-121">**CLS Compliance.**</span></span> <span data-ttu-id="cca92-122">O tipo de dados `UShort` não faz parte do [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), portanto o código em conformidade com CLS não pode consumir um componente que o utiliza.</span><span class="sxs-lookup"><span data-stu-id="cca92-122">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="cca92-123">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="cca92-123">**Widening.**</span></span> <span data-ttu-id="cca92-124">O tipo de dados `UShort` amplia a `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`e `Double`.</span><span class="sxs-lookup"><span data-stu-id="cca92-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="cca92-125">Isso significa que você pode converter `UShort` em qualquer um desses tipos sem encontrar um erro de <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cca92-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="cca92-126">**Digite os caracteres.**</span><span class="sxs-lookup"><span data-stu-id="cca92-126">**Type Characters.**</span></span> <span data-ttu-id="cca92-127">Acrescentar os caracteres do tipo literal `US` a um literal o força ao tipo de dados `UShort`.</span><span class="sxs-lookup"><span data-stu-id="cca92-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="cca92-128">`UShort` não tem um caractere de tipo de identificador.</span><span class="sxs-lookup"><span data-stu-id="cca92-128">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="cca92-129">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="cca92-129">**Framework Type.**</span></span> <span data-ttu-id="cca92-130">O tipo correspondente no .NET Framework é a estrutura <xref:System.UInt16?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cca92-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cca92-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cca92-131">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="cca92-132">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="cca92-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="cca92-133">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="cca92-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="cca92-134">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="cca92-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="cca92-135">Como chamar uma função do Windows que use tipos não assinados</span><span class="sxs-lookup"><span data-stu-id="cca92-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="cca92-136">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="cca92-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
