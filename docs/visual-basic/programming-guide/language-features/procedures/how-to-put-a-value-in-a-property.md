---
title: 'Como: inserir um valor em uma propriedade (Visual Basic) | Documentos do Microsoft'
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
- property values
- Visual Basic code, procedures
- values, properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: e3b2336589b525756a92cb3e26ab6c1950118b01
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Como inserir um valor em uma propriedade (Visual Basic)
Você pode armazenar um valor em uma propriedade, colocando o nome da propriedade no lado esquerdo de uma instrução de atribuição.  
  
 A propriedade `Set` procedimento armazena um valor, mas você não chama explicitamente pelo nome. Use a propriedade exatamente como você usaria uma variável. [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]faz as chamadas aos procedimentos da propriedade.  
  
### <a name="to-store-a-value-in-a-property"></a>Para armazenar um valor em uma propriedade  
  
1.  Use o nome da propriedade no lado esquerdo de uma instrução de atribuição.  
  
     O exemplo a seguir define o valor da [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `TimeOfDay` propriedade ao meio-dia, implicitamente chamando seu `Set` procedimento.  
  
     [!code-vb[VbVbcnProcedures n º&11;](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  Se a propriedade utiliza argumentos, siga o nome da propriedade com parênteses para incluir a lista de argumentos. Se não houver nenhum argumento, opcionalmente, você pode omitir os parênteses.  
  
3.  Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas. Certifique-se de que fornecer os argumentos na mesma ordem que a propriedade define os parâmetros correspondentes.  
  
4.  O valor gerado no lado direito da instrução de atribuição é armazenado na propriedade.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A></xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>   
 [Procedimentos de propriedade](./property-procedures.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md)   
 [Como: criar uma propriedade](./how-to-create-a-property.md)   
 [Como: declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md)   
 [Como: chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md)   
 [Como: declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md)   
Como obter um valor de uma propriedade (Visual Basic) [Como obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)
