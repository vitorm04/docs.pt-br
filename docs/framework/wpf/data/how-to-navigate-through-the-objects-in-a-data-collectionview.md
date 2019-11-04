---
title: Como navegar pelos objetos em um CollectionView de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
ms.openlocfilehash: 5ca386db89dcaa66d364d2ed7169c67393cebead
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459713"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a>Como navegar pelos objetos em um CollectionView de dados
As exibições permitem que a mesma coleção de dados seja visualizada de diferentes maneiras, dependendo da classificação, filtragem ou agrupamento. Os modos de exibição também fornecem um conceito de ponteiro de registro atual e permitem a movimentação do ponteiro. Este exemplo mostra como obter o objeto atual, bem como navegar pelos objetos em uma coleção de dados usando a funcionalidade fornecida na classe <xref:System.Windows.Data.CollectionView>.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, `myCollectionView` é um objeto <xref:System.Windows.Data.CollectionView> que é uma exibição em uma coleção associada.  
  
 No exemplo a seguir, o `OnButton` é um manipulador de eventos para os botões `Previous` e `Next` em um aplicativo, que são botões que permitem que o usuário navegue pela coleção de dados. Observe que as propriedades <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> e <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> relatam se o ponteiro de registro atual chegou ao início e ao fim da lista, respectivamente, para que <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> e <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> possam ser chamados conforme apropriado.  
  
 A propriedade <xref:System.Windows.Data.CollectionView.CurrentItem%2A> da exibição é convertida como uma `Order` para retornar o item do pedido atual na coleção.  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Classificar dados em uma exibição](how-to-sort-data-in-a-view.md)
- [Filtrar dados em uma exibição](how-to-filter-data-in-a-view.md)
- [Classificar e agrupar dados usando uma exibição em XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
