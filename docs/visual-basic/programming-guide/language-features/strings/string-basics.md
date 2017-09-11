---
title: "Noções básicas no Visual Basic de cadeia de caracteres | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
caps.latest.revision: 14
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
ms.openlocfilehash: 98c2707ef8aabc77951b21cfe9f4edcd3a88c863
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="4abfa-102">Noções básicas de cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4abfa-102">String Basics in Visual Basic</span></span>
<span data-ttu-id="4abfa-103">O `String` tipo de dados representa uma série de caracteres (cada um representando por sua vez uma instância das `Char` tipo de dados).</span><span class="sxs-lookup"><span data-stu-id="4abfa-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="4abfa-104">Este tópico apresenta os conceitos básicos de cadeias de caracteres em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="4abfa-104">This topic introduces the basic concepts of strings in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="4abfa-105">Variáveis de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4abfa-105">String Variables</span></span>  
 <span data-ttu-id="4abfa-106">Um valor literal que representa uma sequência de caracteres pode ser atribuída a uma instância de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4abfa-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="4abfa-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4abfa-107">For example:</span></span>  
  
 <span data-ttu-id="4abfa-108">[!code-vb[VbVbalrStrings&#63;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4abfa-108">[!code-vb[VbVbalrStrings#63](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]</span></span>  
  
 <span data-ttu-id="4abfa-109">Um `String` variável também pode aceitar qualquer expressão avaliada como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4abfa-109">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="4abfa-110">São mostrados exemplos abaixo:</span><span class="sxs-lookup"><span data-stu-id="4abfa-110">Examples are shown below:</span></span>  
  
 <span data-ttu-id="4abfa-111">[!code-vb[VbVbalrStrings&#64;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="4abfa-111">[!code-vb[VbVbalrStrings#64](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]</span></span>  
  
 <span data-ttu-id="4abfa-112">Qualquer literal que é atribuído a um `String` variável deve ser colocada entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="4abfa-112">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="4abfa-113">Isso significa que aspas dentro de uma cadeia de caracteres não pode ser representada por aspas.</span><span class="sxs-lookup"><span data-stu-id="4abfa-113">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="4abfa-114">Por exemplo, o código a seguir causa um erro do compilador:</span><span class="sxs-lookup"><span data-stu-id="4abfa-114">For example, the following code causes a compiler error:</span></span>  
  
 <span data-ttu-id="4abfa-115">[!code-vb[VbVbalrStrings&#65;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="4abfa-115">[!code-vb[VbVbalrStrings#65](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]</span></span>  
  
 <span data-ttu-id="4abfa-116">Esse código causa um erro porque o compilador termina a string após a segunda aspas, e o restante da cadeia de caracteres é interpretado como código.</span><span class="sxs-lookup"><span data-stu-id="4abfa-116">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="4abfa-117">Para resolver esse problema, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] interpreta duas aspas em uma cadeia de caracteres literal como uma aspas na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4abfa-117">To solve this problem, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="4abfa-118">O exemplo a seguir demonstra a maneira correta de incluir aspas em uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="4abfa-118">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 <span data-ttu-id="4abfa-119">[!code-vb[VbVbalrStrings&#66;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="4abfa-119">[!code-vb[VbVbalrStrings#66](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]</span></span>  
  
 <span data-ttu-id="4abfa-120">No exemplo anterior, as duas aspas antes da palavra `Look` se tornam uma aspas na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4abfa-120">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="4abfa-121">As três aspas no final da linha representam uma aspas na string e o caractere de terminação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4abfa-121">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="4abfa-122">Literais de cadeia de caracteres podem conter várias linhas:</span><span class="sxs-lookup"><span data-stu-id="4abfa-122">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
  
```  
  
 <span data-ttu-id="4abfa-123">A cadeia de caracteres resultante contém sequências de nova linha que você usou em sua cadeia de caracteres literal (vbcr, vbcrlf, etc.).</span><span class="sxs-lookup"><span data-stu-id="4abfa-123">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="4abfa-124">Você não precisa usar a solução antiga:</span><span class="sxs-lookup"><span data-stu-id="4abfa-124">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="4abfa-125">Caracteres em cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="4abfa-125">Characters in Strings</span></span>  
 <span data-ttu-id="4abfa-126">Uma cadeia de caracteres pode ser pensada como uma série de `Char` valores e o `String` tipo tem funções internas que permitem que você execute muitas manipulações em uma cadeia de caracteres parecidas com as manipulações permitidas por arrays.</span><span class="sxs-lookup"><span data-stu-id="4abfa-126">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="4abfa-127">Como todos os arrays no [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)], esses são arrays baseados em zero.</span><span class="sxs-lookup"><span data-stu-id="4abfa-127">Like all array in [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)], these are zero-based arrays.</span></span> <span data-ttu-id="4abfa-128">Você pode se referir a um caractere específico em uma cadeia de caracteres por meio de `Chars` property, que fornece uma maneira de acessar um caractere pela posição em que aparece na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4abfa-128">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="4abfa-129">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4abfa-129">For example:</span></span>  
  
 <span data-ttu-id="4abfa-130">[!code-vb[VbVbalrStrings&#67;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="4abfa-130">[!code-vb[VbVbalrStrings#67](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]</span></span>  
  
 <span data-ttu-id="4abfa-131">No exemplo acima, o `Chars` propriedade da cadeia de caracteres retorna o quarto caractere na cadeia de caracteres, que é `D`e a atribui `myChar`.</span><span class="sxs-lookup"><span data-stu-id="4abfa-131">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="4abfa-132">Você também pode obter o comprimento de uma cadeia de caracteres específica por meio de `Length` propriedade.</span><span class="sxs-lookup"><span data-stu-id="4abfa-132">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="4abfa-133">Se você precisar executar várias manipulações de tipo de matriz em uma cadeia de caracteres, você pode convertê-la em uma matriz de `Char` instâncias usando o `ToCharArray` função da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4abfa-133">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="4abfa-134">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4abfa-134">For example:</span></span>  
  
 <span data-ttu-id="4abfa-135">[!code-vb[VbVbalrStrings&#68;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="4abfa-135">[!code-vb[VbVbalrStrings#68](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]</span></span>  
  
 <span data-ttu-id="4abfa-136">A variável `myArray` agora contém uma matriz de `Char` valores, cada um representando um caractere de `myString`.</span><span class="sxs-lookup"><span data-stu-id="4abfa-136">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="4abfa-137">A imutabilidade de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="4abfa-137">The Immutability of Strings</span></span>  
 <span data-ttu-id="4abfa-138">Uma cadeia de caracteres *imutável*, que significa que seu valor não pode ser alterado depois ter sido criado.</span><span class="sxs-lookup"><span data-stu-id="4abfa-138">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="4abfa-139">No entanto, isso não impede que você atribua mais de um valor a uma variável de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4abfa-139">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="4abfa-140">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4abfa-140">Consider the following example:</span></span>  
  
 <span data-ttu-id="4abfa-141">[!code-vb[VbVbalrStrings&#69;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="4abfa-141">[!code-vb[VbVbalrStrings#69](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]</span></span>  
  
 <span data-ttu-id="4abfa-142">Aqui, uma variável de cadeia de caracteres é criada, dado um valor, e, em seguida, seu valor é alterado.</span><span class="sxs-lookup"><span data-stu-id="4abfa-142">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="4abfa-143">Mais especificamente, na primeira linha, uma instância do tipo `String` é criada e receberá o valor `This string is immutable`.</span><span class="sxs-lookup"><span data-stu-id="4abfa-143">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="4abfa-144">Na segunda linha do exemplo, uma nova instância é criada e receberá o valor `Or is it?`, e a variável de cadeia de caracteres descarta sua referência para a primeira instância e armazena uma referência para a nova instância.</span><span class="sxs-lookup"><span data-stu-id="4abfa-144">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="4abfa-145">Ao contrário de outros tipos de dados intrínsecos, `String` é um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="4abfa-145">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="4abfa-146">Quando uma variável de tipo de referência é passada como um argumento para uma função ou sub-rotina, uma referência para o endereço de memória onde os dados são armazenados é passada em vez do valor real da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4abfa-146">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="4abfa-147">No exemplo anterior, o nome da variável permanece o mesmo, mas ela aponta para uma instância nova e diferente de `String` classe, que contém o novo valor.</span><span class="sxs-lookup"><span data-stu-id="4abfa-147">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4abfa-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4abfa-148">See Also</span></span>  
 <span data-ttu-id="4abfa-149">[Introdução a cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md) </span><span class="sxs-lookup"><span data-stu-id="4abfa-149">[Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md) </span></span>  
<span data-ttu-id="4abfa-150"> [Tipo de dados String](../../../../visual-basic/language-reference/data-types/string-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="4abfa-150"> [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) </span></span>  
<span data-ttu-id="4abfa-151"> [Tipo de dados char](../../../../visual-basic/language-reference/data-types/char-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="4abfa-151"> [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md) </span></span>  
<span data-ttu-id="4abfa-152"> [Operações de cadeias de caracteres básicas](http://msdn.microsoft.com/library/8133d357-90b5-4b62-9927-43323d99b6b6)</span><span class="sxs-lookup"><span data-stu-id="4abfa-152"> [Basic String Operations](http://msdn.microsoft.com/library/8133d357-90b5-4b62-9927-43323d99b6b6)</span></span>
