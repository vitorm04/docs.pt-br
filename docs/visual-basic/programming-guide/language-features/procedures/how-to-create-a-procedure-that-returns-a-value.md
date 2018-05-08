---
title: Como criar um procedimento que retorne um valor (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 472f55173a4897a23a82812a2b24bf1646c1a6ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Como criar um procedimento que retorne um valor (Visual Basic)
Você usa um `Function` procedimento retorne um valor para o código de chamada.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Para criar um procedimento que retorna um valor  
  
1.  Fora de qualquer outro procedimento, utilize uma `Function` instrução, seguida por um `End Function` instrução.  
  
2.  No `Function` instrução, siga o `Function` palavra-chave com o nome do procedimento e, em seguida, a lista de parâmetros entre parênteses.  
  
3.  Siga os parênteses com uma `As` cláusula para especificar o tipo de dados do valor retornado.  
  
4.  Colocar instruções de código do procedimento entre o `Function` e `End Function` instruções.  
  
5.  Use um `Return` instrução para retornar o valor para o código de chamada.  
  
     O seguinte `Function` procedimento calcula o maior lado, ou hipotenusa, de um triângulo retângulo, dado os valores dos outros dois lados.  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     O exemplo a seguir mostra uma chamada típica para `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Subprocedimentos](./sub-procedures.md)  
 [Procedimentos de Propriedade](./property-procedures.md)  
 [Procedimentos de Operador](./operator-procedures.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Como retornar um valor de um procedimento](./how-to-return-a-value-from-a-procedure.md)  
 [Como chamar um procedimento que retorna um valor](./how-to-call-a-procedure-that-returns-a-value.md)
