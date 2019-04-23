---
title: 'Como: Interligar um comando a um controle com suporte de comando'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: 8d8592ae-0c91-469e-a1cd-d179c4544548
ms.openlocfilehash: 981fecf33b60c76ecab760185db7dab4bbb254d7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165198"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-command-support"></a>Como: Interligar um comando a um controle com suporte de comando
O exemplo a seguir mostra como conectar um <xref:System.Windows.Input.RoutedCommand> a um <xref:System.Windows.Controls.Control> que tem o suporte interno para o comando.  Para um exemplo completo que interliga comandos a várias fontes, consulte o exemplo de [Criar um exemplo de RoutedCommand personalizado](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand).  
  
## <a name="example"></a>Exemplo  
 O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece uma biblioteca de comandos comuns que programadores de aplicativos encontram normalmente.  As classes que compõem a biblioteca de comandos são: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands> e <xref:System.Windows.Documents.EditingCommands>.  
  
 Os objetos <xref:System.Windows.Input.RoutedCommand> estáticos que compõem essas classes não fornecem a lógica de comando.  A lógica para o comando está associada ao comando com uma <xref:System.Windows.Input.CommandBinding>.  Alguns controles têm CommandBindings embutidos para alguns comandos.  Esse mecanismo permite que a semântica de um comando permaneça a mesma, embora a implementação real possa mudar.  Uma <xref:System.Windows.Controls.TextBox>, por exemplo, manipula o comando <xref:System.Windows.Input.ApplicationCommands.Paste%2A> de maneira diferente de um controle criado para dar suporte a imagens, mas a ideia básica do que significa colar algo permanece a mesma.  A lógica de comando não pode ser fornecida pelo comando, mas sim deve ser fornecida pelo controle ou o aplicativo.  
  
 Muitos controles no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] têm suporte interno para alguns dos comandos na biblioteca de comandos.  <xref:System.Windows.Controls.TextBox>, por exemplo, dá suporte a muitos dos comandos de edição de aplicativo, como <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A> e <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  O desenvolvedor do aplicativo não precisa fazer nada especial para fazer com que esses comandos funcionem com esses controles.  Se a <xref:System.Windows.Controls.TextBox> for o destino de comando quando o comando for executado, ela manipulará o comando usando a <xref:System.Windows.Input.CommandBinding> interna do controle.  
  
 O exemplo a seguir mostra como usar um <xref:System.Windows.Controls.MenuItem> como a origem de comando para o comando <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, em que uma <xref:System.Windows.Controls.TextBox> é o destino de comando.  Toda a lógica que define como a <xref:System.Windows.Controls.TextBox> executa a colagem está inserido no controle <xref:System.Windows.Controls.TextBox>.  
  
 Um <xref:System.Windows.Controls.MenuItem> é criado e sua propriedade <xref:System.Windows.Controls.MenuItem.Command%2A> é definida como o comando <xref:System.Windows.Input.ApplicationCommands.Paste%2A>.  O <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> não está explicitamente definido como o objeto <xref:System.Windows.Controls.TextBox>.  Quando o <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> não está definido, o destino para o comando é o elemento que tem o foco do teclado.  Se o elemento que tem o foco do teclado não dá suporte ao comando <xref:System.Windows.Input.ApplicationCommands.Paste%2A> ou não pode executar o comando Colar no momento (a área de transferência está vazia, por exemplo), o <xref:System.Windows.Controls.MenuItem> fica esmaecido.  
  
 [!code-xaml[MenuItemCommandTask_XAML#MenuItemCommanding](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask_XAML/CS/Window1.xaml#menuitemcommanding)]  
  
 [!code-csharp[MenuItemCommandTask#MenuItemCommandingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask/CSharp/Window1.xaml.cs#menuitemcommandingcodebehind)]
 [!code-vb[MenuItemCommandTask#MenuItemCommandingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandTask/VisualBasic/Window1.xaml.vb#menuitemcommandingcodebehind)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de comandos](commanding-overview.md)
- [Enganchar um comando em um controle sem suporte a comandos](how-to-hook-up-a-command-to-a-control-with-no-command-support.md)
