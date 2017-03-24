---
title: "Operadores de comparação em Visual Basic | Documentos do Microsoft"
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
- comparison operators, comparing objects
- strings [Visual Basic], comparing
- comparison operators
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers, comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values, comparing
- comparison operators, comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
caps.latest.revision: 13
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
ms.openlocfilehash: 6185d1676f2cd160c9c3e855cce4a6d2bbe2ffb4
ms.lasthandoff: 03/13/2017

---
# <a name="comparison-operators-in-visual-basic"></a>Operadores de comparação no Visual Basic
Operadores de comparação comparam duas expressões e retornam um `Boolean` valor que representa a relação entre seus valores. Há operadores para comparar valores numéricos, operadores para comparar cadeias de caracteres e operadores para comparar objetos. Todos os três tipos de operadores serão discutidos aqui.  
  
## <a name="comparing-numeric-values"></a>Comparando valores numéricos  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]compara valores numéricos usando seis operadores de comparação numérica. Cada operador toma como operandos duas expressões que retornam valores numéricos. A tabela a seguir lista os operadores e mostra exemplos de cada um.  
  
|Operador|Condição testada|Exemplos|  
|--------------|----------------------|--------------|  
|`=`(Igualdade)|É o valor da primeira expressão é igual ao valor da segunda?|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>`(Desigualdade)|O valor da primeira expressão é diferente do valor da segunda?|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<`(Menor que)|É o valor da primeira expressão menor que o valor da segunda?|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>`(Maior que)|O valor da primeira expressão é maior que o valor da segunda?|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=`(Menor que ou igual a)|O valor da primeira expressão é menor ou igual ao valor da segunda?|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=`(Maior que ou igual a)|É o valor da primeira expressão maior que ou igual ao valor da segunda?|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>Comparando cadeias de caracteres  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]compara cadeias de caracteres usando o [operador Like](../../../../visual-basic/language-reference/operators/like-operator.md) , bem como os operadores de comparação numérica. O `Like` operador permite que você especifique um padrão. A cadeia de caracteres é comparada com o padrão e se há correspondência, o resultado é `True`. Caso contrário, o resultado será `False`. Os operadores numéricos permitem que você compare `String` valores com base em sua ordem de classificação, como mostra o exemplo a seguir.  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 O resultado no exemplo anterior é `True` porque o primeiro caractere na primeira cadeia de caracteres classifica-se antes do primeiro caractere na segunda cadeia de caracteres. Se os primeiros caracteres fossem iguais, a comparação seria continuar com o próximo caractere em ambas as cadeias de caracteres e assim por diante. Você também pode testar a igualdade de cadeias de caracteres usando o operador de igualdade, como mostra o exemplo a seguir.  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 Se uma cadeia de caracteres é um prefixo de outra, como "aa" e "aaa", a cadeia de caracteres mais longa será considerada para ser maior do que a cadeia de caracteres mais curta. O exemplo a seguir ilustra essa situação.  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 A ordem de classificação se baseia em uma comparação binária ou uma comparação textual, dependendo da configuração do `Option Compare`. Para obter mais informações, consulte [Option Compare Statement](../../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="comparing-objects"></a>Comparando objetos  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]compara dois objetos referenciando variáveis com o [operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) e [operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md). Você pode usar qualquer um desses operadores para determinar se duas variáveis de referência se referem à mesma instância de objeto. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators&#65;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 No exemplo anterior, `x Is y` é avaliada como `True`, porque ambas as variáveis referem-se à mesma instância. Compare este resultado com o exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators&#66;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]  
  
 No exemplo anterior, `x Is y` é avaliada como `False`, porque apesar das variáveis se referirem a objetos do mesmo tipo, elas se referem a diferentes instâncias do mesmo tipo.  
  
 Quando você quiser testar se dois objetos não apontam para a mesma instância, o `IsNot` operador permite que você evite a gramaticalmente infeliz combinação de `Not` e `Is`. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators&#67;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]  
  
 No exemplo anterior, `If a IsNot b` é equivalente a `If Not a Is b`.  
  
### <a name="comparing-object-type"></a>Comparando o tipo de objeto  
 Você pode testar se um objeto for de um tipo específico com o `TypeOf`... `Is` expressão. A sintaxe é a seguinte:  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 Quando `typename` Especifica um tipo de interface, então o `TypeOf`... `Is` retorna `True` se o objeto implementa o tipo de interface. Quando `typename` é um tipo de classe, então a expressão retorna `True` se o objeto for uma instância da classe especificada ou de uma classe que deriva da classe especificada. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators&#68;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]  
  
 No exemplo anterior, o `TypeOf x Is Control` expressão é avaliada como `True` porque o tipo de `x` é `Button`, que herda do `Control`.  
  
 Para obter mais informações, consulte [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="see-also"></a>Consulte também  
 [Comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Operadores de comparação](../../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Operadores](../../../../visual-basic/language-reference/operators/index.md)   
 [Operadores aritméticos em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operadores de concatenação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
