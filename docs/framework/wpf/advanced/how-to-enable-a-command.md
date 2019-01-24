---
title: 'Como: Habilitar um comando'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
ms.openlocfilehash: 904d5a3404b693c383731eda01e9e43b2d5126fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622059"
---
# <a name="how-to-enable-a-command"></a>Como: Habilitar um comando
O exemplo a seguir demonstra como usar comandos em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  O exemplo mostra como associar um <xref:System.Windows.Input.RoutedCommand> para um <xref:System.Windows.Controls.Button>, criar um <xref:System.Windows.Input.CommandBinding>e criar manipuladores de eventos que implementam o <xref:System.Windows.Input.RoutedCommand>.  Para obter mais informações sobre comandos, consulte [Visão geral de comandos](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
## <a name="example"></a>Exemplo  
 A primeira seção de código cria o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], que consiste em um <xref:System.Windows.Controls.Button> e uma <xref:System.Windows.Controls.StackPanel>e cria um <xref:System.Windows.Input.CommandBinding> que associa os manipuladores de comandos com o <xref:System.Windows.Input.RoutedCommand>.  
  
 O <xref:System.Windows.Input.ICommandSource.Command%2A> propriedade do <xref:System.Windows.Controls.Button> está associado com o <xref:System.Windows.Input.ApplicationCommands.Close%2A> comando.  
  
 O <xref:System.Windows.Input.CommandBinding> é adicionado para o <xref:System.Windows.Input.CommandBindingCollection> da raiz <xref:System.Windows.Window>. O <xref:System.Windows.Input.CommandBinding.Executed> e <xref:System.Windows.Input.CommandBinding.CanExecute> manipuladores de eventos são anexados a essa associação e associados a <xref:System.Windows.Input.ApplicationCommands.Close%2A> comando.  
  
 Sem o <xref:System.Windows.Input.CommandBinding> há nenhuma lógica de comando, somente um mecanismo para invocar o comando.  Quando o <xref:System.Windows.Controls.Button> é clicado, o <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> é gerado no destino do comando, seguido de <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.  Esses eventos atravessam a árvore de elementos procurando um <xref:System.Windows.Input.CommandBinding> para esse comando específico.  Vale a pena observar que porque <xref:System.Windows.RoutedEvent> túnel e por propagação pela árvore de elementos, é necessário ter cuidado em onde o <xref:System.Windows.Input.CommandBinding> é colocado.   Se o <xref:System.Windows.Input.CommandBinding> está em um irmão do comando alvo ou em outro nó que não está na rota do <xref:System.Windows.RoutedEvent>, o <xref:System.Windows.Input.CommandBinding> não será acessado.  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 A próxima seção de código implementa o <xref:System.Windows.Input.CommandManager.Executed> e <xref:System.Windows.Input.CommandBinding.CanExecute> manipuladores de eventos.  
  
 O <xref:System.Windows.Input.CommandManager.Executed> manipulador chama um método para fechar o arquivo aberto.  O <xref:System.Windows.Input.CommandBinding.CanExecute> manipulador chama um método para determinar se um arquivo está aberto.  Se um arquivo estiver aberto, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> é definido como `true`; caso contrário, ele é definido como `false`.  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de comandos](../../../../docs/framework/wpf/advanced/commanding-overview.md)
