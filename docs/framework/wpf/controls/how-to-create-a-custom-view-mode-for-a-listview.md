---
title: Como criar um modo de exibição personalizado para um ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 3b9ca17bddcecb1895205fca76f0a489ecf25c4f
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243213"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="e8248-102">Como: Criar um modo de exibição personalizado para uma ListView</span><span class="sxs-lookup"><span data-stu-id="e8248-102">How to: Create a custom view mode for a ListView</span></span>

<span data-ttu-id="e8248-103">Este exemplo mostra como <xref:System.Windows.Controls.ListView.View%2A> criar um <xref:System.Windows.Controls.ListView> modo personalizado para um controle.</span><span class="sxs-lookup"><span data-stu-id="e8248-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8248-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e8248-104">Example</span></span>  
 <span data-ttu-id="e8248-105">Você deve <xref:System.Windows.Controls.ViewBase> usar a classe quando criar <xref:System.Windows.Controls.ListView> uma exibição personalizada para o controle.</span><span class="sxs-lookup"><span data-stu-id="e8248-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="e8248-106">O exemplo a seguir `PlainView` mostra um modo de <xref:System.Windows.Controls.ViewBase> exibição chamado derivado da classe.</span><span class="sxs-lookup"><span data-stu-id="e8248-106">The following example shows a view mode called `PlainView` that's derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="e8248-107">Para aplicar um estilo à exibição personalizada, use a <xref:System.Windows.Style> classe.</span><span class="sxs-lookup"><span data-stu-id="e8248-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="e8248-108">O exemplo a <xref:System.Windows.Style> seguir `PlainView` define um para o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="e8248-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="e8248-109">No exemplo anterior, esse estilo é definido <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> como o valor `PlainView`da propriedade definida para .</span><span class="sxs-lookup"><span data-stu-id="e8248-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that's defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="e8248-110">Para definir o layout dos dados em <xref:System.Windows.DataTemplate> um modo de exibição personalizado, defina um objeto.</span><span class="sxs-lookup"><span data-stu-id="e8248-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="e8248-111">O exemplo a <xref:System.Windows.DataTemplate> seguir define um que pode `PlainView` ser usado para exibir dados no modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="e8248-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="e8248-112">O exemplo a seguir <xref:System.Windows.ResourceKey> mostra `PlainView` como definir um <xref:System.Windows.DataTemplate> modo de exibição que usa o que é definido no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="e8248-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="e8248-113">Um <xref:System.Windows.Controls.ListView> controle pode usar uma exibição personalizada se você definir a <xref:System.Windows.Controls.ListView.View%2A> propriedade para a chave de recurso.</span><span class="sxs-lookup"><span data-stu-id="e8248-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="e8248-114">O exemplo a seguir `PlainView` mostra como especificar como o modo de exibição para a <xref:System.Windows.Controls.ListView>.</span><span class="sxs-lookup"><span data-stu-id="e8248-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="e8248-115">Para obter a amostra completa, consulte [ListView com Múltiplas visualizações (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) ou [ListView com múltiplas visualizações (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).</span><span class="sxs-lookup"><span data-stu-id="e8248-115">For the complete sample, see [ListView with Multiple Views (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) or [ListView with Multiple Views (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8248-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="e8248-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="e8248-117">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="e8248-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="e8248-118">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="e8248-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="e8248-119">Visão geral de GridView</span><span class="sxs-lookup"><span data-stu-id="e8248-119">GridView Overview</span></span>](gridview-overview.md)
