---
title: Como definir foco em um controle TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
ms.openlocfilehash: 1bda01a3d330ad384c2f922ff3c7679e10d0f148
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552533"
---
# <a name="how-to-set-focus-in-a-textbox-control"></a><span data-ttu-id="d6ce3-102">Como definir foco em um controle TextBox</span><span class="sxs-lookup"><span data-stu-id="d6ce3-102">How to: Set Focus in a TextBox Control</span></span>
<span data-ttu-id="d6ce3-103">Este exemplo mostra como usar o <xref:System.Windows.UIElement.Focus%2A> método para definir o foco em um <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="d6ce3-103">This example shows how to use the <xref:System.Windows.UIElement.Focus%2A> method to set focus on a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6ce3-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6ce3-104">Example</span></span>  
 <span data-ttu-id="d6ce3-105">O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplo descreve um simples <xref:System.Windows.Controls.TextBox> controle chamado *tbFocusMe.*</span><span class="sxs-lookup"><span data-stu-id="d6ce3-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example describes a simple <xref:System.Windows.Controls.TextBox> control named *tbFocusMe*</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a><span data-ttu-id="d6ce3-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6ce3-106">Example</span></span>  
 <span data-ttu-id="d6ce3-107">A exemplo a seguir chama o <xref:System.Windows.UIElement.Focus%2A> método para definir o foco de <xref:System.Windows.Controls.TextBox> controle com o nome *tbFocusMe*.</span><span class="sxs-lookup"><span data-stu-id="d6ce3-107">The following example calls the <xref:System.Windows.UIElement.Focus%2A> method to set the focus on the <xref:System.Windows.Controls.TextBox> control with the Name *tbFocusMe*.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a><span data-ttu-id="d6ce3-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6ce3-108">See Also</span></span>  
 <xref:System.Windows.UIElement.Focusable%2A>  
 <xref:System.Windows.UIElement.IsFocused%2A>  
 [<span data-ttu-id="d6ce3-109">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="d6ce3-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="d6ce3-110">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="d6ce3-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
