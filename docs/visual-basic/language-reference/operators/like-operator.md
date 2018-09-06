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
ms.openlocfilehash: c5b26bd1d3ebae5136718833c124e3c6e575e9b7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800213"
---
# <a name="like-operator-visual-basic"></a>Operador Like (Visual Basic)
Compara uma cadeia de caracteres com um padrão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Qualquer `Boolean` variável. O resultado é um `Boolean` valor que indica se ou não o `string` satisfaz o `pattern`.  
  
 `string`  
 Necessário. Qualquer expressão de `String` .  
  
 `pattern`  
 Necessário. Qualquer `String` expressão de acordo com as convenções de correspondência de padrão descritas em "Comentários".  
  
## <a name="remarks"></a>Comentários  
 Se o valor em `string` satisfizer o padrão contido em `pattern`, `result` é `True`. Se a cadeia de caracteres não satisfizer o padrão `result` é `False`. Se os dois `string` e `pattern` são cadeias de caracteres vazias, o resultado é `True`.  
  
## <a name="comparison-method"></a>Método de comparação  
 O comportamento do `Like` depende do operador a [instrução opção comparar](../../../visual-basic/language-reference/statements/option-compare-statement.md). O método de comparação de cadeia de caracteres padrão para cada arquivo de origem é `Option Compare Binary`.  
  
## <a name="pattern-options"></a>Opções padrão  
 Correspondência de padrões interna fornece uma ferramenta versátil para comparações de cadeia de caracteres. Os recursos de correspondência de padrões permitem que a correspondência entre cada caractere em `string` em relação a um caractere específico, um caractere curinga, uma lista de caracteres ou um intervalo de caracteres. A tabela a seguir mostra os caracteres permitidos em `pattern` e o que eles correspondem.  
  
|Caracteres em `pattern`|Correspondências em `string`|  
|-----------------------------|-------------------------|  
|`?`|Qualquer caractere único|  
|`*`|Zero ou mais caracteres|  
|`#`|Qualquer dígito único (0 – 9)|  
|`[charlist]`|Qualquer caractere único no `charlist`|  
|`[!charlist]`|Qualquer caractere único que não está em `charlist`|  
  
## <a name="character-lists"></a>Listas de caractere  
 Um grupo de um ou mais caracteres (`charlist`) entre colchetes (`[ ]`) pode ser usado para corresponder a qualquer caractere único no `string` e pode incluir quase qualquer código de caractere, inclusive dígitos.  
  
 Um ponto de exclamação (`!`) no início de `charlist` significa que uma correspondência é feita se qualquer caractere, exceto os caracteres na `charlist` for encontrado no `string`. Quando usado fora de colchetes, o ponto de exclamação corresponde a mesmo.  
  
## <a name="special-characters"></a>Caracteres especiais  
 Para corresponder o colchete esquerdo de caracteres especiais (`[`), ponto de interrogação (`?`), sinal numérico (`#`) e o asterisco (`*`), coloque-as entre colchetes. O colchete direito (`]`) não pode ser usado dentro de um grupo para corresponder em si, mas pode ser usado fora de um grupo como um caractere individual.  
  
 A sequência de caracteres `[]` é considerado uma cadeia de caracteres de comprimento zero (`""`). No entanto, ele não pode ser parte de uma lista de caracteres entre colchetes. Se você quiser verificar se uma posição na `string` contém um de um grupo de caracteres ou nenhum caractere, você pode usar `Like` duas vezes. Por exemplo, consulte [como: corresponder uma cadeia de caracteres com um padrão](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Intervalos de caracteres  
 Usando um hífen (`–`) para separar os limites inferior e superior do intervalo, `charlist` pode especificar um intervalo de caracteres. Por exemplo, `[A–Z]` resulta em uma correspondência se posição do caractere correspondente em `string` contém qualquer caractere no intervalo `A`–`Z`, e `[!H–L]` resulta em uma correspondência se a posição de caractere correspondente contém qualquer caractere fora do intervalo `H`–`L`.  
  
 Quando você especifica um intervalo de caracteres, elas devem aparecer na ordem de classificação, ou seja, crescente do menor para o mais alto. Portanto, `[A–Z]` é um padrão válido, mas `[Z–A]` não é.  
  
### <a name="multiple-character-ranges"></a>Vários intervalos de caracteres  
 Para especificar vários intervalos para a mesma posição de caractere, colocá-los dentro de colchetes mesmos sem delimitadores. Por exemplo, `[A–CX–Z]` resulta em uma correspondência se posição do caractere correspondente em `string` contém qualquer caractere dentro do intervalo `A`–`C` ou o intervalo `X`–`Z`.  
  
### <a name="usage-of-the-hyphen"></a>Uso do hífen  
 Um hífen (`–`) pode aparecer no início (após um ponto de exclamação, se houver) ou no final da `charlist` para corresponder ao próprio. Em qualquer outro local, o hífen identifica um intervalo de caracteres delimitadas por caracteres em ambos os lados do hífen.  
  
## <a name="collating-sequence"></a>Sequência de agrupamento  
 O significado de um intervalo especificado depende do caractere de ordenação em tempo de execução, conforme determinado pela `Option Compare` e a configuração de localidade do sistema qual o código está em execução. Com o `Option Compare Binary`, o intervalo `[A–E]` corresponde a `A`, `B`, `C`, `D`, e `E`. Com o `Option Compare Text`, `[A–E]` corresponde a `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, e `e`. O intervalo não coincide `Ê` ou `ê` porque os caracteres acentuados agrupados após caracteres não acentuados na ordem de classificação.  
  
## <a name="digraph-characters"></a>Dígrafo caracteres  
 Em alguns idiomas, há caracteres alfabéticos que representam dois caracteres distintos. Por exemplo, vários idiomas usam o caractere `æ` para representar os caracteres `a` e `e` quando eles forem exibidos juntos. O `Like` operador reconhece o caractere dígrafo único e os dois caracteres individuais são equivalentes.  
  
 Quando um idioma que usa um caractere dígrafo é especificado nas configurações de localidade do sistema, uma ocorrência do caractere dígrafo única em um `pattern` ou `string` corresponde à sequência de dois caracteres equivalente em outra cadeia de caracteres. Da mesma forma, um caractere dígrafo em `pattern` entre colchetes (por si só, em uma lista ou em um intervalo) corresponde a sequência de dois caracteres equivalente em `string`.  
  
## <a name="overloading"></a>Sobrecarga  
 O `Like` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `Like` operador para comparar cadeias de caracteres para vários padrões. Os resultados entram em um `Boolean` que indica se cada cadeia de caracteres satisfizer o padrão de variável.  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [Operadores de Comparação](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Como corresponder uma cadeia de caracteres a um padrão](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
