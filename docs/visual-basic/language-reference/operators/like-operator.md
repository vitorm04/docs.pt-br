---
title: Operador Like
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
ms.openlocfilehash: 5db9488bbec716156a3ab464042c0853241a82b1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350939"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="155d5-102">Operador Like (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="155d5-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="155d5-103">Compara uma cadeia de caracteres com um padrão.</span><span class="sxs-lookup"><span data-stu-id="155d5-103">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="155d5-104">No momento, o operador de `Like` não tem suporte no .NET Core e .NET Standard projetos.</span><span class="sxs-lookup"><span data-stu-id="155d5-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="155d5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="155d5-105">Syntax</span></span>  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="155d5-106">Partes</span><span class="sxs-lookup"><span data-stu-id="155d5-106">Parts</span></span>  
 `result`  
 <span data-ttu-id="155d5-107">Necessária.</span><span class="sxs-lookup"><span data-stu-id="155d5-107">Required.</span></span> <span data-ttu-id="155d5-108">Qualquer variável `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="155d5-108">Any `Boolean` variable.</span></span> <span data-ttu-id="155d5-109">O resultado é um valor `Boolean` indicando se o `string` satisfaz ou não o `pattern`.</span><span class="sxs-lookup"><span data-stu-id="155d5-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="155d5-110">Necessária.</span><span class="sxs-lookup"><span data-stu-id="155d5-110">Required.</span></span> <span data-ttu-id="155d5-111">Qualquer expressão de `String` .</span><span class="sxs-lookup"><span data-stu-id="155d5-111">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="155d5-112">Necessária.</span><span class="sxs-lookup"><span data-stu-id="155d5-112">Required.</span></span> <span data-ttu-id="155d5-113">Qualquer expressão de `String` que esteja de acordo com as convenções de correspondência de padrões descritas em "Comentários".</span><span class="sxs-lookup"><span data-stu-id="155d5-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="155d5-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="155d5-114">Remarks</span></span>  
 <span data-ttu-id="155d5-115">Se o valor em `string` satisfizer o padrão contido em `pattern`, `result` será `True`.</span><span class="sxs-lookup"><span data-stu-id="155d5-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="155d5-116">Se a cadeia de caracteres não atender ao padrão, `result` será `False`.</span><span class="sxs-lookup"><span data-stu-id="155d5-116">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="155d5-117">Se `string` e `pattern` forem cadeias de caracteres vazias, o resultado será `True`.</span><span class="sxs-lookup"><span data-stu-id="155d5-117">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="155d5-118">Método de comparação</span><span class="sxs-lookup"><span data-stu-id="155d5-118">Comparison Method</span></span>  
 <span data-ttu-id="155d5-119">O comportamento do operador de `Like` depende da [instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="155d5-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span> <span data-ttu-id="155d5-120">O método de comparação de cadeia de caracteres padrão para cada arquivo de origem é `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="155d5-120">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="155d5-121">Opções de padrão</span><span class="sxs-lookup"><span data-stu-id="155d5-121">Pattern Options</span></span>  
 <span data-ttu-id="155d5-122">A correspondência de padrões internos fornece uma ferramenta versátil para comparações de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="155d5-122">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="155d5-123">Os recursos de correspondência de padrões permitem que você corresponda a cada caractere em `string` em um caractere específico, um caractere curinga, uma lista de caracteres ou um intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="155d5-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="155d5-124">A tabela a seguir mostra os caracteres permitidos em `pattern` e o que eles correspondem.</span><span class="sxs-lookup"><span data-stu-id="155d5-124">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="155d5-125">Caracteres em `pattern`</span><span class="sxs-lookup"><span data-stu-id="155d5-125">Characters in `pattern`</span></span>|<span data-ttu-id="155d5-126">Correspondências no `string`</span><span class="sxs-lookup"><span data-stu-id="155d5-126">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="155d5-127">Qualquer caractere único</span><span class="sxs-lookup"><span data-stu-id="155d5-127">Any single character</span></span>|  
