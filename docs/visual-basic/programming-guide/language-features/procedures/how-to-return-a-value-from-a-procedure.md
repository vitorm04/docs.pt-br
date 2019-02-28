---
title: 'Como: Retornar um valor de um procedimento (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 45f175de647887a406f8ae87dae492a5fe58cca9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976727"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Como: Retornar um valor de um procedimento (Visual Basic)
Um `Function` procedimento retorna um valor para o código de chamada seja executando uma `Return` instrução ou encontrando uma `Exit Function` ou `End Function` instrução.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Para retornar um valor usando a instrução Return  
  
1.  Coloque um `Return` instrução no ponto em que as tarefas do procedimento é concluída.  
  
2.  Siga o `Return` palavra-chave com uma expressão que produz o valor que você deseja retornar ao código de chamada.  
  
3.  Você pode ter mais de um demonstrativo `Return` no mesmo procedimento.  
  
     O seguinte `Function` procedimento calcula o lado mais longo, ou hipotenusa de um triângulo e o retorna ao código de chamada.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     O exemplo a seguir mostra uma chamada típica para `hypotenuse`, que armazena o valor retornado.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Para retornar um valor usando Exit Function ou End Function  
  
1.  Em pelo menos um lugar a `Function` procedimento, atribua um valor ao nome do procedimento.  
  
2.  Quando você executa um `Exit Function` ou `End Function` instrução, o Visual Basic retorna o valor mais recentemente atribuído ao nome do procedimento.  
  
3.  Você pode ter mais de um demonstrativo `Exit Function` no mesmo procedimento e mesclar os demonstrativos `Return` e `Exit Function` no mesmo procedimento.  
  
4.  Você pode ter apenas um `End Function` instrução em um `Function` procedimento.  
  
     Para obter mais informações e um exemplo, consulte "Valor de retorno" em [instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Consulte também
- [Procedimentos](./index.md)
- [Subprocedimentos](./sub-procedures.md)
- [Procedimentos de Propriedade](./property-procedures.md)
- [Procedimentos de Operador](./operator-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Return](../../../../visual-basic/language-reference/statements/return-statement.md)
- [Como: Criar um procedimento que retorna um valor](./how-to-create-a-procedure-that-returns-a-value.md)
- [Como: Chamar um procedimento que retorna um valor](./how-to-call-a-procedure-that-returns-a-value.md)
