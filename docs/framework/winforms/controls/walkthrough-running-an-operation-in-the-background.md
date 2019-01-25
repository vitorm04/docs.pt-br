---
title: 'Passo a passo: Executando uma operação em segundo plano'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
ms.openlocfilehash: 24c5a58d0064756b60596907178578f98b557d99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540215"
---
# <a name="walkthrough-running-an-operation-in-the-background"></a>Passo a passo: Executando uma operação em segundo plano
Se você tiver uma operação que levará muito tempo para ser concluída, e você não deseja causar atrasos na interface do usuário, você pode usar o <xref:System.ComponentModel.BackgroundWorker> classe para executar a operação em outro thread.  
  
 Para obter uma listagem completa do código usado neste exemplo, consulte [como: Executar uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-run-an-operation-in-the-background"></a>Executar uma operação na tela de fundo  
  
1.  Com o formulário ativo no Windows Forms Designer, arraste dois <xref:System.Windows.Forms.Button> controla a partir de **caixa de ferramentas** ao formulário e, em seguida, defina o `Name` e <xref:System.Windows.Forms.Control.Text%2A> propriedades dos botões de acordo com a tabela a seguir.  
  
    |Botão|Nome|Texto|  
    |------------|----------|----------|  
    |`button1`|`startBtn`|**Iniciar**|  
    |`button2`|`cancelBtn`|**Cancelar**|  
  
2.  Abra o **caixa de ferramentas**, clique no **componentes** guia e, em seguida, arraste o <xref:System.ComponentModel.BackgroundWorker> componente para seu formulário.  
  
     O componente `backgroundWorker1` aparece na **Bandeja de Componentes**.  
  
3.  No **propriedades** janela, defina as <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> propriedade `true`.  
  
4.  No **propriedades** janela, clique na **eventos** botão e, em seguida, clique duas vezes o <xref:System.ComponentModel.BackgroundWorker.DoWork> e <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> eventos para criar manipuladores de eventos.  
  
5.  Insira seu código demorado no <xref:System.ComponentModel.BackgroundWorker.DoWork> manipulador de eventos.  
  
6.  Extraia os parâmetros necessários para a operação dos <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> propriedade do <xref:System.ComponentModel.DoWorkEventArgs> parâmetro.  
  
7.  Atribuir o resultado da computação para o <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> propriedade do <xref:System.ComponentModel.DoWorkEventArgs>.  
  
     Isso será disponibilizado para o <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> manipulador de eventos.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8.  Inserir código para recuperar o resultado de sua operação no <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> manipulador de eventos.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. Implementar o método de `TimeConsumingOperation` .  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. No Designer de formulários do Windows, clique duas vezes `startButton` para criar o <xref:System.Windows.Forms.Control.Click> manipulador de eventos.  
  
11. Chame o <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> método na <xref:System.Windows.Forms.Control.Click> manipulador de eventos para `startButton`.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. No Designer de formulários do Windows, clique duas vezes `cancelButton` para criar o <xref:System.Windows.Forms.Control.Click> manipulador de eventos.  
  
13. Chame o <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> método na <xref:System.Windows.Forms.Control.Click> manipulador de eventos para `cancelButton`.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. Na parte superior do arquivo, importe os namespaces System.ComponentModel e System.Threading.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. Pressione F6 para compilar a solução e, em seguida, pressione CTRL-F5 para executar o aplicativo fora do depurador.  
  
> [!NOTE]
>  Se você pressionar F5 para executar o aplicativo no depurador, a exceção gerada no método `TimeConsumingOperation` será capturada e exibida pelo depurador. Quando você executar o aplicativo fora do depurador, o <xref:System.ComponentModel.BackgroundWorker> manipula a exceção e armazena em cache na <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> propriedade do <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.  
  
1.  Clique no botão **Iniciar** para executar uma operação assíncrona e, em seguida, no botão **Cancelar** para interromper uma operação assíncrona em execução.  
  
     O resultado de cada operação é exibido em um <xref:System.Windows.Forms.MessageBox>.  
  
## <a name="next-steps"></a>Próximas etapas  
  
-   Implemente um formulário que relata o andamento à medida que uma operação assíncrona prossegue. Para obter mais informações, confira [Como: Implementar um formulário que usa uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
-   Implemente uma classe que dá suporte ao padrão assíncrono para componentes. Para obter mais informações, consulte [Implementando o padrão assíncrono baseado em evento](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [Como: Implementar um formulário que usa uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [Como: Executar uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Componente BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
