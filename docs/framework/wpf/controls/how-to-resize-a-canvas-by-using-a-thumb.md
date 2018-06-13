---
title: Como redimensionar uma tela usando um elevador
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resizing Canvas control [WPF]
- controls [WPF], Thumb
- controls [WPF], Canvas
- Thumb control [WPF]
- Canvas control [WPF]
ms.assetid: 7dc9f435-726c-4d4d-be41-eb24cfe17bef
ms.openlocfilehash: c3e7176b0578c8fdc5f4331ad8f3b464f3a88b51
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555058"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>Como redimensionar uma tela usando um elevador
Este exemplo mostra como usar um <xref:System.Windows.Controls.Primitives.Thumb> controle para redimensionar um <xref:System.Windows.Controls.Canvas> controle.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Controls.Primitives.Thumb> controle oferece funcionalidade de arrastar que pode ser usada para mover ou redimensionar controles monitorando o <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> e <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> eventos de <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 O usuário começa uma operação de arrastar, pressionando o botão esquerdo do mouse quando o ponteiro do mouse está pausado no <xref:System.Windows.Controls.Primitives.Thumb> controle. A operação de arrastar continuará enquanto o botão esquerdo do mouse permanecer pressionado. Durante a operação de arrastar, o <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> pode ocorrer mais de uma vez. Cada vez que ocorrer, o <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> classe fornece a mudança de posição que corresponde a mudança na posição do mouse. Quando o usuário libera o botão esquerdo do mouse, a operação de arrastar é concluída. A operação de arrastar somente fornece novas coordenadas; ele não reposiciona automaticamente o <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 A exemplo a seguir mostra um <xref:System.Windows.Controls.Primitives.Thumb> controlar o que é o elemento filho de um <xref:System.Windows.Controls.Canvas> controle. O manipulador de eventos para sua <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> evento fornece a lógica para mover o <xref:System.Windows.Controls.Primitives.Thumb> e redimensione o <xref:System.Windows.Controls.Canvas>. Manipuladores de eventos para o <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> e <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> evento alterar a cor do <xref:System.Windows.Controls.Primitives.Thumb> durante uma operação de arrastar. O exemplo a seguir define o <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 [!code-xaml[Thumb#thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 A exemplo a seguir mostra o <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> manipulador de eventos que move o <xref:System.Windows.Controls.Primitives.Thumb> e redimensiona a <xref:System.Windows.Controls.Canvas> em resposta a um movimento do mouse.  
  
 [!code-csharp[Thumb#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 A exemplo a seguir mostra o <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> manipulador de eventos.  
  
 [!code-csharp[Thumb#DragStartedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 A exemplo a seguir mostra o <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> manipulador de eventos.  
  
 [!code-csharp[Thumb#DragCompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 Para o exemplo completo, consulte [Exemplo de funcionalidade de arrastar do elevador](http://go.microsoft.com/fwlink/?LinkID=160042).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Primitives.Thumb>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
