---
title: Como implementar ICommandSource
ms.date: 12/05/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 6c18e0b77ec53d9bd3e7ce610f2940effe603c88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174687"
---
# <a name="how-to-implement-icommandsource"></a>Como implementar ICommandSource

Este exemplo mostra como criar uma <xref:System.Windows.Input.ICommandSource>fonte de comando implementando . Uma fonte de comando é um objeto que sabe como invocar um comando. A <xref:System.Windows.Input.ICommandSource> interface expõe três membros:

- <xref:System.Windows.Input.ICommandSource.Command%2A>: o comando que será invocado.
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: um tipo de dados definido pelo usuário que é passado da fonte de comando para o método que lida com o comando.
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: o objeto em que o comando está sendo executado.

Neste exemplo, é criada uma classe que <xref:System.Windows.Controls.Slider> herda do <xref:System.Windows.Input.ICommandSource> controle e implementa a interface.
  
## <a name="example"></a>Exemplo

O WPF fornece uma <xref:System.Windows.Input.ICommandSource>série de <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.MenuItem>classes <xref:System.Windows.Documents.Hyperlink>que implementam, tais como , e . Uma fonte de comandos define como se invoca um comando. Essas classes invocam um comando quando são clicadas e <xref:System.Windows.Input.ICommandSource.Command%2A> só se tornam uma fonte de comando quando sua propriedade é definida.

Neste exemplo, você invocará o comando quando o controle deslizante for <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> movido, ou mais precisamente, quando a propriedade for alterada.

A seguir está a definição de classe:

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

O próximo passo é <xref:System.Windows.Input.ICommandSource> implementar os membros. Neste exemplo, as propriedades <xref:System.Windows.DependencyProperty> são implementadas como objetos. Isso permite que as propriedades usem associação de dados. Para obter mais <xref:System.Windows.DependencyProperty> informações sobre a classe, consulte a [visão geral das propriedades de dependência](dependency-properties-overview.md). Para obter mais informações sobre associação de dados, consulte [Visão geral de associação de dados](../../../desktop-wpf/data/data-binding-overview.md).

Apenas <xref:System.Windows.Input.ICommandSource.Command%2A> a propriedade é mostrada aqui.

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
A seguir <xref:System.Windows.DependencyProperty> está o retorno de chamada de alteração:

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

A próxima etapa é adicionar e remover o comando que está associado à fonte de comando. A <xref:System.Windows.Input.ICommandSource.Command%2A> propriedade não pode simplesmente ser substituída quando um novo comando é adicionado, porque os manipuladores de eventos associados ao comando anterior, se houve um, devem ser removidos primeiro.

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

O próximo passo é criar <xref:System.Windows.Input.ICommand.CanExecuteChanged> lógica para o manipulador.

O <xref:System.Windows.Input.ICommand.CanExecuteChanged> evento notifica a fonte de comando de que a capacidade do comando de executar no alvo de comando atual pode ter mudado. Quando uma fonte de comando recebe esse <xref:System.Windows.Input.ICommand.CanExecute%2A> evento, ele normalmente chama o método no comando. Se o comando não puder executar no destino do comando atual, geralmente, a fonte de comando se desabilitará automaticamente. Se o comando puder executar no destino do comando atual, geralmente, a fonte de comando se habilitará por conta própria.

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

O último passo <xref:System.Windows.Input.ICommand.Execute%2A> é o método. Se o comando <xref:System.Windows.Input.RoutedCommand>for <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> um , o método é chamado; caso contrário, <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> o método é chamado.

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [Visão geral dos comandos](commanding-overview.md)
