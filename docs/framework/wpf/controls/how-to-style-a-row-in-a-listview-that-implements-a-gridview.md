---
title: Como criar uma linha em um ListView que implemente um GridView
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e37d70fe1cb6aefb1404424c1a8f5339e0badf7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>Como criar uma linha em um ListView que implemente um GridView
Este exemplo mostra como definir o estilo de uma linha em uma <xref:System.Windows.Controls.ListView> controle que implementa um <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> modo.  
  
## <a name="example"></a>Exemplo  
 Você pode definir o estilo de uma linha em uma <xref:System.Windows.Controls.ListView> controle definindo uma <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> no <xref:System.Windows.Controls.ListView> controle. Definir o estilo de seus itens que são representados como <xref:System.Windows.Controls.ListViewItem> objetos. O <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> referências a <xref:System.Windows.Controls.ControlTemplate> objetos que são usados para exibir o conteúdo da linha.  
  
 O exemplo completo, do qual os exemplos a seguir foram extraídos, exibe uma coleção de informações de músicas que são armazenadas em um banco de dados do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Cada música no banco de dados tem um campo de classificação e o valor desse campo especifica como exibir uma linha de informações sobre a música.  
  
 O exemplo a seguir mostra como definir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> para o <xref:System.Windows.Controls.ListViewItem> objetos que representam as músicas na coleção de músicas. O <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> referências <xref:System.Windows.Controls.ControlTemplate> objetos que especificam como exibir uma linha de informações de músicas.  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 A exemplo a seguir mostra um <xref:System.Windows.Controls.ControlTemplate> que adiciona a cadeia de caracteres de texto `"Strongly Recommended"` para a linha. Este modelo é referenciado no <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> e exibe quando a classificação da música tem um valor de 5 (cinco). O <xref:System.Windows.Controls.ControlTemplate> inclui um <xref:System.Windows.Controls.GridViewRowPresenter> que dispõe o conteúdo da linha em colunas conforme definido pelo objeto de <xref:System.Windows.Controls.GridView> o modo de exibição.  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 O exemplo a seguir define <xref:System.Windows.Controls.GridView>.  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [Visão geral de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)
