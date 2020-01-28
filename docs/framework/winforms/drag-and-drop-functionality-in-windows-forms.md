---
title: Funcionalidade de arrastar e soltar
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], Windows Forms
- Windows Forms, drag and drop
ms.assetid: 65cd2c03-8782-474e-b958-cbe43eeb902c
ms.openlocfilehash: 603dc158719c0b11def4386eb24a33f235cf3a42
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732751"
---
# <a name="drag-and-drop-functionality-in-windows-forms"></a>Funcionalidade de arrastar e soltar no Windows Forms
O Windows Forms incluem um conjunto de métodos, eventos e classes que implementam o comportamento do tipo "arrastar e soltar". Este tópico fornece uma visão geral do suporte a arrastar e soltar no Windows Forms.  Consulte também [Operações do tipo "arrastar e soltar" e suporte à área de transferência](./advanced/drag-and-drop-operations-and-clipboard-support.md).  
  
## <a name="performing-drag-and-drop-operations"></a>Realizando operações do tipo "arrastar e soltar"  
 Para executar uma operação de arrastar e soltar, use o método <xref:System.Windows.Forms.Control.DoDragDrop%2A> da classe <xref:System.Windows.Forms.Control>. Para obter mais informações sobre como uma operação de arrastar e soltar é executada, consulte <xref:System.Windows.Forms.Control.DoDragDrop%2A>. Para obter o retângulo no qual o ponteiro do mouse deve ser arrastado antes que uma operação de arrastar e soltar seja iniciada, use a propriedade <xref:System.Windows.Forms.SystemInformation.DragSize%2A> da classe <xref:System.Windows.Forms.SystemInformation>.  
  
## <a name="events-related-to-drag-and-drop-operations"></a>Eventos relacionados a operações do tipo "arrastar e soltar"  
 Há duas categorias de eventos em uma operação de arrastar e soltar: os eventos que ocorrem no destino atual da operação do tipo "arrastar e soltar" e eventos que ocorrem na fonte da operação de arrastar e soltar.  
  
### <a name="events-on-the-current-target"></a>Eventos de destino atual  
 A tabela a seguir mostra os eventos que ocorrem no destino atual de uma operação do tipo "arrastar e soltar".  
  
|Evento de mouse|Descrição|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.DragEnter>|Esse evento ocorre quando um objeto é arrastado para os limites do controle. O manipulador para esse evento recebe um argumento do tipo <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragOver>|Esse evento ocorre quando um objeto é arrastado enquanto o ponteiro do mouse está dentro dos limites do controle. O manipulador para esse evento recebe um argumento do tipo <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragDrop>|Esse evento ocorre quando uma operação do tipo "arrastar e soltar" é concluída. O manipulador para esse evento recebe um argumento do tipo <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragLeave>|Esse evento ocorre quando um objeto é arrastado para fora dos limites do controle. O manipulador para esse evento recebe um argumento do tipo <xref:System.EventArgs>.|  
  
 A classe <xref:System.Windows.Forms.DragEventArgs> fornece o local do ponteiro do mouse, o estado atual dos botões do mouse e as teclas modificadoras do teclado, os dados que estão sendo arrastados e <xref:System.Windows.Forms.DragDropEffects> valores que especificam as operações permitidas pela origem do evento de arrastar e o efeito de soltar destino para a operação.  
  
### <a name="events-on-the-source"></a>Eventos na fonte  
 A tabela a seguir mostra os eventos que ocorrem na fonte atual de uma operação do tipo "arrastar e soltar".  
  
|Evento de mouse|Descrição|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.GiveFeedback>|Esse evento ocorre durante uma operação de arrastar. Ele fornece uma indicação visual para o usuário que a operação do tipo "arrastar e soltar" está ocorrendo, como uma alteração no ponteiro do mouse. O manipulador para esse evento recebe um argumento do tipo <xref:System.Windows.Forms.GiveFeedbackEventArgs>.|  
|<xref:System.Windows.Forms.Control.QueryContinueDrag>|Esse evento é gerado durante uma operação do tipo "arrastar e soltar" e permite que a fonte de arrastar determine se a operação do tipo "arrastar e soltar" deve ser cancelada. O manipulador para esse evento recebe um argumento do tipo <xref:System.Windows.Forms.QueryContinueDragEventArgs>.|  
  
 A classe <xref:System.Windows.Forms.QueryContinueDragEventArgs> fornece o estado atual dos botões do mouse e as teclas modificadoras do teclado, um valor que especifica se a tecla ESC foi pressionada e um valor <xref:System.Windows.Forms.DragAction> que pode ser definido para especificar se a operação de arrastar e soltar deve continuar.  
  
## <a name="see-also"></a>Veja também

- [Entrada do mouse em um aplicativo dos Windows Forms](mouse-input-in-a-windows-forms-application.md)
