---
title: "Como verificar se um GridSplitter está visível"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8692d356b1b20c7405b4478cef1d16c173389ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a>Como verificar se um GridSplitter está visível
Este exemplo mostra como verificar se um <xref:System.Windows.Controls.GridSplitter> controle não está oculto pelos outros controles em um <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Controls.Panel.Children%2A> de um <xref:System.Windows.Controls.Grid> controle são renderizados na ordem que eles estão definidos na marcação ou código. <xref:System.Windows.Controls.GridSplitter>controles podem estar ocultos por outros controles, se você não defini-los como os últimos elementos no <xref:System.Windows.Controls.Panel.Children%2A> coleção ou se você fornecer a outros controles de posterior <xref:System.Windows.Controls.Panel.ZIndexProperty>.  
  
 Para impedir que oculta <xref:System.Windows.Controls.GridSplitter> controles, faça o seguinte.  
  
-   Verifique se <xref:System.Windows.Controls.GridSplitter> controles são as últimas <xref:System.Windows.Controls.Panel.Children%2A> adicionado para o <xref:System.Windows.Controls.Grid>. A exemplo a seguir mostra o <xref:System.Windows.Controls.GridSplitter> como o último elemento de <xref:System.Windows.Controls.Panel.Children%2A> coleção do <xref:System.Windows.Controls.Grid>.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   Definir o <xref:System.Windows.Controls.Panel.ZIndexProperty> no <xref:System.Windows.Controls.GridSplitter> seja maior do que um controle que outra forma seria ocultá-lo. O exemplo a seguir fornece o <xref:System.Windows.Controls.GridSplitter> controlar posterior <xref:System.Windows.Controls.Panel.ZIndexProperty> que o <xref:System.Windows.Controls.Button> controle.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   Define as margens do controle que iria ocultar caso contrário, o <xref:System.Windows.Controls.GridSplitter> para que o <xref:System.Windows.Controls.GridSplitter> é exposto. O exemplo a seguir define margens em um controle que iria do contrário sobrepor e ocultar o <xref:System.Windows.Controls.GridSplitter>.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.GridSplitter>  
 [Tópicos explicativos](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
