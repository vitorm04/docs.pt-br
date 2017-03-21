---
title: "Operadores de comparação (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
dev_langs:
- VB
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators, syntax
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
- comparison operators, Visual Basicl
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
caps.latest.revision: 20
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: c132ab50d05a8048a594a6837767fd114ff4c0a7
ms.lasthandoff: 03/13/2017

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
  
 Esses operadores comparam duas expressões para determinar se ou não forem iguais, e se não, como eles diferem. `Is`, `IsNot`, e `Like` são discutidos em detalhes em páginas de Ajuda separadas. Os operadores de comparação relacional são discutidos em detalhes nesta página.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Um `Boolean` valor que representa o resultado da comparação.  
  
 `expression`  
 Necessário. Qualquer expressão.  
  
 `comparisonoperator`  
 Necessário. Qualquer operador de comparação relacional.  
  
 `object1`, `object2`  
 Necessário. Qualquer referência a nomes de objeto.  
  
 `string`  
 Necessário. Qualquer expressão de `String` .  
  
 `pattern`  
 Necessário. Qualquer `String` expressão ou um intervalo de caracteres.  
  
## <a name="remarks"></a>Comentários  
 A tabela a seguir contém uma lista de operadores de comparação relacional e as condições que determinam se `result` é `True` ou `False`.  
  
|Operador|`True`Se|`False`Se|  
|--------------|---------------|----------------|  
|`<`(Menor que)|`expression1` < `expression2`|`expression1` >= `expression2`|  
|`<=`(Menor que ou igual a)|`expression1` <= `expression2`|`expression1` > `expression2`|  
|`>`(Maior que)|`expression1` > `expression2`|`expression1` <= `expression2`|  
|`>=`(Maior que ou igual a)|`expression1` >= `expression2`|`expression1` < `expression2`|  
|`=`(Igual a)|`expression1` = `expression2`|`expression1` <> `expression2`|  
|`<>`(Não igual a)|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  O [= operador](../../../visual-basic/language-reference/operators/assignment-operator.md) também é usado como um operador de atribuição.  
  
 O `Is` operador, o `IsNot` operador e o `Like` operador tem funcionalidades específicas de comparação diferentes dos operadores na tabela anterior.  
  
## <a name="comparing-numbers"></a>Comparação de números  
 Se você comparar uma expressão do tipo `Single` para um tipo `Double`, o `Single` expressão é convertida em `Double`. Esse comportamento é oposição o comportamento encontrado no Visual Basic 6.  
  
 Da mesma forma, se você comparar uma expressão do tipo `Decimal` em uma expressão de tipo `Single` ou `Double`, o `Decimal` expressão é convertida em `Single` ou `Double`. Para `Decimal` expressões, qualquer valor fracionário 1E-28 menor que pode ser perdido. Essa perda de valor fracionário pode causar dois valores sejam comparados como iguais quando não são. Por esse motivo, você deve ter cuidado ao usar igualdade (`=`) para comparar duas variáveis de ponto flutuantes. É mais seguro testar se o valor absoluto da diferença entre os dois números é menor do que um pequeno tolerância aceitável.  
  
### <a name="floating-point-imprecision"></a>Ponto flutuante imprecisão  
 Quando você trabalha com números de ponto flutuante, tenha em mente que eles nem sempre têm uma representação precisa na memória. Isso pode levar a resultados inesperados em certas operações, como comparação de valor e o [operador Mod](../../../visual-basic/language-reference/operators/mod-operator.md). Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="comparing-strings"></a>Comparando cadeias de caracteres  
 Ao comparar cadeias de caracteres, as expressões de cadeia de caracteres são avaliadas com base em sua ordem de classificação alfabética, o que depende de `Option Compare` configuração.  
  
 `Option Compare Binary`bases de comparações em uma ordem de classificação derivada das representações binárias internas dos caracteres de cadeia de caracteres. A ordem de classificação é determinada pela página de código. O exemplo a seguir mostra uma ordem de classificação binária típica.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text`bases de cadeia de caracteres comparações em uma ordem de classificação textual diferenciam maiusculas de minúsculas determinada pela localidade do seu aplicativo. Quando você define `Option Compare Text` e classificar os caracteres no exemplo anterior, a seguinte ordem de classificação se aplica:  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a>Dependência de localidade  
 Quando você define `Option Compare Text`, o resultado de uma comparação de cadeia de caracteres pode depender de localidade no qual o aplicativo é executado. Dois caracteres podem ser comparados como iguais em uma localidade, mas não em outro. Se você estiver usando uma comparação de cadeia de caracteres para tomar decisões importantes, como aceitar uma tentativa de logon, você deve estar alerta a distinção de localidade. Considere uma das configurações `Option Compare Binary` ou chamando o <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, que usa a localidade em consideração.</xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a>Programação sem tipo com operadores de comparação relacional  
 O uso de operadores de comparação relacional com `Object` expressões não é permitido em `Option Strict On`. Quando `Option Strict` é `Off`e `expression1` ou `expression2` é um `Object` expressão, os tipos de tempo de execução determinam como são comparados. A tabela a seguir mostra como as expressões são comparadas e o resultado da comparação, dependendo do tipo de tempo de execução dos operandos.  
  
|Se os operandos forem|Comparação|  
|---------------------|-------------------|  
|Ambos`String`|Comparação com base em características de classificação de cadeia de caracteres de classificação.|  
|Ambas numéricas|Os objetos convertidos em `Double`, comparação numérica.|  
|Um numérico e uma`String`|O `String` é convertido em um `Double` e comparação numérica será realizada. Se o `String` não pode ser convertido em `Double`, um <xref:System.InvalidCastException>é lançada.</xref:System.InvalidCastException>|  
|Um ou ambos são tipos de referência diferente`String`|Um <xref:System.InvalidCastException>é lançada.</xref:System.InvalidCastException>|  
  
 Tratam comparações numéricas `Nothing` como 0. Tratam comparações de cadeia de caracteres `Nothing` como `""` (uma cadeia de caracteres vazia).  
  
## <a name="overloading"></a>Sobrecarga  
 Os operadores de comparação relacional (`<`. `<=``>`, `>=`, `=`, `<>`) pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa qualquer um destes operadores em uma classe ou estrutura, certifique-se de que você compreender o comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
 Observe que o [= operador](../../../visual-basic/language-reference/operators/assignment-operator.md) pode ser sobrecarregado somente como um operador relacional, não como um operador de atribuição.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra vários usos de operadores de comparação relacional que você usar para comparar expressões. Operadores de comparação relacional retornam um `Boolean` resultado que representa se a expressão declarada é avaliada como `True`. Quando você aplica o `>` e `<` operadores em cadeias de caracteres, a comparação é feita usando a ordem de classificação alfabética normal das cadeias de caracteres. Essa ordem pode ser dependente de sua configuração de localidade. Se a classificação diferencia maiusculas de minúsculas ou não depende de [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) configuração.  
  
 [!code-vb[VbVbalrOperators n º&1;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 No exemplo anterior, a primeira comparação retorna `False` e retornam as comparações restantes `True`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.InvalidCastException></xref:System.InvalidCastException>   
 [= Operador](../../../visual-basic/language-reference/operators/assignment-operator.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Operadores de comparação em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
