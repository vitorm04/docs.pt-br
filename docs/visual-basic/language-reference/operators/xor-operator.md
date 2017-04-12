---
title: Operador XOR (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Xor
dev_langs:
- VB
helpviewer_keywords:
- exclusive OR operator
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator
- operators [Visual Basic], bitwise
- bitwise operators, XOR operator
- Xor operator [Visual Basic]
- Xor keyword
- bitwise comparison
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
caps.latest.revision: 17
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
ms.openlocfilehash: a8bc4735536444c7e3b361f2eaf1c43f7ca6584c
ms.lasthandoff: 03/13/2017

---
# <a name="xor-operator-visual-basic"></a>Operador Xor (Visual Basic)
Executa uma exclusão lógica em duas `Boolean` expressões ou uma exclusão bit a bit em duas expressões numéricas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Qualquer `Boolean` ou variável numérica. Para comparação Boolean, `result` é a exclusão lógica (disjunção lógica exclusiva) de dois `Boolean` valores. Para operações bit a bit, `result` é um valor numérico que representa a exclusão bit a bit (disjunção bit a bit exclusiva) dos dois padrões numéricos de bits.  
  
 `expression1`  
 Necessário. Qualquer `Boolean` ou expressão numérica.  
  
 `expression2`  
 Necessário. Qualquer `Boolean` ou expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 Para comparação Boolean, `result` é `True` se e somente se exatamente um `expression1` e `expression2` é avaliada como `True`. Isto é, se e somente se `expression1` e `expression2` avaliar oposta à `Boolean` valores. A tabela a seguir ilustra como `result` é determinado.  
  
|If `expression1` is|E `expression2` é|O valor de `result` é|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Em uma comparação Booleana, o `Xor` operador sempre avalia as duas expressões, que podem incluir chamadas de procedimento. Não há nenhum equivalente de curto-circuito para `Xor`, porque o resultado sempre depende dos dois operandos. Para *Short-circuiting* operadores lógicos, consulte [operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) e [operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 Para operações bit a bit, o `Xor` operador executa uma comparação bit a bit de bits posicionados identicamente em duas expressões numéricas e configura o bit no correspondente `result` acordo com a tabela a seguir.  
  
|Se bit no `expression1` é|E o bit na `expression2` é|O bit no `result` é|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  Como os operadores lógicos e bit a bit possuem uma precedência menor que outros operadores aritméticos e relacionais, quaisquer operações bit a bit devem ser colocadas entre parênteses para garantir execução precisa.  
  
 Por exemplo, 5 `Xor` 3 é 6. Para ver por que isso assim, converta 5 e 3 em suas representações binárias, 101 e 011. Em seguida, use a tabela anterior para determinar que 101 Xor 011 é 110, que é a representação binária do número decimal 6.  
  
## <a name="data-types"></a>Tipos de Dados  
 Se o operando consiste em uma `Boolean` expressão e uma expressão numérica, o Visual Basic converte o `Boolean` expressão para um valor numérico (-1 para `True` e 0 para `False`) e executa uma operação bit a bit.  
  
 Para uma `Boolean` comparação, o tipo de dados do resultado é `Boolean`. Para obter uma comparação bit a bit, o tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`. Consulte a tabela "Comparações relacionais e bit a bit" [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O `Xor` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, verifique se que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Xor` operador para executar exclusão lógica (disjunção lógica exclusiva) em duas expressões. O resultado é um `Boolean` valor que representa se exatamente uma das expressões é `True`.  
  
 [!code-vb[40 VbVbalrOperators](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_1.vb)]  
  
 O exemplo anterior produz resultados `False`, `True`, e `False`, respectivamente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Xor` operador para executar exclusão lógica (disjunção lógica exclusiva) nos bits individuais de duas expressões numéricas. O bit no padrão resultante é definido se exatamente um dos bits correspondentes nos dois operandos é definido como 1.  
  
 [!code-vb[41 VbVbalrOperators](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_2.vb)]  
  
 O exemplo anterior produz resultados 2, 12 e 14, respectivamente.  
  
## <a name="see-also"></a>Consulte também  
 [Operadores lógicos/bit a bit (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
