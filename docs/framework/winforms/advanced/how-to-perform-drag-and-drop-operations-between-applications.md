---
title: Como executar operações de arrastar e soltar entre aplicativos
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
ms.openlocfilehash: 13e884b6afb8fbe7248e59009e89ed749d5727d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525224"
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a>Como executar operações de arrastar e soltar entre aplicativos
Executar operações de arrastar e soltar entre aplicativos é não diferente de ativar esta ação dentro de um aplicativo, como os dois aplicativos envolvidos se comportem de acordo com o "contrato" estabelecido entre o <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> e <xref:System.Windows.Forms.DragEventArgs.Effect%2A> Propriedades.  
  
 No procedimento a seguir, você usará um aplicativo do Windows que você criou e o processador de texto WordPad incluído no sistema operacional Windows para executar operações do tipo "arrastar e soltar" entre aplicativos. O WordPad tem um certo conjunto de efeitos permitidos para o texto que está sendo arrastado e solto; o aplicativo do Windows para o qual o código está sendo escrito funcionará com esses efeitos para que as operações do tipo "arrastar e soltar" possam ser concluídas com êxito.  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a>Realizar um procedimento do tipo "arrastar e soltar" entre aplicativos  
  
1.  Criar um novo aplicativo Windows Form.  
  
2.  Adicione um controle <xref:System.Windows.Forms.TextBox> ao seu formulário.  
  
3.  Configurar o <xref:System.Windows.Forms.TextBox> controle para receber dados soltos.  
  
     Para obter mais informações, consulte [Instruções passo a passo: executando uma operação do tipo "arrastar e soltar" nos Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).  
  
4.  Execute seu aplicativo do Windows e, enquanto o aplicativo está em execução, execute o WordPad.  
  
     O WordPad é um editor de texto instalado pelo Windows que permite realizar operações do tipo "arrastar e soltar". Ele pode ser acessado pressionando o botão **Iniciar**, selecionando **Executar** e digitando `WordPad` na caixa de texto da caixa de diálogo **Executar** e clicando em **OK**.  
  
5.  Após abrir o WordPad, digite uma cadeia de caracteres de texto nele.  
  
6.  Usando o mouse, selecione o texto e arraste o texto selecionado para o <xref:System.Windows.Forms.TextBox> controle em seu aplicativo baseado no Windows.  
  
     Observe que quando você passa o mouse sobre o <xref:System.Windows.Forms.TextBox> controle (e, consequentemente, gera o <xref:System.Windows.Forms.Control.DragEnter> evento), o cursor muda e você pode remover o texto selecionado para o <xref:System.Windows.Forms.TextBox> controle.  
  
     Além disso, você pode configurar seu <xref:System.Windows.Forms.TextBox> controle para permitir que cadeias de caracteres de texto a ser arrastadas e soltas no WordPad. Para obter mais informações, consulte [Instruções passo a passo: executando uma operação do tipo "arrastar e soltar" nos Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como Adicionar Dados à Área de Transferência](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [Como Recuperar Dados da Área de Transferência](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [Operações do Tipo "Arrastar e Soltar" e Suporte à Área de Transferência](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
