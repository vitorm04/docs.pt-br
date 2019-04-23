---
title: 'Como: Verificar se um GridSplitter está visível'
ms.date: 03/30/2017
helpviewer_keywords:
- GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
ms.openlocfilehash: b7543d14ba39d854b5a2c3f4d0d19b9a457ea89b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147141"
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a>Como: Verificar se um GridSplitter está visível
Este exemplo mostra como certificar-se um <xref:System.Windows.Controls.GridSplitter> controle não está oculto pelos outros controles em um <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Controls.Panel.Children%2A> de um <xref:System.Windows.Controls.Grid> controle são renderizados na ordem em que eles estão definidos na marcação ou código. <xref:System.Windows.Controls.GridSplitter> controles podem estar ocultos por outros controles se você não defini-los como os últimos elementos na <xref:System.Windows.Controls.Panel.Children%2A> coleção ou se você fornecer a outros controles um maior <xref:System.Windows.Controls.Panel.ZIndexProperty>.  
  
 Para impedir que oculta <xref:System.Windows.Controls.GridSplitter> controles, faça o seguinte.  
  
-   Certifique-se de que <xref:System.Windows.Controls.GridSplitter> controles são a última <xref:System.Windows.Controls.Panel.Children%2A> adicionado para o <xref:System.Windows.Controls.Grid>. A exemplo a seguir mostra a <xref:System.Windows.Controls.GridSplitter> como o último elemento em de <xref:System.Windows.Controls.Panel.Children%2A> coleção do <xref:System.Windows.Controls.Grid>.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   Defina a <xref:System.Windows.Controls.Panel.ZIndexProperty> no <xref:System.Windows.Controls.GridSplitter> para mais de um controle que o ocultaria. O exemplo a seguir fornece as <xref:System.Windows.Controls.GridSplitter> controlar um maior <xref:System.Windows.Controls.Panel.ZIndexProperty> que o <xref:System.Windows.Controls.Button> controle.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   Defina as margens no controle que ocultaria o <xref:System.Windows.Controls.GridSplitter> para que o <xref:System.Windows.Controls.GridSplitter> é exposto. O exemplo a seguir define margens em um controle que seria sobreporia e ocultar o <xref:System.Windows.Controls.GridSplitter>.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.GridSplitter>
- [Tópicos de instruções](gridsplitter-how-to-topics.md)
