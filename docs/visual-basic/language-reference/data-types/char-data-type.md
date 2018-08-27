---
title: Tipo de dados Char (Visual Basic)
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
ms.openlocfilehash: 09b0162068bc068bd77612816626897ec4a151d9
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42911961"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="8e757-102">Tipo de dados Char (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e757-102">Char Data Type (Visual Basic)</span></span>
<span data-ttu-id="8e757-103">Contém pontos de código de (2 bytes) de 16 bits sem sinal que variam de 0 a 65535.</span><span class="sxs-lookup"><span data-stu-id="8e757-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="8e757-104">Cada *ponto de código*, ou código de caractere, representa um único caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="8e757-104">Each *code point*, or character code, represents a single Unicode character.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e757-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e757-105">Remarks</span></span>  
 <span data-ttu-id="8e757-106">Use o `Char` tipo de dados quando você precisa manter um único caractere e não é necessário para a sobrecarga de `String`.</span><span class="sxs-lookup"><span data-stu-id="8e757-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="8e757-107">Em alguns casos, você pode usar `Char()`, uma matriz de `Char` elementos, para manter vários caracteres.</span><span class="sxs-lookup"><span data-stu-id="8e757-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>  
  
 <span data-ttu-id="8e757-108">O valor padrão de `Char` é o caractere com um ponto de código de 0.</span><span class="sxs-lookup"><span data-stu-id="8e757-108">The default value of `Char` is the character with a code point of 0.</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="8e757-109">Caracteres Unicode</span><span class="sxs-lookup"><span data-stu-id="8e757-109">Unicode Characters</span></span>  
 <span data-ttu-id="8e757-110">Os primeiros pontos de 128 código (0 – 127) do Unicode correspondem às letras e símbolos de um teclado americano padrão.</span><span class="sxs-lookup"><span data-stu-id="8e757-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="8e757-111">Esses primeiros 128 pontos de código são as mesmas que as define o conjunto de caracteres ASCII.</span><span class="sxs-lookup"><span data-stu-id="8e757-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="8e757-112">Os 128 pontos de código (128 – 255) representam caracteres especiais, como letras do alfabeto baseado em latim, acentos, símbolos de moeda e frações.</span><span class="sxs-lookup"><span data-stu-id="8e757-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="8e757-113">O Unicode usa os pontos de código restantes (256 a 65535) para uma ampla variedade de símbolos, incluindo símbolos técnicos e matemáticos, diacríticos e caracteres textuais em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="8e757-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="8e757-114">Você pode usar métodos como <xref:System.Char.IsDigit%2A> e <xref:System.Char.IsPunctuation%2A> em um `Char` variável para determinar sua classificação de Unicode.</span><span class="sxs-lookup"><span data-stu-id="8e757-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="8e757-115">Conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="8e757-115">Type Conversions</span></span>  
 <span data-ttu-id="8e757-116">O Visual Basic não converter diretamente entre `Char` e os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="8e757-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="8e757-117">Você pode usar o <xref:Microsoft.VisualBasic.Strings.Asc%2A> ou <xref:Microsoft.VisualBasic.Strings.AscW%2A> função para converter um `Char` de valor para um `Integer` que representa seu ponto de código.</span><span class="sxs-lookup"><span data-stu-id="8e757-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="8e757-118">Você pode usar o <xref:Microsoft.VisualBasic.Strings.Chr%2A> ou <xref:Microsoft.VisualBasic.Strings.ChrW%2A> função para converter um `Integer` de valor para um `Char` que tem esse ponto de código.</span><span class="sxs-lookup"><span data-stu-id="8e757-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>  
  
 <span data-ttu-id="8e757-119">Se a verificação de tipo muda ([instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)) está ativada, você deve acrescentar o caractere de tipo literal em uma cadeia de caracteres de caractere único literal para identificá-lo como o `Char` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="8e757-119">If the type checking switch ([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="8e757-120">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="8e757-120">The following example illustrates this.</span></span>  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a><span data-ttu-id="8e757-121">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="8e757-121">Programming Tips</span></span>  
  
-   <span data-ttu-id="8e757-122">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="8e757-122">**Negative Numbers.**</span></span> <span data-ttu-id="8e757-123">`Char` é um tipo sem sinal e não pode representar um valor negativo.</span><span class="sxs-lookup"><span data-stu-id="8e757-123">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="8e757-124">Em qualquer caso, você não deve usar `Char` para armazenar valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="8e757-124">In any case, you should not use `Char` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="8e757-125">**Considerações de interoperabilidade.**</span><span class="sxs-lookup"><span data-stu-id="8e757-125">**Interop Considerations.**</span></span> <span data-ttu-id="8e757-126">Se a interface com componentes não escritos para o .NET Framework, como objetos Automation ou COM, lembre-se de que tipos de caractere têm uma largura de dados diferente (8 bits) em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="8e757-126">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="8e757-127">Se você passar um argumento de 8 bits para tal componente, declare-o como `Byte` em vez de `Char` no seu novo código do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8e757-127">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="8e757-128">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="8e757-128">**Widening.**</span></span> <span data-ttu-id="8e757-129">O `Char` tipo de dados é ampliado para `String`.</span><span class="sxs-lookup"><span data-stu-id="8e757-129">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="8e757-130">Isso significa que você pode converter `Char` à `String` e não encontrará um <xref:System.OverflowException?displayProperty=nameWithType> erro.</span><span class="sxs-lookup"><span data-stu-id="8e757-130">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="8e757-131">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="8e757-131">**Type Characters.**</span></span> <span data-ttu-id="8e757-132">Acrescentar o caractere de tipo literal `C` em uma cadeia de caracteres único literal o força ao `Char` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="8e757-132">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="8e757-133">`Char` não tem nenhum caractere de tipo de identificador.</span><span class="sxs-lookup"><span data-stu-id="8e757-133">`Char` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="8e757-134">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="8e757-134">**Framework Type.**</span></span> <span data-ttu-id="8e757-135">O tipo correspondente no .NET Framework é a estrutura <xref:System.Char?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8e757-135">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e757-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e757-136">See Also</span></span>  
 <xref:System.Char?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [<span data-ttu-id="8e757-137">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="8e757-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="8e757-138">Tipo de Dados String</span><span class="sxs-lookup"><span data-stu-id="8e757-138">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [<span data-ttu-id="8e757-139">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="8e757-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="8e757-140">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="8e757-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="8e757-141">Como chamar uma função do Windows que use tipos não assinados</span><span class="sxs-lookup"><span data-stu-id="8e757-141">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="8e757-142">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="8e757-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
