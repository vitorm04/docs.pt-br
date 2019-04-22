---
title: Outras estruturas de controle (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: c42070ce2ea866e59e1b2e190f7c05e1ee7cc922
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819314"
---
# <a name="other-control-structures-visual-basic"></a>Outras estruturas de controle (Visual Basic)
Visual Basic fornece estruturas de controle que ajudam você descartar um recurso ou reduzem o número de vezes que você tenha que repetir uma referência de objeto.  
  
## <a name="usingend-using-construction"></a>Usando... Usando a construção de término  
 O `Using...End Using` construção estabelece um bloco de instrução dentro do qual você faz uso de um recurso como uma conexão SQL. Opcionalmente, você pode adquirir o recurso com o `Using` instrução. Quando você fechar o `Using` bloco, Visual Basic descarta automaticamente o recurso para que ele está disponível para outro código para usar. O recurso deve ser local e descartável. Para obter mais informações, consulte [Instrução using](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="withend-with-construction"></a>Com... Terminar com a construção  
 O `With...End With` construção permite que você especifique uma referência de objeto de uma vez e, em seguida, executar uma série de instruções que acessam seus membros. Isso pode simplificar o seu código e melhorar o desempenho porque o Visual Basic não precisará restabelecer a referência para cada instrução que o acessa. Para obter mais informações, consulte [com... Terminar com a instrução](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## <a name="see-also"></a>Consulte também

- [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Estruturas de Decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Estruturas de Controle Aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Instrução Using](../../../../visual-basic/language-reference/statements/using-statement.md)
- [Instrução With ... End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
