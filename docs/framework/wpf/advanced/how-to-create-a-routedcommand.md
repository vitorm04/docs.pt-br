---
title: 'Como: Criar um RoutedCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
ms.openlocfilehash: d433658a3039c262d2f682eff09df646d978018c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776474"
---
# <a name="how-to-create-a-routedcommand"></a><span data-ttu-id="2293b-102">Como: Criar um RoutedCommand</span><span class="sxs-lookup"><span data-stu-id="2293b-102">How to: Create a RoutedCommand</span></span>
<span data-ttu-id="2293b-103">Este exemplo mostra como criar um personalizado <xref:System.Windows.Input.RoutedCommand> e como implementar o comando personalizado, criando um <xref:System.Windows.Input.ExecutedRoutedEventHandler> e uma <xref:System.Windows.Input.CanExecuteRoutedEventHandler> e anexá-los para um <xref:System.Windows.Input.CommandBinding>.</span><span class="sxs-lookup"><span data-stu-id="2293b-103">This example shows how to create a custom <xref:System.Windows.Input.RoutedCommand> and how to implement the custom command by creating a <xref:System.Windows.Input.ExecutedRoutedEventHandler> and a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> and attaching them to a <xref:System.Windows.Input.CommandBinding>.</span></span>  <span data-ttu-id="2293b-104">Para obter mais informações sobre comandos, consulte [Visão geral de comandos](commanding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2293b-104">For more information on commanding, see the [Commanding Overview](commanding-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2293b-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2293b-105">Example</span></span>  
 <span data-ttu-id="2293b-106">A primeira etapa na criação de um <xref:System.Windows.Input.RoutedCommand> é definir o comando e criar uma instância dele.</span><span class="sxs-lookup"><span data-stu-id="2293b-106">The first step in creating a <xref:System.Windows.Input.RoutedCommand> is defining the command and instantiating it.</span></span>  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 <span data-ttu-id="2293b-107">Para usar o comando em um aplicativo, os manipuladores de eventos que definem o que o comando faz devem ser criados</span><span class="sxs-lookup"><span data-stu-id="2293b-107">In order to use the command in an application, event handlers which define what the command does must be created</span></span>  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 <span data-ttu-id="2293b-108">Em seguida, um <xref:System.Windows.Input.CommandBinding> é criado que associa o comando com os manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="2293b-108">Next, a  <xref:System.Windows.Input.CommandBinding> is created which associates the command with the event handlers.</span></span> <span data-ttu-id="2293b-109">O <xref:System.Windows.Input.CommandBinding> é criado em um objeto específico.</span><span class="sxs-lookup"><span data-stu-id="2293b-109">The <xref:System.Windows.Input.CommandBinding> is created on a specific object.</span></span>  <span data-ttu-id="2293b-110">Este objeto define o escopo do <xref:System.Windows.Input.CommandBinding> na árvore de elementos</span><span class="sxs-lookup"><span data-stu-id="2293b-110">This object defines the scope of the <xref:System.Windows.Input.CommandBinding> in the element tree</span></span>  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 <span data-ttu-id="2293b-111">A etapa final é invocar o comando.</span><span class="sxs-lookup"><span data-stu-id="2293b-111">The final step is invoking the command.</span></span>  <span data-ttu-id="2293b-112">Uma maneira de invocar um comando é associá-lo com um <xref:System.Windows.Input.ICommandSource>, como um <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="2293b-112">One way to invoke a command is to associate it with a <xref:System.Windows.Input.ICommandSource>, such as a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 <span data-ttu-id="2293b-113">Quando o botão é clicado, o <xref:System.Windows.Input.RoutedCommand.Execute%2A> método no personalizado <xref:System.Windows.Input.RoutedCommand> é chamado.</span><span class="sxs-lookup"><span data-stu-id="2293b-113">When the Button is clicked, the <xref:System.Windows.Input.RoutedCommand.Execute%2A> method on the custom <xref:System.Windows.Input.RoutedCommand> is called.</span></span>  <span data-ttu-id="2293b-114">O <xref:System.Windows.Input.RoutedCommand> gera a <xref:System.Windows.Input.CommandManager.PreviewExecuted> e <xref:System.Windows.Input.CommandManager.Executed> eventos roteados.</span><span class="sxs-lookup"><span data-stu-id="2293b-114">The <xref:System.Windows.Input.RoutedCommand> raises the <xref:System.Windows.Input.CommandManager.PreviewExecuted> and <xref:System.Windows.Input.CommandManager.Executed> routed events.</span></span>  <span data-ttu-id="2293b-115">Esses eventos atravessam a árvore de elementos procurando um <xref:System.Windows.Input.CommandBinding> para esse determinado comando.</span><span class="sxs-lookup"><span data-stu-id="2293b-115">These events traverse the element tree looking for a <xref:System.Windows.Input.CommandBinding> for this particular command.</span></span>  <span data-ttu-id="2293b-116">Se um <xref:System.Windows.Input.CommandBinding> for encontrado, o <xref:System.Windows.Input.ExecutedRoutedEventHandler> associado <xref:System.Windows.Input.CommandBinding> é chamado.</span><span class="sxs-lookup"><span data-stu-id="2293b-116">If a <xref:System.Windows.Input.CommandBinding> is found, the <xref:System.Windows.Input.ExecutedRoutedEventHandler> associated with <xref:System.Windows.Input.CommandBinding> is called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2293b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2293b-117">See also</span></span>

- <xref:System.Windows.Input.RoutedCommand>
- [<span data-ttu-id="2293b-118">Visão geral de comandos</span><span class="sxs-lookup"><span data-stu-id="2293b-118">Commanding Overview</span></span>](commanding-overview.md)
