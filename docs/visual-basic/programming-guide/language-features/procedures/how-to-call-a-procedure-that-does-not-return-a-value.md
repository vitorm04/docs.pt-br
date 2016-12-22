---
title: "Como chamar um procedimento que n&#227;o retorne um valor (Visual Basic) | Microsoft Docs"
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
  - "chamadas de procedimento, retornando valores"
  - "procedimentos, Chamando "
  - "código do Visual Basic, procedimentos"
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como chamar um procedimento que n&#227;o retorne um valor (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um procedimento `Sub` não retorna um valor para o código de chamada.  Você chamá\-lo explicitamente com uma instrução de chamada autônoma.  Você não pode chamar ele simplesmente usando seu nome dentro de uma expressão.  
  
### Para chamar um procedimento Sub  
  
1.  Especificar o nome do procedimento de `Sub` .  
  
2.  Acompanhe o nome do procedimento com parênteses para incluir a lista de argumentos.  Se não há argumentos, você pode, opcionalmente, omitir os parênteses.  No entanto, usar os parênteses faz seu código ficar mais fácil de ler.  
  
3.  Coloque os argumentos na lista de argumentos dentro de parênteses, separados por vírgulas.  Não se esqueça de fornecer os argumentos na mesma ordem que o procedimento `Sub` define os parâmetros correspondentes.  
  
     O exemplo a seguir chama a função de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> para ativar uma janela de aplicativo.  <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> leva o título da janela como seu único argumento.  Ela não retorna um valor para o código de chamada.  Se um processo do Bloco de Notas não estiver sendo executado, o exemplo gera uma <xref:System.ArgumentException>.  O procedimento `Shell` considera que os aplicativos estão nos caminhos especificados.  
  
     [!code-vb[VbVbalrCatRef#11](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>   
 <xref:System.ArgumentException>   
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Subprocedimentos](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Como criar um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure.md)   
 [Como chamar um procedimento que retorna um valor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-returns-a-value.md)   
 [Como chamar um manipulador de eventos no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-event-handler.md)