---
title: "Outras estruturas de controle (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "estruturas de controle"
  - "instruções [Visual Basic], fluxo de controle"
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Outras estruturas de controle (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece estruturas de controle que ajudam a descartar um recurso ou reduzir o número de vezes que você terá que repetir uma referência de objeto.  
  
## Construção Using...End Using  
 A construção `Using...End Using` estabelece um bloco de declaração dentro do qual você faz usar de um recurso como uma conexão SQL.  Opcionalmente, você pode adquirir o recurso com a instrução `Using`.  Quando você sai do bloco `Using`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automaticamente descarta os recurso para que fiquem disponível para outro código usar.  O recurso deve ser local e descartável.  Para obter mais informações, consulte [Instrução Using](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## Construção With... End With  
 A construção `With...End With` permite que você especifique uma referência de objeto uma vez e, em seguida, executar uma série de instruções que acessam seus membros.  Isso pode simplificar o seu código e melhorar o desempenho porque [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não precisa restabelecer a referência para cada instrução que acessa\-lo.  Para obter mais informações, consulte [Instrução With ... End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## Consulte também  
 [Fluxo de controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Estruturas de decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Estruturas de loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Estruturas de controle aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Instrução Using](../../../../visual-basic/language-reference/statements/using-statement.md)   
 [Instrução With ... End With](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)