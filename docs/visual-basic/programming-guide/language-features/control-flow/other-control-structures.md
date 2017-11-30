---
title: Outras estruturas de controle (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09e59d25b3b2fc89026295e8500c30dad7b75086
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="other-control-structures-visual-basic"></a>Outras estruturas de controle (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Fornece as estruturas de controle que ajudam você descartar um recurso ou reduzem o número de vezes que você precisa repetir uma referência de objeto.  
  
## <a name="usingend-using-construction"></a>Usando... Usando a construção de término  
 O `Using...End Using` construção estabelece um bloco de instruções dentro do qual você faz uso de um recurso como uma conexão SQL. Opcionalmente, você pode adquirir o recurso com o `Using` instrução. Quando você fechar o `Using` bloco, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] descarta automaticamente o recurso para que ele está disponível para outro código usar. O recurso deve ser local e descartável. Para obter mais informações, consulte [Instrução using](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="withend-with-construction"></a>Com... Terminar com a construção  
 O `With...End With` construção permite que você especifique uma referência de objeto uma vez e, em seguida, executar uma série de instruções que acessam seus membros. Isso pode simplificar o seu código e melhorar o desempenho porque [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] não precisa restabelecer a referência para cada instrução que acessa-lo. Para obter mais informações, consulte [com... Terminar com a instrução](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Estruturas de Decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Estruturas de Controle Aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Instrução Using](../../../../visual-basic/language-reference/statements/using-statement.md)  
 [Instrução With ... End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
