---
title: Identificando a entrada do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
ms.openlocfilehash: f92b742c3f6feec72e5b3150204d7d984636281d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934088"
---
# <a name="handling-user-input"></a>Identificando a entrada do usuário
Este tópico descreve os principais eventos de teclado e mouse fornecidos <xref:System.Windows.Forms.Control?displayProperty=nameWithType>pelo. Ao manipular um evento, os autores do controle devem substituir o método `On`*EventName* protegido em vez de associar um delegado ao evento. Para ver uma análise de eventos, consulte [Gerando eventos de um componente](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
> [!NOTE]
> Se não houver dados associados a um evento, uma instância da classe <xref:System.EventArgs> base será passada como um argumento para o `On`método *EventName* .  
  
## <a name="keyboard-events"></a>Eventos de teclado  
 Os eventos comuns de teclado que seu controle pode manipular <xref:System.Windows.Forms.Control.KeyDown>são <xref:System.Windows.Forms.Control.KeyPress>, e <xref:System.Windows.Forms.Control.KeyUp>.  
  
|Nome do Evento|Método a ser substituído|Descrição do evento|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|Gerado somente quando uma tecla é pressionada pela primeira vez.|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|Gerado sempre que uma tecla é pressionada. Se uma chave for mantida inativa, <xref:System.Windows.Forms.Control.KeyPress> um evento será gerado na taxa de repetição definida pelo sistema operacional.|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|Gerado quando uma tecla é liberada.|  
  
> [!NOTE]
> Manipular a entrada do teclado é consideravelmente mais complexo que substituir os eventos na tabela anterior e está além do escopo deste tópico. Para obter mais informações, consulte [Entrada do usuário no Windows Forms](../user-input-in-windows-forms.md).  
  
## <a name="mouse-events"></a>Eventos de mouse  
 Os eventos do mouse que o controle pode manipular <xref:System.Windows.Forms.Control.MouseDown>são <xref:System.Windows.Forms.Control.MouseEnter> <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave> <xref:System.Windows.Forms.Control.MouseMove>,,, e <xref:System.Windows.Forms.Control.MouseUp>.  
  
|Nome do Evento|Método a ser substituído|Descrição do evento|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|Gerado quando o botão do mouse é pressionado enquanto o ponteiro está sobre o controle.|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|Gerado quando o ponteiro entra pela primeira vez na região do controle.|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|Gerado quando o ponteiro do mouse focaliza o controle.|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|Gerado quando o ponteiro do mouse deixa a região do controle.|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|Gerado quando o ponteiro do mouse se move na região do controle.|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|Gerado quando o botão do mouse é liberado enquanto o ponteiro está sobre o controle ou o ponteiro sai da região do controle.|  
  
 O fragmento de código a seguir mostra um exemplo de <xref:System.Windows.Forms.Control.MouseDown> substituição do evento.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 O fragmento de código a seguir mostra um exemplo de <xref:System.Windows.Forms.Control.MouseMove> substituição do evento.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 O fragmento de código a seguir mostra um exemplo de <xref:System.Windows.Forms.Control.MouseUp> substituição do evento.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 Para obter o código-fonte completo `FlashTrackBar` do exemplo, [consulte Como: Crie um controle de Windows Forms que mostre](how-to-create-a-windows-forms-control-that-shows-progress.md)o progresso.  
  
## <a name="see-also"></a>Consulte também

- [Eventos em controles do Windows Forms](events-in-windows-forms-controls.md)
- [Definindo um evento](defining-an-event-in-windows-forms-controls.md)
- [Eventos](../../../standard/events/index.md)
- [Entrada do usuário nos Windows Forms](../user-input-in-windows-forms.md)