|`*`|<span data-ttu-id="155d5-128">Zero ou mais caracteres</span><span class="sxs-lookup"><span data-stu-id="155d5-128">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="155d5-129">Qualquer dígito único (0 a 9)</span><span class="sxs-lookup"><span data-stu-id="155d5-129">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="155d5-130">Qualquer caractere único no `charlist`</span><span class="sxs-lookup"><span data-stu-id="155d5-130">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="155d5-131">Qualquer caractere único que não esteja em `charlist`</span><span class="sxs-lookup"><span data-stu-id="155d5-131">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="155d5-132">Listas de caracteres</span><span class="sxs-lookup"><span data-stu-id="155d5-132">Character Lists</span></span>  
 <span data-ttu-id="155d5-133">Um grupo de um ou mais caracteres (`charlist`) entre colchetes (`[ ]`) pode ser usado para corresponder a qualquer caractere único em `string` e pode incluir quase qualquer código de caractere, incluindo dígitos.</span><span class="sxs-lookup"><span data-stu-id="155d5-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="155d5-134">Um ponto de exclamação (`!`) no início de `charlist` significa que uma correspondência será feita se qualquer caractere, exceto os caracteres em `charlist`, for encontrado em `string`.</span><span class="sxs-lookup"><span data-stu-id="155d5-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="155d5-135">Quando usados fora dos colchetes, o ponto de exclamação corresponde a si mesmo.</span><span class="sxs-lookup"><span data-stu-id="155d5-135">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="155d5-136">Caracteres especiais</span><span class="sxs-lookup"><span data-stu-id="155d5-136">Special Characters</span></span>  
 <span data-ttu-id="155d5-137">Para coincidir com os caracteres especiais colchetes à esquerda (`[`), ponto de interrogação (`?`), sinal de número (`#`) e asterisco (`*`), coloque-os entre colchetes.</span><span class="sxs-lookup"><span data-stu-id="155d5-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="155d5-138">O colchete direito (`]`) não pode ser usado em um grupo para corresponder a si mesmo, mas pode ser usado fora de um grupo como um caractere individual.</span><span class="sxs-lookup"><span data-stu-id="155d5-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="155d5-139">A sequência de caracteres `[]` é considerada uma cadeia de caracteres de comprimento zero (`""`).</span><span class="sxs-lookup"><span data-stu-id="155d5-139">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="155d5-140">No entanto, ele não pode fazer parte de uma lista de caracteres entre colchetes.</span><span class="sxs-lookup"><span data-stu-id="155d5-140">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="155d5-141">Se você quiser verificar se uma posição em `string` contém um de um grupo de caracteres ou nenhum caractere, você pode usar `Like` duas vezes.</span><span class="sxs-lookup"><span data-stu-id="155d5-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="155d5-142">Para obter um exemplo, consulte [como fazer a correspondência de uma cadeia de caracteres em relação a um padrão](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="155d5-142">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="155d5-143">Intervalos de caracteres</span><span class="sxs-lookup"><span data-stu-id="155d5-143">Character Ranges</span></span>  
 <span data-ttu-id="155d5-144">Usando um hífen (`–`) para separar os limites inferior e superior do intervalo, `charlist` pode especificar um intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="155d5-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="155d5-145">Por exemplo, `[A–Z]` resultará em uma correspondência se a posição de caractere correspondente em `string` contiver qualquer caractere dentro do intervalo `A`–`Z`e `[!H–L]` resultar em uma correspondência se a posição do caractere correspondente contiver qualquer caractere fora do intervalo `H`–`L`.</span><span class="sxs-lookup"><span data-stu-id="155d5-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="155d5-146">Quando você especifica um intervalo de caracteres, eles devem aparecer em ordem de classificação crescente, ou seja, do mais baixo para o mais alto.</span><span class="sxs-lookup"><span data-stu-id="155d5-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="155d5-147">Portanto, `[A–Z]` é um padrão válido, mas `[Z–A]` não é.</span><span class="sxs-lookup"><span data-stu-id="155d5-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="155d5-148">Vários intervalos de caracteres</span><span class="sxs-lookup"><span data-stu-id="155d5-148">Multiple Character Ranges</span></span>  
 <span data-ttu-id="155d5-149">Para especificar vários intervalos para a mesma posição de caractere, coloque-os dentro dos mesmos colchetes sem delimitadores.</span><span class="sxs-lookup"><span data-stu-id="155d5-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="155d5-150">Por exemplo, `[A–CX–Z]` resultará em uma correspondência se a posição de caractere correspondente em `string` contiver qualquer caractere dentro do intervalo `A`–`C` ou o intervalo `X`–`Z`.</span><span class="sxs-lookup"><span data-stu-id="155d5-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="155d5-151">Uso do hífen</span><span class="sxs-lookup"><span data-stu-id="155d5-151">Usage of the Hyphen</span></span>  
 <span data-ttu-id="155d5-152">Um hífen (`–`) pode aparecer no início (após um ponto de exclamação, se houver) ou no final de `charlist` para corresponder a si mesmo.</span><span class="sxs-lookup"><span data-stu-id="155d5-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="155d5-153">Em qualquer outro local, o hífen identifica um intervalo de caracteres delimitado pelos caracteres em ambos os lados do hífen.</span><span class="sxs-lookup"><span data-stu-id="155d5-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="155d5-154">Sequência de agrupamento</span><span class="sxs-lookup"><span data-stu-id="155d5-154">Collating Sequence</span></span>  
 <span data-ttu-id="155d5-155">O significado de um intervalo especificado depende da ordenação de caracteres em tempo de execução, conforme determinado pelo `Option Compare` e pela configuração de localidade do sistema em que o código está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="155d5-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="155d5-156">Com `Option Compare Binary`, o intervalo `[A–E]` corresponde a `A`, `B`, `C`, `D`e `E`.</span><span class="sxs-lookup"><span data-stu-id="155d5-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="155d5-157">Com `Option Compare Text`, `[A–E]` corresponde a `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`e `e`.</span><span class="sxs-lookup"><span data-stu-id="155d5-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="155d5-158">O intervalo não corresponde a `Ê` ou `ê` porque os caracteres acentuados se agrupam após caracteres não acentuados na ordem de classificação.</span><span class="sxs-lookup"><span data-stu-id="155d5-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="155d5-159">Caracteres digrafo</span><span class="sxs-lookup"><span data-stu-id="155d5-159">Digraph Characters</span></span>  
 <span data-ttu-id="155d5-160">Em alguns idiomas, há caracteres alfabéticos que representam dois caracteres separados.</span><span class="sxs-lookup"><span data-stu-id="155d5-160">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="155d5-161">Por exemplo, várias linguagens usam o caractere `æ` para representar os caracteres `a` e `e` quando aparecem juntos.</span><span class="sxs-lookup"><span data-stu-id="155d5-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="155d5-162">O operador `Like` reconhece que o caractere dígrafo único e os dois caracteres individuais são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="155d5-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="155d5-163">Quando um idioma que usa um caractere dígrafo é especificado nas configurações de localidade do sistema, uma ocorrência do caractere digraph único em `pattern` ou `string` corresponde à seqüência de dois caracteres equivalente na outra cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="155d5-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="155d5-164">Da mesma forma, um caractere digrafo em `pattern` entre colchetes (por si só, em uma lista ou em um intervalo) corresponde à sequência de dois caracteres equivalente em `string`.</span><span class="sxs-lookup"><span data-stu-id="155d5-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="155d5-165">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="155d5-165">Overloading</span></span>  
 <span data-ttu-id="155d5-166">O operador `Like` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="155d5-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="155d5-167">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="155d5-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="155d5-168">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="155d5-168">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="155d5-169">Exemplo</span><span class="sxs-lookup"><span data-stu-id="155d5-169">Example</span></span>  
 <span data-ttu-id="155d5-170">Este exemplo usa o operador `Like` para comparar cadeias de caracteres com vários padrões.</span><span class="sxs-lookup"><span data-stu-id="155d5-170">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="155d5-171">Os resultados entram em uma variável `Boolean` indicando se cada cadeia de caracteres satisfaz o padrão.</span><span class="sxs-lookup"><span data-stu-id="155d5-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="155d5-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="155d5-172">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="155d5-173">Operadores de Comparação</span><span class="sxs-lookup"><span data-stu-id="155d5-173">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="155d5-174">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="155d5-174">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="155d5-175">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="155d5-175">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="155d5-176">Instrução Option Compare</span><span class="sxs-lookup"><span data-stu-id="155d5-176">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="155d5-177">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="155d5-177">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="155d5-178">Como corresponder uma cadeia de caracteres a um padrão</span><span class="sxs-lookup"><span data-stu-id="155d5-178">How to: Match a String against a Pattern</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
