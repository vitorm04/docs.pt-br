---
title: Usando eventos do teclado
ms.date: 03/30/2017
helpviewer_keywords:
- KeyPress event [Windows Forms]
- keyboards [Windows Forms], keyboard events
- KeyUp event
- KeyDown event
- keyboard events
- events [Windows Forms], keyboard
ms.assetid: d3f3e14b-a459-4ee6-9875-8957e34f8ee9
ms.openlocfilehash: 9aefe6be17e5d72c86c2c47bf0d373d0a081ca76
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59114264"
---
# <a name="using-keyboard-events"></a>Usando eventos do teclado
A maioria dos programas do Windows Forms processa a entrada do teclado tratando eventos de teclado. Este tópico fornece uma visão geral dos eventos de teclado, incluindo detalhes sobre quando usar cada evento e os dados que são fornecidos para cada evento.  Consulte também [visão geral de manipuladores de eventos (Windows Forms)](event-handlers-overview-windows-forms.md) e [visão geral de eventos (Windows Forms)](events-overview-windows-forms.md).  
  
## <a name="keyboard-events"></a>Eventos de teclado  
 O Windows Forms fornece dois eventos que ocorrem quando um usuário pressiona uma tecla do teclado e um evento quando um usuário libera uma tecla do teclado:  
  
-   O <xref:System.Windows.Forms.Control.KeyDown> evento ocorre uma vez  
  
-   O <xref:System.Windows.Forms.Control.KeyPress> evento, que pode ocorrer várias vezes quando um usuário segura a mesma tecla.  
  
-   O <xref:System.Windows.Forms.Control.KeyUp> evento ocorre uma vez quando um usuário libera uma tecla.  
  
 Quando um usuário pressiona uma tecla, o Windows Forms determina qual evento deve ser gerado com base em se a mensagem do teclado especifica uma tecla de caractere ou uma tecla física. Para obter mais informações sobre teclas de caracteres e físicas, consulte [Como funciona a entrada do teclado](how-keyboard-input-works.md).  
  
 A tabela a seguir descreve os três eventos de teclado.  
  
|Evento de teclado|Descrição|Resultados|  
|--------------------|-----------------|-------------|  
|<xref:System.Windows.Forms.Control.KeyDown>|Esse evento é gerado quando um usuário pressiona uma tecla física.|O manipulador para <xref:System.Windows.Forms.Control.KeyDown> recebe:<br /><br /> <ul><li>Um <xref:System.Windows.Forms.KeyEventArgs> parâmetro, que fornece o <xref:System.Windows.Forms.KeyEventArgs.KeyCode%2A> propriedade (que especifica um botão físico do teclado).</li><li>O <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> propriedade (SHIFT, CTRL ou ALT).</li><li>O <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> propriedade (que combina o código e tecla modificadora). O <xref:System.Windows.Forms.KeyEventArgs> também fornece um parâmetro:<br /><br /> <ul><li>O <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> propriedade, que pode ser definida para impedir que o controle subjacente receba a chave.</li><li>O <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> propriedade, que pode ser usada para suprimir a <xref:System.Windows.Forms.Control.KeyPress> e <xref:System.Windows.Forms.Control.KeyUp> eventos para esse pressionamento de tecla.</li></ul></li></ul>|  
|<xref:System.Windows.Forms.Control.KeyPress>|Esse evento é gerado quando as teclas são pressionadas resultam em um caractere. Por exemplo, um usuário pressiona as teclas SHIFT e a letra “a” minúscula, o que resulta em uma letra “A” maiúscula.|<xref:System.Windows.Forms.Control.KeyPress> é gerado após <xref:System.Windows.Forms.Control.KeyDown>.<br /><br /> <ul><li>O manipulador para <xref:System.Windows.Forms.Control.KeyPress> recebe:</li><li>Um <xref:System.Windows.Forms.KeyPressEventArgs> parâmetro, que contém o código de caractere da tecla que foi pressionada. Esse código de caractere é exclusivo para cada combinação de uma tecla de caractere e tecla modificadora.<br /><br />     Por exemplo, a tecla “A” gerará:<br /><br /> <ul><li>O código de caractere 65, se ela estiver pressionada com a tecla SHIFT</li><li>Ou a tecla CAPS LOCK, 97 se ela for pressionada sozinha,</li><li>E 1 se ela estiver pressionada com a tecla CTRL.</li></ul></li></ul>|  
|<xref:System.Windows.Forms.Control.KeyUp>|Esse evento é gerado quando um usuário libera uma tecla física.|O manipulador para <xref:System.Windows.Forms.Control.KeyUp> recebe:<br /><br /> <ul><li>Um <xref:System.Windows.Forms.KeyEventArgs> parâmetro:<br /><br /> <ul><li>Que fornece o <xref:System.Windows.Forms.KeyEventArgs.KeyCode%2A> propriedade (que especifica um botão físico do teclado).</li><li>O <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> propriedade (SHIFT, CTRL ou ALT).</li><li>O <xref:System.Globalization.SortKey.KeyData%2A> propriedade (que combina o código e tecla modificadora).</li></ul></li></ul>|  
  
## <a name="see-also"></a>Consulte também

- [Entrada do teclado em um aplicativo do Windows Forms](keyboard-input-in-a-windows-forms-application.md)
- [Como a entrada do teclado funciona](how-keyboard-input-works.md)
- [Entrada do mouse em um aplicativo do Windows Forms](mouse-input-in-a-windows-forms-application.md)
