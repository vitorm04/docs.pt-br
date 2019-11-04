---
title: Como criar uma linha em um ListView que implemente um GridView
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 150988aab368e3ffef0107d29bea5ebc53163946
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459312"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>Como criar uma linha em um ListView que implemente um GridView
Este exemplo mostra como Estilizar uma linha em um controle de <xref:System.Windows.Controls.ListView> que implementa um modo de <xref:System.Windows.Controls.ListView.View%2A> de <xref:System.Windows.Controls.GridView>.  
  
## <a name="example"></a>Exemplo  
 Você pode Estilizar uma linha em um controle de <xref:System.Windows.Controls.ListView> definindo um <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> no controle de <xref:System.Windows.Controls.ListView>. Defina o estilo para seus itens que são representados como objetos <xref:System.Windows.Controls.ListViewItem>. O <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> faz referência aos objetos <xref:System.Windows.Controls.ControlTemplate> usados para exibir o conteúdo da linha.  
  
 O exemplo completo, do qual os exemplos a seguir foram extraídos, exibe uma coleção de informações de músicas que são armazenadas em um banco de dados do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Cada música no banco de dados tem um campo de classificação e o valor desse campo especifica como exibir uma linha de informações sobre a música.  
  
 O exemplo a seguir mostra como definir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> para os objetos <xref:System.Windows.Controls.ListViewItem> que representam as músicas na coleção de músicas. O <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> faz referência a objetos <xref:System.Windows.Controls.ControlTemplate> que especificam como exibir uma linha de informações de música.  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 O exemplo a seguir mostra um <xref:System.Windows.Controls.ControlTemplate> que adiciona a cadeia de caracteres de texto `"Strongly Recommended"` à linha. Esse modelo é referenciado na <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> e é exibido quando a classificação da música tem um valor de 5 (cinco). O <xref:System.Windows.Controls.ControlTemplate> inclui um objeto <xref:System.Windows.Controls.GridViewRowPresenter> que dispõe o conteúdo da linha em colunas, conforme definido pelo modo de exibição <xref:System.Windows.Controls.GridView>.  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 O exemplo a seguir define <xref:System.Windows.Controls.GridView>.  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Tópicos explicativos](listview-how-to-topics.md)
- [Visão geral de ListView](listview-overview.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
