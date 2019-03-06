---
title: 'Como: Criar um estilo para um cabeçalho de coluna GridView arrastado'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
ms.openlocfilehash: 442fff7a36a48d5df7ba9e07426e50f602cb93e8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357489"
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a><span data-ttu-id="569e8-102">Como: Criar um estilo para um cabeçalho de coluna GridView arrastado</span><span class="sxs-lookup"><span data-stu-id="569e8-102">How to: Create a Style for a Dragged GridView Column Header</span></span>
<span data-ttu-id="569e8-103">Este exemplo mostra como alterar a aparência de um arrastado <xref:System.Windows.Controls.GridViewColumnHeader> quando o usuário altera a posição de uma coluna.</span><span class="sxs-lookup"><span data-stu-id="569e8-103">This example shows how to change the appearance of a dragged <xref:System.Windows.Controls.GridViewColumnHeader> when the user changes the position of a column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="569e8-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="569e8-104">Example</span></span>  
 <span data-ttu-id="569e8-105">Quando você arrasta um cabeçalho de coluna para outro local em um <xref:System.Windows.Controls.ListView> que usa <xref:System.Windows.Controls.GridView> seu modo de exibição, a coluna é movida para a nova posição.</span><span class="sxs-lookup"><span data-stu-id="569e8-105">When you drag a column header to another location in a <xref:System.Windows.Controls.ListView> that uses <xref:System.Windows.Controls.GridView> for its view mode, the column moves to the new position.</span></span> <span data-ttu-id="569e8-106">Enquanto você estiver arrastando o cabeçalho da coluna, uma cópia flutuante do cabeçalho é exibida além do cabeçalho original.</span><span class="sxs-lookup"><span data-stu-id="569e8-106">While you are dragging the column header, a floating copy of the header appears in addition to the original header.</span></span> <span data-ttu-id="569e8-107">Um cabeçalho de coluna em uma <xref:System.Windows.Controls.GridView> é representado por um <xref:System.Windows.Controls.GridViewColumnHeader> objeto.</span><span class="sxs-lookup"><span data-stu-id="569e8-107">A column header in a <xref:System.Windows.Controls.GridView> is represented by a <xref:System.Windows.Controls.GridViewColumnHeader> object.</span></span>  
  
 <span data-ttu-id="569e8-108">Para personalizar a aparência dos cabeçalhos originais e flutuantes, você pode definir <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> para modificar os <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="569e8-108">To customize the appearance of both the floating and original headers, you can set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to modify the <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>.</span></span> <span data-ttu-id="569e8-109">Esses <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> são aplicadas quando o <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> é o valor da propriedade `true` e o <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> é o valor da propriedade <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span><span class="sxs-lookup"><span data-stu-id="569e8-109">These <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> are applied when the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value is `true` and the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property value is <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="569e8-110">Quando o usuário pressiona o botão do mouse e mantém pressionado enquanto o mouse faz uma pausa sobre o <xref:System.Windows.Controls.GridViewColumnHeader>, o <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> o valor de propriedade é alterado para `true`.</span><span class="sxs-lookup"><span data-stu-id="569e8-110">When the user presses the mouse button and holds it down while the mouse pauses on the <xref:System.Windows.Controls.GridViewColumnHeader>, the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value changes to `true`.</span></span> <span data-ttu-id="569e8-111">Da mesma forma, quando o usuário começa a operação de arrastar, o <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> alteração na propriedade <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span><span class="sxs-lookup"><span data-stu-id="569e8-111">Likewise, when the user begins the drag operation, the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property changes to <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="569e8-112">O exemplo a seguir mostra como definir <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> para alterar o <xref:System.Windows.Controls.Control.Foreground%2A> e <xref:System.Windows.Controls.Control.Background%2A> cores dos cabeçalhos originais e flutuantes quando o usuário arrasta uma coluna para uma nova posição.</span><span class="sxs-lookup"><span data-stu-id="569e8-112">The following example shows how to set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to change the <xref:System.Windows.Controls.Control.Foreground%2A> and <xref:System.Windows.Controls.Control.Background%2A> colors of the original and floating headers when the user drags a column to a new position.</span></span>  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a><span data-ttu-id="569e8-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="569e8-113">See also</span></span>
- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="569e8-114">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="569e8-114">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="569e8-115">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="569e8-115">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="569e8-116">Visão geral de GridView</span><span class="sxs-lookup"><span data-stu-id="569e8-116">GridView Overview</span></span>](gridview-overview.md)
