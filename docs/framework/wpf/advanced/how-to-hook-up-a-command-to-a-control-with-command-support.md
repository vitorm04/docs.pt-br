---
title: Como enganchar um comando em um controle com suporte de comando
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
ms.assetid: 8d8592ae-0c91-469e-a1cd-d179c4544548
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 61148e1249f7bfcf319c3be4a30c706c5c4dc344
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hook-up-a-command-to-a-control-with-command-support"></a>Como enganchar um comando em um controle com suporte de comando
O exemplo a seguir mostra como conectar um <xref:System.Windows.Input.RoutedCommand> para um <xref:System.Windows.Controls.Control> que tem suporte interno para o comando.  Para um exemplo completo que interliga comandos a várias fontes, consulte o exemplo de [Criar um exemplo de RoutedCommand personalizado](http://go.microsoft.com/fwlink/?LinkID=159980).  
  
## <a name="example"></a>Exemplo  
 O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece uma biblioteca de comandos comuns que programadores de aplicativos encontram normalmente.  As classes que compreendem a biblioteca de comando são: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, e <xref:System.Windows.Documents.EditingCommands>.  
  
 Estático <xref:System.Windows.Input.RoutedCommand> objetos que compõem essas classes não fornecem lógica de comando.  A lógica para o comando está associada com o comando com um <xref:System.Windows.Input.CommandBinding>.  Alguns controles têm CommandBindings embutidos para alguns comandos.  Esse mecanismo permite que a semântica de um comando permaneça a mesma, embora a implementação real possa mudar.  Um <xref:System.Windows.Controls.TextBox>, por exemplo, manipula a <xref:System.Windows.Input.ApplicationCommands.Paste%2A> comando diferente de um controle desenvolvido para dar suporte a imagens, mas a ideia básica do que significa colar algo permanece o mesmo.  A lógica de comando não pode ser fornecida pelo comando, mas sim deve ser fornecida pelo controle ou o aplicativo.  
  
 Muitos controles no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] têm suporte interno para alguns dos comandos na biblioteca de comandos.  <xref:System.Windows.Controls.TextBox>, por exemplo, dá suporte a muitos dos comandos de edição de aplicação, como <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, e <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  O desenvolvedor do aplicativo não precisa fazer nada especial para fazer com que esses comandos funcionem com esses controles.  Se o <xref:System.Windows.Controls.TextBox> é o destino de comando quando o comando é executado, ele tratará o comando usando o <xref:System.Windows.Input.CommandBinding> que é embutido no controle.  
  
 A seguir mostra como usar um <xref:System.Windows.Controls.MenuItem> como a origem de comando para o <xref:System.Windows.Input.ApplicationCommands.Paste%2A> comando, onde um <xref:System.Windows.Controls.TextBox> é o destino do comando.  Toda a lógica que define como o <xref:System.Windows.Controls.TextBox> executa a colagem está incorporada a <xref:System.Windows.Controls.TextBox> controle.  
  
 Um <xref:System.Windows.Controls.MenuItem> é criado e é <xref:System.Windows.Controls.MenuItem.Command%2A> está definida como o <xref:System.Windows.Input.ApplicationCommands.Paste%2A> comando.  O <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> não é explicitamente definido como o <xref:System.Windows.Controls.TextBox> objeto.  Quando o <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> não for definido, o destino para o comando é o elemento que tem o foco do teclado.  Se o elemento que tem o foco do teclado não dá suporte a <xref:System.Windows.Input.ApplicationCommands.Paste%2A> de comando ou no momento não é possível executar o comando Colar (a área de transferência está vazia, por exemplo), o <xref:System.Windows.Controls.MenuItem> estará desabilitado.  
  
 [!code-xaml[MenuItemCommandTask_XAML#MenuItemCommanding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask_XAML/CS/Window1.xaml#menuitemcommanding)]  
  
 [!code-csharp[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask/CSharp/Window1.xaml.cs#menuitemcommandingcodebehind)]
 [!code-vb[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandTask/VisualBasic/Window1.xaml.vb#menuitemcommandingcodebehind)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral dos comandos](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Enganchar um comando em um controle sem suporte a comandos](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-no-command-support.md)
