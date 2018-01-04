---
title: Como redimensionar linhas com um GridSplitter
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d4cf06a86a1da7bb34074623f8f19f4bda7a724
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a>Como redimensionar linhas com um GridSplitter
Este exemplo mostra como usar um horizontal <xref:System.Windows.Controls.GridSplitter> para redistribuir o espaço entre duas linhas em uma <xref:System.Windows.Controls.Grid> sem alterar as dimensões do <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Exemplo  
 **Como criar um GridSplitter que sobrepõe a borda de uma linha**  
  
 Para especificar um <xref:System.Windows.Controls.GridSplitter> que redimensiona linhas adjacentes em um <xref:System.Windows.Controls.Grid>, defina o <xref:System.Windows.Controls.Grid.Row%2A> propriedade anexada a uma das linhas que você deseja redimensionar. Se seu <xref:System.Windows.Controls.Grid> tem mais de uma coluna, defina o <xref:System.Windows.Controls.Grid.ColumnSpan%2A> anexado a propriedade para especificar o número de colunas. Em seguida, defina o <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> para <xref:System.Windows.VerticalAlignment.Top> ou <xref:System.Windows.VerticalAlignment.Bottom> (o alinhamento que você define depende de quais duas linhas você deseja redimensionar). Finalmente, defina o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade <xref:System.Windows.HorizontalAlignment.Stretch>.  
  
 O exemplo a seguir mostra como definir um horizontal <xref:System.Windows.Controls.GridSplitter> que redimensiona linhas adjacentes.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 Um <xref:System.Windows.Controls.GridSplitter> que não ocupa sua própria linha podem ser encobertas por outros controles no <xref:System.Windows.Controls.Grid>. Para obter mais informações sobre como evitar esse problema, consulte [Verifique se um GridSplitter está visível](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Como criar um GridSplitter que ocupa uma linha**  
  
 Para especificar um <xref:System.Windows.Controls.GridSplitter> que ocupa uma linha em uma <xref:System.Windows.Controls.Grid>, defina o <xref:System.Windows.Controls.Grid.Row%2A> propriedade anexada a uma das linhas que você deseja redimensionar. Se seu <xref:System.Windows.Controls.Grid> tem mais de uma coluna, defina o <xref:System.Windows.Controls.Grid.ColumnSpan%2A> propriedade anexada ao número de colunas. Em seguida, defina o <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> para <xref:System.Windows.VerticalAlignment.Center>, defina o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade <xref:System.Windows.HorizontalAlignment.Stretch>e defina o <xref:System.Windows.Controls.RowDefinition.Height%2A> da linha que contém o <xref:System.Windows.Controls.GridSplitter> para <xref:System.Windows.GridLength.Auto%2A>.  
  
 O exemplo a seguir mostra como definir um horizontal <xref:System.Windows.Controls.GridSplitter> que ocupa uma linha e redimensione as linhas em dos lados.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.GridSplitter>  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
