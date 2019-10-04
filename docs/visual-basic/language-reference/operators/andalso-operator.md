---
title: Operador AndAlso (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: a52f598c8a7c7a79b0f2436f1add7b3eb5d5261b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835223"
---
# <a name="andalso-operator-visual-basic"></a>Operador AndAlso (Visual Basic)
Executa uma conjunção lógica de curto-circuito em duas expressões.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`result`|Necessário. Qualquer expressão de `Boolean` . O resultado é o resultado `Boolean` de comparação das duas expressões.|  
|`expression1`|Necessário. Qualquer expressão de `Boolean` .|  
|`expression2`|Necessário. Qualquer expressão de `Boolean` .|  
  
## <a name="remarks"></a>Comentários  
 Uma operação lógica é chamada de *curto-circuito* se o código compilado puder ignorar a avaliação de uma expressão, dependendo do resultado de outra expressão. Se o resultado da primeira expressão avaliada determinar o resultado final da operação, não será necessário avaliar a segunda expressão, pois ela não pode alterar o resultado final. O curto circuito pode melhorar o desempenho se a expressão ignorada for complexa ou se envolver chamadas de procedimento.  
  
 Se as duas expressões forem avaliadas como `True`, `result` será `True`. A tabela a seguir ilustra como `result` é determinado.  
  
|Se `expression1` é|E `expression2` é|O valor de `result` é|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(não avaliado)|`False`|  
  
## <a name="data-types"></a>Tipos de Dados  
 O operador `AndAlso` é definido somente para o [tipo de dados booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic converte cada operando conforme necessário para `Boolean` antes de avaliar a expressão. Se você atribuir o resultado a um tipo numérico, Visual Basic o converterá de `Boolean` para esse tipo, de modo que `False` se torne `0` e `True` se tornará `-1`.
Para obter mais informações, consulte [conversões de tipo booliano](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Sobrecarga  
 O [operador and](../../../visual-basic/language-reference/operators/and-operator.md) e o [Operador IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md) podem ser *sobrecarregados*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Sobrecarregar os operadores `And` e `IsFalse` afeta o comportamento do operador `AndAlso`. Se seu código usa `AndAlso` em uma classe ou estrutura que sobrecarrega `And` e `IsFalse`, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `AndAlso` para executar uma conjunção lógica em duas expressões. O resultado é um valor `Boolean` que representa se a expressão conjunta inteira é verdadeira. Se a primeira expressão for `False`, a segunda não será avaliada.  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 O exemplo anterior produz resultados de `True`, `False` e `False`, respectivamente. No cálculo de `secondCheck`, a segunda expressão não é avaliada porque a primeira já é `False`. No entanto, a segunda expressão é avaliada no cálculo de `thirdCheck`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um procedimento `Function` que procura um determinado valor entre os elementos de uma matriz. Se a matriz estiver vazia ou se o comprimento da matriz tiver sido excedido, a instrução `While` não testará o elemento de matriz em relação ao valor de pesquisa.  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>Consulte também

- [Operadores lógicos/bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operador And](../../../visual-basic/language-reference/operators/and-operator.md)
- [Operador IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Operadores lógicos e de bits bit a Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
