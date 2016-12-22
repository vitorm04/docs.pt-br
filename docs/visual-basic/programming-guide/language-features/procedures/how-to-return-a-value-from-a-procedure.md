---
title: "Como retornar um valor de um procedimento (Visual Basic) | Microsoft Docs"
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
  - "procedimentos, retornando um valor"
  - "procedimentos, retornando de"
  - "código do Visual Basic, procedimentos"
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como retornar um valor de um procedimento (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um procedimento `Function`retorna um valor para o código de chamado seja executando uma declaração  `Return` ou encontrando uma declaração `Exit Function` ou `End Function` statement..  
  
### Parar retornar um valor usando a declaração Return.  
  
1.  Coloque uma declaração `Return`no ponto onde as tarefas do procedimento estão completas.  
  
2.  Siga a palavra\-chave `Return` de uma expressão que guarde o valor que você quer retornar ao código de chamada.  
  
3.  Você pode ter mais de uma declaração `Return` no mesmo preocedimento.  
  
     O procedimento `Function` a seguir calcula o maior lado, ou hipotenusa, de um triângulo retângulo, dados os valores dos outros dois lados.  
  
     [!code-vb[VbVbcnProcedures#1](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     O exemplo a seguir postra uma chamada típica a `hypotenuse`, que armazena o valor retornado.  
  
     [!code-vb[VbVbcnProcedures#6](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### Para retornar um valor usando Exit Function ou End Function  
  
1.  Em pelo menos um lugar do procedimento `Function`, atribua um valor ao nome do procedimento.  
  
2.  Quando você executa uma declaração `Exit Function` ou `End Function`,[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] retorna o valor mais recentemente atribuído ao nome do procedimento.  
  
3.  Você pode ter mais de uma declaração `Exit Function` no mesmo procedimento, e você pode mixar as declarações `Return` e `Exit Function` no mesmo procedimento.  
  
4.  Você pode ter apenas uma declaração `End Function` em um procedimento`Function`.  
  
     Para mais informações e um exemplo, consulte [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Subprocedimentos](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedimentos do operador](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução Return](../../../../visual-basic/language-reference/statements/return-statement.md)   
 [Como criar um procedimento que retorne um valor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure-that-returns-a-value.md)   
 [Como chamar um procedimento que retorna um valor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-returns-a-value.md)