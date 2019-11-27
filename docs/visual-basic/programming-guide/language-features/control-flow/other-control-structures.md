---
title: Outras estruturas de controle
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 758df361f421684655147ae288af3f350e53c4d7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348129"
---
# <a name="other-control-structures-visual-basic"></a>Outras estruturas de controle (Visual Basic)
Visual Basic fornece estruturas de controle que ajudam você a descartar um recurso ou reduzir o número de vezes que você precisa repetir uma referência de objeto.  
  
## <a name="usingend-using-construction"></a>Usando... Terminar usando construção  
 A construção `Using...End Using` estabelece um bloco de instruções no qual você usa um recurso, como uma conexão SQL. Opcionalmente, você pode adquirir o recurso com a instrução `Using`. Quando você sai do bloco de `Using`, Visual Basic descarta automaticamente o recurso para que ele esteja disponível para uso por outro código. O recurso deve ser local e descartável. Para obter mais informações, consulte [Instrução using](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="withend-with-construction"></a>Com... Terminar com construção  
 A construção `With...End With` permite especificar uma referência de objeto uma vez e, em seguida, executar uma série de instruções que acessam seus membros. Isso pode simplificar seu código e melhorar o desempenho porque Visual Basic não precisa restabelecer a referência para cada instrução que a acessa. Para obter mais informações, consulte [com... Instrução End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## <a name="see-also"></a>Consulte também

- [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Estruturas de Decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Estruturas de Controle Aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Instrução Using](../../../../visual-basic/language-reference/statements/using-statement.md)
- [Instrução With ... End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
