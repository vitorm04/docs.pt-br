---
title: 'Como: Criar um RoutedCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
ms.openlocfilehash: 4119a762bd0db63108d08a9db9367e367adb6b58
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372077"
---
# <a name="how-to-create-a-routedcommand"></a>Como: Criar um RoutedCommand
Este exemplo mostra como criar um personalizado <xref:System.Windows.Input.RoutedCommand> e como implementar o comando personalizado, criando um <xref:System.Windows.Input.ExecutedRoutedEventHandler> e uma <xref:System.Windows.Input.CanExecuteRoutedEventHandler> e anexá-los para um <xref:System.Windows.Input.CommandBinding>.  Para obter mais informações sobre comandos, consulte [Visão geral de comandos](commanding-overview.md).  
  
## <a name="example"></a>Exemplo  
 A primeira etapa na criação de um <xref:System.Windows.Input.RoutedCommand> é definir o comando e criar uma instância dele.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 Para usar o comando em um aplicativo, os manipuladores de eventos que definem o que o comando faz devem ser criados  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 Em seguida, um <xref:System.Windows.Input.CommandBinding> é criado que associa o comando com os manipuladores de eventos. O <xref:System.Windows.Input.CommandBinding> é criado em um objeto específico.  Este objeto define o escopo do <xref:System.Windows.Input.CommandBinding> na árvore de elementos  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 A etapa final é invocar o comando.  Uma maneira de invocar um comando é associá-lo com um <xref:System.Windows.Input.ICommandSource>, como um <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 Quando o botão é clicado, o <xref:System.Windows.Input.RoutedCommand.Execute%2A> método no personalizado <xref:System.Windows.Input.RoutedCommand> é chamado.  O <xref:System.Windows.Input.RoutedCommand> gera a <xref:System.Windows.Input.CommandManager.PreviewExecuted> e <xref:System.Windows.Input.CommandManager.Executed> eventos roteados.  Esses eventos atravessam a árvore de elementos procurando um <xref:System.Windows.Input.CommandBinding> para esse determinado comando.  Se um <xref:System.Windows.Input.CommandBinding> for encontrado, o <xref:System.Windows.Input.ExecutedRoutedEventHandler> associado <xref:System.Windows.Input.CommandBinding> é chamado.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Input.RoutedCommand>
- [Visão geral de comandos](commanding-overview.md)
