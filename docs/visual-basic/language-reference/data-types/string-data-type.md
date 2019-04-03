---
title: Tipo de dados da cadeia de caracteres (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: 3e87dc6527b4351467b1155439ee8266157c16ff
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842285"
---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="70524-102">Tipo de dados da cadeia de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70524-102">String Data Type (Visual Basic)</span></span>
<span data-ttu-id="70524-103">Contém sequências de pontos de código de (2 bytes) de 16 bits sem sinal que variam em valor de 0 a 65535.</span><span class="sxs-lookup"><span data-stu-id="70524-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="70524-104">Cada *ponto de código*, ou código de caractere, representa um único caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="70524-104">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="70524-105">Uma cadeia de caracteres pode conter de 0 a aproximadamente dois bilhões (2 ^ 31) caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="70524-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70524-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="70524-106">Remarks</span></span>  
 <span data-ttu-id="70524-107">Use o `String` tipo de dados para manter vários caracteres sem a sobrecarga de gerenciamento de matriz de `Char()`, uma matriz de `Char` elementos.</span><span class="sxs-lookup"><span data-stu-id="70524-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="70524-108">O valor padrão de `String` é `Nothing` (uma referência nula).</span><span class="sxs-lookup"><span data-stu-id="70524-108">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="70524-109">Observe que isso não é o mesmo que a cadeia de caracteres vazia (valor `""`).</span><span class="sxs-lookup"><span data-stu-id="70524-109">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="70524-110">Caracteres Unicode</span><span class="sxs-lookup"><span data-stu-id="70524-110">Unicode Characters</span></span>  
 <span data-ttu-id="70524-111">Os primeiros pontos de 128 código (0 – 127) do Unicode correspondem às letras e símbolos de um teclado americano padrão.</span><span class="sxs-lookup"><span data-stu-id="70524-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="70524-112">Esses primeiros 128 pontos de código são as mesmas que as define o conjunto de caracteres ASCII.</span><span class="sxs-lookup"><span data-stu-id="70524-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="70524-113">Os 128 pontos de código (128 – 255) representam caracteres especiais, como letras do alfabeto baseado em latim, acentos, símbolos de moeda e frações.</span><span class="sxs-lookup"><span data-stu-id="70524-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="70524-114">O Unicode usa os pontos de código restantes (256 a 65535) para uma ampla variedade de símbolos.</span><span class="sxs-lookup"><span data-stu-id="70524-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="70524-115">Isso inclui caracteres textuais em todo o mundo, sinais diacríticos e símbolos matemáticos e técnicos.</span><span class="sxs-lookup"><span data-stu-id="70524-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="70524-116">Você pode usar métodos como <xref:System.Char.IsDigit%2A> e <xref:System.Char.IsPunctuation%2A> em um caractere individual em um `String` variável para determinar sua classificação de Unicode.</span><span class="sxs-lookup"><span data-stu-id="70524-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="70524-117">Requisitos de formato</span><span class="sxs-lookup"><span data-stu-id="70524-117">Format Requirements</span></span>  
 <span data-ttu-id="70524-118">Você deve incluir um `String` literal entre aspas (`" "`).</span><span class="sxs-lookup"><span data-stu-id="70524-118">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="70524-119">Se você deve incluir uma marca de aspas simples como um dos caracteres na cadeia de caracteres, você use duas aspas contíguas (`""`).</span><span class="sxs-lookup"><span data-stu-id="70524-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="70524-120">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="70524-120">The following example illustrates this.</span></span>  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="70524-121">Observe que as aspas contíguas que representam as aspas na cadeia de caracteres são independentes das aspas que começam e terminam o `String` literal.</span><span class="sxs-lookup"><span data-stu-id="70524-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="70524-122">Manipulações de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="70524-122">String Manipulations</span></span>  
 <span data-ttu-id="70524-123">Depois que você atribuir uma cadeia de caracteres para um `String` variável, essa cadeia de caracteres é *imutável*, que significa que você não pode alterar seu comprimento ou conteúdo.</span><span class="sxs-lookup"><span data-stu-id="70524-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="70524-124">Ao alterar uma cadeia de caracteres de qualquer forma, o Visual Basic cria uma nova cadeia de caracteres e abandona a anterior.</span><span class="sxs-lookup"><span data-stu-id="70524-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="70524-125">O `String` variável aponta para a nova cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="70524-125">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="70524-126">Você pode manipular o conteúdo de um `String` variável usando uma variedade de funções de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="70524-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="70524-127">O exemplo a seguir ilustra o <xref:Microsoft.VisualBasic.Strings.Left%2A> função</span><span class="sxs-lookup"><span data-stu-id="70524-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="70524-128">Uma cadeia de caracteres criada por outro componente pode ser preenchida com espaços iniciais ou finais.</span><span class="sxs-lookup"><span data-stu-id="70524-128">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="70524-129">Se você receber uma cadeia de caracteres, você pode usar o <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, e <xref:Microsoft.VisualBasic.Strings.RTrim%2A> funções para remover esses espaços.</span><span class="sxs-lookup"><span data-stu-id="70524-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="70524-130">Para obter mais informações sobre as manipulações de cadeia de caracteres, consulte [cadeias de caracteres](../../../visual-basic/programming-guide/language-features/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="70524-130">For more information about string manipulations, see [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="70524-131">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="70524-131">Programming Tips</span></span>  
  
-   <span data-ttu-id="70524-132">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="70524-132">**Negative Numbers.**</span></span> <span data-ttu-id="70524-133">Lembre-se de que os caracteres mantidos pela `String` não assinados e não pode representar valores negativos.</span><span class="sxs-lookup"><span data-stu-id="70524-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="70524-134">Em qualquer caso, você não deve usar `String` para armazenar valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="70524-134">In any case, you should not use `String` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="70524-135">**Considerações de interoperabilidade.**</span><span class="sxs-lookup"><span data-stu-id="70524-135">**Interop Considerations.**</span></span> <span data-ttu-id="70524-136">Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos Automation ou COM, lembre-se de que os caracteres da cadeia de caracteres têm uma largura de dados diferente (8 bits) em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="70524-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="70524-137">Se você estiver passando um argumento de cadeia de caracteres de 8 bits para tal componente, declare-o como `Byte()`, uma matriz de `Byte` elementos, em vez de `String` no seu novo código do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="70524-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="70524-138">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="70524-138">**Type Characters.**</span></span> <span data-ttu-id="70524-139">Acrescentar o caractere de tipo identificador `$` a qualquer identificador o força ao `String` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="70524-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="70524-140">`String` não tem nenhum caractere de tipo literal.</span><span class="sxs-lookup"><span data-stu-id="70524-140">`String` has no literal type character.</span></span> <span data-ttu-id="70524-141">No entanto, o compilador trata literais entre aspas (`" "`) como `String`.</span><span class="sxs-lookup"><span data-stu-id="70524-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
-   <span data-ttu-id="70524-142">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="70524-142">**Framework Type.**</span></span> <span data-ttu-id="70524-143">O tipo correspondente no .NET Framework é o <xref:System.String?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="70524-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70524-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70524-144">See also</span></span>

- <xref:System.String?displayProperty=nameWithType>
- [<span data-ttu-id="70524-145">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="70524-145">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="70524-146">Tipo de Dados de Caractere</span><span class="sxs-lookup"><span data-stu-id="70524-146">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="70524-147">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="70524-147">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="70524-148">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="70524-148">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="70524-149">Como: chamar uma função do Windows que use tipos não assinados</span><span class="sxs-lookup"><span data-stu-id="70524-149">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="70524-150">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="70524-150">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
