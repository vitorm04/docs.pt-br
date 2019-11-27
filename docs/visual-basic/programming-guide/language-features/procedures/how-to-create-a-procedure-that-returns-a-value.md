---
title: Como criar um procedimento que retorne um valor
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 218dbb52abc0100724d38d10be91ef24252d5226
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349716"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Como criar um procedimento que retorne um valor (Visual Basic)
Você usa um procedimento de `Function` para retornar um valor para o código de chamada.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Para criar um procedimento que retorna um valor  
  
1. Fora de qualquer outro procedimento, use uma instrução `Function`, seguida por uma instrução `End Function`.  
  
2. Na instrução `Function`, siga a palavra-chave `Function` com o nome do procedimento e, em seguida, a lista de parâmetros entre parênteses.  
  
3. Siga os parênteses com uma cláusula `As` para especificar o tipo de dados do valor retornado.  
  
4. Coloque as instruções de código do procedimento entre as instruções `Function` e `End Function`.  
  
5. Use uma instrução `Return` para retornar o valor para o código de chamada.  
  
     O procedimento a seguir `Function` calcula o lado mais longo, ou hipotenusa, de um triângulo à direita, dado os valores para os outros dois lados.  
  
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
- [Como retornar um valor de um procedimento](./how-to-return-a-value-from-a-procedure.md)
- [Como chamar um procedimento que retorna um valor](./how-to-call-a-procedure-that-returns-a-value.md)
