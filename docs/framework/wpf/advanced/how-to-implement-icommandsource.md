---
title: Como implementar ICommandSource
ms.date: 12/05/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 755377d25a2deb48aa9da86d4182075e30763530
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345091"
---
# <a name="how-to-implement-icommandsource"></a><span data-ttu-id="3f681-102">Como implementar ICommandSource</span><span class="sxs-lookup"><span data-stu-id="3f681-102">How to: Implement ICommandSource</span></span>

<span data-ttu-id="3f681-103">Este exemplo mostra como criar uma fonte de comando implementando <xref:System.Windows.Input.ICommandSource>.</span><span class="sxs-lookup"><span data-stu-id="3f681-103">This example shows how to create a command source by implementing <xref:System.Windows.Input.ICommandSource>.</span></span> <span data-ttu-id="3f681-104">Uma fonte de comando é um objeto que sabe como invocar um comando.</span><span class="sxs-lookup"><span data-stu-id="3f681-104">A command source is an object that knows how to invoke a command.</span></span> <span data-ttu-id="3f681-105">A interface <xref:System.Windows.Input.ICommandSource> expõe três membros:</span><span class="sxs-lookup"><span data-stu-id="3f681-105">The <xref:System.Windows.Input.ICommandSource> interface exposes three members:</span></span>

- <span data-ttu-id="3f681-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: o comando que será invocado.</span><span class="sxs-lookup"><span data-stu-id="3f681-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: the command that will be invoked.</span></span>
- <span data-ttu-id="3f681-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: um tipo de dados definido pelo usuário que é passado da fonte de comando para o método que manipula o comando.</span><span class="sxs-lookup"><span data-stu-id="3f681-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: a user-defined data type which is passed from the command source to the method that handles the command.</span></span>
- <span data-ttu-id="3f681-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: o objeto no qual o comando está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="3f681-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: the object that the command is being executed on.</span></span>

<span data-ttu-id="3f681-109">Neste exemplo, é criada uma classe que herda do controle de <xref:System.Windows.Controls.Slider> e implementa a interface <xref:System.Windows.Input.ICommandSource>.</span><span class="sxs-lookup"><span data-stu-id="3f681-109">In this example, a class is created that inherits from the <xref:System.Windows.Controls.Slider> control and implements the  <xref:System.Windows.Input.ICommandSource> interface.</span></span>
  
## <a name="example"></a><span data-ttu-id="3f681-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f681-110">Example</span></span>

<span data-ttu-id="3f681-111">O WPF fornece várias classes que implementam <xref:System.Windows.Input.ICommandSource>, como <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>e <xref:System.Windows.Documents.Hyperlink>.</span><span class="sxs-lookup"><span data-stu-id="3f681-111">WPF provides a number of classes which implement <xref:System.Windows.Input.ICommandSource>, such as <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, and <xref:System.Windows.Documents.Hyperlink>.</span></span> <span data-ttu-id="3f681-112">Uma fonte de comandos define como se invoca um comando.</span><span class="sxs-lookup"><span data-stu-id="3f681-112">A command source defines how it invokes a command.</span></span> <span data-ttu-id="3f681-113">Essas classes invocam um comando quando eles são clicados e se tornam apenas uma fonte de comando quando sua propriedade <xref:System.Windows.Input.ICommandSource.Command%2A> é definida.</span><span class="sxs-lookup"><span data-stu-id="3f681-113">These classes invoke a command when they're clicked and they only become a command source when their <xref:System.Windows.Input.ICommandSource.Command%2A> property is set.</span></span>

<span data-ttu-id="3f681-114">Neste exemplo, você invocará o comando quando o controle deslizante for movido ou com mais precisão, quando a propriedade <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> for alterada.</span><span class="sxs-lookup"><span data-stu-id="3f681-114">In this example, you'll invoke the command when the slider is moved, or more accurately, when the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property is changed.</span></span>

<span data-ttu-id="3f681-115">A seguir está a definição de classe:</span><span class="sxs-lookup"><span data-stu-id="3f681-115">The following is the class definition:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

