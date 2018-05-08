---
title: Como chamar um procedimento que retorna um valor (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 35f757609b6d0b36652db3b14e62ecd299a063ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Como chamar um procedimento que retorna um valor (Visual Basic)
Um `Function` procedimento retorna um valor para o código de chamada. Você chama, incluindo seu nome e argumentos no lado direito de uma instrução de atribuição ou em uma expressão.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>Para chamar um procedimento Function em uma expressão  
  
1.  Use o `Function` da mesma maneira que você usaria uma variável de nome do procedimento. Você pode usar um `Function` chamada de procedimento, você pode usar uma variável ou constante em uma expressão em qualquer lugar.  
  
2.  Siga o nome do procedimento com parênteses para incluir a lista de argumentos. Se não houver nenhum argumento, opcionalmente, você pode omitir os parênteses. No entanto, usar os parênteses faz seu código mais fácil de ler.  
  
3.  Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas. Certifique-se de fornecer os argumentos na mesma ordem que a `Function` procedimento define os parâmetros correspondentes.  
  
     Como alternativa, você pode passar um ou mais argumentos por nome. Para obter mais informações, consulte [passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md).  
  
4.  O valor retornado do procedimento participa na expressão apenas como o valor de uma variável ou constante seria.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Para chamar um procedimento Function em uma instrução de atribuição  
  
1.  Use o `Function` nome do procedimento a seguir de igualdade (`=`) entrar na instrução de atribuição.  
  
2.  Siga o nome do procedimento com parênteses para incluir a lista de argumentos. Se não houver nenhum argumento, opcionalmente, você pode omitir os parênteses. No entanto, usar os parênteses faz seu código mais fácil de ler.  
  
3.  Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas. Certifique-se de fornecer os argumentos na mesma ordem que a `Function` procedimento define os parâmetros correspondentes, a menos que você esteja passando-os pelo nome.  
  
4.  O valor retornado do procedimento é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir chama o Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> para recuperar o valor de uma variável de ambiente do sistema operacional. A primeira linha chama `Environ` dentro de uma expressão e a segunda linha chama-o em uma instrução de atribuição. `Environ` usa o nome da variável como seu único argumento. Retorna o valor da variável para o código de chamada.  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos de Função](./function-procedures.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Como criar um procedimento que retorne um valor](./how-to-create-a-procedure-that-returns-a-value.md)  
 [Como retornar um valor de um procedimento](./how-to-return-a-value-from-a-procedure.md)  
 [Como chamar um procedimento que não retorne um valor](./how-to-call-a-procedure-that-does-not-return-a-value.md)
