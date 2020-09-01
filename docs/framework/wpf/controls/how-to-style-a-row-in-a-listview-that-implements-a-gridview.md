---
title: 'Como: Estilizar uma linha em um ListView que usa um GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 4b8b8e2f1b2d7207a37205d981bf2dab3f65122e
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271939"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>Como criar uma linha em um ListView que implemente um GridView
Este exemplo mostra como Estilizar uma linha em um <xref:System.Windows.Controls.ListView> controle que usa um <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> modo.  
  
## <a name="example"></a>Exemplo  
 Você pode Estilizar uma linha em um <xref:System.Windows.Controls.ListView> controle definindo um <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> no <xref:System.Windows.Controls.ListView> controle. Defina o estilo para seus itens que são representados como <xref:System.Windows.Controls.ListViewItem> objetos. O <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> faz referência aos <xref:System.Windows.Controls.ControlTemplate> objetos que são usados para exibir o conteúdo da linha.  
  
 O exemplo completo, do qual os exemplos a seguir são extraídos, exibe uma coleção de informações de música que são armazenadas em um banco de dados XML. Cada música no banco de dados tem um campo de classificação e o valor desse campo especifica como exibir uma linha de informações sobre a música.  
  
 O exemplo a seguir mostra como definir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> para os <xref:System.Windows.Controls.ListViewItem> objetos que representam as músicas na coleção de músicas. Os <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> objetos de referências <xref:System.Windows.Controls.ControlTemplate> que especificam como exibir uma linha de informações de música.  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 O exemplo a seguir mostra um <xref:System.Windows.Controls.ControlTemplate> que adiciona a cadeia de texto `"Strongly Recommended"` à linha. Esse modelo é referenciado no <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> e exibe quando a classificação da música tem um valor de 5 (cinco). O <xref:System.Windows.Controls.ControlTemplate> inclui um <xref:System.Windows.Controls.GridViewRowPresenter> objeto que dispõe o conteúdo da linha em colunas, conforme definido pelo modo de <xref:System.Windows.Controls.GridView> exibição.  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 O exemplo a seguir define <xref:System.Windows.Controls.GridView> .  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Tópicos de instruções](listview-how-to-topics.md)
- [Visão geral de ListView](listview-overview.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
