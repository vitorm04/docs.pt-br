---
title: Como implementar um CompositeCollection
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: f8af8d806b8c889be11533392ee3c831399e9ab7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="657c7-102">Como implementar um CompositeCollection</span><span class="sxs-lookup"><span data-stu-id="657c7-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="657c7-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="657c7-103">Example</span></span>  
 <span data-ttu-id="657c7-104">O exemplo a seguir mostra como exibir várias coleções e itens como uma lista usando o <xref:System.Windows.Data.CompositeCollection> classe.</span><span class="sxs-lookup"><span data-stu-id="657c7-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="657c7-105">Neste exemplo, `GreekGods` é um <xref:System.Collections.ObjectModel.ObservableCollection%601> de `GreekGod` objetos personalizados.</span><span class="sxs-lookup"><span data-stu-id="657c7-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="657c7-106">Modelos de dados são definidos para que `GreekGod` objetos e `GreekHero` objetos são exibidos com um gold e uma cor de primeiro plano ciano respectivamente.</span><span class="sxs-lookup"><span data-stu-id="657c7-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="657c7-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="657c7-107">See Also</span></span>  
 <xref:System.Windows.Data.CollectionContainer>  
 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>  
 <xref:System.Windows.Data.XmlDataProvider>  
 <xref:System.Windows.DataTemplate>  
 [<span data-ttu-id="657c7-108">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="657c7-108">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="657c7-109">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="657c7-109">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
