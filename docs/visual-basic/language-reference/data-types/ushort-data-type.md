---
title: Tipo de Dados UShort
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400690"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="0a1da-102">UShort tipo de dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a1da-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="0a1da-103">Possui inteiros não assinados de 16 bits (2 bytes) variando em valor de 0 a 65.535.</span><span class="sxs-lookup"><span data-stu-id="0a1da-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a1da-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="0a1da-104">Remarks</span></span>

 <span data-ttu-id="0a1da-105">Use `UShort` o tipo de dados para conter `Byte`dados binários muito grandes para .</span><span class="sxs-lookup"><span data-stu-id="0a1da-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="0a1da-106">O valor padrão de `UShort` é 0.</span><span class="sxs-lookup"><span data-stu-id="0a1da-106">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="0a1da-107">Atribuições literais</span><span class="sxs-lookup"><span data-stu-id="0a1da-107">Literal assignments</span></span>

<span data-ttu-id="0a1da-108">Você pode declarar e `UShort` inicializar uma variável atribuindo-a um literal decimal, um literal hexadecimal, um literal octal, ou (começando com Visual Basic 2017) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="0a1da-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="0a1da-109">Se o literal inteiro estiver fora do intervalo de `UShort` (ou seja, se for menor que <xref:System.UInt16.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="0a1da-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="0a1da-110">No exemplo a seguir, inteiros iguais a 65.034 que são representados como decimais, hexadecimais e literais binários são atribuídos aos `UShort` valores.</span><span class="sxs-lookup"><span data-stu-id="0a1da-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="0a1da-111">Você usa `&h` o `&H` prefixo ou para denotar um literal `&b` `&B` hexadecimal, o prefixo ou para denotar um literal binário, e o prefixo `&o` ou `&O` para denotar um literal octal.</span><span class="sxs-lookup"><span data-stu-id="0a1da-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="0a1da-112">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="0a1da-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="0a1da-113">A partir do Visual Basic 2017, você `_`também pode usar o caractere sublinhado, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0a1da-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="0a1da-114">Começando com visual basic 15.5, você também`_`pode usar o caractere sublinhado ( ) como um separador líder entre o prefixo e os dígitos hexadecimal, binário ou octal.</span><span class="sxs-lookup"><span data-stu-id="0a1da-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="0a1da-115">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="0a1da-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="0a1da-116">Literais numéricos `US` também `us` podem incluir o `UShort` caractere ou [tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar o tipo de dados, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0a1da-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="0a1da-117">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="0a1da-117">Programming tips</span></span>
  
- <span data-ttu-id="0a1da-118">**Números Negativos.**</span><span class="sxs-lookup"><span data-stu-id="0a1da-118">**Negative Numbers.**</span></span> <span data-ttu-id="0a1da-119">Por `UShort` ser um tipo não assinado, ele não pode representar um número negativo.</span><span class="sxs-lookup"><span data-stu-id="0a1da-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="0a1da-120">Se você usar o`-`operador unary minus ( ) `UShort`em uma expressão que `Integer` avalia para digitar, visual basic converte a expressão para primeiro.</span><span class="sxs-lookup"><span data-stu-id="0a1da-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="0a1da-121">**Conformidade cls.**</span><span class="sxs-lookup"><span data-stu-id="0a1da-121">**CLS Compliance.**</span></span> <span data-ttu-id="0a1da-122">O `UShort` tipo de dados não faz parte da [Especificação de Linguagem Comum](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), portanto, o código compatível com CLS não pode consumir um componente que o use.</span><span class="sxs-lookup"><span data-stu-id="0a1da-122">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="0a1da-123">**Alargamento.**</span><span class="sxs-lookup"><span data-stu-id="0a1da-123">**Widening.**</span></span> <span data-ttu-id="0a1da-124">O `UShort` tipo de `Integer`dados `UInteger` `Long`se `ULong` `Decimal`expande para, , , , , `Single`, e `Double`.</span><span class="sxs-lookup"><span data-stu-id="0a1da-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="0a1da-125">Isso significa que `UShort` você pode converter para <xref:System.OverflowException?displayProperty=nameWithType> qualquer um desses tipos sem encontrar um erro.</span><span class="sxs-lookup"><span data-stu-id="0a1da-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="0a1da-126">**Digite caracteres.**</span><span class="sxs-lookup"><span data-stu-id="0a1da-126">**Type Characters.**</span></span> <span data-ttu-id="0a1da-127">Anexar os caracteres `US` do tipo literal `UShort` a um literal força-o ao tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="0a1da-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="0a1da-128">`UShort`não tem nenhum tipo de caractere identificador.</span><span class="sxs-lookup"><span data-stu-id="0a1da-128">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="0a1da-129">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="0a1da-129">**Framework Type.**</span></span> <span data-ttu-id="0a1da-130">O tipo correspondente no .NET Framework é a estrutura <xref:System.UInt16?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0a1da-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a1da-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="0a1da-131">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="0a1da-132">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="0a1da-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="0a1da-133">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="0a1da-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="0a1da-134">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="0a1da-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="0a1da-135">Como chamar uma função do Windows que use tipos não assinados</span><span class="sxs-lookup"><span data-stu-id="0a1da-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="0a1da-136">Uso eficiente de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="0a1da-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
