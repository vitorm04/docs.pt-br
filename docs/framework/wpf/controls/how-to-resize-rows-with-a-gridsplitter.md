---
title: Como redimensionar linhas com um GridSplitter
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6621cc0048270b97c42ff4c4e646b0ddd9ca3477
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a><span data-ttu-id="1fd62-102">Como redimensionar linhas com um GridSplitter</span><span class="sxs-lookup"><span data-stu-id="1fd62-102">How to: Resize Rows with a GridSplitter</span></span>
<span data-ttu-id="1fd62-103">Este exemplo mostra como usar um horizontal <xref:System.Windows.Controls.GridSplitter> para redistribuir o espaço entre duas linhas em uma <xref:System.Windows.Controls.Grid> sem alterar as dimensões do <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="1fd62-103">This example shows how to use a horizontal <xref:System.Windows.Controls.GridSplitter> to redistribute the space between two rows in a <xref:System.Windows.Controls.Grid> without changing the dimensions of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fd62-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1fd62-104">Example</span></span>  
 <span data-ttu-id="1fd62-105">**Como criar um GridSplitter que sobrepõe a borda de uma linha**</span><span class="sxs-lookup"><span data-stu-id="1fd62-105">**How to create a GridSplitter that overlays the edge of a row**</span></span>  
  
 <span data-ttu-id="1fd62-106">Para especificar um <xref:System.Windows.Controls.GridSplitter> que redimensiona linhas adjacentes em um <xref:System.Windows.Controls.Grid>, defina o <xref:System.Windows.Controls.Grid.Row%2A> propriedade anexada a uma das linhas que você deseja redimensionar.</span><span class="sxs-lookup"><span data-stu-id="1fd62-106">To specify a <xref:System.Windows.Controls.GridSplitter> that resizes adjacent rows in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Row%2A> attached property to one of the rows that you want to resize.</span></span> <span data-ttu-id="1fd62-107">Se seu <xref:System.Windows.Controls.Grid> tem mais de uma coluna, defina o <xref:System.Windows.Controls.Grid.ColumnSpan%2A> anexado a propriedade para especificar o número de colunas.</span><span class="sxs-lookup"><span data-stu-id="1fd62-107">If your <xref:System.Windows.Controls.Grid> has more than one column, set the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> attached property to specify the number of columns.</span></span> <span data-ttu-id="1fd62-108">Em seguida, defina o <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> para <xref:System.Windows.VerticalAlignment.Top> ou <xref:System.Windows.VerticalAlignment.Bottom> (o alinhamento que você define depende de quais duas linhas você deseja redimensionar).</span><span class="sxs-lookup"><span data-stu-id="1fd62-108">Then set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> to <xref:System.Windows.VerticalAlignment.Top> or <xref:System.Windows.VerticalAlignment.Bottom> (which alignment you set depends on which two rows you want to resize).</span></span> <span data-ttu-id="1fd62-109">Finalmente, defina o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade <xref:System.Windows.HorizontalAlignment.Stretch>.</span><span class="sxs-lookup"><span data-stu-id="1fd62-109">Finally, set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Stretch>.</span></span>  
  
 <span data-ttu-id="1fd62-110">O exemplo a seguir mostra como definir um horizontal <xref:System.Windows.Controls.GridSplitter> que redimensiona linhas adjacentes.</span><span class="sxs-lookup"><span data-stu-id="1fd62-110">The following example shows how to define a horizontal <xref:System.Windows.Controls.GridSplitter> that resizes adjacent rows.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 <span data-ttu-id="1fd62-111">Um <xref:System.Windows.Controls.GridSplitter> que não ocupa sua própria linha podem ser encobertas por outros controles no <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="1fd62-111">A <xref:System.Windows.Controls.GridSplitter> that does not occupy its own row may be obscured by other controls in the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="1fd62-112">Para obter mais informações sobre como evitar esse problema, consulte [Verifique se um GridSplitter está visível](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span><span class="sxs-lookup"><span data-stu-id="1fd62-112">For more information about how to prevent this issue, see [Make Sure That a GridSplitter Is Visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span></span>  
  
 <span data-ttu-id="1fd62-113">**Como criar um GridSplitter que ocupa uma linha**</span><span class="sxs-lookup"><span data-stu-id="1fd62-113">**How to create a GridSplitter that occupies a row**</span></span>  
  
 <span data-ttu-id="1fd62-114">Para especificar um <xref:System.Windows.Controls.GridSplitter> que ocupa uma linha em uma <xref:System.Windows.Controls.Grid>, defina o <xref:System.Windows.Controls.Grid.Row%2A> propriedade anexada a uma das linhas que você deseja redimensionar.</span><span class="sxs-lookup"><span data-stu-id="1fd62-114">To specify a <xref:System.Windows.Controls.GridSplitter> that occupies a row in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Row%2A> attached property to one of the rows that you want to resize.</span></span> <span data-ttu-id="1fd62-115">Se seu <xref:System.Windows.Controls.Grid> tem mais de uma coluna, defina o <xref:System.Windows.Controls.Grid.ColumnSpan%2A> propriedade anexada ao número de colunas.</span><span class="sxs-lookup"><span data-stu-id="1fd62-115">If your <xref:System.Windows.Controls.Grid> has more than one column, set the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> attached property to the number of columns.</span></span> <span data-ttu-id="1fd62-116">Em seguida, defina o <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> para <xref:System.Windows.VerticalAlignment.Center>, defina o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade <xref:System.Windows.HorizontalAlignment.Stretch>e defina o <xref:System.Windows.Controls.RowDefinition.Height%2A> da linha que contém o <xref:System.Windows.Controls.GridSplitter> para <xref:System.Windows.GridLength.Auto%2A>.</span><span class="sxs-lookup"><span data-stu-id="1fd62-116">Then set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> to <xref:System.Windows.VerticalAlignment.Center>, set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Stretch>, and set the <xref:System.Windows.Controls.RowDefinition.Height%2A> of the row that contains the <xref:System.Windows.Controls.GridSplitter> to <xref:System.Windows.GridLength.Auto%2A>.</span></span>  
  
 <span data-ttu-id="1fd62-117">O exemplo a seguir mostra como definir um horizontal <xref:System.Windows.Controls.GridSplitter> que ocupa uma linha e redimensione as linhas em dos lados.</span><span class="sxs-lookup"><span data-stu-id="1fd62-117">The following example shows how to define a horizontal <xref:System.Windows.Controls.GridSplitter> that occupies a row and resizes the rows on either side of it.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a><span data-ttu-id="1fd62-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1fd62-118">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="1fd62-119">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="1fd62-119">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
