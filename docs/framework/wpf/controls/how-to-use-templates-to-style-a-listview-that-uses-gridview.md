---
title: 'Como: Usar modelos para moldar um ListView que use GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
ms.openlocfilehash: 1caa652c4a2a3a7d0a8d40fe703df7a3e8038c9b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147089"
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a><span data-ttu-id="e83b4-102">Como: Usar modelos para moldar um ListView que use GridView</span><span class="sxs-lookup"><span data-stu-id="e83b4-102">How to: Use Templates to Style a ListView That Uses GridView</span></span>
<span data-ttu-id="e83b4-103">Este exemplo mostra como usar o <xref:System.Windows.DataTemplate> e <xref:System.Windows.Style> objetos para especificar a aparência de um <xref:System.Windows.Controls.ListView> controle que usa um <xref:System.Windows.Controls.GridView> modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="e83b4-103">This example shows how to use the <xref:System.Windows.DataTemplate> and <xref:System.Windows.Style> objects to specify the appearance of a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e83b4-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e83b4-104">Example</span></span>  
 <span data-ttu-id="e83b4-105">Os exemplos a seguir mostram <xref:System.Windows.Style> e <xref:System.Windows.DataTemplate> objetos que personalizam a aparência de um cabeçalho de coluna para um <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="e83b4-105">The following examples show <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects that customize the appearance of a column header for a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 <span data-ttu-id="e83b4-106">O exemplo a seguir mostra como usar esses <xref:System.Windows.Style> e <xref:System.Windows.DataTemplate> objetos para definir o <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> e <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> as propriedades de um <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="e83b4-106">The following example shows how to use these <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects to set the <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> properties of a <xref:System.Windows.Controls.GridViewColumn>.</span></span> <span data-ttu-id="e83b4-107">O <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> propriedade define o conteúdo das células da coluna.</span><span class="sxs-lookup"><span data-stu-id="e83b4-107">The <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property defines the content of the column cells.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <span data-ttu-id="e83b4-108">O <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> e <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> são apenas duas das várias propriedades que você pode usar para personalizar a aparência do cabeçalho de coluna para um <xref:System.Windows.Controls.GridView> controle.</span><span class="sxs-lookup"><span data-stu-id="e83b4-108">The <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> are only two of several properties that you can use to customize column header appearance for a <xref:System.Windows.Controls.GridView> control.</span></span> <span data-ttu-id="e83b4-109">Para obter mais informações, consulte [Visão geral de modelos e estilos de cabeçalho de coluna GridView](gridview-column-header-styles-and-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e83b4-109">For more information, see [GridView Column Header Styles and Templates Overview](gridview-column-header-styles-and-templates-overview.md).</span></span>  
  
 <span data-ttu-id="e83b4-110">O exemplo a seguir mostra como definir um <xref:System.Windows.DataTemplate> que personaliza a aparência das células em uma <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="e83b4-110">The following example shows how to define a <xref:System.Windows.DataTemplate> that customizes the appearance of the cells in a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 <span data-ttu-id="e83b4-111">O exemplo a seguir mostra como usar esse <xref:System.Windows.DataTemplate> para definir o conteúdo de um <xref:System.Windows.Controls.GridViewColumn> célula.</span><span class="sxs-lookup"><span data-stu-id="e83b4-111">The following example shows how to use this <xref:System.Windows.DataTemplate> to define the content of a <xref:System.Windows.Controls.GridViewColumn> cell.</span></span> <span data-ttu-id="e83b4-112">Este modelo é usado em vez do <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> mostrado anteriormente na propriedade <xref:System.Windows.Controls.GridViewColumn> exemplo.</span><span class="sxs-lookup"><span data-stu-id="e83b4-112">This template is used instead of the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property that is shown in the previous <xref:System.Windows.Controls.GridViewColumn> example.</span></span>  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="e83b4-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e83b4-113">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="e83b4-114">Visão geral de GridView</span><span class="sxs-lookup"><span data-stu-id="e83b4-114">GridView Overview</span></span>](gridview-overview.md)
- [<span data-ttu-id="e83b4-115">Tópicos explicativos </span><span class="sxs-lookup"><span data-stu-id="e83b4-115">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="e83b4-116">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="e83b4-116">ListView Overview</span></span>](listview-overview.md)
