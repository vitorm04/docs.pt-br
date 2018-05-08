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
ms.openlocfilehash: d46a408bc1b5fc512905aa5bf176b13bd1511865
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-datatemplate-generated-elements"></a>Como encontrar elementos DataTemplate-Generated
Este exemplo mostra como localizar elementos que são gerados por um <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, há um <xref:System.Windows.Controls.ListBox> que é associado a alguns [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados:  
  
 [!code-xaml[FindGeneratedItems#LB](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 O <xref:System.Windows.Controls.ListBox> usa os seguintes <xref:System.Windows.DataTemplate>:  
  
 [!code-xaml[FindGeneratedItems#DT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 Se você quiser recuperar o <xref:System.Windows.Controls.TextBlock> elemento gerado pelo <xref:System.Windows.DataTemplate> de um determinado <xref:System.Windows.Controls.ListBoxItem>, você precisa obter o <xref:System.Windows.Controls.ListBoxItem>, localizar o <xref:System.Windows.Controls.ContentPresenter> dentro desse <xref:System.Windows.Controls.ListBoxItem>e, em seguida, chame <xref:System.Windows.FrameworkTemplate.FindName%2A> no <xref:System.Windows.DataTemplate> que é definido em que <xref:System.Windows.Controls.ContentPresenter>. O exemplo a seguir mostra como executar essas etapas. Para fins de demonstração, este exemplo cria uma caixa de mensagem que mostra o texto do conteúdo do <xref:System.Windows.DataTemplate>-gerado o bloco de texto.  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 O seguinte é a implementação do `FindVisualChild`, que usa o <xref:System.Windows.Media.VisualTreeHelper> métodos:  
  
 [!code-csharp[FindGeneratedItems#FVC](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>Consulte também  
 [Como localizar elementos gerados por ControlTemplate](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Namescopes XAML WPF](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)  
 [Árvores no WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
