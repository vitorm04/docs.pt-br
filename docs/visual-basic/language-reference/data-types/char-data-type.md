---
title: Tipo de dados Char
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: 1ed5b19a307d094fc1d5a6bb0251c57052dc9bc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344057"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="bae15-102">Tipo de dados Char (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bae15-102">Char Data Type (Visual Basic)</span></span>

<span data-ttu-id="bae15-103">Contém pontos de código não assinados de 16 bits (2 bytes) que variam em valor de 0 a 65535.</span><span class="sxs-lookup"><span data-stu-id="bae15-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="bae15-104">Cada *ponto de código*, ou código de caractere, representa um único caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="bae15-104">Each *code point*, or character code, represents a single Unicode character.</span></span>

## <a name="remarks"></a><span data-ttu-id="bae15-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="bae15-105">Remarks</span></span>

<span data-ttu-id="bae15-106">Use o tipo de dados `Char` quando precisar manter apenas um único caractere e não precisar da sobrecarga de `String`.</span><span class="sxs-lookup"><span data-stu-id="bae15-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="bae15-107">Em alguns casos, você pode usar `Char()`, uma matriz de elementos `Char`, para conter vários caracteres.</span><span class="sxs-lookup"><span data-stu-id="bae15-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>

<span data-ttu-id="bae15-108">O valor padrão de `Char` é o caractere com um ponto de código de 0.</span><span class="sxs-lookup"><span data-stu-id="bae15-108">The default value of `Char` is the character with a code point of 0.</span></span>

## <a name="unicode-characters"></a><span data-ttu-id="bae15-109">Caracteres Unicode</span><span class="sxs-lookup"><span data-stu-id="bae15-109">Unicode Characters</span></span>

<span data-ttu-id="bae15-110">Os primeiros 128 pontos de código (0 – 127) de Unicode correspondem às letras e aos símbolos em um teclado americano padrão.</span><span class="sxs-lookup"><span data-stu-id="bae15-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="bae15-111">Esses primeiros 128 pontos de código são os mesmos que os conjuntos de caracteres ASCII define.</span><span class="sxs-lookup"><span data-stu-id="bae15-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="bae15-112">Os segundos pontos de código 128 (128 – 255) representam caracteres especiais, como letras do alfabeto, acentos, símbolos de moeda e frações baseados em latim.</span><span class="sxs-lookup"><span data-stu-id="bae15-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="bae15-113">O Unicode usa os pontos de código restantes (256-65535) para uma grande variedade de símbolos, incluindo caracteres de texto em todo o mundo, sinais diacríticos e símbolos matemáticos e técnicos.</span><span class="sxs-lookup"><span data-stu-id="bae15-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>

<span data-ttu-id="bae15-114">Você pode usar métodos como <xref:System.Char.IsDigit%2A> e <xref:System.Char.IsPunctuation%2A> em uma variável `Char` para determinar sua classificação Unicode.</span><span class="sxs-lookup"><span data-stu-id="bae15-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>

## <a name="type-conversions"></a><span data-ttu-id="bae15-115">Conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="bae15-115">Type Conversions</span></span>

<span data-ttu-id="bae15-116">Visual Basic não converte diretamente entre `Char` e os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="bae15-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="bae15-117">Você pode usar a função <xref:Microsoft.VisualBasic.Strings.Asc%2A> ou <xref:Microsoft.VisualBasic.Strings.AscW%2A> para converter um valor de `Char` em um `Integer` que representa seu ponto de código.</span><span class="sxs-lookup"><span data-stu-id="bae15-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="bae15-118">Você pode usar a função <xref:Microsoft.VisualBasic.Strings.Chr%2A> ou <xref:Microsoft.VisualBasic.Strings.ChrW%2A> para converter um valor de `Integer` em um `Char` que tenha esse ponto de código.</span><span class="sxs-lookup"><span data-stu-id="bae15-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>

