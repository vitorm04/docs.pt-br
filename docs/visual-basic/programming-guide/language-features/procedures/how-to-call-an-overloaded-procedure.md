---
title: "Como chamar um procedimento sobrecarregado (Visual Basic) | Microsoft Docs"
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
  - "chamadas de procedimento, sobrecarregado"
  - "procedimentos, Chamando "
  - "procedimentos, várias versões"
  - "procedimentos, sobrecarga"
  - "código do Visual Basic, procedimentos"
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como chamar um procedimento sobrecarregado (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

A vantagem de sobrecarga de um procedimento é na flexibilidade da chamada.  O código de chamada pode obter as informações necessárias para passar para o procedimento e, em seguida, chamar um único nome de procedimento, não importa quais argumentos ele está passando.  
  
### Para chamar um procedimento que tenha mais de uma versão definida  
  
1.  O código de chamada, determine quais dados a passar para o procedimento.  
  
2.  Escreva o chamada de procedimento da maneira normal, apresentando os dados na lista de argumentos.  Assegure\-se que os argumentos correspondam à lista de parâmetros em uma das versões definidas para o procedimento.  
  
3.  Você não precisará determinar qual versão do procedimento a ser chamado.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]passa o controle para a versão que correspondem a sua lista de argumentos.  
  
     O exemplo a seguir chama o procedimento `post` declarado na [Como definir várias versões de um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md).  Obtém a identificação do cliente, determina se é uma `String` ou um `Integer` e, em seguida, em ambos os casos chama o mesmo procedimento.  
  
     [!code-vb[VbVbcnProcedures#56](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Solucionando problemas de procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [Como definir várias versões de um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [Como sobrecarregar um procedimento que usa parâmetros opcionais](../Topic/How%20to:%20Overload%20a%20Procedure%20that%20Takes%20Optional%20Parameters%20\(Visual%20Basic\).md)   
 [Como sobrecarregar um procedimento que usa um número indefinido de parâmetros](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considerações sobre procedimentos de sobrecarga](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Resolução de sobrecarga](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)   
 [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md)