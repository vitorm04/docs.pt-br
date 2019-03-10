---
title: Entrada do usuário em um aplicativo do Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
ms.openlocfilehash: 351c1e42bb775331cbe0e2005b6bea284716de75
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711922"
---
# <a name="user-input-in-a-windows-forms-application"></a>Entrada do usuário em um aplicativo do Windows Forms
No Windows Forms, a entrada do usuário é enviada para aplicativos na forma de mensagens do Windows. Uma série de métodos substituíveis processam essas mensagens no nível do aplicativo, formulário e controle. Quando esses métodos recebem mensagens de mouse e teclado, eles geram eventos que podem ser manipulados para obter informações sobre a entrada de mouse ou de teclado. Em muitos casos, os aplicativos do Windows Forms serão capazes de processar todas as entradas do usuário simplesmente manipulando esses eventos. Em outros casos, um aplicativo pode precisar substituir um dos métodos que processam mensagens para interceptar uma mensagem específica antes de ela ser recebida pelo aplicativo, formulário ou controle.  
  
## <a name="mouse-and-keyboard-events"></a>Eventos de Mouse e Teclado  
 Todos os controles do Windows Forms herdam um conjunto de eventos relacionados às entradas de mouse e teclado. Por exemplo, um controle pode manipular o <xref:System.Windows.Forms.Control.KeyPress> evento para determinar o código de caractere de uma chave que foi pressionada, ou um controle pode manipular o <xref:System.Windows.Forms.Control.MouseClick> evento para determinar o local de um mouse de clique. Para obter mais informações sobre eventos de mouse e teclado, consulte [Usando Eventos de Teclado](using-keyboard-events.md) e [Eventos de Mouse no Windows Forms](mouse-events-in-windows-forms.md).  
  
## <a name="methods-that-process-user-input-messages"></a>Métodos que Processam Mensagens de Entrada do Usuário  
 Formulários e controles têm acesso para o <xref:System.Windows.Forms.IMessageFilter> interface e um conjunto de métodos substituíveis que processam mensagens do Windows em diferentes pontos na fila de mensagens. Todos estes métodos têm um <xref:System.Windows.Forms.Message> parâmetro, que encapsula os detalhes de baixo nível das mensagens do Windows. É possível implementar ou substituir esses métodos para analisar a mensagem e, então, consumi-la ou passá-la para o próximo consumidor na fila de mensagens. A tabela a seguir apresenta os métodos que processam todas as mensagens do Windows no Windows Forms.  
  
|Método|Observações|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|Este método intercepta mensagens do Windows que estão na fila (também chamadas de postadas) no nível do aplicativo.|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|Este método intercepta as mensagens do Windows no nível do formulário e do controle antes que elas sejam processadas.|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|Este método processa mensagens do Windows no nível do formulário e do controle.|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|Esse método realiza o processamento padrão de mensagens do Windows no nível do formulário e do controle. Isso fornece a funcionalidade mínima de uma janela.|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|Este método intercepta as mensagens do Windows no nível do formulário e do controle após o seu processamento. O <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage> bit de estilo deve ser definida para esse método ser chamado.|  
  
 Mensagens de teclado e mouse também são processadas por um conjunto adicional de métodos substituíveis específicos para esses tipos de mensagens. Para obter mais informações, consulte [Como a Entrada do Teclado Funciona](how-keyboard-input-works.md) e [Como a Entrada do Mouse Funciona no Windows Forms](how-mouse-input-works-in-windows-forms.md).  
  
## <a name="see-also"></a>Consulte também
- [Entrada do usuário nos Windows Forms](user-input-in-windows-forms.md)
- [Entrada do teclado em um aplicativo dos Windows Forms](keyboard-input-in-a-windows-forms-application.md)
- [Entrada do mouse em um Aplicativo do Windows Forms](mouse-input-in-a-windows-forms-application.md)
