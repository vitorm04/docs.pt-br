---
title: Operadores de comparação no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- comparison operators [Visual Basic], comparing objects
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers [Visual Basic], comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values [Visual Basic], comparing
- comparison operators [Visual Basic], comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
ms.openlocfilehash: d08974a929a723d4037300f9d72ae03c072d47fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61827951"
---
# <a name="comparison-operators-in-visual-basic"></a>Operadores de comparação no Visual Basic
Operadores de comparação comparam duas expressões e retornam um `Boolean` valor que representa a relação de seus valores. Há operadores para comparar valores numéricos, operadores para comparar cadeias de caracteres e operadores para comparar objetos. Todos os três tipos de operadores serão discutidos aqui.  
  
## <a name="comparing-numeric-values"></a>Comparando valores numéricos  
 Visual Basic compara valores numéricos usando seis operadores de comparação numérica. Cada operador toma como operandos duas expressões que retornam valores numéricos. A tabela a seguir lista os operadores e mostra exemplos de cada um.  
  
|Operador|Condição testada|Exemplos|  
|--------------|----------------------|--------------|  
|`=` (Igualdade)|É o valor da primeira expressão é igual ao valor do segundo?|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` (Desigualdade)|O valor da primeira expressão é igual ao valor do segundo?|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` (Menor que)|É o valor da primeira expressão menor que o valor do segundo?|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` (Maior que)|O valor da primeira expressão é maior que o valor do segundo?|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` (Menor que ou igual a)|O valor da primeira expressão é menor ou igual ao valor do segundo?|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` (Maior que ou igual a)|O valor da primeira expressão é maior que ou igual ao valor do segundo?|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>Comparando cadeias de caracteres  
 Visual Basic compara cadeias de caracteres usando o [operador Like](../../../../visual-basic/language-reference/operators/like-operator.md) , bem como os operadores de comparação numérica. O `Like` operador permite que você especifique um padrão. A cadeia de caracteres, em seguida, é comparada com o padrão, e se ele corresponder, o resultado é `True`. Caso contrário, o resultado será `False`. Os operadores numéricos permitem que você compare `String` valores com base em sua ordem de classificação, como mostra o exemplo a seguir.  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 O resultado no exemplo anterior é `True` porque o primeiro caractere na primeira cadeia de caracteres classifica antes do primeiro caractere na segunda cadeia de caracteres. Se os primeiros caracteres fossem iguais, a comparação seria continuar para o próximo caractere em ambas as cadeias de caracteres e assim por diante. Você também pode testar a igualdade de cadeias de caracteres usando o operador de igualdade, como mostra o exemplo a seguir.  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 Se uma cadeia de caracteres é um prefixo de outro, como "aa" e "aaa", a cadeia de caracteres mais tempo será considerada para ser maior que a cadeia de caracteres mais curta. O exemplo a seguir ilustra essa situação.  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 A ordem de classificação se baseia em uma comparação binária ou de uma comparação textual, dependendo da configuração `Option Compare`. Para obter mais informações, consulte [instrução opção comparar](../../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="comparing-objects"></a>Comparando objetos  
 Visual Basic compara duas variáveis de referência de objeto com o [operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) e o [operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md). Você pode usar qualquer um desses operadores para determinar se duas variáveis de referência se referem à mesma instância do objeto. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 No exemplo anterior, `x Is y` for avaliada como `True`, porque as duas variáveis se referem à mesma instância. Compare este resultado com o exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 No exemplo anterior, `x Is y` for avaliada como `False`, porque, apesar das variáveis se referirem a objetos do mesmo tipo, elas se referem a diferentes instâncias desse tipo.  
  
 Quando você deseja testar se dois objetos não apontando para a mesma instância, o `IsNot` operador permite que você evite a gramaticalmente infeliz combinação de `Not` e `Is`. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 No exemplo anterior, `If a IsNot b` é equivalente a `If Not a Is b`.  
  
### <a name="comparing-object-type"></a>Comparando o tipo de objeto  
 Você pode testar se um objeto é de um tipo específico com o `TypeOf`... `Is` expressão. A sintaxe é a seguinte:  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 Quando `typename` Especifica um tipo de interface, então o `TypeOf`... `Is` expressão retorna `True` se o objeto implementa o tipo de interface. Quando `typename` é um tipo de classe, então a expressão retorna `True` se o objeto for uma instância da classe especificada ou de uma classe que deriva da classe especificada. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 No exemplo anterior, o `TypeOf x Is Control` expressão é avaliada como `True` porque o tipo de `x` é `Button`, que herda de `Control`.  
  
 Para obter mais informações, consulte [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="see-also"></a>Consulte também

- [Comparações de Valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Operadores de Comparação](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Operadores](../../../../visual-basic/language-reference/operators/index.md)
- [Operadores aritméticos no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operadores de concatenação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
