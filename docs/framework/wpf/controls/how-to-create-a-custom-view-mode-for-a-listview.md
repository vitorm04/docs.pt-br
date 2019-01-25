---
title: 'Como: Criar um modo de exibição personalizado para um ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 336e4ee911d18836eafa6f444c8d900c117acad3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545271"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="6595c-102">Como: Criar um modo de exibição personalizado para um ListView</span><span class="sxs-lookup"><span data-stu-id="6595c-102">How to: Create a Custom View Mode for a ListView</span></span>
<span data-ttu-id="6595c-103">Este exemplo mostra como criar um personalizado <xref:System.Windows.Controls.ListView.View%2A> modo para um <xref:System.Windows.Controls.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="6595c-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6595c-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6595c-104">Example</span></span>  
 <span data-ttu-id="6595c-105">Você deve usar o <xref:System.Windows.Controls.ViewBase> classe quando você cria uma exibição personalizada para o <xref:System.Windows.Controls.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="6595c-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="6595c-106">O exemplo a seguir mostra um modo de exibição que é chamado `PlainView`, que é derivado do <xref:System.Windows.Controls.ViewBase> classe.</span><span class="sxs-lookup"><span data-stu-id="6595c-106">The following example shows a view mode that is called `PlainView`, which is derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="6595c-107">Para aplicar um estilo para o modo de exibição personalizado, use o <xref:System.Windows.Style> classe.</span><span class="sxs-lookup"><span data-stu-id="6595c-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="6595c-108">O exemplo a seguir define uma <xref:System.Windows.Style> para o `PlainView` modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="6595c-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="6595c-109">No exemplo anterior, esse estilo é definido como o valor da <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> propriedade definida para `PlainView`.</span><span class="sxs-lookup"><span data-stu-id="6595c-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that is defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="6595c-110">Para definir o layout dos dados em um modo de exibição personalizado, defina um <xref:System.Windows.DataTemplate> objeto.</span><span class="sxs-lookup"><span data-stu-id="6595c-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="6595c-111">O exemplo a seguir define uma <xref:System.Windows.DataTemplate> que pode ser usado para exibir dados no `PlainView` modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="6595c-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="6595c-112">O exemplo a seguir mostra como definir um <xref:System.Windows.ResourceKey> para o `PlainView` modo de exibição que usa o <xref:System.Windows.DataTemplate> que é definido no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="6595c-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="6595c-113">Um <xref:System.Windows.Controls.ListView> controle pode usar uma exibição personalizada se você definir o <xref:System.Windows.Controls.ListView.View%2A> propriedade para a chave de recurso.</span><span class="sxs-lookup"><span data-stu-id="6595c-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="6595c-114">O exemplo a seguir mostra como especificar `PlainView` como o modo de exibição para um <xref:System.Windows.Controls.ListView>.</span><span class="sxs-lookup"><span data-stu-id="6595c-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="6595c-115">Para o exemplo completo, consulte [ListView com várias exibições (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) ou [ListView com várias Views(Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).</span><span class="sxs-lookup"><span data-stu-id="6595c-115">For the complete sample, see [ListView with Multiple Views(C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) or [ListView with Multiple Views(Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6595c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6595c-116">See also</span></span>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="6595c-117">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="6595c-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
- [<span data-ttu-id="6595c-118">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="6595c-118">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
- [<span data-ttu-id="6595c-119">Visão geral de GridView</span><span class="sxs-lookup"><span data-stu-id="6595c-119">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
