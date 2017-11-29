---
title: "Como testar se dois objetos são iguais (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76f5c19386cce84207f80d217326d2e3babf4e44
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Como testar se dois objetos são iguais (Visual Basic)
Se você tiver duas variáveis que se referem a objetos, você pode usar o `Is` ou `IsNot` operador, ou ambos, para determinar se eles se referem à mesma instância.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>Para testar se dois objetos são iguais  
  
-   Use o [operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) ou [operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) com as duas variáveis como operandos.  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 Convém levar a uma determinada ação dependendo se dois objetos se referem à mesma instância. O exemplo anterior compara controle `c` contra o controle ativo no formulário `f`. Se não há nenhum controle ativo, ou se houver uma, mas não é a mesma instância do controle como `c`, em seguida, o `If` instrução falhará e o procedimento retornará sem processamento adicional.  
  
 Se você usar `Is` ou `IsNot` é uma questão de conveniência pessoal para você. Um pode ser mais fácil de ler que o outro em uma determinada expressão.  
  
## <a name="see-also"></a>Consulte também  
 [Operadores de comparação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
