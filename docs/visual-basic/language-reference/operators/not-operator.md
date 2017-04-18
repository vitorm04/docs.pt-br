---
title: Operador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Not
dev_langs:
- VB
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator
- inverse bit values in variables
- bitwise operators, NOT operator
- bitwise comparison
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
caps.latest.revision: 11
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
ms.openlocfilehash: 83ac8c3240b45f051970b1d8e28beaa7fdd8829a
ms.lasthandoff: 03/13/2017

---
# <a name="not-operator-visual-basic"></a>Operador Not (Visual Basic)
Executa negação lógica em uma `Boolean` expressão ou negação bit a bit em uma expressão numérica.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = Not expression  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Qualquer `Boolean` ou expressão numérica.  
  
 `expression`  
 Necessário. Qualquer `Boolean` ou expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 Para `Boolean` expressões, a tabela a seguir ilustra como `result` é determinado.  
  
|If `expression` is|O valor de `result` é|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 Para expressões numéricas, o `Not` operador inverte os valores dos bits de qualquer expressão numérica e configura o bit no correspondente `result` acordo com a tabela a seguir.  
  
|Se bit no `expression` é|O bit no `result` é|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
>  Como os operadores lógicos e bit a bit possuem uma precedência menor que outros operadores aritméticos e relacionais, quaisquer operações bit a bit devem ser colocadas entre parênteses para garantir execução precisa.  
  
## <a name="data-types"></a>Tipos de Dados  
 Para uma negação Boleana, o tipo de dados do resultado é `Boolean`. Para uma negação bit a bit, o tipo de dados do resultado é o mesmo que `expression`. No entanto, se a expressão for `Decimal`, o resultado é `Long`.  
  
## <a name="overloading"></a>Sobrecarga  
 O `Not` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando seu operando tem o tipo da classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Not` operador para realizar negação lógica em uma `Boolean` expressão. O resultado é um `Boolean` que representa o inverso do valor da expressão.  
  
 [!code-vb[33 VbVbalrOperators](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]  
  
 O exemplo anterior produz resultados de `False` e `True`, respectivamente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Not` operador para realizar negação lógica dos bits individuais de uma expressão numérica. O bit no padrão resultante é definido como o inverso do bit correspondente no padrão de operando, incluindo o bit de sinal.  
  
 [!code-vb[VbVbalrOperators&#34;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]  
  
 O exemplo anterior produz resultados –&11;, –9 e -7, respectivamente.  
  
## <a name="see-also"></a>Consulte também  
 [Operadores lógicos/bit a bit (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
