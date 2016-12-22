---
title: "Como chamar um procedimento que retorna um valor (Visual Basic) | Microsoft Docs"
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
  - "procedimentos, retornando um valor"
  - "código do Visual Basic, procedimentos"
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como chamar um procedimento que retorna um valor (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um procedimento `Function` retorna um valor para o código de chamada.  Você o chama, incluindo seu nome e argumentos no lado direito de uma instrução de atribuição ou em uma expressão.  
  
### Para chamar um procedimento Function em uma expressão  
  
1.  Use o nome do procedimento `Function` da mesma maneira você usaria uma variável.  Você pode usar uma chamada de procedimento `Function` em qualquer lugar que se possa usar uma variável ou constante em uma expressão.  
  
2.  Acompanhe o nome do procedimento com parênteses para incluir a lista de argumentos.  Se não há argumentos, você pode, opcionalmente, omitir os parênteses.  No entanto, usar os parênteses faz seu código ficar mais fácil de ler.  
  
3.  Coloque os argumentos na lista de argumentos dentro de parênteses, separados por vírgulas.  Não se esqueça de fornecer os argumentos na mesma ordem que o procedimento `Function` define os parâmetros correspondentes.  
  
     Como alternativa, você pode passar um ou mais argumentos por nome.  Para mais informações, consulte [Passando argumentos por posição e nome](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).  
  
4.  O valor retornado do procedimento participa na expressão apenas como o valor de uma variável ou constante participaria.  
  
### Para chamar um procedimento Function em um instrução de atribuição  
  
1.  Use o nome da propriedade `Function` seguido do sinal de igual \(`=`\) em uma instrução de atribuição.  
  
2.  Acompanhe o nome do procedimento com parênteses para incluir a lista de argumentos.  Se não há argumentos, você pode, opcionalmente, omitir os parênteses.  No entanto, usar os parênteses faz seu código ficar mais fácil de ler.  
  
3.  Coloque os argumentos na lista de argumentos dentro de parênteses, separados por vírgulas.  Não se esqueça de fornecer os argumentos na mesma ordem em que o procedimento `Function` define os parâmetros correspondentes, a menos que você esteja passando\-os por nome.  
  
4.  O valor retornado do procedimento é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.  
  
## Exemplo  
 O exemplo a seguir chama o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A> para recuperar o valor de uma variável de ambiente do sistema operacional.  A primeira linha chama `Environ` em uma expressão, e a segunda linha chama\-o em uma instrução de atribuição.  `Environ` utiliza o nome de variável como seu único argumento.  Ele retorna o valor da variável para o código de chamada.  
  
 [!code-vb[VbVbcnProcedures#7](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## Consulte também  
 [Procedimentos de função](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Como criar um procedimento que retorne um valor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure-that-returns-a-value.md)   
 [Como retornar um valor de um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-return-a-value-from-a-procedure.md)   
 [Como chamar um procedimento que não retorne um valor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-does-not-return-a-value.md)