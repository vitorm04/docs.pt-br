---
title: Operadores de comparação (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: 10558563b528ce0bae3f77f31a97a217018f455f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666833"
---
# <a name="comparison-operators-visual-basic"></a>Operadores de comparação (Visual Basic)
A seguir estão os operadores de comparação definidos no Visual Basic.

 `<`operador

 `<=`operador

 `>`operador

 `>=`operador

 `=`operador

 `<>`operador

 [Operador Is](../../../visual-basic/language-reference/operators/is-operator.md)

 [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)

 [Operador Like](../../../visual-basic/language-reference/operators/like-operator.md)

 Esses operadores comparam duas expressões para determinar se elas são iguais e se não, como diferem. `Is`, `IsNot` e`Like` são discutidos em detalhes em páginas de ajuda separadas. Os operadores de comparação relacional são discutidos em detalhes nesta página.

## <a name="syntax"></a>Sintaxe
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>Partes
 `result`  
 Necessário. Um `Boolean` valor que representa o resultado da comparação.

 `expression1`, `expression2`  
 Necessário. Qualquer expressão.

 `comparisonoperator`  
 Necessário. Qualquer operador de comparação relacional.

 `object1`, `object2`  
 Necessário. Qualquer nome de objeto de referência.

 `string`  
 Necessário. Qualquer expressão de `String` .

 `pattern`  
 Necessário. Qualquer `String` expressão ou intervalo de caracteres.

## <a name="remarks"></a>Comentários
 A tabela a seguir contém uma lista dos operadores de comparação relacional e as condições que determinam `True` se `False` `result` é ou.

|Operator|`True` se|`False` se|
|--------------|---------------|----------------|
|`<`(Menor que)|`expression1` < `expression2`|`expression1` >= `expression2`|
|`<=`(Menor que ou igual a)|`expression1` <= `expression2`|`expression1` > `expression2`|
|`>`(Maior que)|`expression1` > `expression2`|`expression1` <= `expression2`|
|`>=`(Maior ou igual a)|`expression1` >= `expression2`|`expression1` < `expression2`|
|`=`(Igual a)|`expression1` = `expression2`|`expression1` <> `expression2`|
|`<>`(Diferente de)|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
>  O [operador =](../../../visual-basic/language-reference/operators/assignment-operator.md) também é usado como um operador de atribuição.

 O `Is` operador, o `IsNot` operador e o `Like` operador têm funcionalidades de comparação específicas que diferem dos operadores na tabela anterior.

## <a name="comparing-numbers"></a>Comparando números
 Quando você compara uma expressão do tipo `Single` a um do tipo `Double`, a `Single` expressão é convertida `Double`em. Esse comportamento é oposto ao comportamento encontrado no Visual Basic 6.

 Da mesma forma, quando você compara uma expressão `Decimal` do tipo com uma expressão `Single` do `Double`tipo ou `Decimal` , a expressão é `Single` convertida em ou `Double`. Para `Decimal` expressões, qualquer valor fracionário menor que 1e 28 pode ser perdido. Essa perda de valor fracionário pode fazer com que dois valores sejam comparados como iguais quando não forem. Por esse motivo, você deve tomar cuidado ao usar igualdade (`=`) para comparar duas variáveis de ponto flutuante. É mais seguro testar se o valor absoluto da diferença entre os dois números é menor que uma pequena tolerância aceitável.

### <a name="floating-point-imprecision"></a>Irprecisão de ponto flutuante
 Quando você trabalha com números de ponto flutuante, tenha em mente que eles nem sempre têm uma representação precisa na memória. Isso pode levar a resultados inesperados de determinadas operações, como comparação de valor e o [operador Mod](../../../visual-basic/language-reference/operators/mod-operator.md). Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).

