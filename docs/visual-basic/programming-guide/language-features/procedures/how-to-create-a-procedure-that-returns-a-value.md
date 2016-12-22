---
title: "Como criar um procedimento que retorne um valor (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "procedimentos, definindo"
  - "procedimentos, retornando um valor"
  - "código do Visual Basic, procedimentos"
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar um procedimento que retorne um valor (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você usa um procedimento `Function` para retorna um valor para o código de chamada.  
  
### Para criar um crocedimento que retorna um valor  
  
1.  Fora de qualquer outro procedimento, utilize uma declaração `Function` seguida de uma declaração `End Function`.  
  
2.  Na declaração `Function`, siga a palava\-chave `Function` do nome do procedimento, e, em seguida, da lista de parâmetros em parênteses.  
  
3.  Siga os parênteses com uma cláusula `As` para especificar o tipo de dado o valor retornado.  
  
4.  Posicione as declarações de código do procedimento entre as declarações `Function` e `End Function`.  
  
5.  Use uma declaração `Return` para retornar o valor para o código de chamada.  
  
     O procedimento `Function` a seguir calcula o maior lado, ou hipotenusa, de um triângulo retângulo, dados os valores dos outros dois lados.  
  
     [!code-vb[VbVbcnProcedures#1](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     O exemplo a seguir mostra uma chamada típica a `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures#6](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Subprocedimentos](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedimentos do operador](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Como retornar um valor de um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-return-a-value-from-a-procedure.md)   
 [Como chamar um procedimento que retorna um valor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-returns-a-value.md)