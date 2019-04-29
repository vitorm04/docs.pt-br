---
title: 'Como: Implementar um CompositeCollection'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: 8361c2bfa9c125aeadf0a62ca86af1855e5c3dbc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931661"
---
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="a4209-102">Como: Implementar um CompositeCollection</span><span class="sxs-lookup"><span data-stu-id="a4209-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="a4209-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a4209-103">Example</span></span>  
 <span data-ttu-id="a4209-104">O exemplo a seguir mostra como exibir várias coleções e itens como uma lista usando o <xref:System.Windows.Data.CompositeCollection> classe.</span><span class="sxs-lookup"><span data-stu-id="a4209-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="a4209-105">Neste exemplo, `GreekGods` é um <xref:System.Collections.ObjectModel.ObservableCollection%601> de `GreekGod` objetos personalizados.</span><span class="sxs-lookup"><span data-stu-id="a4209-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="a4209-106">Modelos de dados são definidos para que `GreekGod` objetos e `GreekHero` objetos aparecem com um gold e uma cor de primeiro plano ciano, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="a4209-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a4209-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4209-107">See also</span></span>

- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [<span data-ttu-id="a4209-108">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="a4209-108">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="a4209-109">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="a4209-109">How-to Topics</span></span>](data-binding-how-to-topics.md)
