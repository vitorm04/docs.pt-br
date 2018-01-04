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
ms.workload: dotnet
ms.openlocfilehash: b27f8544a44a252eb1a1afd6e096f303360c14e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-a-command"></a><span data-ttu-id="68484-102">Como habilitar um comando</span><span class="sxs-lookup"><span data-stu-id="68484-102">How to: Enable a Command</span></span>
<span data-ttu-id="68484-103">O exemplo a seguir demonstra como usar comandos em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="68484-103">The following example demonstrates how to use commanding in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  <span data-ttu-id="68484-104">O exemplo mostra como associar um <xref:System.Windows.Input.RoutedCommand> para um <xref:System.Windows.Controls.Button>, crie um <xref:System.Windows.Input.CommandBinding>e criar manipuladores de eventos que implementam o <xref:System.Windows.Input.RoutedCommand>.</span><span class="sxs-lookup"><span data-stu-id="68484-104">The example shows how to associate a <xref:System.Windows.Input.RoutedCommand> to a <xref:System.Windows.Controls.Button>, create a <xref:System.Windows.Input.CommandBinding>, and create the event handlers which implement the <xref:System.Windows.Input.RoutedCommand>.</span></span>  <span data-ttu-id="68484-105">Para obter mais informações sobre comandos, consulte [Visão geral de comandos](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="68484-105">For more information on commanding, see the [Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68484-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68484-106">Example</span></span>  
 <span data-ttu-id="68484-107">A primeira seção de código cria o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], que consiste de um <xref:System.Windows.Controls.Button> e um <xref:System.Windows.Controls.StackPanel>e cria um <xref:System.Windows.Input.CommandBinding> que associa o manipulador de comandos com o <xref:System.Windows.Input.RoutedCommand>.</span><span class="sxs-lookup"><span data-stu-id="68484-107">The first section of code creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], which consists of a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.StackPanel>, and creates a <xref:System.Windows.Input.CommandBinding> that associates the command handlers with the <xref:System.Windows.Input.RoutedCommand>.</span></span>  
  
 <span data-ttu-id="68484-108">O <xref:System.Windows.Input.ICommandSource.Command%2A> propriedade o <xref:System.Windows.Controls.Button> está associado a <xref:System.Windows.Input.ApplicationCommands.Close%2A> comando.</span><span class="sxs-lookup"><span data-stu-id="68484-108">The <xref:System.Windows.Input.ICommandSource.Command%2A> property of the <xref:System.Windows.Controls.Button> is associated with the <xref:System.Windows.Input.ApplicationCommands.Close%2A> command.</span></span>  
  
 <span data-ttu-id="68484-109">O <xref:System.Windows.Input.CommandBinding> é adicionada para o <xref:System.Windows.Input.CommandBindingCollection> da raiz <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="68484-109">The <xref:System.Windows.Input.CommandBinding> is added to the <xref:System.Windows.Input.CommandBindingCollection> of the root <xref:System.Windows.Window>.</span></span> <span data-ttu-id="68484-110">O <xref:System.Windows.Input.CommandBinding.Executed> e <xref:System.Windows.Input.CommandBinding.CanExecute> manipuladores de eventos são anexados a essa associação e associados a <xref:System.Windows.Input.ApplicationCommands.Close%2A> comando.</span><span class="sxs-lookup"><span data-stu-id="68484-110">The <xref:System.Windows.Input.CommandBinding.Executed> and <xref:System.Windows.Input.CommandBinding.CanExecute> event handlers are attached to this binding and associated with the <xref:System.Windows.Input.ApplicationCommands.Close%2A> command.</span></span>  
  
 <span data-ttu-id="68484-111">Sem o <xref:System.Windows.Input.CommandBinding> não existe nenhuma lógica de comando, somente um mecanismo para invocar o comando.</span><span class="sxs-lookup"><span data-stu-id="68484-111">Without the <xref:System.Windows.Input.CommandBinding> there is no command logic, only a mechanism to invoke the command.</span></span>  <span data-ttu-id="68484-112">Quando o <xref:System.Windows.Controls.Button> é clicado, o <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> é gerado no seu destino seguido de <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.</span><span class="sxs-lookup"><span data-stu-id="68484-112">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> is raised on the command target followed by the <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.</span></span>  <span data-ttu-id="68484-113">Esses eventos atravessam a árvore de elementos procurando um <xref:System.Windows.Input.CommandBinding> para esse comando específico.</span><span class="sxs-lookup"><span data-stu-id="68484-113">These events traverse the element tree looking for a <xref:System.Windows.Input.CommandBinding> for that particular command.</span></span>  <span data-ttu-id="68484-114">Vale a pena observar que porque <xref:System.Windows.RoutedEvent> túnel e bolha por meio da árvore de elementos, cuidado em onde o <xref:System.Windows.Input.CommandBinding> é colocado.</span><span class="sxs-lookup"><span data-stu-id="68484-114">It is worth noting that because <xref:System.Windows.RoutedEvent> tunnel and bubble through the element tree, care must be taken in where the <xref:System.Windows.Input.CommandBinding> is put.</span></span>   <span data-ttu-id="68484-115">Se o <xref:System.Windows.Input.CommandBinding> está em um irmão do comando alvo ou outro nó que não está na rota do <xref:System.Windows.RoutedEvent>, o <xref:System.Windows.Input.CommandBinding> não será acessado.</span><span class="sxs-lookup"><span data-stu-id="68484-115">If the <xref:System.Windows.Input.CommandBinding> is on a sibling of the command target or another node that is not on the route of the <xref:System.Windows.RoutedEvent>, the <xref:System.Windows.Input.CommandBinding> will not be accessed.</span></span>  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 <span data-ttu-id="68484-116">A próxima seção de código implementa o <xref:System.Windows.Input.CommandManager.Executed> e <xref:System.Windows.Input.CommandBinding.CanExecute> manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="68484-116">The next section of code implements the <xref:System.Windows.Input.CommandManager.Executed> and <xref:System.Windows.Input.CommandBinding.CanExecute> event handlers.</span></span>  
  
 <span data-ttu-id="68484-117">O <xref:System.Windows.Input.CommandManager.Executed> manipulador chama um método para fechar o arquivo aberto.</span><span class="sxs-lookup"><span data-stu-id="68484-117">The <xref:System.Windows.Input.CommandManager.Executed> handler calls a method to close the open file.</span></span>  <span data-ttu-id="68484-118">O <xref:System.Windows.Input.CommandBinding.CanExecute> manipulador chama um método para determinar se um arquivo está aberto.</span><span class="sxs-lookup"><span data-stu-id="68484-118">The <xref:System.Windows.Input.CommandBinding.CanExecute> handler calls a method to determine whether a file is open.</span></span>  <span data-ttu-id="68484-119">Se um arquivo estiver aberto, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> é definido como `true`; caso contrário, ele é definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="68484-119">If a file is open, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> is set to `true`; otherwise, it is set to `false`.</span></span>  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a><span data-ttu-id="68484-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68484-120">See Also</span></span>  
 [<span data-ttu-id="68484-121">Visão geral dos comandos</span><span class="sxs-lookup"><span data-stu-id="68484-121">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)