## <a name="comparing-strings"></a>Comparando cadeias de caracteres
 Quando você compara Cadeias de caracteres, as expressões de cadeia são avaliadas com base na ordem de classificação alfabética `Option Compare` , que depende da configuração.

 `Option Compare Binary`baseia as comparações de cadeia de caracteres em uma ordem de classificação derivada das representações binárias internas dos caracteres. A ordem de classificação é determinada pela página de código. O exemplo a seguir mostra uma ordem de classificação binária típica.

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 `Option Compare Text`baseia comparações de cadeia de caracteres em uma ordem de classificação textual, que não diferencia maiúsculas de minúsculas, determinada pela localidade do seu aplicativo. Quando você define `Option Compare Text` e classifica os caracteres no exemplo anterior, a ordem de classificação de texto a seguir se aplica:

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a>Dependência de localidade
 Quando você define `Option Compare Text`, o resultado de uma comparação de cadeia de caracteres pode depender da localidade em que o aplicativo está sendo executado. Dois caracteres podem ser comparados como iguais em uma localidade, mas não em outro. Se você estiver usando uma comparação de cadeias de caracteres para tomar decisões importantes, como, por exemplo, se deve aceitar uma tentativa de fazer logon, você deve ser alertado sobre a confidencialidade da localidade. Considere a configuração `Option Compare Binary` ou a chamada <xref:Microsoft.VisualBasic.Strings.StrComp%2A>do, que leva a localidade em conta.

## <a name="typeless-programming-with-relational-comparison-operators"></a>Programação sem tipo com operadores de comparação relacionais
 O uso de operadores de comparação relacional `Object` com expressões não é permitido `Option Strict On`em. Quando `Option Strict` é `Off`, e `expression1` ou é`expression2` uma`Object` expressão, os tipos de tempo de execução determinam como eles são comparados. A tabela a seguir mostra como as expressões são comparadas e o resultado da comparação, dependendo do tipo de tempo de execução dos operandos.

|Se os operandos forem|A comparação é|
|---------------------|-------------------|
|Mesmo`String`|Comparação de classificação com base em características de classificação de cadeia de caracteres.|
|Ambos numéricos|Objetos convertidos `Double`em, comparação numérica.|
|Um numérico e um`String`|O `String` é convertido em a `Double` e uma comparação numérica é executada. Se o `String` não puder ser convertido `Double`em, <xref:System.InvalidCastException> um será lançado.|
|Ou ambos são tipos de referência diferentes de`String`|<xref:System.InvalidCastException> é lançada.|

 Comparações numéricas tratam `Nothing` como 0. Comparações de `Nothing` cadeia `""` de caracteres tratam como (uma cadeia de caracteres vazia).

## <a name="overloading"></a>Sobrecarga
 Os operadores de comparação relacional`<`(. `<=``>`,,,, )podemsersobrecarregados,oquesignificaqueumaclasseouestruturapoderedefinirseucomportamentoquandoumoperandotemotipodessaclasseouestrutura.`<>` `>=` `=` Se o seu código usar qualquer um desses operadores em uma classe ou estrutura desse tipo, certifique-se de entender o comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

 Observe que o [operador =](../../../visual-basic/language-reference/operators/assignment-operator.md) pode ser sobrecarregado apenas como um operador de comparação relacional, não como um operador de atribuição.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra vários usos de operadores de comparação relacionais, que você usa para comparar expressões. Operadores de comparação relacional retornam um `Boolean` resultado que representa se a expressão declarada deve ou não ser `True`avaliada. Quando você aplica os `>` operadores `<` e às cadeias de caracteres, a comparação é feita usando a ordem de classificação alfabética normal das cadeias de caracteres. Essa ordem pode ser dependente de sua configuração de localidade. Se a classificação diferencia maiúsculas de minúsculas ou não depende da configuração de [comparação de opção](../../../visual-basic/language-reference/statements/option-compare-statement.md) .

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 No exemplo anterior, a primeira comparação retorna `False` e as comparações `True`restantes são retornadas.

## <a name="see-also"></a>Consulte também

- <xref:System.InvalidCastException>
- [Operador =](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Solução de problemas de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Operadores de comparação no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
