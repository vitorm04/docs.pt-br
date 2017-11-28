---
title: Como enganchar um comando em um controle sem suporte de comando
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6f38a6f900ee2b253708da4b63bdc2f474fa3ab1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a>Como enganchar um comando em um controle sem suporte de comando
O exemplo a seguir mostra como conectar um <xref:System.Windows.Input.RoutedCommand> para um <xref:System.Windows.Controls.Control> que não tem embutido no suporte para o comando.  Para um exemplo completo que interliga comandos a várias fontes, consulte o exemplo de [Criar um exemplo de RoutedCommand personalizado](http://go.microsoft.com/fwlink/?LinkID=159980).  
  
## <a name="example"></a>Exemplo  
 O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece uma biblioteca de comandos comuns que programadores de aplicativos encontram normalmente.  As classes que compreendem a biblioteca de comando são: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, e <xref:System.Windows.Documents.EditingCommands>.  
  
 Estático <xref:System.Windows.Input.RoutedCommand> objetos que compõem essas classes não fornecem lógica de comando.  A lógica para o comando está associada com o comando com um <xref:System.Windows.Input.CommandBinding>.  Muitos controles no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dão suporte interno para alguns dos comandos na biblioteca de comandos.  <xref:System.Windows.Controls.TextBox>, por exemplo, dá suporte a muitos dos comandos de edição de aplicação, como <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, e <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  O desenvolvedor do aplicativo não precisa fazer nada especial para fazer com que esses comandos funcionem com esses controles.  Se o <xref:System.Windows.Controls.TextBox> é o destino de comando quando o comando é executado, ele tratará o comando usando o <xref:System.Windows.Input.CommandBinding> que é embutido no controle.  
  
 A seguir mostra como usar um <xref:System.Windows.Controls.Button> como a origem de comando para o <xref:System.Windows.Input.ApplicationCommands.Open%2A> comando.  Um <xref:System.Windows.Input.CommandBinding> é criado que associa especificado <xref:System.Windows.Input.CanExecuteRoutedEventHandler> e <xref:System.Windows.Input.CanExecuteRoutedEventHandler> com o <xref:System.Windows.Input.RoutedCommand>.  
  
 Primeiro, a fonte de comando é criada.  Um <xref:System.Windows.Controls.Button> é usado como a origem de comando.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 Em seguida, o <xref:System.Windows.Input.ExecutedRoutedEventHandler> e <xref:System.Windows.Input.CanExecuteRoutedEventHandler> são criados.  O <xref:System.Windows.Input.ExecutedRoutedEventHandler> simplesmente abre um <xref:System.Windows.MessageBox> para significar que o comando é executado.  O <xref:System.Windows.Input.CanExecuteRoutedEventHandler> define o <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> propriedade `true`.  Normalmente, o manipulador realizaria verificações mais robustas para ver se o comando pode ser executado no destino do comando atual.  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 Por fim, um <xref:System.Windows.Input.CommandBinding> é criado na raiz <xref:System.Windows.Window> do aplicativo que associa os manipuladores de eventos roteados para a <xref:System.Windows.Input.ApplicationCommands.Open%2A> comando.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral dos comandos](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Interligar um comando a um controle com suporte de comando](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-command-support.md)
