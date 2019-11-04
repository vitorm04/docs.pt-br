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
# <a name="how-to-implement-a-compositecollection"></a>Como implementar um CompositeCollection
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como exibir várias coleções e itens como uma lista usando a classe <xref:System.Windows.Data.CompositeCollection>. Neste exemplo, `GreekGods` é uma <xref:System.Collections.ObjectModel.ObservableCollection%601> de `GreekGod` objetos personalizados. Os modelos de dados são definidos de forma que `GreekGod` objetos e `GreekHero` objetos apareçam com uma cor de primeiro plano Gold e ciano, respectivamente.  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
