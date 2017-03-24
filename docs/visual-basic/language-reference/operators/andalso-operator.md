---
title: Operador AndAlso (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AndAlso
- AndAlso
dev_langs:
- VB
helpviewer_keywords:
- short-circuiting
- AndAlso operator
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
caps.latest.revision: 19
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
ms.openlocfilehash: 120636e599742ef48f5c5d8cebf0f338edb7c24a
ms.lasthandoff: 03/13/2017

---
# <a name="andalso-operator-visual-basic"></a>Operador AndAlso (Visual Basic)
Executa uma conjunção lógica em duas expressões.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`result`|Necessário. Qualquer expressão de `Boolean` . O resultado é o `Boolean` resultado da comparação de duas expressões.|  
|`expression1`|Necessário. Qualquer expressão de `Boolean` .|  
|`expression2`|Necessário. Qualquer expressão de `Boolean` .|  
  
## <a name="remarks"></a>Comentários  
 Uma operação lógica será considerada *Short-circuiting* se o código compilado pode ignorar a avaliação de uma expressão, dependendo do resultado da outra expressão. Se o resultado da primeira expressão avaliada determina o resultado final da operação, não é necessário para avaliar a segunda expressão, porque ele não pode alterar o resultado final. Short-circuiting pode melhorar o desempenho se a expressão ignorada é complexa, ou se ela envolve chamadas de procedimento.  
  
 Se as duas expressões são `True`, `result` é `True`. A tabela a seguir ilustra como `result` é determinado.  
  
|If `expression1` is|E `expression2` é|O valor de `result` é|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(não avaliado)|`False`|  
  
## <a name="data-types"></a>Tipos de Dados  
 O `AndAlso` operador é definido somente para o [tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic converte cada operando conforme necessário para `Boolean` e executa a operação completamente em `Boolean`. Se você atribuir o resultado a um tipo numérico, Visual Basic converte do `Boolean` para esse tipo. Isso pode produzir um comportamento inesperado. Por exemplo, `5 AndAlso 12` resulta em `–1` quando convertido em `Integer`.  
  
## <a name="overloading"></a>Sobrecarga  
 O [operador e](../../../visual-basic/language-reference/operators/and-operator.md) e [Operador IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md) podem ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarga de `And` e `IsFalse` operadores afeta o comportamento do `AndAlso` operador. Se seu código usa `AndAlso` em uma classe ou estrutura que sobrecarrega `And` e `IsFalse`, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `AndAlso` operador para executar uma conjunção lógica em duas expressões. O resultado é um `Boolean` valor que indica se todo o conjoined expressão é true. Se a primeira expressão for `False`, a segunda não será avaliada.  
  
 [!code-vb[VbVbalrOperators&#24;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_1.vb)]  
  
 O exemplo anterior produz resultados de `True`, `False`, e `False`, respectivamente. No cálculo de `secondCheck`, a segunda expressão é avaliada não porque a primeira já é `False`. No entanto, a segunda expressão é avaliada no cálculo de `thirdCheck`.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra uma `Function` procedimento que procura por um determinado valor entre os elementos de uma matriz. Se a matriz está vazia ou se o comprimento da matriz foi excedido, o `While` instrução não testa o elemento da matriz em relação ao valor de pesquisa.  
  
 [!code-vb[25 VbVbalrOperators](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operadores lógicos/bit a bit (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operador and](../../../visual-basic/language-reference/operators/and-operator.md)   
 [Operador IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
