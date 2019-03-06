---
title: 'Como: Tratar o evento ScrollChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], raising ScrollChanged events
- ScrollChanged events [WPF]
ms.assetid: 42c695d8-ee28-49d4-80fd-fc71e9be7f29
ms.openlocfilehash: 34a3c97453df334e8c12da1a31cfb029294da687
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352510"
---
# <a name="how-to-handle-the-scrollchanged-event"></a><span data-ttu-id="f81df-102">Como: Tratar o evento ScrollChanged</span><span class="sxs-lookup"><span data-stu-id="f81df-102">How to: Handle the ScrollChanged Event</span></span>
## <a name="example"></a><span data-ttu-id="f81df-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f81df-103">Example</span></span>  
 <span data-ttu-id="f81df-104">Este exemplo mostra como lidar com o <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> eventos de um <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="f81df-104">This example shows how to handle the <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> event of a <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
 <span data-ttu-id="f81df-105">Um <xref:System.Windows.Documents.FlowDocument> elemento com <xref:System.Windows.Documents.Paragraph> partes é definido em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f81df-105">A <xref:System.Windows.Documents.FlowDocument> element with <xref:System.Windows.Documents.Paragraph> parts is defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="f81df-106">Quando o <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> evento ocorre devido à interação do usuário, um manipulador é invocado e o texto foi escrito para um <xref:System.Windows.Controls.TextBlock> indicando que o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="f81df-106">When the <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> event occurs due to user interaction, a handler is invoked, and text is written to a <xref:System.Windows.Controls.TextBlock> indicating that the event has occurred.</span></span>  
  
 [!code-xaml[scrollchangedeventargsLayout#1](~/samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#1)]  
[!code-xaml[scrollchangedeventargsLayout#2](~/samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[scrollchangedeventargsLayout#3](~/samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml.cs#3)]
 [!code-vb[scrollchangedeventargsLayout#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/scrollchangedeventargsLayout/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f81df-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f81df-107">See also</span></span>
- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.ScrollViewer.ScrollChanged>
- <xref:System.Windows.Controls.ScrollChangedEventHandler>
- <xref:System.Windows.Controls.ScrollChangedEventArgs>
