---
title: Como usar componentes compatíveis com o padrão assíncrono baseado em evento
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
ms.openlocfilehash: f0bf9b1da76033ef40cc72657ee722083a6f8b1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567621"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>Como usar componentes compatíveis com o padrão assíncrono baseado em evento
Muitos componentes oferecem a opção de executar seu trabalho de forma assíncrona. Os componentes <xref:System.Media.SoundPlayer> e <xref:System.Windows.Forms.PictureBox>, por exemplo, permite que você carregue sons e imagens "em segundo plano", enquanto o thread principal continua em execução sem interrupções.  
  
 Usar métodos assíncronos em uma classe que oferece suporte a [Visão geral do padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) pode ser tão simples quanto anexar um manipulador de eventos ao evento *MethodName***Completed** do componente, assim como você faria com qualquer outro evento. Quando você chama o método *MethodName***Async**, seu aplicativo continuará em execução sem interrupção até que o evento *MethodName***Completed** seja gerado. No manipulador de eventos, você pode examinar o parâmetro <xref:System.ComponentModel.AsyncCompletedEventArgs> para determinar se a operação assíncrona foi concluída com êxito ou se foi cancelada.  
  
 Para saber mais sobre como usar manipuladores de evento, consulte [Visão geral dos manipuladores de evento](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
 O procedimento a seguir mostra como usar o recurso de carregamento de imagem assíncrono de um controle <xref:System.Windows.Forms.PictureBox>.  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>Para ativar um controle PictureBox para carregar assincronamente uma imagem  
  
1.  Crie uma instância do componente <xref:System.Windows.Forms.PictureBox> no formulário.  
  
2.  Atribua um manipulador de eventos ao evento <xref:System.Windows.Forms.PictureBox.LoadCompleted>.  
  
     Verifique se ocorreu algum erro durante o download assíncrono aqui. Verifique também o cancelamento.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  Adicione dois botões, chamados `loadButton` e `cancelLoadButton`, ao formulário. Adicione <xref:System.Windows.Forms.Control.Click> manipuladores de eventos para iniciar e cancelar o download.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  Execute seu aplicativo.  
  
     Conforme o download da imagem prossegue, você pode mover o formulário livremente, minimizá-lo e maximizá-lo.  
  
## <a name="see-also"></a>Consulte também  
 [Como executar uma operação em segundo plano](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Visão Geral do Padrão Assíncrono Baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [NÃO ESTÁ NO BUILD: multithreading no Visual Basic](https://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)
