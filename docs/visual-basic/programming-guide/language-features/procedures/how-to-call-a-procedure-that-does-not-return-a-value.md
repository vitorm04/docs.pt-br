---
title: 'Como: Chamar um procedimento que não retorna um valor (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 05b4b1cb29abff97c44c33d462375fc4d5ab159d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818573"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>Como: Chamar um procedimento que não retorna um valor (Visual Basic)
Um `Sub` procedimento não retornar um valor para o código de chamada. Você chamá-lo explicitamente com uma instrução de chamada autônoma. Você não pode chamá-lo simplesmente usando seu nome dentro de uma expressão.  
  
### <a name="to-call-a-sub-procedure"></a>Para chamar um procedimento Sub  
  
1.  Especifique o nome da `Sub` procedimento.  
  
2.  Siga o nome do procedimento com parênteses para incluir a lista de argumentos. Se não houver nenhum argumento, você pode, opcionalmente, omitir os parênteses. No entanto, usar os parênteses que torna o código mais fácil de ler.  
  
3.  Coloque os argumentos na lista de argumentos entre parênteses, separados por vírgulas. Certifique-se de fornecer os argumentos na mesma ordem em que o `Sub` procedimento define os parâmetros correspondentes.  
  
     O exemplo a seguir chama o Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> função para ativar uma janela do aplicativo. <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> leva o título da janela como seu único argumento. Ele não retorna um valor para o código de chamada. Se um processo do bloco de notas não está em execução, o exemplo gera um <xref:System.ArgumentException>. O `Shell` procedimento pressupõe que os aplicativos estão nos caminhos especificados.  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [Procedimentos](./index.md)
- [Subprocedimentos](./sub-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Como: Criar um procedimento](./how-to-create-a-procedure.md)
- [Como: Chamar um procedimento que retorna um valor](./how-to-call-a-procedure-that-returns-a-value.md)
- [Como: Chamar um manipulador de eventos no Visual Basic](./how-to-call-an-event-handler.md)
