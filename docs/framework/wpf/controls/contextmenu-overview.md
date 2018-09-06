---
title: Visão geral de ContextMenu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
ms.openlocfilehash: 54fd823594fba4500f35ed1d69720a3309e54a36
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43787032"
---
# <a name="contextmenu-overview"></a><span data-ttu-id="c4230-102">Visão geral de ContextMenu</span><span class="sxs-lookup"><span data-stu-id="c4230-102">ContextMenu Overview</span></span>
<span data-ttu-id="c4230-103">O <xref:System.Windows.Controls.ContextMenu> classe representa o elemento que expõe a funcionalidade por meio de um contexto específico <xref:System.Windows.Controls.Menu>.</span><span class="sxs-lookup"><span data-stu-id="c4230-103">The <xref:System.Windows.Controls.ContextMenu> class represents the element that exposes functionality by using a context-specific <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="c4230-104">Normalmente, um usuário expõe o <xref:System.Windows.Controls.ContextMenu> no [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] clicando com o botão do mouse.</span><span class="sxs-lookup"><span data-stu-id="c4230-104">Typically, a user exposes the <xref:System.Windows.Controls.ContextMenu> in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] by right-clicking the mouse button.</span></span> <span data-ttu-id="c4230-105">Este tópico apresenta os <xref:System.Windows.Controls.ContextMenu> elemento e fornece exemplos de como usá-lo no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e código.</span><span class="sxs-lookup"><span data-stu-id="c4230-105">This topic introduces the <xref:System.Windows.Controls.ContextMenu> element and provides examples of how to use it in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span>  
  
  
  
<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a><span data-ttu-id="c4230-106">Controle ContextMenu</span><span class="sxs-lookup"><span data-stu-id="c4230-106">ContextMenu Control</span></span>  
 <span data-ttu-id="c4230-107">Um <xref:System.Windows.Controls.ContextMenu> é anexado a um controle específico.</span><span class="sxs-lookup"><span data-stu-id="c4230-107">A <xref:System.Windows.Controls.ContextMenu> is attached to a specific control.</span></span> <span data-ttu-id="c4230-108">O <xref:System.Windows.Controls.ContextMenu> elemento permite apresentar aos usuários uma lista de itens que especificam comandos ou opções que estão associadas um determinado controle, por exemplo, um <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="c4230-108">The <xref:System.Windows.Controls.ContextMenu> element enables you to present users with a list of items that specify commands or options that are associated with a particular control, for example, a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="c4230-109">Os usuários clicam com o botão direito do mouse no controle para exibir o menu.</span><span class="sxs-lookup"><span data-stu-id="c4230-109">Users right-click the control to make the menu appear.</span></span> <span data-ttu-id="c4230-110">Geralmente, clicar em um <xref:System.Windows.Controls.MenuItem> abre um submenu ou faz com que um aplicativo para executar um comando.</span><span class="sxs-lookup"><span data-stu-id="c4230-110">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a><span data-ttu-id="c4230-111">Criando ContextMenus</span><span class="sxs-lookup"><span data-stu-id="c4230-111">Creating ContextMenus</span></span>  
 <span data-ttu-id="c4230-112">Os exemplos a seguir mostram como criar um <xref:System.Windows.Controls.ContextMenu> com submenus.</span><span class="sxs-lookup"><span data-stu-id="c4230-112">The following examples show how to create a <xref:System.Windows.Controls.ContextMenu> with submenus.</span></span> <span data-ttu-id="c4230-113">O <xref:System.Windows.Controls.ContextMenu> controles são anexados aos controles de botão.</span><span class="sxs-lookup"><span data-stu-id="c4230-113">The <xref:System.Windows.Controls.ContextMenu> controls are attached to button controls.</span></span>  
  
 [!code-xaml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a><span data-ttu-id="c4230-114">Aplicando estilos a um ContextMenu</span><span class="sxs-lookup"><span data-stu-id="c4230-114">Applying Styles to a ContextMenu</span></span>  
 <span data-ttu-id="c4230-115">Usando um controle <xref:System.Windows.Style>, você pode alterar consideravelmente a aparência e comportamento de um <xref:System.Windows.Controls.ContextMenu> sem precisar escrever um controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="c4230-115">By using a control <xref:System.Windows.Style>, you can dramatically change the appearance and behavior of a <xref:System.Windows.Controls.ContextMenu> without writing a custom control.</span></span> <span data-ttu-id="c4230-116">Além de definir propriedades visuais, você também pode aplicar estilos a partes de um controle.</span><span class="sxs-lookup"><span data-stu-id="c4230-116">In addition to setting visual properties, you can also apply styles to parts of a control.</span></span> <span data-ttu-id="c4230-117">Por exemplo, você pode alterar o comportamento das partes do controle usando propriedades, ou você pode adicionar partes ou alterar o layout de um <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="c4230-117">For example, you can change the behavior of parts of the control by using properties, or you can add parts to, or change the layout of, a <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="c4230-118">Os exemplos a seguir mostram várias maneiras de adicionar estilos para <xref:System.Windows.Controls.ContextMenu> controles.</span><span class="sxs-lookup"><span data-stu-id="c4230-118">The following examples show several ways to add styles to <xref:System.Windows.Controls.ContextMenu> controls.</span></span>  
  
 <span data-ttu-id="c4230-119">O primeiro exemplo define um estilo chamado `SimpleSysResources`, que mostra como usar as configurações atuais do sistema no seu estilo.</span><span class="sxs-lookup"><span data-stu-id="c4230-119">The first example defines a style called `SimpleSysResources`, which shows how to use the current system settings in your style.</span></span> <span data-ttu-id="c4230-120">O exemplo atribui <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> como o <xref:System.Windows.Controls.Control.Background%2A> cor e <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> como o <xref:System.Windows.Controls.Control.Foreground%2A> cor do <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="c4230-120">The example assigns <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> as the <xref:System.Windows.Controls.Control.Background%2A> color and <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> as the <xref:System.Windows.Controls.Control.Foreground%2A> color of the <xref:System.Windows.Controls.ContextMenu>.</span></span>  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 <span data-ttu-id="c4230-121">O exemplo a seguir usa o <xref:System.Windows.Trigger> elemento para alterar a aparência de um <xref:System.Windows.Controls.Menu> em resposta a eventos que são gerados no <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="c4230-121">The following example uses the <xref:System.Windows.Trigger> element to change the appearance of a <xref:System.Windows.Controls.Menu> in response to events that are raised on the <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="c4230-122">Quando um usuário move o mouse sobre o menu, a aparência do <xref:System.Windows.Controls.ContextMenu> itens alterações.</span><span class="sxs-lookup"><span data-stu-id="c4230-122">When a user moves the mouse over the menu, the appearance of the <xref:System.Windows.Controls.ContextMenu> items changes.</span></span>  
  
```xaml  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4230-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4230-123">See Also</span></span>  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.Menu>  
 <xref:System.Windows.Controls.MenuItem>  
 [<span data-ttu-id="c4230-124">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="c4230-124">ContextMenu</span></span>](../../../../docs/framework/wpf/controls/contextmenu.md)  
 [<span data-ttu-id="c4230-125">Estilos e modelos ContextMenu</span><span class="sxs-lookup"><span data-stu-id="c4230-125">ContextMenu Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/contextmenu-styles-and-templates.md)  
 [<span data-ttu-id="c4230-126">Exemplo da galeria de controles de WPF</span><span class="sxs-lookup"><span data-stu-id="c4230-126">WPF Controls Gallery Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160053)
