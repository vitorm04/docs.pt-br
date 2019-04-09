---
title: 'Como: Criar ListViewItems com um CheckBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
ms.openlocfilehash: b09d5ad11b0961febf524cec1e19cb1e59832e44
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083095"
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a><span data-ttu-id="ff458-102">Como: Criar ListViewItems com um CheckBox</span><span class="sxs-lookup"><span data-stu-id="ff458-102">How to: Create ListViewItems with a CheckBox</span></span>
<span data-ttu-id="ff458-103">Este exemplo mostra como exibir uma coluna de <xref:System.Windows.Controls.CheckBox> controles em um <xref:System.Windows.Controls.ListView> controle que usa um <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="ff458-103">This example shows how to display a column of <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff458-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ff458-104">Example</span></span>  
 <span data-ttu-id="ff458-105">Para criar uma coluna que contém <xref:System.Windows.Controls.CheckBox> controles em um <xref:System.Windows.Controls.ListView>, criar um <xref:System.Windows.DataTemplate> que contém um <xref:System.Windows.Controls.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="ff458-105">To create a column that contains <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView>, create a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="ff458-106">Em seguida, defina as <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> de um <xref:System.Windows.Controls.GridViewColumn> para o <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="ff458-106">Then set the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> of a <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 <span data-ttu-id="ff458-107">A exemplo a seguir mostra uma <xref:System.Windows.DataTemplate> que contém um <xref:System.Windows.Controls.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="ff458-107">The following example shows a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="ff458-108">O exemplo associa a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> propriedade do <xref:System.Windows.Controls.CheckBox> para o <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> valor da propriedade a <xref:System.Windows.Controls.ListViewItem> que o contém.</span><span class="sxs-lookup"><span data-stu-id="ff458-108">The example binds the <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> property of the <xref:System.Windows.Controls.CheckBox> to the <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> property value of the <xref:System.Windows.Controls.ListViewItem> that contains it.</span></span> <span data-ttu-id="ff458-109">Portanto, quando o <xref:System.Windows.Controls.ListViewItem> que contém o <xref:System.Windows.Controls.CheckBox> for selecionada, o <xref:System.Windows.Controls.CheckBox> é verificada.</span><span class="sxs-lookup"><span data-stu-id="ff458-109">Therefore, when the <xref:System.Windows.Controls.ListViewItem> that contains the <xref:System.Windows.Controls.CheckBox> is selected, the <xref:System.Windows.Controls.CheckBox> is checked.</span></span>  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 <span data-ttu-id="ff458-110">O exemplo a seguir mostra como criar uma coluna de <xref:System.Windows.Controls.CheckBox> controles.</span><span class="sxs-lookup"><span data-stu-id="ff458-110">The following example shows how to create a column of <xref:System.Windows.Controls.CheckBox> controls.</span></span> <span data-ttu-id="ff458-111">Para tornar a coluna, o exemplo define o <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> propriedade do <xref:System.Windows.Controls.GridViewColumn> para o <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="ff458-111">To make the column, the example sets the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> property of the <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a><span data-ttu-id="ff458-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff458-112">See also</span></span>

- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="ff458-113">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="ff458-113">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="ff458-114">Tópicos explicativos </span><span class="sxs-lookup"><span data-stu-id="ff458-114">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="ff458-115">Visão geral de GridView</span><span class="sxs-lookup"><span data-stu-id="ff458-115">GridView Overview</span></span>](gridview-overview.md)
