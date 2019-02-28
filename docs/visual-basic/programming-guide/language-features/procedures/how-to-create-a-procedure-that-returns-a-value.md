---
title: 'Como: Criar um procedimento que retorna um valor (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: ce0010762374baf5b19ab2e64f50e12fefda2dee
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966953"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Como: Criar um procedimento que retorna um valor (Visual Basic)
Você usa um `Function` procedimento retornar um valor para o código de chamada.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Para criar um procedimento que retorna um valor  
  
1.  Fora de qualquer outro procedimento, utilize uma `Function` instrução, seguida por um `End Function` instrução.  
  
2.  No `Function` instrução, siga o `Function` palavra-chave com o nome do procedimento e, em seguida, a lista de parâmetros entre parênteses.  
  
3.  Siga os parênteses com um `As` cláusula para especificar o tipo de dados do valor retornado.  
  
4.  Colocar instruções de código do procedimento entre o `Function` e `End Function` instruções.  
  
5.  Use um `Return` instrução para retornar o valor para o código de chamada.  
  
     O seguinte `Function` procedimento calcula o lado mais longo, ou hipotenusa de um triângulo, considerando os valores para os dois lados.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     O exemplo a seguir mostra uma chamada típica para `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Consulte também
- [Procedimentos](./index.md)
- [Subprocedimentos](./sub-procedures.md)
- [Procedimentos de Propriedade](./property-procedures.md)
- [Procedimentos de Operador](./operator-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Como: Retornar um valor de um procedimento](./how-to-return-a-value-from-a-procedure.md)
- [Como: Chamar um procedimento que retorna um valor](./how-to-call-a-procedure-that-returns-a-value.md)
