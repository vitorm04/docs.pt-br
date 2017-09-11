---
title: Tipo de dados (Visual Basic) char | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Char
dev_langs:
- VB
helpviewer_keywords:
- literal type characters, C
- Char data type
- C literal type character
- data types [Visual Basic], assigning
- Char data type, character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 95141b6a35a7ae462df74d0fc29d18a0b38faf1d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="96fc2-102">Tipo de dados Char (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96fc2-102">Char Data Type (Visual Basic)</span></span>
<span data-ttu-id="96fc2-103">Armazena pontos de código de (2 bytes) de 16 bits sem sinal cujo valor varia de 0 a 65535.</span><span class="sxs-lookup"><span data-stu-id="96fc2-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="96fc2-104">Cada *ponto de código*, ou código de caractere, representa um único caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="96fc2-104">Each *code point*, or character code, represents a single Unicode character.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96fc2-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="96fc2-105">Remarks</span></span>  
 <span data-ttu-id="96fc2-106">Use o `Char` de tipo de dados quando você precisa armazenar um único caractere e não é necessário para a sobrecarga de `String`.</span><span class="sxs-lookup"><span data-stu-id="96fc2-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="96fc2-107">Em alguns casos, você pode usar `Char()`, uma matriz de `Char` elementos, para manter vários caracteres.</span><span class="sxs-lookup"><span data-stu-id="96fc2-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>  
  
 <span data-ttu-id="96fc2-108">O valor padrão de `Char` é o caractere com um ponto de código de 0.</span><span class="sxs-lookup"><span data-stu-id="96fc2-108">The default value of `Char` is the character with a code point of 0.</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="96fc2-109">Caracteres Unicode</span><span class="sxs-lookup"><span data-stu-id="96fc2-109">Unicode Characters</span></span>  
 <span data-ttu-id="96fc2-110">Os primeiro 128 pontos de código (0 – 127) do Unicode correspondem às letras e símbolos de um teclado americano padrão.</span><span class="sxs-lookup"><span data-stu-id="96fc2-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="96fc2-111">Esses pontos de 128 código primeiro são as mesmas que as define o conjunto de caracteres ASCII.</span><span class="sxs-lookup"><span data-stu-id="96fc2-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="96fc2-112">Os 128 pontos de código (128 – 255) representam caracteres especiais, como letras do alfabeto latino, acentos, símbolos monetários e frações.</span><span class="sxs-lookup"><span data-stu-id="96fc2-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="96fc2-113">O Unicode usa os pontos de código restantes (256-65535) para uma ampla variedade de símbolos, incluindo caracteres textuais em todo o mundo, sinais diacríticos e símbolos matemáticos e técnicos.</span><span class="sxs-lookup"><span data-stu-id="96fc2-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="96fc2-114">Você pode usar métodos como <xref:System.Char.IsDigit%2A>e <xref:System.Char.IsPunctuation%2A>em um `Char` variável para determinar sua classificação Unicode.</xref:System.Char.IsPunctuation%2A> </xref:System.Char.IsDigit%2A></span><span class="sxs-lookup"><span data-stu-id="96fc2-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="96fc2-115">Conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="96fc2-115">Type Conversions</span></span>  
 <span data-ttu-id="96fc2-116">O Visual Basic não converter diretamente entre `Char` e os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="96fc2-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="96fc2-117">Você pode usar o <xref:Microsoft.VisualBasic.Strings.Asc%2A>ou <xref:Microsoft.VisualBasic.Strings.AscW%2A>função para converter um `Char` valor para um `Integer` que representa seu ponto de código.</xref:Microsoft.VisualBasic.Strings.AscW%2A> </xref:Microsoft.VisualBasic.Strings.Asc%2A></span><span class="sxs-lookup"><span data-stu-id="96fc2-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="96fc2-118">Você pode usar o <xref:Microsoft.VisualBasic.Strings.Chr%2A>ou <xref:Microsoft.VisualBasic.Strings.ChrW%2A>função para converter um `Integer` valor para um `Char` que tem esse ponto de código.</xref:Microsoft.VisualBasic.Strings.ChrW%2A> </xref:Microsoft.VisualBasic.Strings.Chr%2A></span><span class="sxs-lookup"><span data-stu-id="96fc2-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>  
  
 <span data-ttu-id="96fc2-119">Se a verificação de tipo muda ([instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)) estiver ativado, você deve acrescentar o caractere de tipo literal em uma cadeia de único caractere literal para identificá-lo como o `Char` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="96fc2-119">If the type checking switch ([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="96fc2-120">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="96fc2-120">The following example illustrates this.</span></span>  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a><span data-ttu-id="96fc2-121">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="96fc2-121">Programming Tips</span></span>  
  
-   <span data-ttu-id="96fc2-122">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="96fc2-122">**Negative Numbers.**</span></span> <span data-ttu-id="96fc2-123">`Char`é um tipo sem sinal e não pode representar um valor negativo.</span><span class="sxs-lookup"><span data-stu-id="96fc2-123">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="96fc2-124">Em qualquer caso, você não deve usar `Char` para armazenar valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="96fc2-124">In any case, you should not use `Char` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="96fc2-125">**Considerações de interoperabilidade.**</span><span class="sxs-lookup"><span data-stu-id="96fc2-125">**Interop Considerations.**</span></span> <span data-ttu-id="96fc2-126">Interface com componentes não escritos para o .NET Framework, como objetos de automação ou COM, lembre-se de que tipos de caracteres uma largura de dados diferente (8 bits) em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="96fc2-126">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="96fc2-127">Se você passar um argumento de 8 bits para tal um componente, declare-o como `Byte` em vez de `Char` em seu novo código Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="96fc2-127">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="96fc2-128">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="96fc2-128">**Widening.**</span></span> <span data-ttu-id="96fc2-129">O `Char` tipo de dados amplia a `String`.</span><span class="sxs-lookup"><span data-stu-id="96fc2-129">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="96fc2-130">Isso significa que você pode converter `Char` para `String` e não encontrará um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="96fc2-130">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=fullName> error.</span></span>  
  
-   <span data-ttu-id="96fc2-131">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="96fc2-131">**Type Characters.**</span></span> <span data-ttu-id="96fc2-132">Acrescentar o caractere de tipo literal `C` para uma cadeia de caracteres único literal força-o `Char` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="96fc2-132">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="96fc2-133">`Char`não tem nenhum caractere de tipo identificador.</span><span class="sxs-lookup"><span data-stu-id="96fc2-133">`Char` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="96fc2-134">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="96fc2-134">**Framework Type.**</span></span> <span data-ttu-id="96fc2-135">O tipo correspondente no .NET Framework é o <xref:System.Char?displayProperty=fullName>estrutura.</xref:System.Char?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="96fc2-135">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=fullName> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96fc2-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96fc2-136">See Also</span></span>  
 <span data-ttu-id="96fc2-137"><xref:System.Char?displayProperty=fullName></xref:System.Char?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="96fc2-137"><xref:System.Char?displayProperty=fullName></span></span>   
 <span data-ttu-id="96fc2-138"><xref:Microsoft.VisualBasic.Strings.Asc%2A></xref:Microsoft.VisualBasic.Strings.Asc%2A></span><span class="sxs-lookup"><span data-stu-id="96fc2-138"><xref:Microsoft.VisualBasic.Strings.Asc%2A></span></span>   
 <span data-ttu-id="96fc2-139"><xref:Microsoft.VisualBasic.Strings.AscW%2A></xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="96fc2-139"><xref:Microsoft.VisualBasic.Strings.AscW%2A></span></span>   
 <span data-ttu-id="96fc2-140"><xref:Microsoft.VisualBasic.Strings.Chr%2A></xref:Microsoft.VisualBasic.Strings.Chr%2A></span><span class="sxs-lookup"><span data-stu-id="96fc2-140"><xref:Microsoft.VisualBasic.Strings.Chr%2A></span></span>   
 <span data-ttu-id="96fc2-141"><xref:Microsoft.VisualBasic.Strings.ChrW%2A></xref:Microsoft.VisualBasic.Strings.ChrW%2A></span><span class="sxs-lookup"><span data-stu-id="96fc2-141"><xref:Microsoft.VisualBasic.Strings.ChrW%2A></span></span>   
<span data-ttu-id="96fc2-142"> [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="96fc2-142"> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="96fc2-143"> [Tipo de dados String](../../../visual-basic/language-reference/data-types/string-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="96fc2-143"> [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md) </span></span>  
<span data-ttu-id="96fc2-144"> [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="96fc2-144"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="96fc2-145"> [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="96fc2-145"> [Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
<span data-ttu-id="96fc2-146"> [Como: chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md) </span><span class="sxs-lookup"><span data-stu-id="96fc2-146"> [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md) </span></span>  
<span data-ttu-id="96fc2-147"> [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="96fc2-147"> [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span></span>
