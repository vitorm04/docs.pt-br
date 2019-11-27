---
title: Como testar se dois objetos são iguais
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 22e8e1e688d9e3bc3804899103ee78814aac235b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343625"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Como testar se dois objetos são iguais (Visual Basic)
Se você tiver duas variáveis que se referem a objetos, poderá usar o operador `Is` ou `IsNot`, ou ambos, para determinar se eles se referem à mesma instância.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>Para testar se dois objetos são iguais  
  
- Use o [operador is](../../../../visual-basic/language-reference/operators/is-operator.md) ou o [operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) com as duas variáveis como operandos.  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 Talvez você queira executar uma determinada ação dependendo se dois objetos se referem à mesma instância. O exemplo anterior compara o controle `c` com o controle ativo no `f`de formulário. Se não houver nenhum controle ativo, ou se houver um, mas não for a mesma instância de controle que `c`, a instrução `If` falhará e o procedimento retornará sem processamento adicional.  
  
 Se você usa `Is` ou `IsNot` é uma questão de conveniência pessoal. Uma delas pode ser mais fácil de ler do que a outra em uma determinada expressão.  
  
## <a name="see-also"></a>Consulte também

- [Operadores de comparação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
