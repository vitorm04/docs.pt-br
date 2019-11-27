---
title: Tipo de dados Byte
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344072"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="f1730-102">Tipo de dados byte (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1730-102">Byte data type (Visual Basic)</span></span>

<span data-ttu-id="f1730-103">Mantém inteiros de 8 bits (1 byte) não assinados que variam em valor de 0 a 255.</span><span class="sxs-lookup"><span data-stu-id="f1730-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="f1730-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1730-104">Remarks</span></span>

<span data-ttu-id="f1730-105">Use o tipo de dados `Byte` para conter dados binários.</span><span class="sxs-lookup"><span data-stu-id="f1730-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="f1730-106">O valor padrão de `Byte` é 0.</span><span class="sxs-lookup"><span data-stu-id="f1730-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="f1730-107">Atribuições de literal</span><span class="sxs-lookup"><span data-stu-id="f1730-107">Literal assignments</span></span>

<span data-ttu-id="f1730-108">Você pode declarar e inicializar uma variável `Byte` atribuindo-lhe um literal decimal, um literal hexadecimal, um literal octal ou (começando com Visual Basic 2017) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="f1730-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="f1730-109">Se o literal integral estiver fora do intervalo de um `Byte` (ou seja, se for menor que <xref:System.Byte.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Byte.MaxValue?displayProperty=nameWithType>), ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="f1730-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="f1730-110">No exemplo a seguir, números inteiros iguais a 201 que são representados como decimais, hexadecimais e literais binários são convertidos implicitamente de [inteiro](integer-data-type.md) para `byte` valores.</span><span class="sxs-lookup"><span data-stu-id="f1730-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="f1730-111">Você usa o prefixo `&h` ou `&H` para indicar um literal hexadecimal, o prefixo `&b` ou `&B` para denotar um literal binário e o prefixo `&o` ou `&O` para indicar um literal octal.</span><span class="sxs-lookup"><span data-stu-id="f1730-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="f1730-112">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="f1730-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="f1730-113">A partir do Visual Basic 2017, você também pode usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f1730-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="f1730-114">A partir do Visual Basic 15,5, você também pode usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos hexadecimal, binário ou octal.</span><span class="sxs-lookup"><span data-stu-id="f1730-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="f1730-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f1730-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="f1730-116">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="f1730-116">Programming tips</span></span>

- <span data-ttu-id="f1730-117">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="f1730-117">**Negative Numbers.**</span></span> <span data-ttu-id="f1730-118">Como `Byte` é um tipo não assinado, ele não pode representar um número negativo.</span><span class="sxs-lookup"><span data-stu-id="f1730-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="f1730-119">Se você usar o operador menos unário (`-`) em uma expressão avaliada como tipo `Byte`, Visual Basic converterá a expressão para `Short` primeiro.</span><span class="sxs-lookup"><span data-stu-id="f1730-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
- <span data-ttu-id="f1730-120">**Conversões de formato.**</span><span class="sxs-lookup"><span data-stu-id="f1730-120">**Format Conversions.**</span></span> <span data-ttu-id="f1730-121">Quando Visual Basic lê ou grava arquivos, ou quando chama DLLs, métodos e propriedades, ele pode converter automaticamente entre os formatos de dados.</span><span class="sxs-lookup"><span data-stu-id="f1730-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="f1730-122">Os dados binários armazenados em `Byte` variáveis e matrizes são preservados durante as conversões de formato.</span><span class="sxs-lookup"><span data-stu-id="f1730-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="f1730-123">Você não deve usar uma variável `String` para dados binários, porque seu conteúdo pode ser corrompido durante a conversão entre os formatos ANSI e Unicode.</span><span class="sxs-lookup"><span data-stu-id="f1730-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

- <span data-ttu-id="f1730-124">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="f1730-124">**Widening.**</span></span> <span data-ttu-id="f1730-125">O tipo de dados `Byte` amplia a `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="f1730-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="f1730-126">Isso significa que você pode converter `Byte` em qualquer um desses tipos sem encontrar um erro de <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f1730-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
- <span data-ttu-id="f1730-127">**Digite os caracteres.**</span><span class="sxs-lookup"><span data-stu-id="f1730-127">**Type Characters.**</span></span> <span data-ttu-id="f1730-128">`Byte` não tem nenhum caractere de tipo literal ou caractere de tipo de identificador.</span><span class="sxs-lookup"><span data-stu-id="f1730-128">`Byte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="f1730-129">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="f1730-129">**Framework Type.**</span></span> <span data-ttu-id="f1730-130">O tipo correspondente no .NET Framework é a estrutura <xref:System.Byte?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f1730-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="f1730-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1730-131">Example</span></span>

 <span data-ttu-id="f1730-132">No exemplo a seguir, `b` é uma variável `Byte`.</span><span class="sxs-lookup"><span data-stu-id="f1730-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="f1730-133">As instruções demonstram o intervalo da variável e o aplicativo de operadores de deslocamento de bits a ela.</span><span class="sxs-lookup"><span data-stu-id="f1730-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a><span data-ttu-id="f1730-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1730-134">See also</span></span>

- <xref:System.Byte?displayProperty=nameWithType>
- [<span data-ttu-id="f1730-135">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="f1730-135">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="f1730-136">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="f1730-136">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="f1730-137">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="f1730-137">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="f1730-138">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="f1730-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
