---
title: 'Como: Chamar um procedimento que retorna um valor (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 6f45f01489ee84b6addb1f7c7c8dc584332f38dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333880"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Como: Chamar um procedimento que retorna um valor (Visual Basic)
Um `Function` procedimento retorna um valor para o código de chamada. Você chamá-lo, incluindo seu nome e argumentos no lado direito de uma instrução de atribuição ou em uma expressão.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>Para chamar um procedimento de função dentro de uma expressão  
  
1. Use o `Function` da mesma maneira que você usaria uma variável de nome do procedimento. Você pode usar um `Function` chamada de procedimento, você pode usar uma variável ou constante em uma expressão em qualquer lugar.  
  
2. Siga o nome do procedimento com parênteses para incluir a lista de argumentos. Se não houver nenhum argumento, você pode, opcionalmente, omitir os parênteses. No entanto, usar os parênteses que torna o código mais fácil de ler.  
  
3. Coloque os argumentos na lista de argumentos entre parênteses, separados por vírgulas. Certifique-se de fornecer os argumentos na mesma ordem em que o `Function` procedimento define os parâmetros correspondentes.  
  
     Como alternativa, você pode passar um ou mais argumentos por nome. Para obter mais informações, consulte [passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md).  
  
4. O valor retornado do procedimento participa na expressão, assim como o valor de uma variável ou constante seria.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Para chamar um procedimento de função em uma instrução de atribuição  
  
1. Use o `Function` nome do procedimento igual a seguir (`=`) entrar a instrução de atribuição.  
  
2. Siga o nome do procedimento com parênteses para incluir a lista de argumentos. Se não houver nenhum argumento, você pode, opcionalmente, omitir os parênteses. No entanto, usar os parênteses que torna o código mais fácil de ler.  
  
3. Coloque os argumentos na lista de argumentos entre parênteses, separados por vírgulas. Certifique-se de fornecer os argumentos na mesma ordem em que o `Function` procedimento define os parâmetros correspondentes, a menos que você esteja passando-os por nome.  
  
4. O valor retornado do procedimento é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir chama o Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> para recuperar o valor de uma variável de ambiente do sistema operacional. A primeira linha chama `Environ` dentro de uma expressão e a segunda linha chama-o em uma instrução de atribuição. `Environ` usa o nome da variável como seu único argumento. Ele retorna o valor da variável para o código de chamada.  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos de Função](./function-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Como: Criar um procedimento que retorna um valor](./how-to-create-a-procedure-that-returns-a-value.md)
- [Como: Retornar um valor de um procedimento](./how-to-return-a-value-from-a-procedure.md)
- [Como: Chamar um procedimento que não retorna um valor](./how-to-call-a-procedure-that-does-not-return-a-value.md)
