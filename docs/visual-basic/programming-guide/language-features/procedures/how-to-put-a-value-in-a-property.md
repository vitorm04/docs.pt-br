---
title: "Como inserir um valor em uma propriedade (Visual Basic) | Microsoft Docs"
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
  - "propriedades [Visual Basic], Valores"
  - "valores de propriedade"
  - "Valores, propriedades"
  - "código do Visual Basic, procedimentos"
  - "código do Visual Basic, propriedades"
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como inserir um valor em uma propriedade (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode armazenar um valor em uma propriedade colocando o nome da propriedade no lado esquerdo de uma instrução de atribuição.  
  
 A propriedade `Set` procedimento armazena um valor, mas você não o chame explicitamente por nome.  Você pode utilizar a propriedade exatamente como você usaria uma variável.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]faz as chamadas a procedimentos da propriedade.  
  
### Para armazenar um valor em uma propriedade  
  
1.  Use o nome da propriedade no lado esquerdo de uma instrução de atribuição.  
  
     O exemplo a seguir define o valor da [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]`TimeOfDay` propriedade para o meio\-dia, implicitamente chamando seu `Set` procedimento.  
  
     [!code-vb[VbVbcnProcedures#11](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  Se a propriedade utiliza argumentos, coloque parêntese após o nome da propriedade para cercar a lista de argumentos.  Se não há argumentos, você pode, opcionalmente, omitir os parênteses.  
  
3.  Coloque os argumentos na lista de argumentos dentro de parênteses, separados por vírgulas.  Não se esqueça de fornecer os argumentos na mesma ordem que a propriedade define os parâmetros correspondentes.  
  
4.  O valor gerado no lado direito do instrução de atribuição é armazenado na propriedade.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>   
 [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Diferenças entre propriedades e variáveis no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [Como criar uma propriedade](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [Como declarar uma propriedade com níveis de acesso mistos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [Como chamar um procedimento de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [Como declarar e chamar uma propriedade padrão no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [Como obter um valor a partir de uma propriedade](../Topic/How%20to:%20Get%20a%20Value%20from%20a%20Property%20\(Visual%20Basic\).md)