---
title: Operador OrElse
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 361de44711c3b41411f2fa1dd81a3dd8db6b01e6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348240"
---
# <a name="orelse-operator-visual-basic"></a>Operador OrElse (Visual Basic)
Executa uma disjunção lógica inclusiva de curto-circuito em duas expressões.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Qualquer expressão de `Boolean` .  
  
 `expression1`  
 Necessário. Qualquer expressão de `Boolean` .  
  
 `expression2`  
 Necessário. Qualquer expressão de `Boolean` .  
  
## <a name="remarks"></a>Comentários  
 Uma operação lógica é chamada de *curto-circuito* se o código compilado puder ignorar a avaliação de uma expressão, dependendo do resultado de outra expressão. Se o resultado da primeira expressão avaliada determinar o resultado final da operação, não será necessário avaliar a segunda expressão, pois ela não pode alterar o resultado final. O curto circuito pode melhorar o desempenho se a expressão ignorada for complexa ou se envolver chamadas de procedimento.  
  
 Se uma ou ambas as expressões forem avaliadas como `True`, `result` será `True`. A tabela a seguir ilustra como `result` é determinado.  
  
|Se `expression1` for|E `expression2` é|O valor de `result` é|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(não avaliado)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Tipos de Dados  
 O operador `OrElse` é definido somente para o [tipo de dados booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic converte cada operando conforme necessário para `Boolean` antes de avaliar a expressão. Se você atribuir o resultado a um tipo numérico, Visual Basic o converterá de `Boolean` para esse tipo, de modo que `False` se tornará `0` e `True` se tornará `-1`.
Para obter mais informações, consulte [conversões de tipo booliano](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Sobrecarga  
 O [operador OR](../../../visual-basic/language-reference/operators/or-operator.md) e o [operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) podem ser *sobrecarregados*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura. Sobrecarregar os operadores de `Or` e `IsTrue` afeta o comportamento do operador de `OrElse`. Se o seu código usa `OrElse` em uma classe ou estrutura que sobrecarrega `Or` e `IsTrue`, certifique-se de entender seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o operador `OrElse` para executar a disjunção lógica em duas expressões. O resultado é um valor `Boolean` que representa se uma das duas expressões é true. Se a primeira expressão for `True`, a segunda não será avaliada.  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 O exemplo anterior produz resultados de `True`, `True`e `False`, respectivamente. No cálculo de `firstCheck`, a segunda expressão não é avaliada porque a primeira já é `True`. No entanto, a segunda expressão é avaliada no cálculo de `secondCheck`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma instrução `If`...`Then` que contém duas chamadas de procedimento. Se a primeira chamada retornar `True`, o segundo procedimento não será chamado. Isso poderá produzir resultados inesperados se o segundo procedimento executar tarefas importantes que sempre devem ser executadas quando esta seção do código for executada.  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>Consulte também

- [Operadores lógicos/bits (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operador Or](../../../visual-basic/language-reference/operators/or-operator.md)
- [Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Operadores lógicos e de bits bit a Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
