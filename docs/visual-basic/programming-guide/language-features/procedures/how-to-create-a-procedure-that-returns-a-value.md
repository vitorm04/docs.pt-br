---
title: 'Como: criar um procedimento que retorna um valor (Visual Basic) | Documentos do Microsoft'
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
- procedures, defining
- Visual Basic code, procedures
- procedures, returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: 16
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
ms.openlocfilehash: af47d296bcfd7ef5f579148954b589cac7fe99ba
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Como criar um procedimento que retorne um valor (Visual Basic)
Você usa uma `Function` procedimento retorne um valor para o código de chamada.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Para criar um procedimento que retorna um valor  
  
1.  Fora de qualquer outro procedimento, utilize uma `Function` instrução, seguida por um `End Function` instrução.  
  
2.  No `Function` instrução, siga o `Function` palavra-chave com o nome do procedimento e, em seguida, a lista de parâmetros entre parênteses.  
  
3.  Siga os parênteses com uma `As` cláusula para especificar o tipo de dados do valor retornado.  
  
4.  Coloque as declarações de código do procedimento entre o `Function` e `End Function` instruções.  
  
5.  Use um `Return` instrução para retornar o valor para o código de chamada.  
  
     O seguinte `Function` procedimento calcula o maior lado, ou hipotenusa, de um triângulo, considerando os valores para os dois lados.  
  
     [!code-vb[VbVbcnProcedures n º&1;](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     O exemplo a seguir mostra uma chamada típica para `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures n º&6;](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Procedimentos Sub](./sub-procedures.md)   
 [Procedimentos de propriedade](./property-procedures.md)   
 [Procedimentos de operador](./operator-procedures.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Como: retornar um valor de um procedimento](./how-to-return-a-value-from-a-procedure.md)   
 [Como chamar um procedimento que retorna um valor](./how-to-call-a-procedure-that-returns-a-value.md)
