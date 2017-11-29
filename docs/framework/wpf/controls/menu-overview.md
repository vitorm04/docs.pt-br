---
title: "Visão geral do menu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81611e7c5f509314b10e3188106870bdc67dfb0e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="menu-overview"></a><span data-ttu-id="582f8-102">Visão geral do menu</span><span class="sxs-lookup"><span data-stu-id="582f8-102">Menu Overview</span></span>
<span data-ttu-id="582f8-103">O <xref:System.Windows.Controls.Menu> classe permite que você organize elementos associados com comandos e manipuladores de eventos em ordem hierárquica.</span><span class="sxs-lookup"><span data-stu-id="582f8-103">The <xref:System.Windows.Controls.Menu> class enables you to organize elements associated with commands and event handlers in a hierarchical order.</span></span> <span data-ttu-id="582f8-104">Cada <xref:System.Windows.Controls.Menu> elemento contém uma coleção de <xref:System.Windows.Controls.MenuItem> elementos.</span><span class="sxs-lookup"><span data-stu-id="582f8-104">Each <xref:System.Windows.Controls.Menu> element contains a collection of <xref:System.Windows.Controls.MenuItem> elements.</span></span>  
  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a><span data-ttu-id="582f8-105">Controle de Menu</span><span class="sxs-lookup"><span data-stu-id="582f8-105">Menu Control</span></span>  
 <span data-ttu-id="582f8-106">O <xref:System.Windows.Controls.Menu> controle apresenta uma lista de itens que especificam comandos ou opções para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="582f8-106">The <xref:System.Windows.Controls.Menu> control presents a list of items that specify commands or options for an application.</span></span> <span data-ttu-id="582f8-107">Geralmente, clicar em um <xref:System.Windows.Controls.MenuItem> abre um submenu ou faz com que um aplicativo executar um comando.</span><span class="sxs-lookup"><span data-stu-id="582f8-107">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a><span data-ttu-id="582f8-108">Criando Menus</span><span class="sxs-lookup"><span data-stu-id="582f8-108">Creating Menus</span></span>  
 <span data-ttu-id="582f8-109">O exemplo a seguir cria um <xref:System.Windows.Controls.Menu> para manipular texto em um <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="582f8-109">The following example creates a <xref:System.Windows.Controls.Menu> to manipulate text in a <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="582f8-110">O <xref:System.Windows.Controls.Menu> contém <xref:System.Windows.Controls.MenuItem> objetos que usam o <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, e <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> propriedades e o <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, e <xref:System.Windows.Controls.MenuItem.Click> eventos.</span><span class="sxs-lookup"><span data-stu-id="582f8-110">The <xref:System.Windows.Controls.Menu> contains <xref:System.Windows.Controls.MenuItem> objects that use the <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, and <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> properties and the <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, and <xref:System.Windows.Controls.MenuItem.Click> events.</span></span>  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a><span data-ttu-id="582f8-111">MenuItems com Atalhos de Teclado</span><span class="sxs-lookup"><span data-stu-id="582f8-111">MenuItems with Keyboard Shortcuts</span></span>  
 <span data-ttu-id="582f8-112">Atalhos de teclado são combinações de caracteres que podem ser inseridas com o teclado para invocar <xref:System.Windows.Controls.Menu> comandos.</span><span class="sxs-lookup"><span data-stu-id="582f8-112">Keyboard shortcuts are character combinations that can be entered with the keyboard to invoke <xref:System.Windows.Controls.Menu> commands.</span></span> <span data-ttu-id="582f8-113">Por exemplo, o atalho para **Copiar** é CTRL+C.</span><span class="sxs-lookup"><span data-stu-id="582f8-113">For example, the shortcut for **Copy** is CTRL+C.</span></span> <span data-ttu-id="582f8-114">Há duas propriedades para usar com atalhos de teclado e itens de menu —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> ou <xref:System.Windows.Controls.MenuItem.Command%2A>.</span><span class="sxs-lookup"><span data-stu-id="582f8-114">There are two properties to use with keyboard shortcuts and menu items —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> or <xref:System.Windows.Controls.MenuItem.Command%2A>.</span></span>  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a><span data-ttu-id="582f8-115">InputGestureText</span><span class="sxs-lookup"><span data-stu-id="582f8-115">InputGestureText</span></span>  
 <span data-ttu-id="582f8-116">O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> propriedade para atribuir texto de atalho de teclado <xref:System.Windows.Controls.MenuItem> controles.</span><span class="sxs-lookup"><span data-stu-id="582f8-116">The following example shows how to use the <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> property to assign keyboard shortcut text to <xref:System.Windows.Controls.MenuItem> controls.</span></span> <span data-ttu-id="582f8-117">Isso somente coloca o atalho de teclado no item de menu.</span><span class="sxs-lookup"><span data-stu-id="582f8-117">This only places the keyboard shortcut in the menu item.</span></span>  <span data-ttu-id="582f8-118">Ele não associa o comando com o <xref:System.Windows.Controls.MenuItem>.</span><span class="sxs-lookup"><span data-stu-id="582f8-118">It does not associate the command with the <xref:System.Windows.Controls.MenuItem>.</span></span> <span data-ttu-id="582f8-119">O aplicativo deve manipular a entrada do usuário para executar a ação.</span><span class="sxs-lookup"><span data-stu-id="582f8-119">The application must handle the user's input to carry out the action.</span></span>  
  
 [!code-xaml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a><span data-ttu-id="582f8-120">Comando</span><span class="sxs-lookup"><span data-stu-id="582f8-120">Command</span></span>  
 <span data-ttu-id="582f8-121">O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.MenuItem.Command%2A> propriedade para associar o **abrir** e **salvar** comandos com <xref:System.Windows.Controls.MenuItem> controles.</span><span class="sxs-lookup"><span data-stu-id="582f8-121">The following example shows how to use the <xref:System.Windows.Controls.MenuItem.Command%2A> property to associate the **Open** and **Save** commands with <xref:System.Windows.Controls.MenuItem> controls.</span></span> <span data-ttu-id="582f8-122">Não apenas a propriedade de comando associa um comando com um <xref:System.Windows.Controls.MenuItem>, mas ela também fornece o gesto de entrada de texto a ser usado como um atalho.</span><span class="sxs-lookup"><span data-stu-id="582f8-122">Not only does the command property associate a command with a <xref:System.Windows.Controls.MenuItem>, but it also supplies the input gesture text to use as a shortcut.</span></span>  
  
 [!code-xaml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <span data-ttu-id="582f8-123">O <xref:System.Windows.Controls.MenuItem> classe também tem um <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> propriedade, que especifica o elemento no qual o comando ocorre.</span><span class="sxs-lookup"><span data-stu-id="582f8-123">The <xref:System.Windows.Controls.MenuItem> class also has a <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> property, which specifies the element where the command occurs.</span></span> <span data-ttu-id="582f8-124">Se <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> não estiver definido, o elemento que tem o foco do teclado recebe o comando.</span><span class="sxs-lookup"><span data-stu-id="582f8-124">If <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> is not set, the element that has keyboard focus receives the command.</span></span> <span data-ttu-id="582f8-125">Para obter mais informações sobre comandos, consulte [Visão Geral dos Comandos](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="582f8-125">For more information about commands, see [Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span></span>  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a><span data-ttu-id="582f8-126">Estilo de Menu</span><span class="sxs-lookup"><span data-stu-id="582f8-126">Menu Styling</span></span>  
 <span data-ttu-id="582f8-127">Com estilo de controle, você pode alterar consideravelmente a aparência e comportamento de <xref:System.Windows.Controls.Menu> controles sem precisar escrever um controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="582f8-127">With control styling, you can dramatically change the appearance and behavior of <xref:System.Windows.Controls.Menu> controls without having to write a custom control.</span></span> <span data-ttu-id="582f8-128">Além de definir propriedades visuais, você também pode aplicar um <xref:System.Windows.Style> a partes individuais de um controle, alterar o comportamento das partes do controle através das propriedades, ou adicionar partes adicionais ou alterar o layout de um controle.</span><span class="sxs-lookup"><span data-stu-id="582f8-128">In addition to setting visual properties, you can also apply a <xref:System.Windows.Style> to individual parts of a control, change the behavior of parts of the control through properties, or add additional parts or change the layout of a control.</span></span> <span data-ttu-id="582f8-129">Os exemplos a seguir demonstram várias maneiras de adicionar um <xref:System.Windows.Style> para um <xref:System.Windows.Controls.Menu> controle.</span><span class="sxs-lookup"><span data-stu-id="582f8-129">The following examples demonstrate several ways to add a <xref:System.Windows.Style> to a <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 <span data-ttu-id="582f8-130">O primeiro exemplo de código define uma <xref:System.Windows.Style> chamado `Simple` que mostra como usar as configurações atuais do sistema no seu estilo.</span><span class="sxs-lookup"><span data-stu-id="582f8-130">The first code example defines a <xref:System.Windows.Style> called `Simple` that shows how to use the current system settings in your style.</span></span> <span data-ttu-id="582f8-131">O código atribui a cor do `MenuHighlightBrush` como cor da tela de fundo do menu e o `MenuTextBrush` como cor de primeiro plano do menu.</span><span class="sxs-lookup"><span data-stu-id="582f8-131">The code assigns the color of the `MenuHighlightBrush` as the menu's background color and the `MenuTextBrush` as the menu's foreground color.</span></span> <span data-ttu-id="582f8-132">Observe que as chaves de recurso são utilizadas para atribuir os pincéis.</span><span class="sxs-lookup"><span data-stu-id="582f8-132">Notice that you use resource keys to assign the brushes.</span></span>  
  
 [!code-xaml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 <span data-ttu-id="582f8-133">O exemplo a seguir usa <xref:System.Windows.Trigger> elementos que permitem que você alterar a aparência de um <xref:System.Windows.Controls.MenuItem> em resposta a eventos que ocorrem no <xref:System.Windows.Controls.Menu>.</span><span class="sxs-lookup"><span data-stu-id="582f8-133">The following sample uses <xref:System.Windows.Trigger> elements that enable you to change the appearance of a <xref:System.Windows.Controls.MenuItem> in response to events that occur on the <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="582f8-134">Quando você move o mouse sobre o <xref:System.Windows.Controls.Menu>, a cor de primeiro plano e as características da fonte dos itens de menu alterar.</span><span class="sxs-lookup"><span data-stu-id="582f8-134">When you move the mouse over the <xref:System.Windows.Controls.Menu>, the foreground color and the font characteristics of the menu items change.</span></span>  
  
 [!code-xaml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a><span data-ttu-id="582f8-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="582f8-135">See Also</span></span>  
 [<span data-ttu-id="582f8-136">Exemplo da galeria de controles de WPF</span><span class="sxs-lookup"><span data-stu-id="582f8-136">WPF Controls Gallery Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160053)
