---
title: 'Como: Alinhar horizontal ou verticalmente o conteúdo em um StackPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: 03348aa0eb5b6c1791c27683c1c6c6a5d4a8a9d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771027"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a>Como: Alinhar horizontal ou verticalmente o conteúdo em um StackPanel
Este exemplo mostra como ajustar o <xref:System.Windows.Controls.StackPanel.Orientation%2A> de conteúdo dentro de uma <xref:System.Windows.Controls.StackPanel> elemento e também como ajustar o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> e <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> do conteúdo filho.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria três <xref:System.Windows.Controls.ListBox> elementos em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Cada <xref:System.Windows.Controls.ListBox> representa os possíveis valores da <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, e <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> as propriedades de um <xref:System.Windows.Controls.StackPanel>. Quando um usuário seleciona um valor em qualquer um dos <xref:System.Windows.Controls.ListBox> elementos, a propriedade associada do <xref:System.Windows.Controls.StackPanel> e seu filho <xref:System.Windows.Controls.Button> alterar elementos.  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 O arquivo de code-behind a seguir define as alterações para os eventos que estão associados a <xref:System.Windows.Controls.ListBox> alterações de seleção. <xref:System.Windows.Controls.StackPanel> é identificado pela <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [Visão geral de painéis](panels-overview.md)
