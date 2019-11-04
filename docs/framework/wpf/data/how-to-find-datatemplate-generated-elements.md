---
title: Como encontrar elementos DataTemplate-Generated
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- finding DataTemplate elements [WPF]
- DataTemplate [WPF]
ms.assetid: bfcd564e-5e9e-451e-8641-a9b5c3cfac90
ms.openlocfilehash: f9265e3f7b287e1e8c264e89325f7c9649eebe2c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459135"
---
# <a name="how-to-find-datatemplate-generated-elements"></a>Como encontrar elementos DataTemplate-Generated
Este exemplo mostra como localizar elementos que são gerados por um <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, há um <xref:System.Windows.Controls.ListBox> associado a alguns dados de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]:  
  
 [!code-xaml[FindGeneratedItems#LB](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 O <xref:System.Windows.Controls.ListBox> usa os seguintes <xref:System.Windows.DataTemplate>:  
  
 [!code-xaml[FindGeneratedItems#DT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 Se você quiser recuperar o elemento <xref:System.Windows.Controls.TextBlock> gerado pela <xref:System.Windows.DataTemplate> de um determinado <xref:System.Windows.Controls.ListBoxItem>, você precisará obter o <xref:System.Windows.Controls.ListBoxItem>, localizar o <xref:System.Windows.Controls.ContentPresenter> dentro desse <xref:System.Windows.Controls.ListBoxItem>e, em seguida, chamar <xref:System.Windows.FrameworkTemplate.FindName%2A> na <xref:System.Windows.DataTemplate> que está definida em Esse <xref:System.Windows.Controls.ContentPresenter>. O exemplo a seguir mostra como executar essas etapas. Para fins de demonstração, este exemplo cria uma caixa de mensagem que mostra o conteúdo de texto do bloco de texto gerado pelo <xref:System.Windows.DataTemplate>.  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 A seguir está a implementação de `FindVisualChild`, que usa os métodos de <xref:System.Windows.Media.VisualTreeHelper>:  
  
 [!code-csharp[FindGeneratedItems#FVC](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>Consulte também

- [Como localizar elementos gerados por ControlTemplate](../controls/how-to-find-controltemplate-generated-elements.md)
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Namescopes XAML WPF](../advanced/wpf-xaml-namescopes.md)
- [Árvores no WPF](../advanced/trees-in-wpf.md)
