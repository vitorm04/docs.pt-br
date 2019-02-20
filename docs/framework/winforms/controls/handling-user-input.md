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
ms.openlocfilehash: 8c6319929d4b419cc0a2e1cfd097bfae7d997120
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442992"
---
# <a name="handling-user-input"></a>Identificando a entrada do usuário
Este tópico descreve os principais eventos de teclado e mouse fornecidos pelo <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Ao manipular um evento, os autores do controle devem substituir o método `On`*EventName* protegido em vez de associar um delegado ao evento. Para ver uma análise de eventos, consulte [Gerando eventos de um componente](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
> [!NOTE]
>  Se não há nenhum dado associado a um evento, uma instância da classe base <xref:System.EventArgs> é passado como um argumento para o `On` *EventName* método.  
  
## <a name="keyboard-events"></a>Eventos de teclado  
 Os eventos de teclado comuns que seu controle pode manipular são <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, e <xref:System.Windows.Forms.Control.KeyUp>.  
  
|Nome do Evento|Método a ser substituído|Descrição do evento|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|Gerado somente quando uma tecla é pressionada pela primeira vez.|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|Gerado sempre que uma tecla é pressionada. Se uma tecla é pressionada, um <xref:System.Windows.Forms.Control.KeyPress> é gerado com a taxa de repetição definida pelo sistema operacional.|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|Gerado quando uma tecla é liberada.|  
  
> [!NOTE]
>  Manipular a entrada do teclado é consideravelmente mais complexo que substituir os eventos na tabela anterior e está além do escopo deste tópico. Para obter mais informações, consulte [Entrada do usuário no Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).  
  
## <a name="mouse-events"></a>Eventos de mouse  
 Os eventos de mouse que seu controle pode manipular são <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, e <xref:System.Windows.Forms.Control.MouseUp>.  
  
|Nome do Evento|Método a ser substituído|Descrição do evento|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|Gerado quando o botão do mouse é pressionado enquanto o ponteiro está sobre o controle.|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|Gerado quando o ponteiro entra pela primeira vez na região do controle.|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|Gerado quando o ponteiro do mouse focaliza o controle.|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|Gerado quando o ponteiro do mouse deixa a região do controle.|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|Gerado quando o ponteiro do mouse se move na região do controle.|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|Gerado quando o botão do mouse é liberado enquanto o ponteiro está sobre o controle ou o ponteiro sai da região do controle.|  
  
 O fragmento de código a seguir mostra um exemplo de substituição a <xref:System.Windows.Forms.Control.MouseDown> eventos.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 O fragmento de código a seguir mostra um exemplo de substituição a <xref:System.Windows.Forms.Control.MouseMove> eventos.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 O fragmento de código a seguir mostra um exemplo de substituição a <xref:System.Windows.Forms.Control.MouseUp> eventos.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 Para o código-fonte completo para o `FlashTrackBar` de exemplo, consulte [como: Criar um controle de formulários do Windows que mostre o progresso](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="see-also"></a>Consulte também
- [Eventos em controles do Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
- [Definindo um evento](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
- [Eventos](../../../../docs/standard/events/index.md)
- [Entrada do usuário nos Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
