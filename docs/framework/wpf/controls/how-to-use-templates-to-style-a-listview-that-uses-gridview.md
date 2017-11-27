---
title: Como usar modelos para criar um ListView que use GridView
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 246c144a18d7c1014096a6e37ad09b6eec5ad932
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a>Como usar modelos para criar um ListView que use GridView
Este exemplo mostra como usar o <xref:System.Windows.DataTemplate> e <xref:System.Windows.Style> objetos para especificar a aparência de um <xref:System.Windows.Controls.ListView> controle que usa um <xref:System.Windows.Controls.GridView> modo de exibição.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram <xref:System.Windows.Style> e <xref:System.Windows.DataTemplate> objetos que personalizam a aparência de um cabeçalho de coluna para um <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 O exemplo a seguir mostra como usar esses <xref:System.Windows.Style> e <xref:System.Windows.DataTemplate> objetos para definir o <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> e <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> propriedades de um <xref:System.Windows.Controls.GridViewColumn>. O <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> propriedade define o conteúdo das células da coluna.  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 O <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> e <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> são apenas duas das várias propriedades que você pode usar para personalizar a aparência de cabeçalho de coluna para um <xref:System.Windows.Controls.GridView> controle. Para obter mais informações, consulte [Visão geral de modelos e estilos de cabeçalho de coluna GridView](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).  
  
 O exemplo a seguir mostra como definir um <xref:System.Windows.DataTemplate> que personaliza a aparência de células em um <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 O exemplo a seguir mostra como usar este <xref:System.Windows.DataTemplate> para definir o conteúdo de um <xref:System.Windows.Controls.GridViewColumn> célula. Este modelo é usado em vez do <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> mostrado anteriormente na propriedade <xref:System.Windows.Controls.GridViewColumn> exemplo.  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Visão geral de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Tópicos explicativos](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [Visão geral de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)
