---
title: Como implementar ICommandSource
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
helpviewer_keywords: ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bdff5ebeb51daff4e8848e9a7c8282c2eee6f208
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-icommandsource"></a>Como implementar ICommandSource
Este exemplo mostra como criar uma fonte de comandos, implementando <xref:System.Windows.Input.ICommandSource>.  Uma fonte de comando é um objeto que sabe como invocar um comando.  O <xref:System.Windows.Input.ICommandSource> interface expõe três membros: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>, e <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>.  <xref:System.Windows.Input.ICommandSource.Command%2A>é o comando que será chamado. O <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> é um tipo de dados definido pelo usuário que é passado da fonte de comandos para o método que trata o comando. O <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> é o objeto que o comando está sendo executado.  
  
 Neste exemplo, uma classe é criada que herda do <xref:System.Windows.Controls.Slider> controle e implementa <xref:System.Windows.Input.ICommandSource>.  
  
## <a name="example"></a>Exemplo  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Fornece um número de classes que implementam <xref:System.Windows.Input.ICommandSource>, como <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, e <xref:System.Windows.Controls.ListBoxItem>.  Uma fonte de comandos define como se invoca um comando.   <xref:System.Windows.Controls.Button>e <xref:System.Windows.Controls.MenuItem> invocar um comando quando eles são clicados.  Um <xref:System.Windows.Controls.ListBoxItem> invoca um comando quando é clicada duas vezes. Essas classes tornam-se apenas um comando de origem quando seus <xref:System.Windows.Input.ICommandSource.Command%2A> está definida.  
  
 Para esse exemplo nós iremos invocar o comando quando o controle deslizante for movido, ou mais precisamente, quando o <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> propriedade é alterada.  
  
 A seguir está a definição de classe.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 A próxima etapa é implementar o <xref:System.Windows.Input.ICommandSource> membros.  Neste exemplo, as propriedades são implementadas como <xref:System.Windows.DependencyProperty> objetos.  Isso permite que as propriedades usem associação de dados.  Para obter mais informações sobre o <xref:System.Windows.DependencyProperty> de classe, consulte o [visão geral de propriedades de dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  Para obter mais informações sobre associação de dados, consulte [Visão geral de associação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Somente o <xref:System.Windows.Input.ICommandSource.Command%2A> propriedade é mostrada aqui.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 A seguir está o <xref:System.Windows.DependencyProperty> alterar o retorno de chamada.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 A próxima etapa é adicionar e remover o comando que está associado à fonte de comando.  O <xref:System.Windows.Input.ICommandSource.Command%2A> propriedade não pode ser simplesmente sobrescrita quando um comando novo é adicionado, pois os manipuladores de eventos associados ao comando anterior, se houver algum, devem ser removidas primeiro.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 A última etapa é criar a lógica para o <xref:System.Windows.Input.ICommand.CanExecuteChanged> manipulador e <xref:System.Windows.Input.ICommand.Execute%2A> método.  
  
 O <xref:System.Windows.Input.ICommand.CanExecuteChanged> evento informa a fonte de comando que a capacidade do comando a ser executado no seu atual destino pode ter sido alterado.  Quando uma fonte de comandos recebe esse evento, ela normalmente chama o <xref:System.Windows.Input.ICommand.CanExecute%2A> método no comando.  Se o comando não puder executar no destino do comando atual, geralmente, a fonte de comando se desabilitará automaticamente.  Se o comando puder executar no destino do comando atual, geralmente, a fonte de comando se habilitará por conta própria.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 A última etapa é o <xref:System.Windows.Input.ICommand.Execute%2A> método.  Se o comando for um <xref:System.Windows.Input.RoutedCommand>, o <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> método é chamado; caso contrário, o <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> método é chamado.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Input.ICommandSource>  
 <xref:System.Windows.Input.ICommand>  
 <xref:System.Windows.Input.RoutedCommand>  
 [Visão geral dos comandos](../../../../docs/framework/wpf/advanced/commanding-overview.md)
