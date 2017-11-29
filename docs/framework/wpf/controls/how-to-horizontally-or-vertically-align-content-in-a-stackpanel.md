---
title: "Como alinhar horizontal e verticalmente o conteúdo em um StackPanel"
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
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bccf0455c736d14bd77113841603022d4c362787
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a>Como alinhar horizontal e verticalmente o conteúdo em um StackPanel
Este exemplo mostra como ajustar o <xref:System.Windows.Controls.StackPanel.Orientation%2A> de conteúdo em um <xref:System.Windows.Controls.StackPanel> elemento e também como ajustar o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> e <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> conteúdo filho.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria três <xref:System.Windows.Controls.ListBox> elementos [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Cada <xref:System.Windows.Controls.ListBox> representa os possíveis valores a <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, e <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriedades de um <xref:System.Windows.Controls.StackPanel>. Quando um usuário seleciona um valor em qualquer uma da <xref:System.Windows.Controls.ListBox> elementos, a propriedade associada do <xref:System.Windows.Controls.StackPanel> e seu filho <xref:System.Windows.Controls.Button> alterar elementos.  
  
 [!code-xaml[StackPanelIntroSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 O arquivo de code-behind a seguir define as alterações para os eventos que estão associados a <xref:System.Windows.Controls.ListBox> alterações de seleção. <xref:System.Windows.Controls.StackPanel>é identificado pelo <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.  
  
 [!code-csharp[StackPanelIntroSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>  
 [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)
