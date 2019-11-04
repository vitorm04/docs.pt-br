---
title: Como classificar dados em uma exibição
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], sorting data in views
- data binding [WPF], grouping data in views
- grouping data in views [WPF]
- views [WPF], sorting data
- views [WPF], grouping data
- sorting data in views [WPF]
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
ms.openlocfilehash: 14314ed019f9194a657787bd767ae68615e94ac7
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454834"
---
# <a name="how-to-sort-data-in-a-view"></a><span data-ttu-id="f3ac2-102">Como classificar dados em uma exibição</span><span class="sxs-lookup"><span data-stu-id="f3ac2-102">How to: Sort Data in a View</span></span>
<span data-ttu-id="f3ac2-103">Este exemplo descreve como classificar dados em uma exibição.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-103">This example describes how to sort data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3ac2-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3ac2-104">Example</span></span>  
 <span data-ttu-id="f3ac2-105">O exemplo a seguir cria um <xref:System.Windows.Controls.ListBox> simples e um <xref:System.Windows.Controls.Button>:</span><span class="sxs-lookup"><span data-stu-id="f3ac2-105">The following example creates a simple <xref:System.Windows.Controls.ListBox> and a <xref:System.Windows.Controls.Button>:</span></span>  
  
 [!code-xaml[ListBoxSort_snip#HowTo](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <span data-ttu-id="f3ac2-106">O manipulador de eventos <xref:System.Windows.Controls.Primitives.ButtonBase.Click> do botão contém a lógica para classificar os itens na <xref:System.Windows.Controls.ListBox> na ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-106">The <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler of the button contains logic to sort the items in the <xref:System.Windows.Controls.ListBox> in the descending order.</span></span> <span data-ttu-id="f3ac2-107">Você pode fazer isso porque adicionar itens a um <xref:System.Windows.Controls.ListBox> dessa maneira os adiciona ao <xref:System.Windows.Controls.ItemCollection> do <xref:System.Windows.Controls.ListBox>e <xref:System.Windows.Controls.ItemCollection> deriva da classe <xref:System.Windows.Data.CollectionView>.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-107">You can do this because adding items to a <xref:System.Windows.Controls.ListBox> this way adds them to the <xref:System.Windows.Controls.ItemCollection> of the <xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.ItemCollection> derives from the <xref:System.Windows.Data.CollectionView> class.</span></span> <span data-ttu-id="f3ac2-108">Se você estiver associando seu <xref:System.Windows.Controls.ListBox> a uma coleção usando a propriedade <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, poderá usar a mesma técnica para classificar.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-108">If you are binding your <xref:System.Windows.Controls.ListBox> to a collection using the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property, you can use the same technique to sort.</span></span>  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 <span data-ttu-id="f3ac2-109">Desde que você tenha uma referência ao objeto de exibição, é possível usar a mesma técnica para classificar o conteúdo de outros modos de exibição de coleção.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-109">As long as you have a reference to the view object, you can use the same technique to sort the content of other collection views.</span></span> <span data-ttu-id="f3ac2-110">Para um exemplo de como obter uma exibição, consulte [Obter a exibição padrão de uma coleção de dados](how-to-get-the-default-view-of-a-data-collection.md).</span><span class="sxs-lookup"><span data-stu-id="f3ac2-110">For an example of how to obtain a view, see [Get the Default View of a Data Collection](how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="f3ac2-111">Para outro exemplo, consulte [Classificar uma coluna GridView quando um cabeçalho é clicado](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span><span class="sxs-lookup"><span data-stu-id="f3ac2-111">For another example, see [Sort a GridView Column When a Header Is Clicked](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span></span> <span data-ttu-id="f3ac2-112">Para obter mais informações sobre modos de exibição, consulte associação a coleções em [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f3ac2-112">For more information about views, see Binding to Collections in [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="f3ac2-113">Para obter um exemplo de como aplicar a lógica de classificação em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], consulte [Classificar e agrupar dados usando um modo de exibição em XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="f3ac2-113">For an example of how to apply sorting logic in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], see [Sort and Group Data Using a View in XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3ac2-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3ac2-114">See also</span></span>

- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [<span data-ttu-id="f3ac2-115">Classificar uma coluna GridView quando um cabeçalho é clicado</span><span class="sxs-lookup"><span data-stu-id="f3ac2-115">Sort a GridView Column When a Header Is Clicked</span></span>](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [<span data-ttu-id="f3ac2-116">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="f3ac2-116">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="f3ac2-117">Filtrar dados em uma exibição</span><span class="sxs-lookup"><span data-stu-id="f3ac2-117">Filter Data in a View</span></span>](how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="f3ac2-118">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="f3ac2-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
