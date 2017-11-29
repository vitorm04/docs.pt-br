---
title: "Visão geral dos comandos"
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
- interfaces [WPF], ICommandSource
- command library [WPF]
- commands [WPF], definition of
- CommandBindings [WPF]
- ICommandSource interfaces [WPF]
- commanding [WPF]
- CommandManager [WPF]
ms.assetid: bc208dfe-367d-426a-99de-52b7e7511e81
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9b75319b5a07ac2ee1601f30394da641eb2b781c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="commanding-overview"></a>Visão geral dos comandos
<a name="introduction"></a> Os comandos são um mecanismo de entrada do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] que oferecem manipulação de entrada em um nível mais semântico do que a entrada do dispositivo. Os exemplos de comandos são as operações **Copiar**, **Recortar** e **Colar**, encontradas em muitos aplicativos.  
  
 Esta visão geral define quais comandos estão no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], quais classes fazem parte do modelo de comandos e como utilizar e criar comandos nos seus aplicativos.  
  
 Esse tópico contém as seguintes seções:  
  
-   [O que são comandos?](#commands_at_10000_feet)  
  
-   [Exemplo de comando simples no WPF](#simple_command)  
  
-   [Quatro conceitos principais em comandos do WPF](#Four_main_Concepts)  
  
-   [Biblioteca de comandos](#Command_Library)  
  
-   [Criando comandos personalizados](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>   
## <a name="what-are-commands"></a>O que são comandos?  
 Os comandos têm várias finalidades. A primeira finalidade é separar a semântica e o objeto que invoca um comando da lógica que o executa. Isso permite que fontes múltiplas e distintas invoquem a mesma lógica de comando, além de permitir que a lógica de comando seja personalizada para destinos diferentes. Por exemplo, as operações de edição **Copiar**, **Recortar** e **Colar**, que são encontradas em muitos aplicativos, podem ser invocadas por meio de ações do usuário diferentes se forem implementadas por meio do uso de comandos. Um aplicativo pode permitir que um usuário recorte texto ou objetos selecionados ao clicar em um botão, escolher um item em um menu ou usar uma combinação de teclas, como CTRL+X. Usando comandos, é possível associar cada tipo de ação do usuário à mesma lógica.  
  
 Outra finalidade dos comandos é indicar se uma ação está disponível. Para continuar o exemplo de recortar um objeto ou texto, a ação só faz sentido quando algo está selecionado. Se um usuário tentar recortar um objeto ou texto sem ter selecionado alguma coisa, nada acontece. Para indicar isso para o usuário, muitos aplicativos desabilitam botões e itens de menu para indicar se é possível executar uma ação. Um comando pode indicar se uma ação é possível implementar a <xref:System.Windows.Input.ICommand.CanExecute%2A> método. Um botão pode assinar o <xref:System.Windows.Input.ICommand.CanExecuteChanged> eventos e ser desabilitado se <xref:System.Windows.Input.ICommand.CanExecute%2A> retorna `false` ou ser ativado se <xref:System.Windows.Input.ICommand.CanExecute%2A> retorna `true`.  
  
 A semântica de um comando pode ser consistente entre aplicativos e classes; porém, a lógica da ação é específica para o objeto específico da ação. A combinação de teclas CTRL+X invoca o comando **Recortar** em classes de texto, classes de imagens e navegadores da Web, enquanto a lógica real para executar a operação **Recortar** é definida pelo aplicativo que faz o recorte. Um <xref:System.Windows.Input.RoutedCommand> permite que os clientes implementar a lógica. Um objeto de texto poderá recortar o texto selecionado na área de transferência, enquanto um objeto de imagem poderá recortar a imagem selecionada. Quando um aplicativo manipula o <xref:System.Windows.Input.CommandManager.Executed> evento, ele tem acesso para o destino do comando e pode levar a ação apropriada dependendo do tipo de destino.  
  
<a name="simple_command"></a>   
## <a name="simple-command-example-in-wpf"></a>Exemplo de comando simples no WPF  
 A maneira mais simples para usar um comando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é usar um modelo predefinido <xref:System.Windows.Input.RoutedCommand> de uma das classes de biblioteca de comando; use um controle que tem o suporte nativo para tratar o comando; e usar um controle que tem o suporte nativo para invocar um comando.  O <xref:System.Windows.Input.ApplicationCommands.Paste%2A> comando é um dos comandos predefinidos na <xref:System.Windows.Input.ApplicationCommands> classe.  O <xref:System.Windows.Controls.TextBox> controle criado na lógica para manipular o <xref:System.Windows.Input.ApplicationCommands.Paste%2A> comando.  E o <xref:System.Windows.Controls.MenuItem> classe tem suporte nativo para chamar comandos.  
  
 O exemplo a seguir mostra como configurar um <xref:System.Windows.Controls.MenuItem> para que, quando ele for clicado ele chamará o <xref:System.Windows.Input.ApplicationCommands.Paste%2A> comando em uma <xref:System.Windows.Controls.TextBox>, supondo que o <xref:System.Windows.Controls.TextBox> tem o foco do teclado.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>   
## <a name="four-main-concepts-in-wpf-commanding"></a>Quatro conceitos principais em comandos do WPF  
 O modelo de comando roteado no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode ser dividido em quatro conceitos principais: o comando, a fonte do comando, o destino do comando e a associação do comando:  
  
-   O *comando* é a ação que será executada.  
  
-   A *fonte do comando* é o objeto que invoca o comando.  
  
-   O *destino do comando* é o objeto no qual o comando está sendo executado.  
  
-   A *associação do comando* é o objeto que mapeia a lógica de comando até o comando.  
  
 No exemplo anterior, o <xref:System.Windows.Input.ApplicationCommands.Paste%2A> comando é o comando, o <xref:System.Windows.Controls.MenuItem> é a origem de comando, o <xref:System.Windows.Controls.TextBox> é o destino de comando, e a associação de comando é fornecida pelo <xref:System.Windows.Controls.TextBox> controle.  Vale a pena observar que não é sempre o caso que a <xref:System.Windows.Input.CommandBinding> é fornecido pelo controle que é a classe de destino do comando.  Com muita frequência, o <xref:System.Windows.Input.CommandBinding> devem ser criadas pelo desenvolvedor de aplicativos, ou o <xref:System.Windows.Input.CommandBinding> pode ser anexado a um predecessor do destino de comando.  
  
<a name="Commands"></a>   
### <a name="commands"></a>Comandos  
 Comandos em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são criados Implementando a <xref:System.Windows.Input.ICommand> interface.  <xref:System.Windows.Input.ICommand>apresenta dois métodos, <xref:System.Windows.Input.ICommand.Execute%2A>, e <xref:System.Windows.Input.ICommand.CanExecute%2A>e um evento <xref:System.Windows.Input.ICommand.CanExecuteChanged>. <xref:System.Windows.Input.ICommand.Execute%2A>executa as ações que estão associadas com o comando. <xref:System.Windows.Input.ICommand.CanExecute%2A>Determina se o comando pode executar no destino de comando atual. <xref:System.Windows.Input.ICommand.CanExecuteChanged>é gerado se o Gerenciador de comando que centraliza as operações de comando detecta uma alteração na fonte de comando que pode invalidar um comando que foi gerado, mas ainda não foi executado pela associação de comando.  O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementação de <xref:System.Windows.Input.ICommand> é o <xref:System.Windows.Input.RoutedCommand> de classe e é o foco desta visão geral.  
  
 As principais fontes de entrada no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são o mouse, o teclado, tinta e comandos roteados.  As entradas mais orientadas a dispositivos usam um <xref:System.Windows.RoutedEvent> para notificar objetos em uma página de aplicativo que ocorreu um evento de entrada.  Um <xref:System.Windows.Input.RoutedCommand> não é diferente.  O <xref:System.Windows.Input.RoutedCommand.Execute%2A> e <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> métodos de um <xref:System.Windows.Input.RoutedCommand> não contêm a lógica do aplicativo para o comando, mas em vez disso, eles geram eventos roteados que túnel e de bolhas por meio da árvore de elementos até que eles encontrem um objeto com um <xref:System.Windows.Input.CommandBinding>.  O <xref:System.Windows.Input.CommandBinding> contém os manipuladores para esses eventos e são os manipuladores que executam o comando.  Para obter mais informações sobre o roteamento de eventos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 O <xref:System.Windows.Input.RoutedCommand.Execute%2A> método em um <xref:System.Windows.Input.RoutedCommand> gera o <xref:System.Windows.Input.CommandManager.PreviewExecuted> e <xref:System.Windows.Input.CommandManager.Executed> eventos no destino de comando.  O <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> método em um <xref:System.Windows.Input.RoutedCommand> gera o <xref:System.Windows.Input.CommandManager.CanExecute> e <xref:System.Windows.Input.CommandManager.PreviewCanExecute> eventos no destino de comando.  Esses túnel de eventos e de bolhas por meio da árvore de elementos até que eles encontrem um objeto que tem um <xref:System.Windows.Input.CommandBinding> para esse comando específico.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Fornece um conjunto de comandos roteados comuns espalhado entre várias classes: <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.ComponentCommands>, e <xref:System.Windows.Documents.EditingCommands>.  Essas classes consistem apenas o <xref:System.Windows.Input.RoutedCommand> objetos e não a lógica de implementação do comando.  A lógica de implementação é de responsabilidade do objeto no qual o comando está sendo executado.  
  
<a name="Command_Sources"></a>   
### <a name="command-sources"></a>Fontes de comando  
 Uma fonte do comando é o objeto que invoca o comando.  Exemplos de fontes de comando são <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.Button>, e <xref:System.Windows.Input.KeyGesture>.  
  
 Fontes de comando no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geralmente implementa o <xref:System.Windows.Input.ICommandSource> interface.  
  
 <xref:System.Windows.Input.ICommandSource>expõe três propriedades: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>, e <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>:  
  
-   <xref:System.Windows.Input.ICommandSource.Command%2A>é o comando a ser executado quando a fonte de comando é chamada.  
  
-   <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>é o objeto no qual executar o comando.  Vale a pena observar que, em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> propriedade <xref:System.Windows.Input.ICommandSource> só é aplicável quando o <xref:System.Windows.Input.ICommand> é um <xref:System.Windows.Input.RoutedCommand>.  Se o <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> é definido em um <xref:System.Windows.Input.ICommandSource> e o comando correspondente não é um <xref:System.Windows.Input.RoutedCommand>, o destino do comando será ignorado. Se o <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> não está definida, o elemento com o foco do teclado será o destino do comando.  
  
-   <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>é um tipo de dados definido pelo usuário usado para passar informações para os manipuladores de implementar o comando.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as classes que implementam <xref:System.Windows.Input.ICommandSource> são <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Documents.Hyperlink>, e <xref:System.Windows.Input.InputBinding>.  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, e <xref:System.Windows.Documents.Hyperlink> invocar um comando quando eles são clicados e uma <xref:System.Windows.Input.InputBinding> invoca um comando quando o <xref:System.Windows.Input.InputGesture> associado é realizado.  
  
 O exemplo a seguir mostra como usar um <xref:System.Windows.Controls.MenuItem> em uma <xref:System.Windows.Controls.ContextMenu> como uma fonte de comando para o <xref:System.Windows.Input.ApplicationCommands.Properties%2A> comando.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 Normalmente, uma fonte de comando escutará o <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> evento.  Esse evento informa à fonte de comando que a capacidade do comando de executar o destino do comando atual pode ter sido alterada.  A fonte de comando pode consultar o status atual do <xref:System.Windows.Input.RoutedCommand> usando o <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> método.  Em seguida, ela poderá ser desabilitada se não for possível executar o comando.  Um exemplo disso é um <xref:System.Windows.Controls.MenuItem> se retirando quando não é possível executar um comando.  
  
 Um <xref:System.Windows.Input.InputGesture> pode ser usado como uma fonte de comando.  Dois tipos de gestos de entrada no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são o <xref:System.Windows.Input.KeyGesture> e <xref:System.Windows.Input.MouseGesture>.  Você pode pensar um <xref:System.Windows.Input.KeyGesture> como um atalho de teclado, como CTRL + C.  Um <xref:System.Windows.Input.KeyGesture> é composta de uma <xref:System.Windows.Input.Key> e um conjunto de <xref:System.Windows.Input.ModifierKeys>.  Um <xref:System.Windows.Input.MouseGesture> é composta de uma <xref:System.Windows.Input.MouseAction> e um conjunto opcional de <xref:System.Windows.Input.ModifierKeys>.  
  
 Para que um <xref:System.Windows.Input.InputGesture> para agir como uma fonte de comando, ele deve ser associado um comando. Existem algumas maneiras de fazer isso.  Uma maneira é usar um <xref:System.Windows.Input.InputBinding>.  
  
 O exemplo a seguir mostra como criar um <xref:System.Windows.Input.KeyBinding> entre um <xref:System.Windows.Input.KeyGesture> e um <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Outra maneira de associar um <xref:System.Windows.Input.InputGesture> para um <xref:System.Windows.Input.RoutedCommand> é adicionar a <xref:System.Windows.Input.InputGesture> para o <xref:System.Windows.Input.InputGestureCollection> no <xref:System.Windows.Input.RoutedCommand>.  
  
 O exemplo a seguir mostra como adicionar um <xref:System.Windows.Input.KeyGesture> para o <xref:System.Windows.Input.InputGestureCollection> de um <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### <a name="commandbinding"></a>CommandBinding  
 Um <xref:System.Windows.Input.CommandBinding> associa um comando com os manipuladores de eventos que implementam o comando.  
  
 O <xref:System.Windows.Input.CommandBinding> classe contém um <xref:System.Windows.Input.CommandBinding.Command%2A> propriedade e <xref:System.Windows.Input.CommandBinding.PreviewExecuted>, <xref:System.Windows.Input.CommandBinding.Executed>, <xref:System.Windows.Input.CommandBinding.PreviewCanExecute>, e <xref:System.Windows.Input.CommandBinding.CanExecute> eventos.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A>o comando que o <xref:System.Windows.Input.CommandBinding> está sendo associado.  Os manipuladores de eventos que são anexados para o <xref:System.Windows.Input.CommandBinding.PreviewExecuted> e <xref:System.Windows.Input.CommandBinding.Executed> eventos implementam a lógica de comando.  Os manipuladores de eventos anexados para o <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> e <xref:System.Windows.Input.CommandBinding.CanExecute> eventos determinam se o comando pode executar o destino do comando atual.  
  
 O exemplo a seguir mostra como criar um <xref:System.Windows.Input.CommandBinding> na raiz <xref:System.Windows.Window> de um aplicativo.  O <xref:System.Windows.Input.CommandBinding> associa o <xref:System.Windows.Input.ApplicationCommands.Open%2A> com <xref:System.Windows.Input.CommandManager.Executed> e <xref:System.Windows.Input.CommandBinding.CanExecute> manipuladores.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Em seguida, o <xref:System.Windows.Input.ExecutedRoutedEventHandler> e um <xref:System.Windows.Input.CanExecuteRoutedEventHandler> são criados.  O <xref:System.Windows.Input.ExecutedRoutedEventHandler> abre uma <xref:System.Windows.MessageBox> que exibe uma cadeia de caracteres indicando que o comando foi executado.  O <xref:System.Windows.Input.CanExecuteRoutedEventHandler> define o <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> propriedade `true`.  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 Um <xref:System.Windows.Input.CommandBinding> está anexado a um objeto específico, como a raiz <xref:System.Windows.Window> do aplicativo ou um controle.  O objeto que o <xref:System.Windows.Input.CommandBinding> é anexado define o escopo da associação.  Por exemplo, um <xref:System.Windows.Input.CommandBinding> anexado a um predecessor do comando destino pode ser alcançado pelo <xref:System.Windows.Input.CommandBinding.Executed> evento, mas um <xref:System.Windows.Input.CommandBinding> anexado a um descendente do comando de destino não pode ser alcançado.  Esta é uma consequência direta da maneira como um <xref:System.Windows.RoutedEvent> túneis e bolhas do objeto que gera o evento.  
  
 Em algumas situações a <xref:System.Windows.Input.CommandBinding> está conectada ao destino de comando, como o <xref:System.Windows.Controls.TextBox> classe e o <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, e <xref:System.Windows.Input.ApplicationCommands.Paste%2A> comandos. Com muita frequência, no entanto, é mais conveniente anexar o <xref:System.Windows.Input.CommandBinding> a um predecessor do destino de comando, como o principal <xref:System.Windows.Window> ou o objeto de aplicativo, especialmente se o mesmo <xref:System.Windows.Input.CommandBinding> pode ser usado para vários destinos de comando.  São decisões de design que você deverá considerar no momento de criar sua infraestrutura de comando.  
  
<a name="Commane_Target"></a>   
### <a name="command-target"></a>Destino do comando  
 O destino do comando é o elemento no qual o comando é executado.  Com relação a um <xref:System.Windows.Input.RoutedCommand>, o destino do comando é o elemento no qual o roteamento do <xref:System.Windows.Input.CommandManager.Executed> e <xref:System.Windows.Input.CommandManager.CanExecute> inicia.  Conforme observado anteriormente, em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> propriedade <xref:System.Windows.Input.ICommandSource> só é aplicável quando o <xref:System.Windows.Input.ICommand> é um <xref:System.Windows.Input.RoutedCommand>.  Se o <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> é definido em um <xref:System.Windows.Input.ICommandSource> e o comando correspondente não é um <xref:System.Windows.Input.RoutedCommand>, o destino do comando será ignorado.  
  
 A fonte do comando pode definir explicitamente o destino do comando.  Se o destino do comando não for definido, o elemento com o foco do teclado será usado como destino do comando.  Uma das vantagens de usar o elemento com o foco do teclado como destino do comando é que ele permite que o desenvolvedor do aplicativo use a mesma fonte de comando para invocar um comando em vários destinos, sem a necessidade de controlar o destino do comando.  Por exemplo, se um <xref:System.Windows.Controls.MenuItem> invoca o **colar** comando em um aplicativo que tenha um <xref:System.Windows.Controls.TextBox> controle e um <xref:System.Windows.Controls.PasswordBox> controle, o destino pode ser o <xref:System.Windows.Controls.TextBox> ou <xref:System.Windows.Controls.PasswordBox> dependendo de qual controle tem foco do teclado.  
  
 O exemplo a seguir mostra como definir explicitamente o destino do comando na marcação e no code-behind.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### <a name="the-commandmanager"></a>O CommandManager  
 O <xref:System.Windows.Input.CommandManager> serve um número de comando funções relacionadas.  Ele fornece um conjunto de métodos estáticos para adicionar e remover <xref:System.Windows.Input.CommandManager.PreviewExecuted>, <xref:System.Windows.Input.CommandManager.Executed>, <xref:System.Windows.Input.CommandManager.PreviewCanExecute>, e <xref:System.Windows.Input.CommandManager.CanExecute> manipuladores de eventos para e de um elemento específico.  Ele fornece um meio para registrar <xref:System.Windows.Input.CommandBinding> e <xref:System.Windows.Input.InputBinding> objetos em uma classe específica.  O <xref:System.Windows.Input.CommandManager> também fornece um meio, por meio de <xref:System.Windows.Input.CommandManager.RequerySuggested> eventos, para notificar um comando quando ele deve gerar o <xref:System.Windows.Input.ICommand.CanExecuteChanged> evento.  
  
 O <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> método força a <xref:System.Windows.Input.CommandManager> para gerar o <xref:System.Windows.Input.CommandManager.RequerySuggested> evento.  Isso é útil em condições que devem desabilitar/habilitar um comando mas não são as condições que o <xref:System.Windows.Input.CommandManager> reconhece.  
  
<a name="Command_Library"></a>   
## <a name="command-library"></a>Biblioteca de comandos  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece um conjunto de comandos predefinidos.  A biblioteca de comandos consiste das seguintes classes: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Documents.EditingCommands>e o <xref:System.Windows.Input.ComponentCommands>.  Essas classes fornecem comandos como <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> e <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>, <xref:System.Windows.Input.MediaCommands.Play%2A>, <xref:System.Windows.Input.MediaCommands.Stop%2A>, e <xref:System.Windows.Input.MediaCommands.Pause%2A>.  
  
 Muitos desses comandos incluem um conjunto de associações de entrada padrão.  Se você especificar, por exemplo, que seu aplicativo manipula o comando de cópia, receberá automaticamente a associação de teclado “CTRL+C”. Também receberá associações para outros dispositivos de entrada, tais como informações de fala e gestos de caneta do [!INCLUDE[TLA2#tla_tpc](../../../../includes/tla2sharptla-tpc-md.md)].  
  
 Quando você faz referência a comandos nas várias bibliotecas de comandos usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], geralmente é possível omitir o nome de classe da classe da biblioteca que expõe a propriedade de comando estático. De modo geral, os nomes dos comandos são cadeias de caracteres não ambíguas; os tipos de propriedade existem para fornecer um agrupamento lógico de comandos, mas não são necessários para eliminar a ambiguidade. Por exemplo, é possível especificar o `Command="Cut"` em vez do `Command="ApplicationCommands.Cut"`, mais detalhado. Esse é um mecanismo de conveniência interna para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processador de comandos (mais precisamente, ele é um comportamento do conversor de tipo de <xref:System.Windows.Input.ICommand>, que o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] referências de processador em tempo de carregamento).  
  
<a name="creating_commands"></a>   
## <a name="creating-custom-commands"></a>Criando comandos personalizados  
 Se os comandos nas classes de biblioteca de comandos não satisfizerem suas necessidades, você poderá criar seus próprios comandos.  Há duas maneiras de criar um comando personalizado.  A primeira é para iniciar desde o início até e implementar o <xref:System.Windows.Input.ICommand> interface.  De outra forma e a abordagem mais comum, é criar um <xref:System.Windows.Input.RoutedCommand> ou <xref:System.Windows.Input.RoutedUICommand>.  
  
 Para obter um exemplo de criar um personalizado <xref:System.Windows.Input.RoutedCommand>, consulte [Create a Custom RoutedCommand Sample](http://go.microsoft.com/fwlink/?LinkID=159980).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Input.RoutedCommand>  
 <xref:System.Windows.Input.CommandBinding>  
 <xref:System.Windows.Input.InputBinding>  
 <xref:System.Windows.Input.CommandManager>  
 [Visão geral da entrada](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Implementar ICommandSource](../../../../docs/framework/wpf/advanced/how-to-implement-icommandsource.md)  
 [Como adicionar um comando a um MenuItem](http://msdn.microsoft.com/en-us/013d68a0-5373-4a68-bd91-5de574307370)  
 [Criar uma amostra personalizada do RoutedCommand](http://go.microsoft.com/fwlink/?LinkID=159980)
