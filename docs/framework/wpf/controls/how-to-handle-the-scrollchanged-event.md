---
title: Como tratar o evento ScrollChanged
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], raising ScrollChanged events
- ScrollChanged events [WPF]
ms.assetid: 42c695d8-ee28-49d4-80fd-fc71e9be7f29
ms.openlocfilehash: da7c1d1174e3264b21763177487ebcb75a4b3192
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552695"
---
# <a name="how-to-handle-the-scrollchanged-event"></a>Como tratar o evento ScrollChanged
## <a name="example"></a>Exemplo  
 Este exemplo mostra como tratar o <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> eventos de um <xref:System.Windows.Controls.ScrollViewer>.  
  
 Um <xref:System.Windows.Documents.FlowDocument> elemento com <xref:System.Windows.Documents.Paragraph> partes é definido em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Quando o <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> evento ocorre devido à interação do usuário, um manipulador é chamado e o texto foi escrito para um <xref:System.Windows.Controls.TextBlock> indicando que o evento ocorreu.  
  
 [!code-xaml[scrollchangedeventargsLayout#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#1)]  
[!code-xaml[scrollchangedeventargsLayout#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[scrollchangedeventargsLayout#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml.cs#3)]
 [!code-vb[scrollchangedeventargsLayout#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/scrollchangedeventargsLayout/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.ScrollViewer.ScrollChanged>  
 <xref:System.Windows.Controls.ScrollChangedEventHandler>  
 <xref:System.Windows.Controls.ScrollChangedEventArgs>
