---
title: 'Como: Enganchar um comando em um controle sem suporte a comandos'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
ms.openlocfilehash: 3ae45c9a9e33a3cb53ada6e1e5430ae0f9e6c198
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216971"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a>Como: Enganchar um comando em um controle sem suporte a comandos
O exemplo a seguir mostra como conectar um <xref:System.Windows.Input.RoutedCommand> a um <xref:System.Windows.Controls.Control> que não tem o suporte interno para o comando.  Para um exemplo completo que interliga comandos a várias fontes, consulte o exemplo de [Criar um exemplo de RoutedCommand personalizado](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand).  
  
## <a name="example"></a>Exemplo  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Fornece uma biblioteca de comandos comuns que programadores de aplicativos encontram normalmente.  As classes que compõem a biblioteca de comandos são: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands> e <xref:System.Windows.Documents.EditingCommands>.  
  
 Os objetos <xref:System.Windows.Input.RoutedCommand> estáticos que compõem essas classes não fornecem a lógica de comando.  A lógica para o comando está associada ao comando com uma <xref:System.Windows.Input.CommandBinding>.  Muitos controles no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dão suporte interno para alguns dos comandos na biblioteca de comandos.  <xref:System.Windows.Controls.TextBox>, por exemplo, dá suporte a muitos dos comandos de edição de aplicação, como <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, e <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  O desenvolvedor do aplicativo não precisa fazer nada especial para fazer com que esses comandos funcionem com esses controles.  Se a <xref:System.Windows.Controls.TextBox> for o destino de comando quando o comando for executado, ela manipulará o comando usando a <xref:System.Windows.Input.CommandBinding> interna do controle.  
  
 O exemplo a seguir mostra como usar um <xref:System.Windows.Controls.Button> como a origem de comando para o comando <xref:System.Windows.Input.ApplicationCommands.Open%2A>.  Uma <xref:System.Windows.Input.CommandBinding> é criada, que associa o <xref:System.Windows.Input.CanExecuteRoutedEventHandler> especificado e o <xref:System.Windows.Input.CanExecuteRoutedEventHandler> ao <xref:System.Windows.Input.RoutedCommand>.  
  
 Primeiro, a fonte de comando é criada.  Um <xref:System.Windows.Controls.Button> é usado como a origem de comando.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 Em seguida, o <xref:System.Windows.Input.ExecutedRoutedEventHandler> e o <xref:System.Windows.Input.CanExecuteRoutedEventHandler> são criados.  O <xref:System.Windows.Input.ExecutedRoutedEventHandler> apenas abre uma <xref:System.Windows.MessageBox> para indicar que o comando foi executado.  O <xref:System.Windows.Input.CanExecuteRoutedEventHandler> define a propriedade <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> como `true`.  Normalmente, o manipulador realizaria verificações mais robustas para ver se o comando pode ser executado no destino do comando atual.  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 Por fim, uma <xref:System.Windows.Input.CommandBinding> é criada na <xref:System.Windows.Window> raiz do aplicativo que associa os manipuladores de eventos roteados ao comando <xref:System.Windows.Input.ApplicationCommands.Open%2A>.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral dos comandos](commanding-overview.md)
- [Interligar um comando a um controle com suporte de comando](how-to-hook-up-a-command-to-a-control-with-command-support.md)