<span data-ttu-id="bae15-119">Se a opção de verificação de tipo (a [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)) estiver on, você deverá acrescentar o caractere de tipo literal a um literal de cadeia de caracteres de caractere único para identificá-lo como o tipo de dados `Char`.</span><span class="sxs-lookup"><span data-stu-id="bae15-119">If the type checking switch (the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="bae15-120">O exemplo a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="bae15-120">The following example illustrates this.</span></span> <span data-ttu-id="bae15-121">A primeira atribuição para a variável `charVar` gera o erro [BC30512](../../misc/bc30512.md) do compilador porque `Option Strict` está ativada.</span><span class="sxs-lookup"><span data-stu-id="bae15-121">The first assignment to the `charVar` variable generates compiler error [BC30512](../../misc/bc30512.md) because `Option Strict` is on.</span></span> <span data-ttu-id="bae15-122">O segundo é compilado com êxito porque o `c` caractere de tipo literal identifica o literal como um valor de `Char`.</span><span class="sxs-lookup"><span data-stu-id="bae15-122">The second compiles successfully because the `c` literal type character identifies the literal as a `Char` value.</span></span>

```vb
Option Strict On

Module CharType
    Public Sub Main()
        Dim charVar As Char

        ' This statement generates compiler error BC30512 because Option Strict is On.  
        charVar = "Z"  

        ' The following statement succeeds because it specifies a Char literal.  
        charVar = "Z"c
    End Sub
End Module
```

## <a name="programming-tips"></a><span data-ttu-id="bae15-123">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="bae15-123">Programming Tips</span></span>

- <span data-ttu-id="bae15-124">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="bae15-124">**Negative Numbers.**</span></span> <span data-ttu-id="bae15-125">`Char` é um tipo não assinado e não pode representar um valor negativo.</span><span class="sxs-lookup"><span data-stu-id="bae15-125">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="bae15-126">Em qualquer caso, você não deve usar `Char` para armazenar valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="bae15-126">In any case, you should not use `Char` to hold numeric values.</span></span>

- <span data-ttu-id="bae15-127">**Considerações sobre interoperabilidade.**</span><span class="sxs-lookup"><span data-stu-id="bae15-127">**Interop Considerations.**</span></span> <span data-ttu-id="bae15-128">Se você interface com componentes não escritos para o .NET Framework, por exemplo, automação ou objetos COM, lembre-se de que os tipos de caracteres têm uma largura de dados diferente (8 bits) em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="bae15-128">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="bae15-129">Se você passar um argumento de 8 bits para esse componente, declare-o como `Byte` em vez de `Char` no seu novo código de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bae15-129">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>

- <span data-ttu-id="bae15-130">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="bae15-130">**Widening.**</span></span> <span data-ttu-id="bae15-131">O tipo de dados `Char` amplia a `String`.</span><span class="sxs-lookup"><span data-stu-id="bae15-131">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="bae15-132">Isso significa que você pode converter `Char` em `String` e não encontrará uma <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bae15-132">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="bae15-133">**Digite os caracteres.**</span><span class="sxs-lookup"><span data-stu-id="bae15-133">**Type Characters.**</span></span> <span data-ttu-id="bae15-134">Acrescentar o caractere de tipo literal `C` a um literal de cadeia de caracteres de caractere único força-o para o tipo de dados `Char`.</span><span class="sxs-lookup"><span data-stu-id="bae15-134">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="bae15-135">`Char` não tem um caractere de tipo de identificador.</span><span class="sxs-lookup"><span data-stu-id="bae15-135">`Char` has no identifier type character.</span></span>

- <span data-ttu-id="bae15-136">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="bae15-136">**Framework Type.**</span></span> <span data-ttu-id="bae15-137">O tipo correspondente no .NET Framework é a estrutura <xref:System.Char?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bae15-137">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="bae15-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bae15-138">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="bae15-139">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="bae15-139">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="bae15-140">Tipo de Dados String</span><span class="sxs-lookup"><span data-stu-id="bae15-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="bae15-141">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="bae15-141">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="bae15-142">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="bae15-142">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="bae15-143">Como chamar uma função do Windows que use tipos não assinados</span><span class="sxs-lookup"><span data-stu-id="bae15-143">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="bae15-144">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="bae15-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
