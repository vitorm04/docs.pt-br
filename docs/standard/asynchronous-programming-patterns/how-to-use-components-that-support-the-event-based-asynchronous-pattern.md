---
title: "Como usar componentes compatíveis com o padrão assíncrono baseado em evento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 49e03a8d886ccd4ed6e4b2a19692c1874f5928ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>Como usar componentes compatíveis com o padrão assíncrono baseado em evento
Muitos componentes oferecem a opção de executar seu trabalho de forma assíncrona. O <xref:System.Media.SoundPlayer> e <xref:System.Windows.Forms.PictureBox> componentes, por exemplo, habilitar a carga sons e imagens "em segundo plano", enquanto o thread principal continua em execução sem interrupções.  
  
 Usando métodos assíncronos em uma classe que oferece suporte a [baseado em evento visão geral do padrão assíncrono](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) pode ser tão simples quanto anexando um manipulador de eventos para o componente *MethodName* `Completed` evento, Assim como faria para qualquer outro evento. Quando você chama o *MethodName* `Async` método, seu aplicativo continuará em execução sem interrupção até que o *MethodName* `Completed` é gerado. O manipulador de eventos, você pode examinar o <xref:System.ComponentModel.AsyncCompletedEventArgs> parâmetro para determinar se a operação assíncrona foi concluída com êxito ou se foi cancelada.  
  
 Para obter mais informações sobre o uso de manipuladores de eventos, consulte [visão geral de manipuladores de evento](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
 O procedimento a seguir mostra como usar o recurso de carregamento de imagem assíncrono de um <xref:System.Windows.Forms.PictureBox> controle.  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>Para ativar um controle PictureBox assincronamente carregar uma imagem  
  
1.  Criar uma instância do <xref:System.Windows.Forms.PictureBox> componente no formulário.  
  
2.  Atribuir um manipulador de eventos para o <xref:System.Windows.Forms.PictureBox.LoadCompleted> evento.  
  
     Verifique os erros que possam ter ocorrido durante o download assíncrono aqui. Isso também é onde você verifica o cancelamento.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  Adicione dois botões, chamados `loadButton` e `cancelLoadButton`, ao formulário. Adicionar <xref:System.Windows.Forms.Control.Click> manipuladores de eventos para iniciar e cancelar o download.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  Execute o aplicativo.  
  
     Conforme o download da imagem prossegue, mover o formulário gratuitamente, minimize- e maximizá-lo.  
  
## <a name="see-also"></a>Consulte também  
 [Como executar uma operação em segundo plano](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Visão Geral do Padrão Assíncrono Baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [NÃO está em compilação: Multithread no Visual Basic](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)
