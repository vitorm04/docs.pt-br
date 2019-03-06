---
title: 'Como: Implementar um CompositeCollection'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: 71d55a23711b116a91386a537d5572e8506d4c6b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372666"
---
# <a name="how-to-implement-a-compositecollection"></a>Como: Implementar um CompositeCollection
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como exibir várias coleções e itens como uma lista usando o <xref:System.Windows.Data.CompositeCollection> classe. Neste exemplo, `GreekGods` é um <xref:System.Collections.ObjectModel.ObservableCollection%601> de `GreekGod` objetos personalizados. Modelos de dados são definidos para que `GreekGod` objetos e `GreekHero` objetos aparecem com um gold e uma cor de primeiro plano ciano, respectivamente.  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)
