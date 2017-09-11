---
title: "Como: corresponder uma cadeia de caracteres com um padrão (Visual Basic) | Documentos do Microsoft"
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
- comparison operators, comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching, string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
caps.latest.revision: 8
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
ms.openlocfilehash: f4ec3ec42fff5bf2b855a55a192b1a5bb98d7463
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="8bdd0-102">Como corresponder uma cadeia de caracteres a um padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bdd0-102">How to: Match a String against a Pattern (Visual Basic)</span></span>
<span data-ttu-id="8bdd0-103">Se você quiser saber se uma expressão do [tipo de dados String](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfaz um padrão, você pode usar o [operador Like](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="8bdd0-103">If you want to find out if an expression of the [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
 <span data-ttu-id="8bdd0-104">`Like`leva dois operandos.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-104">`Like` takes two operands.</span></span> <span data-ttu-id="8bdd0-105">O operando esquerdo é uma expressão de cadeia de caracteres, e o operando à direita é uma cadeia de caracteres contendo o padrão a ser usado para correspondência.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="8bdd0-106">`Like`Retorna um `Boolean` valor que indica se a expressão de cadeia de caracteres satisfaz o padrão.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>  
  
 <span data-ttu-id="8bdd0-107">Você pode corresponder a cada caractere na expressão de cadeia de caracteres com um caractere específico, um caractere curinga, uma lista de caracteres ou um intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="8bdd0-108">As posições das especificações na cadeia de caracteres padrão correspondem às posições dos caracteres a ser correspondida na expressão de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="8bdd0-109">Para corresponder um caractere na expressão de cadeia de caracteres com um caractere específico</span><span class="sxs-lookup"><span data-stu-id="8bdd0-109">To match a character in the string expression against a specific character</span></span>  
  
-   <span data-ttu-id="8bdd0-110">Coloque o caractere específico diretamente na cadeia de caracteres padrão.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="8bdd0-111">Certos caracteres especiais devem ser colocados entre colchetes (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="8bdd0-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="8bdd0-112">Para obter mais informações, consulte [operador Like](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="8bdd0-112">For more information, see [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
     <span data-ttu-id="8bdd0-113">A exemplo a seguir testa se `myString` consiste exatamente do único caractere `H`.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>  
  
     <span data-ttu-id="8bdd0-114">[!code-vb[VbVbalrOperators&#70;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bdd0-114">[!code-vb[VbVbalrOperators#70](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_1.vb)]</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="8bdd0-115">Para corresponder um caractere na expressão de cadeia de caracteres com um caractere curinga</span><span class="sxs-lookup"><span data-stu-id="8bdd0-115">To match a character in the string expression against a wildcard character</span></span>  
  
-   <span data-ttu-id="8bdd0-116">Coloque um ponto de interrogação (`?`) na cadeia de caracteres padrão.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-116">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="8bdd0-117">Qualquer caractere válido nessa posição é uma correspondência com êxito.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-117">Any valid character in this position makes a successful match.</span></span>  
  
     <span data-ttu-id="8bdd0-118">A exemplo a seguir testa se `myString` consiste no caractere único `W` seguido por exatamente dois caracteres de quaisquer valores.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-118">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>  
  
     <span data-ttu-id="8bdd0-119">[!code-vb[VbVbalrOperators&#71;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bdd0-119">[!code-vb[VbVbalrOperators#71](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_2.vb)]</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="8bdd0-120">Para corresponder um caractere na expressão de cadeia de caracteres em uma lista de caracteres</span><span class="sxs-lookup"><span data-stu-id="8bdd0-120">To match a character in the string expression against a list of characters</span></span>  
  
-   <span data-ttu-id="8bdd0-121">Coloque colchetes (`[ ]`) na cadeia de caracteres padrão e dentro dos colchetes coloque a lista de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-121">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="8bdd0-122">Não separe os caracteres com vírgulas ou qualquer outro separador.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-122">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="8bdd0-123">Qualquer caractere único na lista é uma correspondência com êxito.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-123">Any single character in the list makes a successful match.</span></span>  
  
     <span data-ttu-id="8bdd0-124">A exemplo a seguir testa se `myString` consiste de qualquer caractere válido seguido por exatamente um dos caracteres `A`, `C`, ou `E`.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-124">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>  
  
     <span data-ttu-id="8bdd0-125">[!code-vb[VbVbalrOperators&#72;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bdd0-125">[!code-vb[VbVbalrOperators#72](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_3.vb)]</span></span>  
  
     <span data-ttu-id="8bdd0-126">Observe que essa correspondência diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-126">Note that this match is case-sensitive.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="8bdd0-127">Para corresponder um caractere na expressão de cadeia de caracteres com um intervalo de caracteres</span><span class="sxs-lookup"><span data-stu-id="8bdd0-127">To match a character in the string expression against a range of characters</span></span>  
  
-   <span data-ttu-id="8bdd0-128">Coloque colchetes (`[ ]`) na cadeia de caracteres padrão e dentro dos colchetes colocados os caracteres mais baixos e mais altos do intervalo, separados por um hífen (`–`).</span><span class="sxs-lookup"><span data-stu-id="8bdd0-128">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="8bdd0-129">Qualquer caractere único dentro do intervalo é uma correspondência com êxito.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-129">Any single character within the range makes a successful match.</span></span>  
  
     <span data-ttu-id="8bdd0-130">A exemplo a seguir testa se `myString` consiste em caracteres `num` seguidos por exatamente um dos caracteres `i`, `j`, `k`, `l`, `m`, ou `n`.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-130">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>  
  
     <span data-ttu-id="8bdd0-131">[!code-vb[VbVbalrOperators&#73;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bdd0-131">[!code-vb[VbVbalrOperators#73](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_4.vb)]</span></span>  
  
     <span data-ttu-id="8bdd0-132">Observe que essa correspondência diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-132">Note that this match is case-sensitive.</span></span>  
  
## <a name="matching-empty-strings"></a><span data-ttu-id="8bdd0-133">Correspondência de cadeias de caracteres vazias</span><span class="sxs-lookup"><span data-stu-id="8bdd0-133">Matching Empty Strings</span></span>  
 <span data-ttu-id="8bdd0-134">`Like`trata a sequência `[]` como uma cadeia de caracteres de comprimento zero (`""`).</span><span class="sxs-lookup"><span data-stu-id="8bdd0-134">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="8bdd0-135">Você pode usar `[]` para testar se a expressão de cadeia de caracteres inteira está vazia, mas você não pode usá-lo para testar se uma determinada posição na expressão de cadeia de caracteres está vazia.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-135">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="8bdd0-136">Se uma posição vazia é uma das opções que você precisa testar, você pode usar `Like` mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-136">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="8bdd0-137">Para corresponder um caractere na expressão de cadeia de caracteres em uma lista de caracteres ou nenhum caractere</span><span class="sxs-lookup"><span data-stu-id="8bdd0-137">To match a character in the string expression against a list of characters or no character</span></span>  
  
1.  <span data-ttu-id="8bdd0-138">Chamar o `Like` operador duas vezes na mesma expressão de cadeia de caracteres e conecte as duas chamadas com o [operador ou](../../../../visual-basic/language-reference/operators/or-operator.md) ou [operador OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="8bdd0-138">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) or the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
2.  <span data-ttu-id="8bdd0-139">Na cadeia de caracteres padrão para o primeiro `Like` cláusula, inclua a lista de caracteres entre colchetes (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="8bdd0-139">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>  
  
3.  <span data-ttu-id="8bdd0-140">Na cadeia de caracteres padrão para o segundo `Like` cláusula, não coloque nenhum caractere na posição em questão.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-140">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>  
  
     <span data-ttu-id="8bdd0-141">O exemplo a seguir testa o número de telefone de sete dígitos `phoneNum` exatamente três dígitos numéricos, seguidos por um espaço, um hífen (`–`), um período (`.`), ou nenhum caractere, seguidos por exatamente quatro dígitos numéricos.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-141">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>  
  
     <span data-ttu-id="8bdd0-142">[!code-vb[VbVbalrOperators&#74;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bdd0-142">[!code-vb[VbVbalrOperators#74](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_5.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bdd0-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8bdd0-143">See Also</span></span>  
 <span data-ttu-id="8bdd0-144">[Operadores de comparação](../../../../visual-basic/language-reference/operators/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="8bdd0-144">[Comparison Operators](../../../../visual-basic/language-reference/operators/comparison-operators.md) </span></span>  
<span data-ttu-id="8bdd0-145"> [Operadores e expressões](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="8bdd0-145"> [Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span></span>  
<span data-ttu-id="8bdd0-146"> [Operador LIKE](../../../../visual-basic/language-reference/operators/like-operator.md) </span><span class="sxs-lookup"><span data-stu-id="8bdd0-146"> [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md) </span></span>  
<span data-ttu-id="8bdd0-147"> [Tipo de Dados String](../../../../visual-basic/language-reference/data-types/string-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="8bdd0-147"> [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md)</span></span>
