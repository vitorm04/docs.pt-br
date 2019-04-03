---
title: Operador Like (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
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
ms.openlocfilehash: 38e56b8c0ec6bab89052ee42a2cd9c24053c658e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835694"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="4f6ba-102">Operador Like (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f6ba-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="4f6ba-103">Compara uma cadeia de caracteres com um padrão.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-103">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="4f6ba-104">O `Like` operador não é suportado atualmente em projetos do .NET Core e .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="4f6ba-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f6ba-105">Syntax</span></span>  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="4f6ba-106">Partes</span><span class="sxs-lookup"><span data-stu-id="4f6ba-106">Parts</span></span>  
 `result`  
 <span data-ttu-id="4f6ba-107">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-107">Required.</span></span> <span data-ttu-id="4f6ba-108">Qualquer `Boolean` variável.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-108">Any `Boolean` variable.</span></span> <span data-ttu-id="4f6ba-109">O resultado é um `Boolean` valor que indica se ou não o `string` satisfaz o `pattern`.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="4f6ba-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-110">Required.</span></span> <span data-ttu-id="4f6ba-111">Qualquer expressão de `String` .</span><span class="sxs-lookup"><span data-stu-id="4f6ba-111">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="4f6ba-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-112">Required.</span></span> <span data-ttu-id="4f6ba-113">Qualquer `String` expressão de acordo com as convenções de correspondência de padrão descritas em "Comentários".</span><span class="sxs-lookup"><span data-stu-id="4f6ba-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f6ba-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f6ba-114">Remarks</span></span>  
 <span data-ttu-id="4f6ba-115">Se o valor em `string` satisfizer o padrão contido em `pattern`, `result` é `True`.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="4f6ba-116">Se a cadeia de caracteres não satisfizer o padrão `result` é `False`.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-116">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="4f6ba-117">Se os dois `string` e `pattern` são cadeias de caracteres vazias, o resultado é `True`.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-117">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="4f6ba-118">Método de comparação</span><span class="sxs-lookup"><span data-stu-id="4f6ba-118">Comparison Method</span></span>  
 <span data-ttu-id="4f6ba-119">O comportamento do `Like` depende do operador a [instrução opção comparar](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4f6ba-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span> <span data-ttu-id="4f6ba-120">O método de comparação de cadeia de caracteres padrão para cada arquivo de origem é `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-120">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="4f6ba-121">Opções padrão</span><span class="sxs-lookup"><span data-stu-id="4f6ba-121">Pattern Options</span></span>  
 <span data-ttu-id="4f6ba-122">Correspondência de padrões interna fornece uma ferramenta versátil para comparações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-122">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="4f6ba-123">Os recursos de correspondência de padrões permitem que a correspondência entre cada caractere em `string` em relação a um caractere específico, um caractere curinga, uma lista de caracteres ou um intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="4f6ba-124">A tabela a seguir mostra os caracteres permitidos em `pattern` e o que eles correspondem.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-124">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="4f6ba-125">Caracteres em `pattern`</span><span class="sxs-lookup"><span data-stu-id="4f6ba-125">Characters in `pattern`</span></span>|<span data-ttu-id="4f6ba-126">Correspondências em `string`</span><span class="sxs-lookup"><span data-stu-id="4f6ba-126">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="4f6ba-127">Qualquer caractere único</span><span class="sxs-lookup"><span data-stu-id="4f6ba-127">Any single character</span></span>|  
|`*`|<span data-ttu-id="4f6ba-128">Zero ou mais caracteres</span><span class="sxs-lookup"><span data-stu-id="4f6ba-128">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="4f6ba-129">Qualquer dígito único (0 – 9)</span><span class="sxs-lookup"><span data-stu-id="4f6ba-129">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="4f6ba-130">Qualquer caractere único no `charlist`</span><span class="sxs-lookup"><span data-stu-id="4f6ba-130">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="4f6ba-131">Qualquer caractere único que não está em `charlist`</span><span class="sxs-lookup"><span data-stu-id="4f6ba-131">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="4f6ba-132">Listas de caractere</span><span class="sxs-lookup"><span data-stu-id="4f6ba-132">Character Lists</span></span>  
 <span data-ttu-id="4f6ba-133">Um grupo de um ou mais caracteres (`charlist`) entre colchetes (`[ ]`) pode ser usado para corresponder a qualquer caractere único no `string` e pode incluir quase qualquer código de caractere, inclusive dígitos.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="4f6ba-134">Um ponto de exclamação (`!`) no início de `charlist` significa que uma correspondência é feita se qualquer caractere, exceto os caracteres na `charlist` for encontrado no `string`.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="4f6ba-135">Quando usado fora de colchetes, o ponto de exclamação corresponde a mesmo.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-135">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="4f6ba-136">Caracteres especiais</span><span class="sxs-lookup"><span data-stu-id="4f6ba-136">Special Characters</span></span>  
 <span data-ttu-id="4f6ba-137">Para corresponder o colchete esquerdo de caracteres especiais (`[`), ponto de interrogação (`?`), sinal numérico (`#`) e o asterisco (`*`), coloque-as entre colchetes.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="4f6ba-138">O colchete direito (`]`) não pode ser usado dentro de um grupo para corresponder em si, mas pode ser usado fora de um grupo como um caractere individual.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="4f6ba-139">A sequência de caracteres `[]` é considerado uma cadeia de caracteres de comprimento zero (`""`).</span><span class="sxs-lookup"><span data-stu-id="4f6ba-139">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="4f6ba-140">No entanto, ele não pode ser parte de uma lista de caracteres entre colchetes.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-140">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="4f6ba-141">Se você quiser verificar se uma posição na `string` contém um de um grupo de caracteres ou nenhum caractere, você pode usar `Like` duas vezes.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="4f6ba-142">Para obter um exemplo, consulte [ Corresponder um padrão de um cadeia de caracteres](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="4f6ba-142">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="4f6ba-143">Intervalos de caracteres</span><span class="sxs-lookup"><span data-stu-id="4f6ba-143">Character Ranges</span></span>  
 <span data-ttu-id="4f6ba-144">Usando um hífen (`–`) para separar os limites inferior e superior do intervalo, `charlist` pode especificar um intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="4f6ba-145">Por exemplo, `[A–Z]` resulta em uma correspondência se posição do caractere correspondente em `string` contém qualquer caractere no intervalo `A`–`Z`, e `[!H–L]` resulta em uma correspondência se a posição de caractere correspondente contém qualquer caractere fora do intervalo `H`–`L`.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="4f6ba-146">Quando você especifica um intervalo de caracteres, elas devem aparecer na ordem de classificação, ou seja, crescente do menor para o mais alto.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="4f6ba-147">Portanto, `[A–Z]` é um padrão válido, mas `[Z–A]` não é.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="4f6ba-148">Vários intervalos de caracteres</span><span class="sxs-lookup"><span data-stu-id="4f6ba-148">Multiple Character Ranges</span></span>  
 <span data-ttu-id="4f6ba-149">Para especificar vários intervalos para a mesma posição de caractere, colocá-los dentro de colchetes mesmos sem delimitadores.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="4f6ba-150">Por exemplo, `[A–CX–Z]` resulta em uma correspondência se posição do caractere correspondente em `string` contém qualquer caractere dentro do intervalo `A`–`C` ou o intervalo `X`–`Z`.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="4f6ba-151">Uso do hífen</span><span class="sxs-lookup"><span data-stu-id="4f6ba-151">Usage of the Hyphen</span></span>  
 <span data-ttu-id="4f6ba-152">Um hífen (`–`) pode aparecer no início (após um ponto de exclamação, se houver) ou no final da `charlist` para corresponder ao próprio.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="4f6ba-153">Em qualquer outro local, o hífen identifica um intervalo de caracteres delimitadas por caracteres em ambos os lados do hífen.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="4f6ba-154">Sequência de agrupamento</span><span class="sxs-lookup"><span data-stu-id="4f6ba-154">Collating Sequence</span></span>  
 <span data-ttu-id="4f6ba-155">O significado de um intervalo especificado depende do caractere de ordenação em tempo de execução, conforme determinado pela `Option Compare` e a configuração de localidade do sistema qual o código está em execução.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="4f6ba-156">Com o `Option Compare Binary`, o intervalo `[A–E]` corresponde a `A`, `B`, `C`, `D`, e `E`.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="4f6ba-157">Com o `Option Compare Text`, `[A–E]` corresponde a `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, e `e`.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="4f6ba-158">O intervalo não coincide `Ê` ou `ê` porque os caracteres acentuados agrupados após caracteres não acentuados na ordem de classificação.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="4f6ba-159">Dígrafo caracteres</span><span class="sxs-lookup"><span data-stu-id="4f6ba-159">Digraph Characters</span></span>  
 <span data-ttu-id="4f6ba-160">Em alguns idiomas, há caracteres alfabéticos que representam dois caracteres distintos.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-160">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="4f6ba-161">Por exemplo, vários idiomas usam o caractere `æ` para representar os caracteres `a` e `e` quando eles forem exibidos juntos.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="4f6ba-162">O `Like` operador reconhece o caractere dígrafo único e os dois caracteres individuais são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="4f6ba-163">Quando um idioma que usa um caractere dígrafo é especificado nas configurações de localidade do sistema, uma ocorrência do caractere dígrafo única em um `pattern` ou `string` corresponde à sequência de dois caracteres equivalente em outra cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="4f6ba-164">Da mesma forma, um caractere dígrafo em `pattern` entre colchetes (por si só, em uma lista ou em um intervalo) corresponde a sequência de dois caracteres equivalente em `string`.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="4f6ba-165">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="4f6ba-165">Overloading</span></span>  
 <span data-ttu-id="4f6ba-166">O `Like` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="4f6ba-167">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="4f6ba-168">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4f6ba-168">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f6ba-169">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f6ba-169">Example</span></span>  
 <span data-ttu-id="4f6ba-170">Este exemplo usa o `Like` operador para comparar cadeias de caracteres para vários padrões.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-170">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="4f6ba-171">Os resultados entram em um `Boolean` que indica se cada cadeia de caracteres satisfizer o padrão de variável.</span><span class="sxs-lookup"><span data-stu-id="4f6ba-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="4f6ba-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f6ba-172">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="4f6ba-173">Operadores de Comparação</span><span class="sxs-lookup"><span data-stu-id="4f6ba-173">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="4f6ba-174">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4f6ba-174">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="4f6ba-175">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="4f6ba-175">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="4f6ba-176">Instrução Option Compare</span><span class="sxs-lookup"><span data-stu-id="4f6ba-176">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="4f6ba-177">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="4f6ba-177">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="4f6ba-178">Como: Corresponder um padrão de um cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4f6ba-178">How to: Match a String against a Pattern</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
