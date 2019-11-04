---
title: Como associar a uma coleção e exibir informações com base na seleção
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
ms.openlocfilehash: 032a1d98e1aa80ea755f5922f79d43a796e9697e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459151"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>Como associar a uma coleção e exibir informações com base na seleção
Em um cenário de detalhes mestre simples, você tem um <xref:System.Windows.Controls.ItemsControl> associado a dados, como um <xref:System.Windows.Controls.ListBox>. Com base na seleção do usuário, se exibe mais informações sobre o item selecionado. Este exemplo mostra como implementar este cenário.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, `People` é uma <xref:System.Collections.ObjectModel.ObservableCollection%601> de classes de `Person`. Esta classe `Person` contém três propriedades: `FirstName`, `LastName` e `HomeTown`, todas de tipo `string`.  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 O <xref:System.Windows.Controls.ContentControl> usa as seguintes <xref:System.Windows.DataTemplate> que definem como as informações de um `Person` são apresentadas:  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 A seguir temos uma imagem do que o exemplo produz. O <xref:System.Windows.Controls.ContentControl> mostra as outras propriedades da pessoa selecionada.  
  
 ![Associação a uma coleção](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 As duas coisas a se observar neste exemplo são:  
  
1. O <xref:System.Windows.Controls.ListBox> e o <xref:System.Windows.Controls.ContentControl> se associam à mesma fonte. As propriedades <xref:System.Windows.Data.Binding.Path%2A> de ambas as associações não são especificadas porque ambos os controles estão sendo vinculados a todo o objeto da coleção.  
  
2. Você deve definir a propriedade <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> como `true` para que isso funcione. Definir essa propriedade garante que o item selecionado sempre seja definido como o <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Como alternativa, se o <xref:System.Windows.Controls.ListBox> obtém dados de um <xref:System.Windows.Data.CollectionViewSource>, ele sincroniza a seleção e a moeda automaticamente.  
  
 Observe que a classe `Person` substitui o método `ToString` da seguinte forma. Por padrão, o <xref:System.Windows.Controls.ListBox> chama `ToString` e exibe uma representação de cadeia de caracteres de cada objeto na coleção associada. É por isso que cada `Person` aparece como um primeiro nome na <xref:System.Windows.Controls.ListBox>.  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>Consulte também

- [Usar o padrão de detalhes mestre com os dados hierárquicos](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [Usar o padrão de detalhes mestre com os dados XML hierárquicos](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Visão geral de modelagem dos dados](data-templating-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
