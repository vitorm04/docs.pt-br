---
title: 'Como: chamar um procedimento que retorna um valor (Visual Basic) | Documentos do Microsoft'
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
- procedure calls, returning values
- Visual Basic code, procedures
- procedures, calling
- procedures, returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: 15
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
ms.openlocfilehash: df6bb1ed8acf5f86a290d67fec9c053cfe5245d2
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Como chamar um procedimento que retorna um valor (Visual Basic)
Um `Function` procedimento retorna um valor para o código de chamada. Você chamá-lo, incluindo seu nome e argumentos no lado direito de uma instrução de atribuição ou em uma expressão.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>Para chamar um procedimento Function em uma expressão  
  
1.  Use o `Function` da mesma maneira que você usaria uma variável de nome do procedimento. Você pode usar um `Function` chamada de procedimento, você pode usar uma variável ou constante em uma expressão em qualquer lugar.  
  
2.  Siga o nome do procedimento com parênteses para incluir a lista de argumentos. Se não houver nenhum argumento, opcionalmente, você pode omitir os parênteses. No entanto, usar os parênteses torna seu código mais fácil de ler.  
  
3.  Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas. Certifique-se de fornecer os argumentos na mesma ordem que a `Function` procedimento define os parâmetros correspondentes.  
  
     Como alternativa, você pode passar um ou mais argumentos por nome. Para obter mais informações, consulte [passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md).  
  
4.  O valor retornado do procedimento participa na expressão apenas como o valor de uma variável ou constante participaria.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Para chamar um procedimento Function em uma instrução de atribuição  
  
1.  Use o `Function` nome do procedimento a seguir a igual (`=`) entrar a instrução de atribuição.  
  
2.  Siga o nome do procedimento com parênteses para incluir a lista de argumentos. Se não houver nenhum argumento, opcionalmente, você pode omitir os parênteses. No entanto, usar os parênteses torna seu código mais fácil de ler.  
  
3.  Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas. Certifique-se de fornecer os argumentos na mesma ordem que a `Function` procedimento define os parâmetros correspondentes, a menos que você esteja passando-os por nome.  
  
4.  O valor retornado do procedimento é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir chama o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A>para recuperar o valor de uma variável de ambiente do sistema operacional.</xref:Microsoft.VisualBasic.Interaction.Environ%2A> A primeira linha chama `Environ` dentro de uma expressão e a segunda linha chama-o em uma instrução de atribuição. `Environ`usa o nome da variável como seu único argumento. Ele retorna o valor da variável para o código de chamada.  
  
 [!code-vb[VbVbcnProcedures&#7;](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos de função](./function-procedures.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Como: criar um procedimento que retorna um valor](./how-to-create-a-procedure-that-returns-a-value.md)   
 [Como: retornar um valor de um procedimento](./how-to-return-a-value-from-a-procedure.md)   
 [Como chamar um procedimento que não retorne um valor](./how-to-call-a-procedure-that-does-not-return-a-value.md)
