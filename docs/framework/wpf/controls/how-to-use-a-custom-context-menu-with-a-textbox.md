---
title: Como usar um menu contextual personalizado com um TextBox
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
- context menus [WPF], custom
- menus [WPF], custom
- custom context menus [WPF]
- TextBox control [WPF], custom content menus
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4552031a08680af2f4d41702d2f76ed0c44af21b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a><span data-ttu-id="14f61-102">Como usar um menu contextual personalizado com um TextBox</span><span class="sxs-lookup"><span data-stu-id="14f61-102">How to: Use a Custom Context Menu with a TextBox</span></span>
<span data-ttu-id="14f61-103">Este exemplo mostra como definir e implementar um menu de contexto personalizado simples para um <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="14f61-103">This example shows how to define and implement a simple custom context menu for a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14f61-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="14f61-104">Example</span></span>  
 <span data-ttu-id="14f61-105">O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplo define um <xref:System.Windows.Controls.TextBox> controle que inclui um menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="14f61-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example defines a <xref:System.Windows.Controls.TextBox> control that includes a custom context menu.</span></span>  
  
 <span data-ttu-id="14f61-106">O menu de contexto é definido usando um <xref:System.Windows.Controls.ContextMenu> elemento.</span><span class="sxs-lookup"><span data-stu-id="14f61-106">The context menu is defined using a <xref:System.Windows.Controls.ContextMenu> element.</span></span>  <span data-ttu-id="14f61-107">O menu de contexto consiste em uma série de <xref:System.Windows.Controls.MenuItem> elementos e <xref:System.Windows.Controls.Separator> elementos.</span><span class="sxs-lookup"><span data-stu-id="14f61-107">The context menu itself consists of a series of <xref:System.Windows.Controls.MenuItem> elements and <xref:System.Windows.Controls.Separator> elements.</span></span>  <span data-ttu-id="14f61-108">Cada <xref:System.Windows.Controls.MenuItem> elemento define um comando no menu de contexto; o <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> atributo define o texto exibido para o comando de menu e a <xref:System.Windows.Controls.MenuItem.Click> atributo especifica um método de manipulador para cada item de menu.</span><span class="sxs-lookup"><span data-stu-id="14f61-108">Each <xref:System.Windows.Controls.MenuItem> element defines a command in the context menu; the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> attribute defines the display text for the menu command, and the <xref:System.Windows.Controls.MenuItem.Click> attribute specifies a handler method for each menu item.</span></span>  <span data-ttu-id="14f61-109">O <xref:System.Windows.Controls.Separator> elemento simplesmente faz com que uma linha de separação seja renderizada entre os itens de menu anterior e posterior.</span><span class="sxs-lookup"><span data-stu-id="14f61-109">The <xref:System.Windows.Controls.Separator> element simply causes a separating line to be rendered between the previous and subsequent menu items.</span></span>  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a><span data-ttu-id="14f61-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="14f61-110">Example</span></span>  
 <span data-ttu-id="14f61-111">O exemplo a seguir mostra o código de implementação para a definição de menu de contexto anterior, bem como o código que habilita e desabilita o menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="14f61-111">The following example shows the implementation code for the preceding context menu definition, as well as the code that enables and disables the context menu.</span></span>  <span data-ttu-id="14f61-112">O <xref:System.Windows.Controls.ContextMenu.Opened> evento é usado para ativar ou desativar determinados comandos dependendo do estado atual do dinamicamente o <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="14f61-112">The <xref:System.Windows.Controls.ContextMenu.Opened> event is used to dynamically enable or disable certain commands depending on the current state of the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 <span data-ttu-id="14f61-113">Para restaurar o menu de contexto padrão, use o <xref:System.Windows.DependencyObject.ClearValue%2A> método para limpar o valor da <xref:System.Windows.FrameworkElement.ContextMenu%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="14f61-113">To restore the default context menu, use the <xref:System.Windows.DependencyObject.ClearValue%2A> method to clear the value of the <xref:System.Windows.FrameworkElement.ContextMenu%2A> property.</span></span>  <span data-ttu-id="14f61-114">Para desabilitar completamente o menu de contexto, defina o <xref:System.Windows.FrameworkElement.ContextMenu%2A> propriedade como uma referência nula (`Nothing` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="14f61-114">To disable the context menu altogether, set the <xref:System.Windows.FrameworkElement.ContextMenu%2A> property to a null reference (`Nothing` in Visual Basic).</span></span>  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a><span data-ttu-id="14f61-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14f61-115">See Also</span></span>  
 [<span data-ttu-id="14f61-116">Usar verificação ortográfica com um menu de contexto</span><span class="sxs-lookup"><span data-stu-id="14f61-116">Use Spell Checking with a Context Menu</span></span>](../../../../docs/framework/wpf/controls/how-to-use-spell-checking-with-a-context-menu.md)  
 [<span data-ttu-id="14f61-117">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="14f61-117">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="14f61-118">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="14f61-118">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
