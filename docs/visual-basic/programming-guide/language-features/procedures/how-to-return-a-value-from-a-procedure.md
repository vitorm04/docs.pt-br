---
title: 'Como: retornar um valor de um procedimento (Visual Basic) | Documentos do Microsoft'
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
- Visual Basic code, procedures
- procedures, returning from
- procedures, returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: 12
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
ms.openlocfilehash: 98f0fb0740a021a16e87454bfaebbfad7858477c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Como retornar um valor de um procedimento (Visual Basic)
A `Function` procedimento retorna um valor para o código de chamada seja executando uma `Return` instrução ou encontrando uma `Exit Function` ou `End Function` instrução.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Para retornar um valor usando a instrução Return  
  
1.  Colocar um `Return` instrução no ponto onde as tarefas do procedimento estão completas.  
  
2.  Execute o `Return` palavra-chave com uma expressão que produz o valor que você deseja retornar ao código de chamada.  
  
3.  Você pode ter mais de uma `Return` instrução no mesmo procedimento.  
  
     O seguinte `Function` procedimento calcula o maior lado, ou hipotenusa, de um triângulo e retorna para o código de chamada.  
  
     [!code-vb[VbVbcnProcedures n º&1;](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     O exemplo a seguir mostra uma chamada típica para `hypotenuse`, que armazena o valor retornado.  
  
     [!code-vb[VbVbcnProcedures n º&6;](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Para retornar um valor usando Exit Function ou End Function  
  
1.  Em pelo menos um lugar a `Function` procedimento, atribua um valor ao nome do procedimento.  
  
2.  Quando você executa um `Exit Function` ou `End Function` instrução, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] retorna o valor mais recentemente atribuído ao nome do procedimento.  
  
3.  Você pode ter mais de uma `Exit Function` instrução no mesmo procedimento e você pode misturar `Return` e `Exit Function` instruções no mesmo procedimento.  
  
4.  Você pode ter apenas uma `End Function` instrução em uma `Function` procedimento.  
  
     Para obter mais informações e um exemplo, consulte "Valor de retorno" em [declaração de função](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Procedimentos Sub](./sub-procedures.md)   
 [Procedimentos de propriedade](./property-procedures.md)   
 [Procedimentos de operador](./operator-procedures.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução Return](../../../../visual-basic/language-reference/statements/return-statement.md)   
 [Como: criar um procedimento que retorna um valor](./how-to-create-a-procedure-that-returns-a-value.md)   
 [Como chamar um procedimento que retorna um valor](./how-to-call-a-procedure-that-returns-a-value.md)
