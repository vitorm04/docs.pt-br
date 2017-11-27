---
title: Como habilitar um comando
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
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e90f7f69aebf48bbc27321d3808468a2df49f793
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-enable-a-command"></a>Como habilitar um comando
O exemplo a seguir demonstra como usar comandos em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  O exemplo mostra como associar um <xref:System.Windows.Input.RoutedCommand> para um <xref:System.Windows.Controls.Button>, crie um <xref:System.Windows.Input.CommandBinding>e criar manipuladores de eventos que implementam o <xref:System.Windows.Input.RoutedCommand>.  Para obter mais informações sobre comandos, consulte [Visão geral de comandos](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
## <a name="example"></a>Exemplo  
 A primeira seção de código cria o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], que consiste de um <xref:System.Windows.Controls.Button> e um <xref:System.Windows.Controls.StackPanel>e cria um <xref:System.Windows.Input.CommandBinding> que associa o manipulador de comandos com o <xref:System.Windows.Input.RoutedCommand>.  
  
 O <xref:System.Windows.Input.ICommandSource.Command%2A> propriedade o <xref:System.Windows.Controls.Button> está associado a <xref:System.Windows.Input.ApplicationCommands.Close%2A> comando.  
  
 O <xref:System.Windows.Input.CommandBinding> é adicionada para o <xref:System.Windows.Input.CommandBindingCollection> da raiz <xref:System.Windows.Window>. O <xref:System.Windows.Input.CommandBinding.Executed> e <xref:System.Windows.Input.CommandBinding.CanExecute> manipuladores de eventos são anexados a essa associação e associados a <xref:System.Windows.Input.ApplicationCommands.Close%2A> comando.  
  
 Sem o <xref:System.Windows.Input.CommandBinding> não existe nenhuma lógica de comando, somente um mecanismo para invocar o comando.  Quando o <xref:System.Windows.Controls.Button> é clicado, o <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> é gerado no seu destino seguido de <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.  Esses eventos atravessam a árvore de elementos procurando um <xref:System.Windows.Input.CommandBinding> para esse comando específico.  Vale a pena observar que porque <xref:System.Windows.RoutedEvent> túnel e bolha por meio da árvore de elementos, cuidado em onde o <xref:System.Windows.Input.CommandBinding> é colocado.   Se o <xref:System.Windows.Input.CommandBinding> está em um irmão do comando alvo ou outro nó que não está na rota do <xref:System.Windows.RoutedEvent>, o <xref:System.Windows.Input.CommandBinding> não será acessado.  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 A próxima seção de código implementa o <xref:System.Windows.Input.CommandManager.Executed> e <xref:System.Windows.Input.CommandBinding.CanExecute> manipuladores de eventos.  
  
 O <xref:System.Windows.Input.CommandManager.Executed> manipulador chama um método para fechar o arquivo aberto.  O <xref:System.Windows.Input.CommandBinding.CanExecute> manipulador chama um método para determinar se um arquivo está aberto.  Se um arquivo estiver aberto, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> é definido como `true`; caso contrário, ele é definido como `false`.  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral dos comandos](../../../../docs/framework/wpf/advanced/commanding-overview.md)
