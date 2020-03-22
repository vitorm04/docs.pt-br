---
title: Tipo de Dados UInteger
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400781"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="d7488-102">tipo de dados UInteger</span><span class="sxs-lookup"><span data-stu-id="d7488-102">UInteger data type</span></span>

<span data-ttu-id="d7488-103">Possui inteiros não assinados de 32 bits (4 bytes) variando em valor de 0 a 4.294.967.295.</span><span class="sxs-lookup"><span data-stu-id="d7488-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7488-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7488-104">Remarks</span></span>

<span data-ttu-id="d7488-105">O `UInteger` tipo de dados fornece o maior valor não assinado na largura de dados mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="d7488-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="d7488-106">O valor padrão de `UInteger` é 0.</span><span class="sxs-lookup"><span data-stu-id="d7488-106">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="d7488-107">Atribuições literais</span><span class="sxs-lookup"><span data-stu-id="d7488-107">Literal assignments</span></span>

<span data-ttu-id="d7488-108">Você pode declarar e `UInteger` inicializar uma variável atribuindo-a um literal decimal, um literal hexadecimal, um literal octal, ou (começando com Visual Basic 2017) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="d7488-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="d7488-109">Se o literal inteiro estiver fora do intervalo de `UInteger` (ou seja, se for menor que <xref:System.UInt32.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="d7488-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="d7488-110">No exemplo a seguir, inteiros iguais a 3.000.000.000 representados como literais decimais, hexadecimais e binários são atribuídos a valores `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="d7488-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="d7488-111">Você usa `&h` o `&H` prefixo ou para denotar um literal `&b` `&B` hexadecimal, o prefixo ou para denotar um literal binário, e o prefixo `&o` ou `&O` para denotar um literal octal.</span><span class="sxs-lookup"><span data-stu-id="d7488-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="d7488-112">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="d7488-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="d7488-113">A partir do Visual Basic 2017, você `_`também pode usar o caractere sublinhado, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d7488-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="d7488-114">Começando com visual basic 15.5, você também`_`pode usar o caractere sublinhado ( ) como um separador líder entre o prefixo e os dígitos hexadecimal, binário ou octal.</span><span class="sxs-lookup"><span data-stu-id="d7488-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="d7488-115">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="d7488-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="d7488-116">Literais numéricos `UI` também `ui` podem incluir o `UInteger` caractere ou [tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar o tipo de dados, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d7488-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="d7488-117">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="d7488-117">Programming tips</span></span>

<span data-ttu-id="d7488-118">Os `UInteger` `Integer` tipos de dados fornecem um desempenho ótimo em um processador de`UShort`32 bits, porque os tipos inteiros menores ( , `Short`e `Byte` `SByte`), mesmo que eles usam menos bits, levam mais tempo para carregar, armazenar e buscar.</span><span class="sxs-lookup"><span data-stu-id="d7488-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="d7488-119">**Números Negativos.**</span><span class="sxs-lookup"><span data-stu-id="d7488-119">**Negative Numbers.**</span></span> <span data-ttu-id="d7488-120">Por `UInteger` ser um tipo não assinado, ele não pode representar um número negativo.</span><span class="sxs-lookup"><span data-stu-id="d7488-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="d7488-121">Se você usar o`-`operador unary minus ( ) `UInteger`em uma expressão que `Long` avalia para digitar, visual basic converte a expressão para primeiro.</span><span class="sxs-lookup"><span data-stu-id="d7488-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="d7488-122">**Conformidade cls.**</span><span class="sxs-lookup"><span data-stu-id="d7488-122">**CLS Compliance.**</span></span> <span data-ttu-id="d7488-123">O `UInteger` tipo de dados não faz parte da [Especificação de Linguagem Comum](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), portanto, o código compatível com CLS não pode consumir um componente que o use.</span><span class="sxs-lookup"><span data-stu-id="d7488-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="d7488-124">**Interop Considerações.**</span><span class="sxs-lookup"><span data-stu-id="d7488-124">**Interop Considerations.**</span></span> <span data-ttu-id="d7488-125">Se você estiver interagindo com componentes não gravados para o .NET Framework, por `uint` exemplo, automação ou objetos COM, tenha em mente que tipos como podem ter uma largura de dados diferente (16 bits) em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="d7488-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="d7488-126">Se você estiver passando um argumento de 16 bits para um componente, declare-o como `UShort` em vez de `UInteger` em seu código Visual Basic gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d7488-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="d7488-127">**Alargamento.**</span><span class="sxs-lookup"><span data-stu-id="d7488-127">**Widening.**</span></span> <span data-ttu-id="d7488-128">O `UInteger` tipo de `Long`dados `ULong` `Decimal`se `Single`expande para, , , e `Double`.</span><span class="sxs-lookup"><span data-stu-id="d7488-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="d7488-129">Isso significa que `UInteger` você pode converter para <xref:System.OverflowException?displayProperty=nameWithType> qualquer um desses tipos sem encontrar um erro.</span><span class="sxs-lookup"><span data-stu-id="d7488-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="d7488-130">**Digite caracteres.**</span><span class="sxs-lookup"><span data-stu-id="d7488-130">**Type Characters.**</span></span> <span data-ttu-id="d7488-131">Anexar os caracteres `UI` do tipo literal `UInteger` a um literal força-o ao tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="d7488-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="d7488-132">`UInteger`não tem nenhum tipo de caractere identificador.</span><span class="sxs-lookup"><span data-stu-id="d7488-132">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="d7488-133">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="d7488-133">**Framework Type.**</span></span> <span data-ttu-id="d7488-134">O tipo correspondente no .NET Framework é a estrutura <xref:System.UInt32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d7488-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7488-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="d7488-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="d7488-136">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="d7488-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="d7488-137">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="d7488-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="d7488-138">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="d7488-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="d7488-139">Como chamar uma função do Windows que use tipos não assinados</span><span class="sxs-lookup"><span data-stu-id="d7488-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="d7488-140">Uso eficiente de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="d7488-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
