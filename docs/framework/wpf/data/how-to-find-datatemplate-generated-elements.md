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
ms.openlocfilehash: 3b222880aa4eda32502e3dcece2fa5c0b57b7a51
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646428"
---
# <a name="how-to-find-datatemplate-generated-elements"></a>Como encontrar elementos DataTemplate-Generated
Este exemplo mostra como encontrar elementos <xref:System.Windows.DataTemplate>gerados por um .  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, há <xref:System.Windows.Controls.ListBox> um que está vinculado a alguns dados XML:  
  
 [!code-xaml[FindGeneratedItems#LB](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 Os <xref:System.Windows.Controls.ListBox> usos <xref:System.Windows.DataTemplate>são:  
  
 [!code-xaml[FindGeneratedItems#DT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 Se você quiser <xref:System.Windows.Controls.TextBlock> recuperar o <xref:System.Windows.DataTemplate> elemento gerado <xref:System.Windows.Controls.ListBoxItem>pelo de um <xref:System.Windows.Controls.ListBoxItem>certo <xref:System.Windows.Controls.ContentPresenter> , <xref:System.Windows.Controls.ListBoxItem>você precisa <xref:System.Windows.FrameworkTemplate.FindName%2A> obter <xref:System.Windows.DataTemplate> o , encontrar <xref:System.Windows.Controls.ContentPresenter>o dentro disso , e, em seguida, chamar o que está definido sobre isso . O exemplo a seguir mostra como executar essas etapas. Para fins de demonstração, este exemplo cria uma <xref:System.Windows.DataTemplate>caixa de mensagem que mostra o conteúdo do texto do bloco de texto gerado.  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 A seguir está `FindVisualChild`a implementação <xref:System.Windows.Media.VisualTreeHelper> de , que usa os métodos:  
  
 [!code-csharp[FindGeneratedItems#FVC](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>Confira também

- [Como localizar elementos gerados por ControlTemplate](../controls/how-to-find-controltemplate-generated-elements.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Namescopes XAML WPF](../advanced/wpf-xaml-namescopes.md)
- [Árvores no WPF](../advanced/trees-in-wpf.md)
