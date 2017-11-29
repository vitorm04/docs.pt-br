---
title: Como encontrar elementos DataTemplate-Generated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- finding DataTemplate elements [WPF]
- DataTemplate [WPF]
ms.assetid: bfcd564e-5e9e-451e-8641-a9b5c3cfac90
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 22d5f393d376935f04459e2713e9658c80af6efa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
 [Tópicos explicativos](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Namescopes XAML WPF](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)  
 [Árvores no WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
