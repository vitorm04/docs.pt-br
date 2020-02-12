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
ms.openlocfilehash: 84f5ac2b53124b7f4d7c15741e94b40e7ee81526
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124293"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>Como redimensionar uma tela usando um elevador
Este exemplo mostra como usar um controle de <xref:System.Windows.Controls.Primitives.Thumb> para redimensionar um controle de <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O controle de <xref:System.Windows.Controls.Primitives.Thumb> fornece funcionalidade de arrastar que pode ser usada para mover ou redimensionar controles monitorando os eventos <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> e <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> do <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 O usuário inicia uma operação de arrastar pressionando o botão esquerdo do mouse quando o ponteiro do mouse é pausado no controle de <xref:System.Windows.Controls.Primitives.Thumb>. A operação de arrastar continuará enquanto o botão esquerdo do mouse permanecer pressionado. Durante a operação de arrastar, o <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> pode ocorrer mais de uma vez. Cada vez que ele ocorre, a classe <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> fornece a alteração na posição que corresponde à alteração na posição do mouse. Quando o usuário libera o botão esquerdo do mouse, a operação de arrastar é concluída. A operação de arrastar fornece apenas novas coordenadas; Ele não reposiciona automaticamente o <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 O exemplo a seguir mostra um controle <xref:System.Windows.Controls.Primitives.Thumb> que é o elemento filho de um controle <xref:System.Windows.Controls.Canvas>. O manipulador de eventos para seu evento de <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> fornece a lógica para mover o <xref:System.Windows.Controls.Primitives.Thumb> e redimensionar o <xref:System.Windows.Controls.Canvas>. Os manipuladores de eventos para o evento <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> e <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> alteram a cor do <xref:System.Windows.Controls.Primitives.Thumb> durante uma operação de arrastar. O exemplo a seguir define o <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 O exemplo a seguir mostra o manipulador de eventos <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> que move o <xref:System.Windows.Controls.Primitives.Thumb> e redimensiona o <xref:System.Windows.Controls.Canvas> em resposta a um movimento do mouse.  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 O exemplo a seguir mostra o manipulador de eventos <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>.  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 O exemplo a seguir mostra o manipulador de eventos <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>.  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 Para o exemplo completo, consulte [Exemplo de funcionalidade de arrastar do elevador](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
