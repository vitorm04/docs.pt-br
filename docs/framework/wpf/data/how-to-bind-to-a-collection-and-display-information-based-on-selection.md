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
ms.openlocfilehash: 154f4b9b6024d064e73d64c44e2398a5da47052c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557401"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>Como associar a uma coleção e exibir informações com base na seleção
Em um cenário mestre-detalhes simples, você tem uma associação de dados <xref:System.Windows.Controls.ItemsControl> como um <xref:System.Windows.Controls.ListBox>. Com base na seleção do usuário, se exibe mais informações sobre o item selecionado. Este exemplo mostra como implementar este cenário.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, `People` é um <xref:System.Collections.ObjectModel.ObservableCollection%601> de `Person` classes. Esta classe `Person` contém três propriedades: `FirstName`, `LastName` e `HomeTown`, todas de tipo `string`.  
  
 [!code-xaml[CollectionBinding#Source](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 O <xref:System.Windows.Controls.ContentControl> usa os seguintes <xref:System.Windows.DataTemplate> que define como as informações de um `Person` é apresentado:  
  
 [!code-xaml[CollectionBinding#DetailTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 A seguir temos uma imagem do que o exemplo produz. O <xref:System.Windows.Controls.ContentControl> mostra as outras propriedades da pessoa selecionada.  
  
 ![Associando a uma coleção](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 As duas coisas a se observar neste exemplo são:  
  
1.  O <xref:System.Windows.Controls.ListBox> e <xref:System.Windows.Controls.ContentControl> ligar à mesma fonte. O <xref:System.Windows.Data.Binding.Path%2A> propriedades de ambas as associações não são especificadas porque ambos os controles são associação ao objeto de coleção inteira.  
  
2.  Você deve definir o <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> propriedade `true` para este trabalho. A definição dessa propriedade garante que o item selecionado é sempre definido como o <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Como alternativa, se o <xref:System.Windows.Controls.ListBox> obtém seus dados de um <xref:System.Windows.Data.CollectionViewSource>, ele sincroniza automaticamente seleção e moeda.  
  
 Observe que a classe `Person` substitui o método `ToString` da seguinte forma. Por padrão, o <xref:System.Windows.Controls.ListBox> chamadas `ToString` e exibe uma representação de cadeia de caracteres de cada objeto na coleção associada. É por isso que cada `Person` aparece como um nome no <xref:System.Windows.Controls.ListBox>.  
  
 [!code-csharp[CollectionBinding#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>Consulte também  
 [Usar o padrão de detalhes mestre com os dados hierárquicos](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)  
 [Usar o padrão de detalhes mestre com os dados XML hierárquicos](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Visão geral de modelagem dos dados](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
