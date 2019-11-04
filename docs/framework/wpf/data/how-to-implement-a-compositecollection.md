---
title: Como implementar um CompositeCollection
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: b3450cdc476b7090251a06b5b2b2718d29e18209
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454033"
---
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="c5059-102">Como implementar um CompositeCollection</span><span class="sxs-lookup"><span data-stu-id="c5059-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="c5059-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c5059-103">Example</span></span>  
 <span data-ttu-id="c5059-104">O exemplo a seguir mostra como exibir várias coleções e itens como uma lista usando a classe <xref:System.Windows.Data.CompositeCollection>.</span><span class="sxs-lookup"><span data-stu-id="c5059-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="c5059-105">Neste exemplo, `GreekGods` é uma <xref:System.Collections.ObjectModel.ObservableCollection%601> de `GreekGod` objetos personalizados.</span><span class="sxs-lookup"><span data-stu-id="c5059-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="c5059-106">Os modelos de dados são definidos de forma que `GreekGod` objetos e `GreekHero` objetos apareçam com uma cor de primeiro plano Gold e ciano, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="c5059-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c5059-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5059-107">See also</span></span>

- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [<span data-ttu-id="c5059-108">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="c5059-108">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c5059-109">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="c5059-109">How-to Topics</span></span>](data-binding-how-to-topics.md)
