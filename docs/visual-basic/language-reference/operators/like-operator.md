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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4fb71bdb111681e3e8c7a2762605284105a672dd
ms.lasthandoff: 03/13/2017

---
# <a name="like-operator-visual-basic"></a>Operador Like (Visual Basic)
Compara uma cadeia de caracteres com um padrão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = string Like pattern  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Qualquer `Boolean` variável. O resultado é um `Boolean` valor que indica se ou não o `string` satisfaz a `pattern`.  
  
 `string`  
 Necessário. Qualquer expressão de `String` .  
  
 `pattern`  
 Necessário. Qualquer `String` expressão de acordo com as convenções de correspondência de padrão descritas em "Comentários".  
  
## <a name="remarks"></a>Comentários  
 Se o valor em `string` satisfizer o padrão contido em `pattern`, `result` é `True`. Se a cadeia de caracteres não satisfizer o padrão, `result` é `False`. Se ambos os `string` e `pattern` são cadeias de caracteres vazias, o resultado é `True`.  
  
## <a name="comparison-method"></a>Método de comparação  
 O comportamento do `Like` depende do operador de [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md). O método de comparação de cadeia de caracteres padrão para cada arquivo de origem é `Option Compare Binary`.  
  
## <a name="pattern-options"></a>Opções padrão  
 Correspondência de padrões interna fornece uma ferramenta versátil para comparações de cadeia de caracteres. Os recursos de correspondência permitem que você coincida cada caractere em `string` em relação a um caractere específico, um caractere curinga, uma lista de caracteres ou um intervalo de caracteres. A tabela a seguir mostra os caracteres permitidos em `pattern` e o que eles correspondem.  
  
|Caracteres em`pattern`|Correspondências em`string`|  
|-----------------------------|-------------------------|  
|`?`|Qualquer caractere único|  
|`*`|Zero ou mais caracteres|  
|`#`|Qualquer dígito único (0 –&9;)|  
|`[` `charlist` `]`|Qualquer caractere único no`charlist`|  
|`[!` `charlist` `]`|Qualquer caractere único não em`charlist`|  
  
## <a name="character-lists"></a>Listas de caracteres  
 Um grupo de um ou mais caracteres (`charlist`) entre colchetes (`[ ]`) pode ser usado para corresponder a qualquer caractere único no `string` e pode incluir qualquer código de caractere, inclusive dígitos.  
  
 Um ponto de exclamação (`!`) no início do `charlist` significa que uma coincidência é feita se qualquer caractere, exceto os caracteres em `charlist` encontrado em `string`. Quando usado fora de colchetes, o ponto de exclamação corresponde a mesmo.  
  
## <a name="special-characters"></a>Caracteres especiais  
 Para coincidir o colchete esquerdo de caracteres especiais (`[`), ponto de interrogação (`?`), sinal numérico (`#`) e o asterisco (`*`), coloque-os entre colchetes. O colchete direito (`]`) não pode ser usado dentro de um grupo para corresponder em si, mas pode ser usado fora de um grupo como um caractere individual.  
  
 A sequência de caracteres `[]` é considerado uma cadeia de caracteres de comprimento zero (`""`). No entanto, ele não pode ser parte de uma lista de caracteres entre colchetes. Se você quiser verificar se uma posição na `string` contém um de um grupo de caracteres ou nenhum caractere, você pode usar `Like` duas vezes. Para obter um exemplo, consulte [como: corresponder uma cadeia de caracteres com um padrão](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Intervalos de caracteres  
 Usando um hífen (`–`) para separar os limites inferior e superior do intervalo, `charlist` pode especificar um intervalo de caracteres. Por exemplo, `[A–Z]` resulta em uma coincidência se a posição do caractere correspondente em `string` contiver qualquer caractere dentro do intervalo `A`–`Z`, e `[!H–L]` resulta em uma coincidência se a posição do caractere correspondente contém qualquer caractere fora do intervalo `H`–`L`.  
  
 Quando você especificar um intervalo de caracteres, eles devem aparecer em ordem de classificação, ou seja, crescente de menor para maior. Portanto, `[A–Z]` é um padrão válido, mas `[Z–A]` não é.  
  
### <a name="multiple-character-ranges"></a>Vários intervalos de caracteres  
 Para especificar vários intervalos para a mesma posição de caractere, coloque-os entre os mesmos colchetes sem delimitadores. Por exemplo, `[A–CX–Z]` resulta em uma coincidência se a posição do caractere correspondente em `string` contiver qualquer caractere dentro do intervalo `A`–`C` ou o intervalo de `X`–`Z`.  
  
### <a name="usage-of-the-hyphen"></a>Uso do hífen  
 Um hífen (`–`) pode aparecer no início (após um ponto de exclamação, se houver) ou no final da `charlist` para corresponder ao próprio. Em qualquer outro local, o hífen identifica um intervalo de caracteres delimitada por caracteres em ambos os lados do hífen.  
  
## <a name="collating-sequence"></a>Sequência de agrupamento  
 O significado de um intervalo especificado depende do caractere de ordenação em tempo de execução, conforme determinado pela `Option``Compare` e a configuração de localidade do sistema qual o código está em execução. With `Option``Compare``Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`. With `Option``Compare``Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`. O intervalo não coincide com `Ê` ou `ê` porque caracteres acentuados agupam após caracteres não acentuados na ordem de classificação.  
  
## <a name="digraph-characters"></a>Caracteres de digraph  
 Em alguns idiomas, há caracteres alfabéticos que representam dois caracteres distintos. Por exemplo, vários idiomas usam o caractere `æ` para representar os caracteres `a` e `e` quando aparecem juntos. O `Like` operador reconhece que o caractere dígrafo único e os dois caracteres individuais são equivalentes.  
  
 Quando um idioma que usa um caractere dígrafo for especificado nas configurações de localidade do sistema, uma ocorrência do caractere dígrafo única em uma `pattern` ou `string` corresponde à sequência de dois caracteres equivalente na outra sequência de caracteres. Da mesma forma, um caractere dígrafo em `pattern` entre colchetes (por si só, em uma lista ou em um intervalo) coincide com a sequência de dois caracteres equivalente na `string`.  
  
## <a name="overloading"></a>Sobrecarga  
 O `Like` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `Like` operador para comparar cadeias de caracteres para vários padrões. Os resultados entram em uma `Boolean` variável que indica se cada cadeia de caracteres satisfaz o padrão.  
  
 [!code-vb[30 VbVbalrOperators](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A></xref:Microsoft.VisualBasic.Strings.InStr%2A>   
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A></xref:Microsoft.VisualBasic.Strings.StrComp%2A>   
 [Operadores de comparação](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Operadores e expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Como corresponder uma cadeia de caracteres a um padrão](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
