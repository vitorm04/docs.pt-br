---
title: "Como: testar se dois objetos são iguais (Visual Basic) | Documentos do Microsoft"
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
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
caps.latest.revision: 11
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
ms.openlocfilehash: 0253a2f13b2326ee3d109c92b85c7a328791fece
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Como testar se dois objetos são iguais (Visual Basic)
Se você tiver duas variáveis que se referem a objetos, você pode usar o `Is` ou `IsNot` operador, ou ambos, para determinar se eles se referem à mesma instância.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>Para testar se dois objetos são iguais  
  
-   Use o [operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) ou [operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) com as duas variáveis como operandos.  
  
     [!code-vb[VbVbalrOperators&#69;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 Você talvez queira levar uma determinada ação dependendo se dois objetos se referem à mesma instância. O exemplo anterior compara controle `c` contra o controle ativo no formulário `f`. Se não há nenhum controle ativo, ou se houver um, mas não é a mesma instância de controle como `c`, o `If` instrução falhará e o procedimento retornará sem processamento adicional.  
  
 Se você usar `Is` ou `IsNot` é uma questão de conveniência pessoal para você. Um pode ser mais fácil de ler do que a outra em uma determinada expressão.  
  
## <a name="see-also"></a>Consulte também  
 [Operadores de comparação em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
