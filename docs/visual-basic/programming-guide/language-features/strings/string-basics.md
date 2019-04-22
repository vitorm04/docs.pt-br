---
title: Noções básicas de cadeias de caracteres no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 9d2d3c82f5512bc1e37e3b05086fbd364ee12298
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820877"
---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="1bf7c-102">Noções básicas de cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1bf7c-102">String Basics in Visual Basic</span></span>
<span data-ttu-id="1bf7c-103">O `String` tipo de dados representa uma série de caracteres (cada uma instância de um por vez representando o `Char` tipo de dados).</span><span class="sxs-lookup"><span data-stu-id="1bf7c-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="1bf7c-104">Este tópico apresenta os conceitos básicos de cadeias de caracteres no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-104">This topic introduces the basic concepts of strings in Visual Basic.</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="1bf7c-105">Variáveis de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1bf7c-105">String Variables</span></span>  
 <span data-ttu-id="1bf7c-106">Um valor literal que representa uma série de caracteres pode ser atribuída a uma instância de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="1bf7c-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1bf7c-107">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 <span data-ttu-id="1bf7c-108">Um `String` variável também pode aceitar qualquer expressão que é avaliada como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-108">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="1bf7c-109">São mostrados exemplos abaixo:</span><span class="sxs-lookup"><span data-stu-id="1bf7c-109">Examples are shown below:</span></span>  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 <span data-ttu-id="1bf7c-110">Qualquer literal que é atribuído a um `String` variável deve ser colocada entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="1bf7c-110">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="1bf7c-111">Isso significa que aspas dentro de uma cadeia de caracteres não pode ser representada por uma marca de aspas.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-111">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="1bf7c-112">Por exemplo, o código a seguir causa um erro do compilador:</span><span class="sxs-lookup"><span data-stu-id="1bf7c-112">For example, the following code causes a compiler error:</span></span>  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 <span data-ttu-id="1bf7c-113">Esse código causa um erro porque o compilador encerra a cadeia de caracteres após a segunda aspa, e o restante da cadeia de caracteres é interpretado como código.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-113">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="1bf7c-114">Para resolver esse problema, o Visual Basic interpreta duas aspas em uma cadeia de caracteres literal como uma aspa na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-114">To solve this problem, Visual Basic interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="1bf7c-115">O exemplo a seguir demonstra a maneira correta de incluir uma marca de aspas em uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="1bf7c-115">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 <span data-ttu-id="1bf7c-116">No exemplo anterior, as duas aspas antes da palavra `Look` se tornam uma aspas na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-116">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="1bf7c-117">As três aspas no final da linha representam uma aspas na cadeia de caracteres e o caractere de terminação da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-117">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="1bf7c-118">Literais de cadeia de caracteres podem conter várias linhas:</span><span class="sxs-lookup"><span data-stu-id="1bf7c-118">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
```  
  
 <span data-ttu-id="1bf7c-119">A cadeia de caracteres resultante contém sequências de nova linha que você usou em sua cadeia de caracteres literal (vbcr, vbcrlf, etc.).</span><span class="sxs-lookup"><span data-stu-id="1bf7c-119">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="1bf7c-120">Você não precisa usar a solução alternativa antiga:</span><span class="sxs-lookup"><span data-stu-id="1bf7c-120">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="1bf7c-121">Caracteres em cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="1bf7c-121">Characters in Strings</span></span>  
 <span data-ttu-id="1bf7c-122">Uma cadeia de caracteres pode ser pensada como uma série de `Char` valores e o `String` tipo tem funções internas que permitem que você execute várias manipulações em uma cadeia de caracteres parecidas com as manipulações permitidas por arrays.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-122">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="1bf7c-123">Como todos os arrays em [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], essas são as matrizes com base em zero.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-123">Like all array in [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], these are zero-based arrays.</span></span> <span data-ttu-id="1bf7c-124">Você pode se referir a um caractere específico em uma cadeia de caracteres por meio de `Chars` propriedade, que fornece uma maneira de acessar um caractere pela posição em que aparece na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-124">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="1bf7c-125">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1bf7c-125">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 <span data-ttu-id="1bf7c-126">No exemplo acima, o `Chars` propriedade da cadeia de caracteres retorna o quarto caractere na cadeia de caracteres, que é `D`e a atribui `myChar`.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-126">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="1bf7c-127">Você também pode obter o comprimento de uma cadeia de caracteres específica por meio de `Length` propriedade.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-127">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="1bf7c-128">Se você precisar executar várias manipulações de tipo de matriz em uma cadeia de caracteres, você pode convertê-la para uma matriz de `Char` instâncias usando o `ToCharArray` função da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-128">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="1bf7c-129">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1bf7c-129">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 <span data-ttu-id="1bf7c-130">A variável `myArray` agora contém uma matriz de `Char` valores, cada um representando um caractere de `myString`.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-130">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="1bf7c-131">A imutabilidade de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="1bf7c-131">The Immutability of Strings</span></span>  
 <span data-ttu-id="1bf7c-132">É uma cadeia de caracteres *imutável*, que significa que seu valor não pode ser alterado quando ele foi criado.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-132">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="1bf7c-133">No entanto, isso não impede que você atribuir mais de um valor a uma variável de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-133">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="1bf7c-134">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1bf7c-134">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 <span data-ttu-id="1bf7c-135">Aqui, uma variável de cadeia de caracteres é criada, dado um valor, e, em seguida, seu valor é alterado.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-135">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="1bf7c-136">Mais especificamente, na primeira linha, uma instância do tipo `String` é criado e receberá o valor `This string is immutable`.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-136">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="1bf7c-137">Na segunda linha do exemplo, uma nova instância é criada e recebe o valor `Or is it?`, e a variável de cadeia de caracteres descarta sua referência para a primeira instância e armazena uma referência para a nova instância.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-137">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="1bf7c-138">Ao contrário de outros tipos de dados intrínsecos, `String` é um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-138">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="1bf7c-139">Quando uma variável do tipo de referência é passada como um argumento para uma função ou sub-rotina, uma referência para o endereço de memória onde os dados são armazenados é passada em vez do valor real da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-139">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="1bf7c-140">Portanto, no exemplo anterior, o nome da variável permanece o mesmo, mas ele aponta para uma instância nova e diferente de `String` classe, que contém o novo valor.</span><span class="sxs-lookup"><span data-stu-id="1bf7c-140">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bf7c-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bf7c-141">See also</span></span>

- [<span data-ttu-id="1bf7c-142">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1bf7c-142">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [<span data-ttu-id="1bf7c-143">Tipo de Dados String</span><span class="sxs-lookup"><span data-stu-id="1bf7c-143">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="1bf7c-144">Tipo de Dados de Caractere</span><span class="sxs-lookup"><span data-stu-id="1bf7c-144">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="1bf7c-145">Operações básicas de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="1bf7c-145">Basic String Operations</span></span>](../../../../standard/base-types/basic-string-operations.md)
