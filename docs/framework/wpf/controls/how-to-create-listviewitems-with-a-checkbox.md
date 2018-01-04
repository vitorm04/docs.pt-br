---
title: Como criar um ListViewItems com um CheckBox
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be87183efd8101233bd5cbda49d556d09802b630
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a><span data-ttu-id="7d19e-102">Como criar um ListViewItems com um CheckBox</span><span class="sxs-lookup"><span data-stu-id="7d19e-102">How to: Create ListViewItems with a CheckBox</span></span>
<span data-ttu-id="7d19e-103">Este exemplo mostra como exibir uma coluna de <xref:System.Windows.Controls.CheckBox> controles em um <xref:System.Windows.Controls.ListView> controle que usa um <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="7d19e-103">This example shows how to display a column of <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d19e-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7d19e-104">Example</span></span>  
 <span data-ttu-id="7d19e-105">Para criar uma coluna que contém <xref:System.Windows.Controls.CheckBox> controles em um <xref:System.Windows.Controls.ListView>, crie um <xref:System.Windows.DataTemplate> que contém um <xref:System.Windows.Controls.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="7d19e-105">To create a column that contains <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView>, create a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="7d19e-106">Em seguida, defina o <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> de um <xref:System.Windows.Controls.GridViewColumn> para o <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="7d19e-106">Then set the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> of a <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 <span data-ttu-id="7d19e-107">A exemplo a seguir mostra um <xref:System.Windows.DataTemplate> que contém um <xref:System.Windows.Controls.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="7d19e-107">The following example shows a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="7d19e-108">O exemplo associa o <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> propriedade do <xref:System.Windows.Controls.CheckBox> para o <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> valor da propriedade a <xref:System.Windows.Controls.ListViewItem> que o contém.</span><span class="sxs-lookup"><span data-stu-id="7d19e-108">The example binds the <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> property of the <xref:System.Windows.Controls.CheckBox> to the <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> property value of the <xref:System.Windows.Controls.ListViewItem> that contains it.</span></span> <span data-ttu-id="7d19e-109">Portanto, quando o <xref:System.Windows.Controls.ListViewItem> que contém o <xref:System.Windows.Controls.CheckBox> for selecionada, o <xref:System.Windows.Controls.CheckBox> é verificada.</span><span class="sxs-lookup"><span data-stu-id="7d19e-109">Therefore, when the <xref:System.Windows.Controls.ListViewItem> that contains the <xref:System.Windows.Controls.CheckBox> is selected, the <xref:System.Windows.Controls.CheckBox> is checked.</span></span>  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 <span data-ttu-id="7d19e-110">O exemplo a seguir mostra como criar uma coluna de <xref:System.Windows.Controls.CheckBox> controles.</span><span class="sxs-lookup"><span data-stu-id="7d19e-110">The following example shows how to create a column of <xref:System.Windows.Controls.CheckBox> controls.</span></span> <span data-ttu-id="7d19e-111">Para tornar a coluna, o exemplo define o <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> propriedade o <xref:System.Windows.Controls.GridViewColumn> para o <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="7d19e-111">To make the column, the example sets the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> property of the <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a><span data-ttu-id="7d19e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d19e-112">See Also</span></span>  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="7d19e-113">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="7d19e-113">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="7d19e-114">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="7d19e-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="7d19e-115">Visão geral de GridView</span><span class="sxs-lookup"><span data-stu-id="7d19e-115">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
