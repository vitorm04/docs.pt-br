---
title: Como corresponder uma cadeia de caracteres a um padrão (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: aef378bfc32d6deff431a2caac1261a6cd7520c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655204"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="28ac8-102">Como corresponder uma cadeia de caracteres a um padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28ac8-102">How to: Match a String against a Pattern (Visual Basic)</span></span>
<span data-ttu-id="28ac8-103">Se você quiser saber se uma expressão do [tipo de dados de cadeia de caracteres](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfaz um padrão, você pode usar o [operador Like](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="28ac8-103">If you want to find out if an expression of the [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
 <span data-ttu-id="28ac8-104">`Like` leva dois operandos.</span><span class="sxs-lookup"><span data-stu-id="28ac8-104">`Like` takes two operands.</span></span> <span data-ttu-id="28ac8-105">O operando esquerdo é uma expressão de cadeia de caracteres, e o operando à direita é uma cadeia de caracteres contendo o padrão a ser usado para correspondência.</span><span class="sxs-lookup"><span data-stu-id="28ac8-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="28ac8-106">`Like` Retorna um `Boolean` valor que indica se a expressão de cadeia de caracteres satisfaz o padrão.</span><span class="sxs-lookup"><span data-stu-id="28ac8-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>  
  
 <span data-ttu-id="28ac8-107">Você pode corresponder a cada caractere na expressão de cadeia de caracteres com um caractere específico, um caractere curinga, uma lista de caracteres ou um intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="28ac8-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="28ac8-108">As posições das especificações na cadeia de caracteres padrão correspondem às posições dos caracteres a ser correspondido na expressão de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="28ac8-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="28ac8-109">Para corresponder um caractere na expressão de cadeia de caracteres com um caractere específico</span><span class="sxs-lookup"><span data-stu-id="28ac8-109">To match a character in the string expression against a specific character</span></span>  
  
-   <span data-ttu-id="28ac8-110">Coloque o caractere específico diretamente na cadeia de caracteres padrão.</span><span class="sxs-lookup"><span data-stu-id="28ac8-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="28ac8-111">Certos caracteres especiais devem ser colocados entre colchetes (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="28ac8-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="28ac8-112">Para obter mais informações, consulte [operador Like](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="28ac8-112">For more information, see [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
     <span data-ttu-id="28ac8-113">A exemplo a seguir testa se `myString` consiste exatamente o único caractere `H`.</span><span class="sxs-lookup"><span data-stu-id="28ac8-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>  
  
     [!code-vb[VbVbalrOperators#70](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_1.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="28ac8-114">Para corresponder um caractere na expressão de cadeia de caracteres com um caractere curinga</span><span class="sxs-lookup"><span data-stu-id="28ac8-114">To match a character in the string expression against a wildcard character</span></span>  
  
-   <span data-ttu-id="28ac8-115">Colocar um ponto de interrogação (`?`) na cadeia de caracteres padrão.</span><span class="sxs-lookup"><span data-stu-id="28ac8-115">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="28ac8-116">Qualquer caractere válido nessa posição é uma correspondência com êxito.</span><span class="sxs-lookup"><span data-stu-id="28ac8-116">Any valid character in this position makes a successful match.</span></span>  
  
     <span data-ttu-id="28ac8-117">A exemplo a seguir testa se `myString` consiste o único caractere `W` seguido por exatamente dois caracteres de quaisquer valores.</span><span class="sxs-lookup"><span data-stu-id="28ac8-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>  
  
     [!code-vb[VbVbalrOperators#71](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_2.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="28ac8-118">Para corresponder um caractere na expressão de cadeia de caracteres com uma lista de caracteres</span><span class="sxs-lookup"><span data-stu-id="28ac8-118">To match a character in the string expression against a list of characters</span></span>  
  
-   <span data-ttu-id="28ac8-119">Coloque colchetes (`[ ]`) na cadeia de caracteres padrão e dentro dos colchetes coloque a lista de caracteres.</span><span class="sxs-lookup"><span data-stu-id="28ac8-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="28ac8-120">Não separe os caracteres com vírgulas ou qualquer outro separador.</span><span class="sxs-lookup"><span data-stu-id="28ac8-120">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="28ac8-121">Qualquer caractere único na lista é uma correspondência com êxito.</span><span class="sxs-lookup"><span data-stu-id="28ac8-121">Any single character in the list makes a successful match.</span></span>  
  
     <span data-ttu-id="28ac8-122">A exemplo a seguir testa se `myString` consiste em qualquer caractere válido seguido por exatamente um dos caracteres `A`, `C`, ou `E`.</span><span class="sxs-lookup"><span data-stu-id="28ac8-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>  
  
     [!code-vb[VbVbalrOperators#72](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_3.vb)]  
  
     <span data-ttu-id="28ac8-123">Observe que essa correspondência diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="28ac8-123">Note that this match is case-sensitive.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="28ac8-124">Para corresponder um caractere na expressão de cadeia de caracteres com um intervalo de caracteres</span><span class="sxs-lookup"><span data-stu-id="28ac8-124">To match a character in the string expression against a range of characters</span></span>  
  
-   <span data-ttu-id="28ac8-125">Coloque colchetes (`[ ]`) na cadeia de caracteres padrão e dentro dos colchetes colocados os caracteres de menor e mais altos do intervalo, separados por um hífen (`–`).</span><span class="sxs-lookup"><span data-stu-id="28ac8-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="28ac8-126">Qualquer caractere único dentro do intervalo é uma correspondência com êxito.</span><span class="sxs-lookup"><span data-stu-id="28ac8-126">Any single character within the range makes a successful match.</span></span>  
  
     <span data-ttu-id="28ac8-127">A exemplo a seguir testa se `myString` consiste em caracteres `num` seguidos por exatamente um dos caracteres `i`, `j`, `k`, `l`, `m`, ou `n`.</span><span class="sxs-lookup"><span data-stu-id="28ac8-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>  
  
     [!code-vb[VbVbalrOperators#73](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_4.vb)]  
  
     <span data-ttu-id="28ac8-128">Observe que essa correspondência diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="28ac8-128">Note that this match is case-sensitive.</span></span>  
  
## <a name="matching-empty-strings"></a><span data-ttu-id="28ac8-129">Correspondência de cadeias de caracteres vazias</span><span class="sxs-lookup"><span data-stu-id="28ac8-129">Matching Empty Strings</span></span>  
 <span data-ttu-id="28ac8-130">`Like` trata a sequência `[]` como uma cadeia de caracteres de comprimento zero (`""`).</span><span class="sxs-lookup"><span data-stu-id="28ac8-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="28ac8-131">Você pode usar `[]` para testar se a expressão de cadeia de caracteres inteira está vazia, mas você não pode usá-lo para testar se uma determinada posição na expressão de cadeia de caracteres está vazia.</span><span class="sxs-lookup"><span data-stu-id="28ac8-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="28ac8-132">Se uma posição vazia é uma das opções que você precisa testar, você pode usar `Like` mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="28ac8-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="28ac8-133">Para corresponder um caractere na expressão de cadeia de caracteres com uma lista de caracteres ou nenhum caractere</span><span class="sxs-lookup"><span data-stu-id="28ac8-133">To match a character in the string expression against a list of characters or no character</span></span>  
  
1.  <span data-ttu-id="28ac8-134">Chamar o `Like` operador duas vezes na mesma expressão de cadeia de caracteres e conecte as duas chamadas com o [operador ou](../../../../visual-basic/language-reference/operators/or-operator.md) ou [operador OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="28ac8-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) or the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
2.  <span data-ttu-id="28ac8-135">Na cadeia de caracteres padrão para o primeiro `Like` cláusula, inclua a lista de caracteres entre colchetes (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="28ac8-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>  
  
3.  <span data-ttu-id="28ac8-136">Na cadeia de caracteres padrão para o segundo `Like` cláusula, não coloque nenhum caractere na posição em questão.</span><span class="sxs-lookup"><span data-stu-id="28ac8-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>  
  
     <span data-ttu-id="28ac8-137">O exemplo a seguir testa o número de telefone de sete dígitos `phoneNum` exatamente três dígitos numéricos, seguido por um espaço, um hífen (`–`), um período (`.`), ou nenhum caractere, seguidos por exatamente quatro dígitos numéricos.</span><span class="sxs-lookup"><span data-stu-id="28ac8-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>  
  
     [!code-vb[VbVbalrOperators#74](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="28ac8-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28ac8-138">See Also</span></span>  
 [<span data-ttu-id="28ac8-139">Operadores de Comparação</span><span class="sxs-lookup"><span data-stu-id="28ac8-139">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="28ac8-140">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="28ac8-140">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="28ac8-141">Operador Like</span><span class="sxs-lookup"><span data-stu-id="28ac8-141">Like Operator</span></span>](../../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="28ac8-142">Tipo de Dados String</span><span class="sxs-lookup"><span data-stu-id="28ac8-142">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
