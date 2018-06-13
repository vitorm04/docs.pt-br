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
ms.locfileid: "33556111"
---
# <a name="how-to-implement-a-compositecollection"></a>Como implementar um CompositeCollection
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como exibir várias coleções e itens como uma lista usando o <xref:System.Windows.Data.CompositeCollection> classe. Neste exemplo, `GreekGods` é um <xref:System.Collections.ObjectModel.ObservableCollection%601> de `GreekGod` objetos personalizados. Modelos de dados são definidos para que `GreekGod` objetos e `GreekHero` objetos são exibidos com um gold e uma cor de primeiro plano ciano respectivamente.  
  
 [!code-xaml[CompositeCollections#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Data.CollectionContainer>  
 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>  
 <xref:System.Windows.Data.XmlDataProvider>  
 <xref:System.Windows.DataTemplate>  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
