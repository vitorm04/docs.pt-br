---
title: Funcionalidade de arrastar e soltar no Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], Windows Forms
- Windows Forms, drag and drop
ms.assetid: 65cd2c03-8782-474e-b958-cbe43eeb902c
ms.openlocfilehash: b1189da9fa0b76ede3261cf6da5305a09147bba5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865079"
---
# <a name="drag-and-drop-functionality-in-windows-forms"></a>Funcionalidade de arrastar e soltar no Windows Forms
O Windows Forms incluem um conjunto de métodos, eventos e classes que implementam o comportamento do tipo "arrastar e soltar". Este tópico fornece uma visão geral do suporte a arrastar e soltar no Windows Forms.  Consulte também [Operações do tipo "arrastar e soltar" e suporte à área de transferência](https://msdn.microsoft.com/library/fe5ebfwe\(v=vs.110\)).  
  
## <a name="performing-drag-and-drop-operations"></a>Realizando operações do tipo "arrastar e soltar"  
 Para executar uma operação de arrastar e soltar, use o <xref:System.Windows.Forms.Control.DoDragDrop%2A> método da <xref:System.Windows.Forms.Control> classe. Para obter mais informações sobre como uma operação de arrastar e soltar é executada, consulte <xref:System.Windows.Forms.Control.DoDragDrop%2A>. Para obter o retângulo que o ponteiro do mouse deve ser arrastado antes do início de uma operação de arrastar e soltar, use o <xref:System.Windows.Forms.SystemInformation.DragSize%2A> propriedade do <xref:System.Windows.Forms.SystemInformation> classe.  
  
## <a name="events-related-to-drag-and-drop-operations"></a>Eventos relacionados a operações do tipo "arrastar e soltar"  
 Há duas categorias de eventos em uma operação de arrastar e soltar: os eventos que ocorrem no destino atual da operação do tipo "arrastar e soltar" e eventos que ocorrem na fonte da operação de arrastar e soltar.  
  
### <a name="events-on-the-current-target"></a>Eventos de destino atual  
 A tabela a seguir mostra os eventos que ocorrem no destino atual de uma operação do tipo "arrastar e soltar".  
  
|Eventos de mouse|Descrição|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.DragEnter>|Esse evento ocorre quando um objeto é arrastado para os limites do controle. O manipulador deste evento recebe um argumento do tipo <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragOver>|Esse evento ocorre quando um objeto é arrastado enquanto o ponteiro do mouse está dentro dos limites do controle. O manipulador deste evento recebe um argumento do tipo <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragDrop>|Esse evento ocorre quando uma operação do tipo "arrastar e soltar" é concluída. O manipulador deste evento recebe um argumento do tipo <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragLeave>|Esse evento ocorre quando um objeto é arrastado para fora dos limites do controle. O manipulador deste evento recebe um argumento do tipo <xref:System.EventArgs>.|  
  
 O <xref:System.Windows.Forms.DragEventArgs> classe fornece a localização do ponteiro do mouse, o estado atual dos botões do mouse e teclas modificadoras do teclado, os dados sendo arrastados e <xref:System.Windows.Forms.DragDropEffects> valores que especificam as operações permitidas pela origem do evento de arrastar e o efeito de soltar de destino para a operação.  
  
### <a name="events-on-the-source"></a>Eventos na fonte  
 A tabela a seguir mostra os eventos que ocorrem na fonte atual de uma operação do tipo "arrastar e soltar".  
  
|Eventos de mouse|Descrição|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.GiveFeedback>|Esse evento ocorre durante uma operação de arrastar. Ele fornece uma indicação visual para o usuário que a operação do tipo "arrastar e soltar" está ocorrendo, como uma alteração no ponteiro do mouse. O manipulador deste evento recebe um argumento do tipo <xref:System.Windows.Forms.GiveFeedbackEventArgs>.|  
|<xref:System.Windows.Forms.Control.QueryContinueDrag>|Esse evento é gerado durante uma operação do tipo "arrastar e soltar" e permite que a fonte de arrastar determine se a operação do tipo "arrastar e soltar" deve ser cancelada. O manipulador deste evento recebe um argumento do tipo <xref:System.Windows.Forms.QueryContinueDragEventArgs>.|  
  
 O <xref:System.Windows.Forms.QueryContinueDragEventArgs> classe fornece o estado atual do mouse botões e teclas modificadoras do teclado, um valor que especifica se a tecla ESC foi pressionada e um <xref:System.Windows.Forms.DragAction> valor que pode ser definido para especificar se a operação de arrastar e soltar deve continuar.  
  
## <a name="see-also"></a>Consulte também  
 [Entrada do mouse em um Aplicativo do Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
