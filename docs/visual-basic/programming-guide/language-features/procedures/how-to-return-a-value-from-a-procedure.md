---
title: Como retornar um valor de um procedimento (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: affcb25951a6647604286bc91dcaec8898fe2e30
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Como retornar um valor de um procedimento (Visual Basic)
Um `Function` procedimento retorna um valor para o código de chamada seja executando um `Return` instrução ou encontrando um `Exit Function` ou `End Function` instrução.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Para retornar um valor usando a instrução Return  
  
1.  Colocar um `Return` instrução no ponto em que as tarefas do procedimento é concluída.  
  
2.  Siga o `Return` palavra-chave com uma expressão que produz o valor que você deseja retornar ao código de chamada.  
  
3.  Você pode ter mais de um demonstrativo `Return` no mesmo procedimento.  
  
     O seguinte `Function` procedimento calcula o maior lado, ou hipotenusa, de um triângulo e o retorna ao código de chamada.  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     O exemplo a seguir mostra uma chamada típica para `hypotenuse`, que armazena o valor retornado.  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Para retornar um valor usando Exit Function ou End Function  
  
1.  Em pelo menos um lugar a `Function` procedimento, atribua um valor para o nome do procedimento.  
  
2.  Quando você executa um `Exit Function` ou `End Function` do Visual Basic de instrução, retorna o valor mais recentemente atribuído ao nome do procedimento.  
  
3.  Você pode ter mais de um demonstrativo `Exit Function` no mesmo procedimento e mesclar os demonstrativos `Return` e `Exit Function` no mesmo procedimento.  
  
4.  Você pode ter apenas um `End Function` instrução em uma `Function` procedimento.  
  
     Para obter mais informações e um exemplo, consulte "Valor de retorno" em [instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Subprocedimentos](./sub-procedures.md)  
 [Procedimentos de Propriedade](./property-procedures.md)  
 [Procedimentos de Operador](./operator-procedures.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Instrução Return](../../../../visual-basic/language-reference/statements/return-statement.md)  
 [Como criar um procedimento que retorne um valor](./how-to-create-a-procedure-that-returns-a-value.md)  
 [Como chamar um procedimento que retorna um valor](./how-to-call-a-procedure-that-returns-a-value.md)
