---
title: Tipo de Dados ULong
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: 3c6cd4086e08b808c158948756b4806f098196b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400697"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="02d60-102">ULong data type (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02d60-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="02d60-103">Possui inteiros não assinados de 64 bits (8 bytes) variando em valor de 0 a 18.446.744.073.709.551.615 (mais de 1,84 vezes 10 ^ 19).</span><span class="sxs-lookup"><span data-stu-id="02d60-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>

## <a name="remarks"></a><span data-ttu-id="02d60-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="02d60-104">Remarks</span></span>

<span data-ttu-id="02d60-105">Use `ULong` o tipo de dados para conter `UInteger`dados binários muito grandes para , ou os maiores valores inteiros não assinados possíveis.</span><span class="sxs-lookup"><span data-stu-id="02d60-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>

<span data-ttu-id="02d60-106">O valor padrão de `ULong` é 0.</span><span class="sxs-lookup"><span data-stu-id="02d60-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="02d60-107">Atribuições literais</span><span class="sxs-lookup"><span data-stu-id="02d60-107">Literal assignments</span></span>

<span data-ttu-id="02d60-108">Você pode declarar e `ULong` inicializar uma variável atribuindo-a um literal decimal, um literal hexadecimal, um literal octal, ou (começando com Visual Basic 2017) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="02d60-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="02d60-109">Se o literal inteiro estiver fora do intervalo de `ULong` (ou seja, se for menor que <xref:System.UInt64.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="02d60-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="02d60-110">No exemplo a seguir, inteiros iguais a 7.934.076.125 representados como literais decimais, hexadecimais e binários são atribuídos a valores `ULong`.</span><span class="sxs-lookup"><span data-stu-id="02d60-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> <span data-ttu-id="02d60-111">Você usa `&h` o `&H` prefixo ou para denotar um literal `&b` `&B` hexadecimal, o prefixo ou para denotar um literal binário, e o prefixo `&o` ou `&O` para denotar um literal octal.</span><span class="sxs-lookup"><span data-stu-id="02d60-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="02d60-112">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="02d60-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="02d60-113">A partir do Visual Basic 2017, você `_`também pode usar o caractere sublinhado, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="02d60-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="02d60-114">Começando com visual basic 15.5, você também`_`pode usar o caractere sublinhado ( ) como um separador líder entre o prefixo e os dígitos hexadecimal, binário ou octal.</span><span class="sxs-lookup"><span data-stu-id="02d60-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="02d60-115">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="02d60-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="02d60-116">Literais numéricos `UL` também `ul` podem incluir o `ULong` caractere ou [tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar o tipo de dados, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="02d60-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="02d60-117">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="02d60-117">Programming tips</span></span>

- <span data-ttu-id="02d60-118">**Números Negativos.**</span><span class="sxs-lookup"><span data-stu-id="02d60-118">**Negative Numbers.**</span></span> <span data-ttu-id="02d60-119">Por `ULong` ser um tipo não assinado, ele não pode representar um número negativo.</span><span class="sxs-lookup"><span data-stu-id="02d60-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="02d60-120">Se você usar o`-`operador unary minus ( ) `ULong`em uma expressão que `Decimal` avalia para digitar, visual basic converte a expressão para primeiro.</span><span class="sxs-lookup"><span data-stu-id="02d60-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>

- <span data-ttu-id="02d60-121">**Conformidade cls.**</span><span class="sxs-lookup"><span data-stu-id="02d60-121">**CLS Compliance.**</span></span> <span data-ttu-id="02d60-122">O `ULong` tipo de dados não faz parte da [Especificação de Linguagem Comum](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), portanto, o código compatível com CLS não pode consumir um componente que o use.</span><span class="sxs-lookup"><span data-stu-id="02d60-122">The `ULong` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="02d60-123">**Interop Considerações.**</span><span class="sxs-lookup"><span data-stu-id="02d60-123">**Interop Considerations.**</span></span> <span data-ttu-id="02d60-124">Se você estiver interagindo com componentes não gravados para o .NET Framework, por `ulong` exemplo, automação ou objetos COM, tenha em mente que tipos como podem ter uma largura de dados diferente (32 bits) em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="02d60-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="02d60-125">Se você estiver passando um argumento de 32 bits para um componente, declare-o como `UInteger` em vez de `ULong` em seu código Visual Basic gerenciado.</span><span class="sxs-lookup"><span data-stu-id="02d60-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>

  <span data-ttu-id="02d60-126">Além disso, a Automação não suporta inteiros de 64 bits no Windows 95, Windows 98, Windows ME ou Windows 2000.</span><span class="sxs-lookup"><span data-stu-id="02d60-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="02d60-127">Não é possível `ULong` passar um argumento Visual Basic para um componente de Automação nessas plataformas.</span><span class="sxs-lookup"><span data-stu-id="02d60-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>

- <span data-ttu-id="02d60-128">**Alargamento.**</span><span class="sxs-lookup"><span data-stu-id="02d60-128">**Widening.**</span></span> <span data-ttu-id="02d60-129">O `ULong` tipo de `Decimal`dados `Single`se `Double`expande para, e .</span><span class="sxs-lookup"><span data-stu-id="02d60-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="02d60-130">Isso significa que `ULong` você pode converter para <xref:System.OverflowException?displayProperty=nameWithType> qualquer um desses tipos sem encontrar um erro.</span><span class="sxs-lookup"><span data-stu-id="02d60-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="02d60-131">**Digite caracteres.**</span><span class="sxs-lookup"><span data-stu-id="02d60-131">**Type Characters.**</span></span> <span data-ttu-id="02d60-132">Anexar os caracteres `UL` do tipo literal `ULong` a um literal força-o ao tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="02d60-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="02d60-133">`ULong`não tem nenhum tipo de caractere identificador.</span><span class="sxs-lookup"><span data-stu-id="02d60-133">`ULong` has no identifier type character.</span></span>

- <span data-ttu-id="02d60-134">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="02d60-134">**Framework Type.**</span></span> <span data-ttu-id="02d60-135">O tipo correspondente no .NET Framework é a estrutura <xref:System.UInt64?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="02d60-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="02d60-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="02d60-136">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="02d60-137">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="02d60-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="02d60-138">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="02d60-138">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="02d60-139">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="02d60-139">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="02d60-140">Como chamar uma função do Windows que use tipos não assinados</span><span class="sxs-lookup"><span data-stu-id="02d60-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="02d60-141">Uso eficiente de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="02d60-141">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