<span data-ttu-id="3f681-116">A próxima etapa é implementar os membros do <xref:System.Windows.Input.ICommandSource>.</span><span class="sxs-lookup"><span data-stu-id="3f681-116">The next step is to implement the <xref:System.Windows.Input.ICommandSource> members.</span></span> <span data-ttu-id="3f681-117">Neste exemplo, as propriedades são implementadas como objetos <xref:System.Windows.DependencyProperty>.</span><span class="sxs-lookup"><span data-stu-id="3f681-117">In this example, the properties are implemented as <xref:System.Windows.DependencyProperty> objects.</span></span> <span data-ttu-id="3f681-118">Isso permite que as propriedades usem associação de dados.</span><span class="sxs-lookup"><span data-stu-id="3f681-118">This enables the properties to use data binding.</span></span> <span data-ttu-id="3f681-119">Para obter mais informações sobre a classe <xref:System.Windows.DependencyProperty>, consulte [visão geral das propriedades de dependência](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3f681-119">For more information about the <xref:System.Windows.DependencyProperty> class, see the [Dependency Properties Overview](dependency-properties-overview.md).</span></span> <span data-ttu-id="3f681-120">Para obter mais informações sobre associação de dados, consulte [Visão geral de associação de dados](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3f681-120">For more information about data binding, see the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="3f681-121">Somente a propriedade <xref:System.Windows.Input.ICommandSource.Command%2A> é mostrada aqui.</span><span class="sxs-lookup"><span data-stu-id="3f681-121">Only the <xref:System.Windows.Input.ICommandSource.Command%2A> property is shown here.</span></span>
 
[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
<span data-ttu-id="3f681-122">Este é o <xref:System.Windows.DependencyProperty> retorno de chamada de alteração:</span><span class="sxs-lookup"><span data-stu-id="3f681-122">The following is the <xref:System.Windows.DependencyProperty> change callback:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

<span data-ttu-id="3f681-123">A próxima etapa é adicionar e remover o comando que está associado à fonte de comando.</span><span class="sxs-lookup"><span data-stu-id="3f681-123">The next step is to add and remove the command which is associated with the command source.</span></span> <span data-ttu-id="3f681-124">A propriedade <xref:System.Windows.Input.ICommandSource.Command%2A> não pode simplesmente ser substituída quando um novo comando é adicionado, porque os manipuladores de eventos associados ao comando anterior, se houver um, devem ser removidos primeiro.</span><span class="sxs-lookup"><span data-stu-id="3f681-124">The <xref:System.Windows.Input.ICommandSource.Command%2A> property cannot simply be overwritten when a new command is added, because the event handlers associated with the previous command, if there was one, must be removed first.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

<span data-ttu-id="3f681-125">A próxima etapa é criar uma lógica para o manipulador de <xref:System.Windows.Input.ICommand.CanExecuteChanged>.</span><span class="sxs-lookup"><span data-stu-id="3f681-125">The next step is to create logic for the <xref:System.Windows.Input.ICommand.CanExecuteChanged> handler.</span></span>

<span data-ttu-id="3f681-126">O evento <xref:System.Windows.Input.ICommand.CanExecuteChanged> notifica a fonte de comando que a capacidade do comando para executar no destino do comando atual pode ter sido alterada.</span><span class="sxs-lookup"><span data-stu-id="3f681-126">The <xref:System.Windows.Input.ICommand.CanExecuteChanged> event notifies the command source that the ability of the command to execute on the current command target may have changed.</span></span> <span data-ttu-id="3f681-127">Quando uma fonte de comando recebe esse evento, ela normalmente chama o método <xref:System.Windows.Input.ICommand.CanExecute%2A> no comando.</span><span class="sxs-lookup"><span data-stu-id="3f681-127">When a command source receives this event, it typically calls the <xref:System.Windows.Input.ICommand.CanExecute%2A> method on the command.</span></span> <span data-ttu-id="3f681-128">Se o comando não puder executar no destino do comando atual, geralmente, a fonte de comando se desabilitará automaticamente.</span><span class="sxs-lookup"><span data-stu-id="3f681-128">If the command cannot execute on the current command target, the command source will typically disable itself.</span></span> <span data-ttu-id="3f681-129">Se o comando puder executar no destino do comando atual, geralmente, a fonte de comando se habilitará por conta própria.</span><span class="sxs-lookup"><span data-stu-id="3f681-129">If the command can execute on the current command target, the command source will typically enable itself.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

<span data-ttu-id="3f681-130">A última etapa é o método <xref:System.Windows.Input.ICommand.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="3f681-130">The last step is the <xref:System.Windows.Input.ICommand.Execute%2A> method.</span></span> <span data-ttu-id="3f681-131">Se o comando for um <xref:System.Windows.Input.RoutedCommand>, o método <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> será chamado; caso contrário, o método <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> será chamado.</span><span class="sxs-lookup"><span data-stu-id="3f681-131">If the command is a <xref:System.Windows.Input.RoutedCommand>, the <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> method is called; otherwise, the <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> method is called.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a><span data-ttu-id="3f681-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="3f681-132">See also</span></span>

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [<span data-ttu-id="3f681-133">Visão geral dos comandos</span><span class="sxs-lookup"><span data-stu-id="3f681-133">Commanding Overview</span></span>](commanding-overview.md)
