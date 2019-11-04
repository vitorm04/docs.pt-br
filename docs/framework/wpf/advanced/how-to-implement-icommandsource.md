---
title: Como implementar ICommandSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 974b145a125a158bcafff93f8e9bc11001e00bf1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453586"
---
# <a name="how-to-implement-icommandsource"></a>Como implementar ICommandSource
Este exemplo mostra como criar uma fonte de comando implementando <xref:System.Windows.Input.ICommandSource>.  Uma fonte de comando é um objeto que sabe como invocar um comando.  A interface <xref:System.Windows.Input.ICommandSource> expõe três membros: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>e <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>.  <xref:System.Windows.Input.ICommandSource.Command%2A> é o comando que será invocado. O <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> é um tipo de dados definido pelo usuário que é passado da fonte de comando para o método que manipula o comando. O <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> é o objeto no qual o comando está sendo executado.  
  
 Neste exemplo, é criada uma classe que faz a subclasse do controle de <xref:System.Windows.Controls.Slider> e implementa <xref:System.Windows.Input.ICommandSource>.  
  
## <a name="example"></a>Exemplo  
 o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece várias classes que implementam <xref:System.Windows.Input.ICommandSource>, como <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>e <xref:System.Windows.Controls.ListBoxItem>.  Uma fonte de comandos define como se invoca um comando.   <xref:System.Windows.Controls.Button> e <xref:System.Windows.Controls.MenuItem> invocar um comando quando eles forem clicados.  Uma <xref:System.Windows.Controls.ListBoxItem> invoca um comando quando ele é clicado duas vezes. Essas classes se tornam apenas uma fonte de comando quando sua propriedade <xref:System.Windows.Input.ICommandSource.Command%2A> é definida.  
  
 Para este exemplo, invocaremos o comando quando o controle deslizante for movido, ou mais precisamente, quando a propriedade <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> for alterada.  
  
 A seguir está a definição de classe.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 A próxima etapa é implementar os membros do <xref:System.Windows.Input.ICommandSource>.  Neste exemplo, as propriedades são implementadas como objetos <xref:System.Windows.DependencyProperty>.  Isso permite que as propriedades usem associação de dados.  Para obter mais informações sobre a classe <xref:System.Windows.DependencyProperty>, consulte [visão geral das propriedades de dependência](dependency-properties-overview.md).  Para obter mais informações sobre associação de dados, consulte [Visão geral de associação de dados](../../../desktop-wpf/data/data-binding-overview.md).  
  
 Somente a propriedade <xref:System.Windows.Input.ICommandSource.Command%2A> é mostrada aqui.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 Este é o <xref:System.Windows.DependencyProperty> retorno de chamada de alteração.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 A próxima etapa é adicionar e remover o comando que está associado à fonte de comando.  A propriedade <xref:System.Windows.Input.ICommandSource.Command%2A> não pode simplesmente ser substituída quando um novo comando é adicionado, porque os manipuladores de eventos associados ao comando anterior, se houver um, devem ser removidos primeiro.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 A última etapa é criar uma lógica para o manipulador de <xref:System.Windows.Input.ICommand.CanExecuteChanged> e o método <xref:System.Windows.Input.ICommand.Execute%2A>.  
  
 O evento <xref:System.Windows.Input.ICommand.CanExecuteChanged> notifica a fonte de comando que a capacidade do comando para executar no destino do comando atual pode ter sido alterada.  Quando uma fonte de comando recebe esse evento, ela normalmente chama o método <xref:System.Windows.Input.ICommand.CanExecute%2A> no comando.  Se o comando não puder executar no destino do comando atual, geralmente, a fonte de comando se desabilitará automaticamente.  Se o comando puder executar no destino do comando atual, geralmente, a fonte de comando se habilitará por conta própria.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 A última etapa é o método <xref:System.Windows.Input.ICommand.Execute%2A>.  Se o comando for um <xref:System.Windows.Input.RoutedCommand>, o método <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> será chamado; caso contrário, o método <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> será chamado.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [Visão geral de comandos](commanding-overview.md)
