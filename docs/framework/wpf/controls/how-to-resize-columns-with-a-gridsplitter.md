---
title: Como redimensionar colunas com um GridSplitter
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d68d829e5543b1c299668493c11b62ccb11d81af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a><span data-ttu-id="f7fe6-102">Como redimensionar colunas com um GridSplitter</span><span class="sxs-lookup"><span data-stu-id="f7fe6-102">How to: Resize Columns with a GridSplitter</span></span>
<span data-ttu-id="f7fe6-103">Este exemplo mostra como criar um vertical <xref:System.Windows.Controls.GridSplitter> para redistribuir o espaço entre duas colunas em uma <xref:System.Windows.Controls.Grid> sem alterar as dimensões do <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-103">This example shows how to create a vertical <xref:System.Windows.Controls.GridSplitter> in order to redistribute the space between two columns in a <xref:System.Windows.Controls.Grid> without changing the dimensions of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7fe6-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7fe6-104">Example</span></span>  
 <span data-ttu-id="f7fe6-105">**Como criar um GridSplitter que sobrepõe a borda de uma coluna**</span><span class="sxs-lookup"><span data-stu-id="f7fe6-105">**How to create a GridSplitter that overlays the edge of a column**</span></span>  
  
 <span data-ttu-id="f7fe6-106">Para especificar um <xref:System.Windows.Controls.GridSplitter> que redimensiona colunas adjacentes em uma <xref:System.Windows.Controls.Grid>, defina o <xref:System.Windows.Controls.Grid.Column%2A> propriedade anexada a uma das colunas que você deseja redimensionar.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-106">To specify a <xref:System.Windows.Controls.GridSplitter> that resizes adjacent columns in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Column%2A> attached property to one of the columns that you want to resize.</span></span> <span data-ttu-id="f7fe6-107">Se seu <xref:System.Windows.Controls.Grid> tem mais de uma linha, defina a <xref:System.Windows.Controls.Grid.RowSpan%2A> propriedade anexada ao número de linhas.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-107">If your <xref:System.Windows.Controls.Grid> has more than one row, set the <xref:System.Windows.Controls.Grid.RowSpan%2A> attached property to the number of rows.</span></span> <span data-ttu-id="f7fe6-108">Em seguida, defina o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade <xref:System.Windows.HorizontalAlignment.Left> ou <xref:System.Windows.HorizontalAlignment.Right> (o alinhamento que você define depende de quais duas colunas você deseja redimensionar).</span><span class="sxs-lookup"><span data-stu-id="f7fe6-108">Then set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Left> or <xref:System.Windows.HorizontalAlignment.Right> (which alignment you set depends on which two columns you want to resize).</span></span> <span data-ttu-id="f7fe6-109">Finalmente, defina o <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriedade <xref:System.Windows.VerticalAlignment.Stretch>.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-109">Finally, set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> property to <xref:System.Windows.VerticalAlignment.Stretch>.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 <span data-ttu-id="f7fe6-110">Um <xref:System.Windows.Controls.GridSplitter> que não tem sua própria coluna podem ser encobertas por outros controles no <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-110">A <xref:System.Windows.Controls.GridSplitter> that does not have its own column may be obscured by other controls in the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="f7fe6-111">Para obter mais informações sobre como evitar esse problema, consulte [Verifique se um GridSplitter está visível](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span><span class="sxs-lookup"><span data-stu-id="f7fe6-111">For more information about how to prevent this issue, see [Make Sure That a GridSplitter Is Visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span></span>  
  
 <span data-ttu-id="f7fe6-112">**Como criar um GridSplitter que ocupa uma coluna**</span><span class="sxs-lookup"><span data-stu-id="f7fe6-112">**How to create a GridSplitter that occupies a column**</span></span>  
  
 <span data-ttu-id="f7fe6-113">Para especificar um <xref:System.Windows.Controls.GridSplitter> que ocupa uma coluna em uma <xref:System.Windows.Controls.Grid>, defina o <xref:System.Windows.Controls.Grid.Column%2A> propriedade anexada a uma das colunas que você deseja redimensionar.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-113">To specify a <xref:System.Windows.Controls.GridSplitter> that occupies a column in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Column%2A> attached property to one of the columns that you want to resize.</span></span> <span data-ttu-id="f7fe6-114">Se a grade tem mais de uma linha, defina a <xref:System.Windows.Controls.Grid.RowSpan%2A> propriedade anexada ao número de linhas.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-114">If your Grid has more than one row, set the <xref:System.Windows.Controls.Grid.RowSpan%2A> attached property to the number of rows.</span></span> <span data-ttu-id="f7fe6-115">Em seguida, defina o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> para <xref:System.Windows.HorizontalAlignment.Center>, defina o <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriedade <xref:System.Windows.VerticalAlignment.Stretch>e defina o <xref:System.Windows.Controls.ColumnDefinition.Width%2A> da coluna que contém o <xref:System.Windows.Controls.GridSplitter> para <xref:System.Windows.GridLength.Auto%2A>.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-115">Then set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> to <xref:System.Windows.HorizontalAlignment.Center>, set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> property to <xref:System.Windows.VerticalAlignment.Stretch>, and set the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the column that contains the <xref:System.Windows.Controls.GridSplitter> to <xref:System.Windows.GridLength.Auto%2A>.</span></span>  
  
 <span data-ttu-id="f7fe6-116">O exemplo a seguir mostra como definir um vertical <xref:System.Windows.Controls.GridSplitter> que ocupa uma coluna e redimensiona as colunas em dos lados.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-116">The following example shows how to define a vertical <xref:System.Windows.Controls.GridSplitter> that occupies a column and resizes the columns on either side of it.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a><span data-ttu-id="f7fe6-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7fe6-117">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="f7fe6-118">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="f7fe6-118">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
