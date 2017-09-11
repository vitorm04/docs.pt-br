---
title: Como o operador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Like
- vb.Like
dev_langs:
- VB
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
caps.latest.revision: 18
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
ms.openlocfilehash: 4cbc569866c39342227c8c33e6237c1370fdbe0a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="8327f-102">Operador Like (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8327f-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="8327f-103">Compara uma cadeia de caracteres com um padrão.</span><span class="sxs-lookup"><span data-stu-id="8327f-103">Compares a string against a pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8327f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8327f-104">Syntax</span></span>  
  
```  
  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="8327f-105">Partes</span><span class="sxs-lookup"><span data-stu-id="8327f-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="8327f-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8327f-106">Required.</span></span> <span data-ttu-id="8327f-107">Qualquer `Boolean` variável.</span><span class="sxs-lookup"><span data-stu-id="8327f-107">Any `Boolean` variable.</span></span> <span data-ttu-id="8327f-108">O resultado é um `Boolean` valor que indica se ou não o `string` satisfaz a `pattern`.</span><span class="sxs-lookup"><span data-stu-id="8327f-108">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="8327f-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8327f-109">Required.</span></span> <span data-ttu-id="8327f-110">Qualquer expressão de `String` .</span><span class="sxs-lookup"><span data-stu-id="8327f-110">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="8327f-111">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8327f-111">Required.</span></span> <span data-ttu-id="8327f-112">Qualquer `String` expressão de acordo com as convenções de correspondência de padrão descritas em "Comentários".</span><span class="sxs-lookup"><span data-stu-id="8327f-112">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8327f-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="8327f-113">Remarks</span></span>  
 <span data-ttu-id="8327f-114">Se o valor em `string` satisfizer o padrão contido em `pattern`, `result` é `True`.</span><span class="sxs-lookup"><span data-stu-id="8327f-114">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="8327f-115">Se a cadeia de caracteres não satisfizer o padrão, `result` é `False`.</span><span class="sxs-lookup"><span data-stu-id="8327f-115">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="8327f-116">Se ambos os `string` e `pattern` são cadeias de caracteres vazias, o resultado é `True`.</span><span class="sxs-lookup"><span data-stu-id="8327f-116">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="8327f-117">Método de comparação</span><span class="sxs-lookup"><span data-stu-id="8327f-117">Comparison Method</span></span>  
 <span data-ttu-id="8327f-118">O comportamento do `Like` depende do operador de [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8327f-118">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span> <span data-ttu-id="8327f-119">O método de comparação de cadeia de caracteres padrão para cada arquivo de origem é `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="8327f-119">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="8327f-120">Opções padrão</span><span class="sxs-lookup"><span data-stu-id="8327f-120">Pattern Options</span></span>  
 <span data-ttu-id="8327f-121">Correspondência de padrões interna fornece uma ferramenta versátil para comparações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8327f-121">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="8327f-122">Os recursos de correspondência permitem que você coincida cada caractere em `string` em relação a um caractere específico, um caractere curinga, uma lista de caracteres ou um intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8327f-122">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="8327f-123">A tabela a seguir mostra os caracteres permitidos em `pattern` e o que eles correspondem.</span><span class="sxs-lookup"><span data-stu-id="8327f-123">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="8327f-124">Caracteres em`pattern`</span><span class="sxs-lookup"><span data-stu-id="8327f-124">Characters in `pattern`</span></span>|<span data-ttu-id="8327f-125">Correspondências em`string`</span><span class="sxs-lookup"><span data-stu-id="8327f-125">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="8327f-126">Qualquer caractere único</span><span class="sxs-lookup"><span data-stu-id="8327f-126">Any single character</span></span>|  
|`*`|<span data-ttu-id="8327f-127">Zero ou mais caracteres</span><span class="sxs-lookup"><span data-stu-id="8327f-127">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="8327f-128">Qualquer dígito único (0 –&9;)</span><span class="sxs-lookup"><span data-stu-id="8327f-128">Any single digit (0–9)</span></span>|  
|<span data-ttu-id="8327f-129">`[` `charlist` `]`</span><span class="sxs-lookup"><span data-stu-id="8327f-129">`[` `charlist` `]`</span></span>|<span data-ttu-id="8327f-130">Qualquer caractere único no`charlist`</span><span class="sxs-lookup"><span data-stu-id="8327f-130">Any single character in `charlist`</span></span>|  
|<span data-ttu-id="8327f-131">`[!` `charlist` `]`</span><span class="sxs-lookup"><span data-stu-id="8327f-131">`[!` `charlist` `]`</span></span>|<span data-ttu-id="8327f-132">Qualquer caractere único não em`charlist`</span><span class="sxs-lookup"><span data-stu-id="8327f-132">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="8327f-133">Listas de caracteres</span><span class="sxs-lookup"><span data-stu-id="8327f-133">Character Lists</span></span>  
 <span data-ttu-id="8327f-134">Um grupo de um ou mais caracteres (`charlist`) entre colchetes (`[ ]`) pode ser usado para corresponder a qualquer caractere único no `string` e pode incluir qualquer código de caractere, inclusive dígitos.</span><span class="sxs-lookup"><span data-stu-id="8327f-134">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="8327f-135">Um ponto de exclamação (`!`) no início do `charlist` significa que uma coincidência é feita se qualquer caractere, exceto os caracteres em `charlist` encontrado em `string`.</span><span class="sxs-lookup"><span data-stu-id="8327f-135">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="8327f-136">Quando usado fora de colchetes, o ponto de exclamação corresponde a mesmo.</span><span class="sxs-lookup"><span data-stu-id="8327f-136">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="8327f-137">Caracteres especiais</span><span class="sxs-lookup"><span data-stu-id="8327f-137">Special Characters</span></span>  
 <span data-ttu-id="8327f-138">Para coincidir o colchete esquerdo de caracteres especiais (`[`), ponto de interrogação (`?`), sinal numérico (`#`) e o asterisco (`*`), coloque-os entre colchetes.</span><span class="sxs-lookup"><span data-stu-id="8327f-138">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="8327f-139">O colchete direito (`]`) não pode ser usado dentro de um grupo para corresponder em si, mas pode ser usado fora de um grupo como um caractere individual.</span><span class="sxs-lookup"><span data-stu-id="8327f-139">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="8327f-140">A sequência de caracteres `[]` é considerado uma cadeia de caracteres de comprimento zero (`""`).</span><span class="sxs-lookup"><span data-stu-id="8327f-140">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="8327f-141">No entanto, ele não pode ser parte de uma lista de caracteres entre colchetes.</span><span class="sxs-lookup"><span data-stu-id="8327f-141">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="8327f-142">Se você quiser verificar se uma posição na `string` contém um de um grupo de caracteres ou nenhum caractere, você pode usar `Like` duas vezes.</span><span class="sxs-lookup"><span data-stu-id="8327f-142">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="8327f-143">Para obter um exemplo, consulte [como: corresponder uma cadeia de caracteres com um padrão](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="8327f-143">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="8327f-144">Intervalos de caracteres</span><span class="sxs-lookup"><span data-stu-id="8327f-144">Character Ranges</span></span>  
 <span data-ttu-id="8327f-145">Usando um hífen (`–`) para separar os limites inferior e superior do intervalo, `charlist` pode especificar um intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8327f-145">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="8327f-146">Por exemplo, `[A–Z]` resulta em uma coincidência se a posição do caractere correspondente em `string` contiver qualquer caractere dentro do intervalo `A`–`Z`, e `[!H–L]` resulta em uma coincidência se a posição do caractere correspondente contém qualquer caractere fora do intervalo `H`–`L`.</span><span class="sxs-lookup"><span data-stu-id="8327f-146">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="8327f-147">Quando você especificar um intervalo de caracteres, eles devem aparecer em ordem de classificação, ou seja, crescente de menor para maior.</span><span class="sxs-lookup"><span data-stu-id="8327f-147">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="8327f-148">Portanto, `[A–Z]` é um padrão válido, mas `[Z–A]` não é.</span><span class="sxs-lookup"><span data-stu-id="8327f-148">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="8327f-149">Vários intervalos de caracteres</span><span class="sxs-lookup"><span data-stu-id="8327f-149">Multiple Character Ranges</span></span>  
 <span data-ttu-id="8327f-150">Para especificar vários intervalos para a mesma posição de caractere, coloque-os entre os mesmos colchetes sem delimitadores.</span><span class="sxs-lookup"><span data-stu-id="8327f-150">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="8327f-151">Por exemplo, `[A–CX–Z]` resulta em uma coincidência se a posição do caractere correspondente em `string` contiver qualquer caractere dentro do intervalo `A`–`C` ou o intervalo de `X`–`Z`.</span><span class="sxs-lookup"><span data-stu-id="8327f-151">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="8327f-152">Uso do hífen</span><span class="sxs-lookup"><span data-stu-id="8327f-152">Usage of the Hyphen</span></span>  
 <span data-ttu-id="8327f-153">Um hífen (`–`) pode aparecer no início (após um ponto de exclamação, se houver) ou no final da `charlist` para corresponder ao próprio.</span><span class="sxs-lookup"><span data-stu-id="8327f-153">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="8327f-154">Em qualquer outro local, o hífen identifica um intervalo de caracteres delimitada por caracteres em ambos os lados do hífen.</span><span class="sxs-lookup"><span data-stu-id="8327f-154">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="8327f-155">Sequência de agrupamento</span><span class="sxs-lookup"><span data-stu-id="8327f-155">Collating Sequence</span></span>  
 <span data-ttu-id="8327f-156">O significado de um intervalo especificado depende do caractere de ordenação em tempo de execução, conforme determinado pela `Option``Compare` e a configuração de localidade do sistema qual o código está em execução.</span><span class="sxs-lookup"><span data-stu-id="8327f-156">The meaning of a specified range depends on the character ordering at run time, as determined by `Option``Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="8327f-157">With `Option``Compare``Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span><span class="sxs-lookup"><span data-stu-id="8327f-157">With `Option``Compare``Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="8327f-158">With `Option``Compare``Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span><span class="sxs-lookup"><span data-stu-id="8327f-158">With `Option``Compare``Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="8327f-159">O intervalo não coincide com `Ê` ou `ê` porque caracteres acentuados agupam após caracteres não acentuados na ordem de classificação.</span><span class="sxs-lookup"><span data-stu-id="8327f-159">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="8327f-160">Caracteres de digraph</span><span class="sxs-lookup"><span data-stu-id="8327f-160">Digraph Characters</span></span>  
 <span data-ttu-id="8327f-161">Em alguns idiomas, há caracteres alfabéticos que representam dois caracteres distintos.</span><span class="sxs-lookup"><span data-stu-id="8327f-161">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="8327f-162">Por exemplo, vários idiomas usam o caractere `æ` para representar os caracteres `a` e `e` quando aparecem juntos.</span><span class="sxs-lookup"><span data-stu-id="8327f-162">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="8327f-163">O `Like` operador reconhece que o caractere dígrafo único e os dois caracteres individuais são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="8327f-163">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="8327f-164">Quando um idioma que usa um caractere dígrafo for especificado nas configurações de localidade do sistema, uma ocorrência do caractere dígrafo única em uma `pattern` ou `string` corresponde à sequência de dois caracteres equivalente na outra sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8327f-164">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="8327f-165">Da mesma forma, um caractere dígrafo em `pattern` entre colchetes (por si só, em uma lista ou em um intervalo) coincide com a sequência de dois caracteres equivalente na `string`.</span><span class="sxs-lookup"><span data-stu-id="8327f-165">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8327f-166">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="8327f-166">Overloading</span></span>  
 <span data-ttu-id="8327f-167">O `Like` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="8327f-167">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8327f-168">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="8327f-168">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8327f-169">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8327f-169">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8327f-170">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8327f-170">Example</span></span>  
 <span data-ttu-id="8327f-171">Este exemplo usa o `Like` operador para comparar cadeias de caracteres para vários padrões.</span><span class="sxs-lookup"><span data-stu-id="8327f-171">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="8327f-172">Os resultados entram em uma `Boolean` variável que indica se cada cadeia de caracteres satisfaz o padrão.</span><span class="sxs-lookup"><span data-stu-id="8327f-172">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 <span data-ttu-id="8327f-173">[!code-vb[30 VbVbalrOperators](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8327f-173">[!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8327f-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8327f-174">See Also</span></span>  
 <span data-ttu-id="8327f-175"><xref:Microsoft.VisualBasic.Strings.InStr%2A></xref:Microsoft.VisualBasic.Strings.InStr%2A></span><span class="sxs-lookup"><span data-stu-id="8327f-175"><xref:Microsoft.VisualBasic.Strings.InStr%2A></span></span>   
 <span data-ttu-id="8327f-176"><xref:Microsoft.VisualBasic.Strings.StrComp%2A></xref:Microsoft.VisualBasic.Strings.StrComp%2A></span><span class="sxs-lookup"><span data-stu-id="8327f-176"><xref:Microsoft.VisualBasic.Strings.StrComp%2A></span></span>   
<span data-ttu-id="8327f-177"> [Operadores de comparação](../../../visual-basic/language-reference/operators/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="8327f-177"> [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md) </span></span>  
<span data-ttu-id="8327f-178"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="8327f-178"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="8327f-179"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="8327f-179"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="8327f-180"> [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="8327f-180"> [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span></span>  
<span data-ttu-id="8327f-181"> [Operadores e expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="8327f-181"> [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span></span>  
<span data-ttu-id="8327f-182"> [Como corresponder uma cadeia de caracteres a um padrão](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="8327f-182"> [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)</span></span>
