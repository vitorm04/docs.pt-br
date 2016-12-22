---
title: "Como chamar um procedimento de propriedade (Visual Basic) | Microsoft Docs"
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
  - "chamadas de procedimento, procedimentos de propriedade"
  - "procedimentos, Chamando "
  - "propriedades [Visual Basic], procedimentos de propriedade"
  - "código do Visual Basic, procedimentos"
  - "código do Visual Basic, propriedades"
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como chamar um procedimento de propriedade (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você chama um procedimento de propriedade ao armazenar um valor na propriedade ou recuperar seu valor.  Acessar uma propriedade da mesma maneira que você acessa uma variável.  
  
 O procedimento da propriedade `Set` armazena um valor, e seu procedimento `Get` recupera o valor.  No entanto, você não explicitamente chamar esses procedimentos pelo nome.  Você pode usar a propriedade em uma instrução de atribuição ou uma expressão, exatamente como você poderia armazenar ou recuperar o valor de uma variável.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]faz as chamadas a procedimentos da propriedade.  
  
### Para chamar uma propriedade do procedimento Get  
  
1.  Use o nome da propriedade em uma expressão da mesma maneira que você usaria um nome de variável.  Você pode usar uma propriedade em qualquer lugar você pode usar uma variável ou uma constante.  
  
     \- ou \-  
  
     Use o nome da propriedade seguido do sinal de igual \(`=`\) em uma instrução de atribuição.  
  
     O exemplo a seguir lê o valor da <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> propriedade, implicitamente chamando seu `Get` procedimento.  
  
     [!code-vb[VbVbalrDateProperties#4](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  Se a propriedade utiliza argumentos, coloque parêntese após o nome da propriedade para cercar a lista de argumentos.  Se não há argumentos, você pode, opcionalmente, omitir os parênteses.  
  
3.  Coloque os argumentos na lista de argumentos dentro de parênteses, separados por vírgulas.  Não se esqueça de fornecer os argumentos na mesma ordem que a propriedade define os parâmetros correspondentes.  
  
 O valor da propriedade participa na expressão apenas como uma variável ou uma constante seria, ou ele é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.  
  
### Para chamar uma propriedade do procedimento Set  
  
1.  Use o nome da propriedade no lado esquerdo de uma instrução de atribuição.  
  
     O exemplo a seguir define o valor da <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> propriedade, implicitamente chamando o `Set` procedimento.  
  
     [!code-vb[VbVbcnProcedures#11](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  Se a propriedade utiliza argumentos, coloque parêntese após o nome da propriedade para cercar a lista de argumentos.  Se não há argumentos, você pode, opcionalmente, omitir os parênteses.  
  
3.  Coloque os argumentos na lista de argumentos dentro de parênteses, separados por vírgulas.  Não se esqueça de fornecer os argumentos na mesma ordem que a propriedade define os parâmetros correspondentes.  
  
 O valor gerado no lado direito do instrução de atribuição é armazenado na propriedade.  
  
## Consulte também  
 [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Diferenças entre propriedades e variáveis no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [Como criar uma propriedade](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [Como declarar uma propriedade com níveis de acesso mistos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [Como declarar e chamar uma propriedade padrão no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [Como inserir um valor em uma propriedade](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [Como obter um valor a partir de uma propriedade](../Topic/How%20to:%20Get%20a%20Value%20from%20a%20Property%20\(Visual%20Basic\).md)   
 [Instrução Get](../../../../visual-basic/language-reference/statements/get-statement.md)   
 [Instrução Set](../../../../visual-basic/language-reference/statements/set-statement.md)