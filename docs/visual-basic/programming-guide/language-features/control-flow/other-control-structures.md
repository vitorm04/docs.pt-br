---
title: Outras estruturas de controle (Visual Basic) | Documentos do Microsoft
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
- statements [Visual Basic], control flow
- control structures
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 639571b493037f26951bd8fbf140d7bce3244889
ms.lasthandoff: 03/13/2017

---
# <a name="other-control-structures-visual-basic"></a>Outras estruturas de controle (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fornece estruturas de controle que ajudam você descartar um recurso ou reduzem o número de vezes que você terá que repetir uma referência de objeto.  
  
## <a name="usingend-using-construction"></a>Usando... End usando a construção  
 O `Using...End Using` construção estabelece um bloco de declaração dentro do qual você faz usar de um recurso, como uma conexão SQL. Opcionalmente, você pode adquirir o recurso com o `Using` instrução. Quando você sai do `Using` bloco, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automaticamente descarta o recurso para que ele esteja disponível para outro código usar. O recurso deve ser local e descartável. Para obter mais informações, consulte [usando instrução](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="withend-with-construction"></a>Com... Terminar com a construção  
 O `With...End With` construção permite que você especifique uma referência de objeto uma vez e, em seguida, executar uma série de instruções que acessam seus membros. Isso pode simplificar o seu código e melhorar o desempenho porque [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não precisa restabelecer a referência para cada instrução que acessa-lo. Para obter mais informações, consulte [com... Terminar com a instrução](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Estruturas de decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Estruturas de loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Estruturas de controle aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Instrução Using](../../../../visual-basic/language-reference/statements/using-statement.md)   
 [Instrução With ... End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
