---
title: 'Como: Navegar pelos objetos em um CollectionView de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
ms.openlocfilehash: 1507ab4db0c91b670d8bca754f6fd67d887c7041
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138171"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a>Como: Navegar pelos objetos em um CollectionView de dados
As exibições permitem que a mesma coleção de dados seja visualizada de diferentes maneiras, dependendo da classificação, filtragem ou agrupamento. Os modos de exibição também fornecem um conceito de ponteiro de registro atual e permitem a movimentação do ponteiro. Este exemplo mostra como obter o objeto atual, bem como navegar pelos objetos em uma coleção de dados usando a funcionalidade fornecida no <xref:System.Windows.Data.CollectionView> classe.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, `myCollectionView` é um <xref:System.Windows.Data.CollectionView> objeto que é um modo de exibição sobre uma coleção associada.  
  
 No exemplo a seguir, o `OnButton` é um manipulador de eventos para os botões `Previous` e `Next` em um aplicativo, que são botões que permitem que o usuário navegue pela coleção de dados. Observe que o <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> e <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> propriedades de relatório se o ponteiro de registro atual chegou até o início e o final da lista respectivamente assim que <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> e <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> podem ser chamados adequadamente.  
  
 O <xref:System.Windows.Data.CollectionView.CurrentItem%2A> propriedade do modo de exibição é convertida como um `Order` para retornar o item atual da ordem na coleção.  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Classificar dados em uma exibição](how-to-sort-data-in-a-view.md)
- [Filtrar dados em uma exibição](how-to-filter-data-in-a-view.md)
- [Classificar e agrupar dados usando uma exibição em XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Tópicos explicativos ](data-binding-how-to-topics.md)
