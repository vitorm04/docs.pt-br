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
ms.openlocfilehash: 3876fd9c32d486b8ebecc9ee2428486a687a1624
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817117"
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
|`result`|Necessário. Qualquer expressão de `Boolean` . O resultado é o `Boolean` resultado da comparação das duas expressões.|  
|`expression1`|Necessário. Qualquer expressão de `Boolean` .|  
|`expression2`|Necessário. Qualquer expressão de `Boolean` .|  
  
## <a name="remarks"></a>Comentários  
 Uma operação lógica será considerada *Short-circuiting* se o código compilado pode ignorar a avaliação de uma expressão, dependendo do resultado de outra expressão. Se o resultado da primeira expressão avaliada determina o resultado final da operação, não é necessário para avaliar a segunda expressão, porque ele não é possível alterar o resultado final. Short-circuiting pode melhorar o desempenho se a expressão ignorada é complexa, ou se ela envolve chamadas de procedimento.  
  
 Se ambas as expressões são avaliadas como `True`, `result` é `True`. A tabela a seguir ilustra como `result` é determinado.  
  
|Se `expression1` é|E `expression2` é|O valor de `result` é|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(não avaliado)|`False`|  
  
## <a name="data-types"></a>Tipos de Dados  
 O `AndAlso` operador está definido apenas para o [tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Cada operando conforme necessário para o Visual Basic converte `Boolean` e executa a operação completamente em `Boolean`. Se você atribuir o resultado a um tipo numérico, Visual Basic converte-o de `Boolean` a esse tipo. Isso pode produzir um comportamento inesperado. Por exemplo, `5 AndAlso 12` resulta em `–1` quando convertido em `Integer`.  
  
## <a name="overloading"></a>Sobrecarga  
 O [operador And](../../../visual-basic/language-reference/operators/and-operator.md) e o [Operador IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md) pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo que classe ou estrutura. Sobrecarregando o `And` e `IsFalse` operadores afeta o comportamento do `AndAlso` operador. Se seu código usa `AndAlso` em uma classe ou estrutura que sobrecarrega `And` e `IsFalse`, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `AndAlso` operador para executar uma conjunção lógica em duas expressões. O resultado é um `Boolean` valor que indica se todo o unidas a expressão é true. Se a primeira expressão é `False`, a segunda não será avaliada.  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 O exemplo anterior produz resultados `True`, `False`, e `False`, respectivamente. No cálculo da `secondCheck`, a segunda expressão é avaliada não porque a primeira já é `False`. No entanto, a segunda expressão é avaliada no cálculo de `thirdCheck`.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra um `Function` procedimento que procura por um determinado valor entre os elementos de uma matriz. Se a matriz está vazia ou se o comprimento da matriz foi excedido, o `While` instrução não testa o elemento da matriz com relação ao valor de pesquisa.  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>Consulte também

- [Operadores lógicos/bit a bit (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operador And](../../../visual-basic/language-reference/operators/and-operator.md)
- [Operador IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
