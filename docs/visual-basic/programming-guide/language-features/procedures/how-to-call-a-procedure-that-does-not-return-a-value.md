---
title: Como chamar um procedimento que não retorne um valor (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb9f13d5387f4a440a7fdd39c5e8f50cb8d56270
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>Como chamar um procedimento que não retorne um valor (Visual Basic)
Um `Sub` procedimento não retornar um valor para o código de chamada. Você chamá-lo explicitamente com uma instrução de chamada autônoma. Você não pode chamá-lo simplesmente usando seu nome dentro de uma expressão.  
  
### <a name="to-call-a-sub-procedure"></a>Para chamar um procedimento Sub  
  
1.  Especifique o nome do `Sub` procedimento.  
  
2.  Siga o nome do procedimento com parênteses para incluir a lista de argumentos. Se não houver nenhum argumento, opcionalmente, você pode omitir os parênteses. No entanto, usar os parênteses faz seu código mais fácil de ler.  
  
3.  Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas. Certifique-se de fornecer os argumentos na mesma ordem que a `Sub` procedimento define os parâmetros correspondentes.  
  
     O exemplo a seguir chama o Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> função para ativar uma janela de aplicativo. <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> usa o título da janela como seu único argumento. Ele não retorna um valor para o código de chamada. Se um processo do bloco de notas não está em execução, o exemplo gera um <xref:System.ArgumentException>. O `Shell` procedimento pressupõe que os aplicativos estão nos caminhos especificados.  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:System.ArgumentException>  
 [Procedimentos](./index.md)  
 [Subprocedimentos](./sub-procedures.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Como criar um procedimento](./how-to-create-a-procedure.md)  
 [Como chamar um procedimento que retorna um valor](./how-to-call-a-procedure-that-returns-a-value.md)  
 [Como: chamar um manipulador de eventos no Visual Basic](./how-to-call-an-event-handler.md)
