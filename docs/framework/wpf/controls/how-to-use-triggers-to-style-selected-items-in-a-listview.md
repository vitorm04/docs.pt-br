---
title: 'Como: Usar gatilhos para criar itens selecionados em um ListView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
ms.openlocfilehash: 8c2d4adb2471c0f1891288573ce6b6460b20151d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367915"
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a><span data-ttu-id="9cd63-102">Como: Usar gatilhos para criar itens selecionados em um ListView</span><span class="sxs-lookup"><span data-stu-id="9cd63-102">How to: Use Triggers to Style Selected Items in a ListView</span></span>
<span data-ttu-id="9cd63-103">Este exemplo mostra como definir <xref:System.Windows.Style.Triggers%2A> para um <xref:System.Windows.Controls.ListViewItem> controle, de modo que quando um valor de propriedade de um <xref:System.Windows.Controls.ListViewItem> alterações, o <xref:System.Windows.Style> do <xref:System.Windows.Controls.ListViewItem> alterações na resposta.</span><span class="sxs-lookup"><span data-stu-id="9cd63-103">This example shows how to define <xref:System.Windows.Style.Triggers%2A> for a <xref:System.Windows.Controls.ListViewItem> control so that when a property value of a <xref:System.Windows.Controls.ListViewItem> changes, the <xref:System.Windows.Style> of the <xref:System.Windows.Controls.ListViewItem> changes in response.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cd63-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9cd63-104">Example</span></span>  
 <span data-ttu-id="9cd63-105">Se você quiser que o <xref:System.Windows.Style> de um <xref:System.Windows.Controls.ListViewItem> para alterar em resposta às alterações de propriedade, defina <xref:System.Windows.Style.Triggers%2A> para o <xref:System.Windows.Style> alterar.</span><span class="sxs-lookup"><span data-stu-id="9cd63-105">If you want the <xref:System.Windows.Style> of a <xref:System.Windows.Controls.ListViewItem> to change in response to property changes, define <xref:System.Windows.Style.Triggers%2A> for the <xref:System.Windows.Style> change.</span></span>  
  
 <span data-ttu-id="9cd63-106">O exemplo a seguir define uma <xref:System.Windows.Trigger> que define o <xref:System.Windows.Controls.Control.Foreground%2A> propriedade <xref:System.Windows.Media.Brushes.Blue%2A> e altera o <xref:System.Windows.FrameworkElement.Cursor%2A> para exibir um <xref:System.Windows.Input.CursorType.Hand> quando o <xref:System.Windows.UIElement.IsMouseOver%2A> alteração na propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="9cd63-106">The following example defines a <xref:System.Windows.Trigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property to <xref:System.Windows.Media.Brushes.Blue%2A> and changes the <xref:System.Windows.FrameworkElement.Cursor%2A> to display a <xref:System.Windows.Input.CursorType.Hand> when the <xref:System.Windows.UIElement.IsMouseOver%2A> property changes to `true`.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 <span data-ttu-id="9cd63-107">O exemplo a seguir define uma <xref:System.Windows.MultiTrigger> que define o <xref:System.Windows.Controls.Control.Foreground%2A> propriedade de um <xref:System.Windows.Controls.ListViewItem> à <xref:System.Windows.Media.Brushes.Yellow%2A> quando o <xref:System.Windows.Controls.ListViewItem> é o item selecionado e tem o foco do teclado.</span><span class="sxs-lookup"><span data-stu-id="9cd63-107">The following example defines a <xref:System.Windows.MultiTrigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.ListViewItem> to <xref:System.Windows.Media.Brushes.Yellow%2A> when the <xref:System.Windows.Controls.ListViewItem> is the selected item and has keyboard focus.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a><span data-ttu-id="9cd63-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cd63-108">See also</span></span>
- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="9cd63-109">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="9cd63-109">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="9cd63-110">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="9cd63-110">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="9cd63-111">Visão geral de GridView</span><span class="sxs-lookup"><span data-stu-id="9cd63-111">GridView Overview</span></span>](gridview-overview.md)
