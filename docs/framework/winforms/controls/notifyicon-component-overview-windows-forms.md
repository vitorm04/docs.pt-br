---
title: Visão geral do componente NotifyIcon (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: 0da485bf377b263d07a2f0ec27c5e94e4274d8ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="notifyicon-component-overview-windows-forms"></a>Visão geral do componente NotifyIcon (Windows Forms)
Windows Forms <xref:System.Windows.Forms.NotifyIcon> componente normalmente é usado para exibir ícones para processos que são executados em segundo plano e não mostram um usuário da interface grande parte do tempo. Por exemplo, um programa de proteção contra vírus que pode ser acessado clicando em um ícone na área de notificação de status da barra de tarefas.  
  
## <a name="key-properties-of-notifyicons"></a>Propriedades chave do NotifyIcons  
 Cada <xref:System.Windows.Forms.NotifyIcon> componente exibe um único ícone na área de status. Se você tiver três processos de plano de fundo e deseja exibir um ícone para cada um, você deve adicionar três <xref:System.Windows.Forms.NotifyIcon> componentes para o formulário. Propriedades de chave do <xref:System.Windows.Forms.NotifyIcon> componente são <xref:System.Windows.Forms.NotifyIcon.Icon%2A> e <xref:System.Windows.Forms.NotifyIcon.Visible%2A>. O <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriedade define o ícone que aparece na área de status. Para que o ícone a ser exibido, o <xref:System.Windows.Forms.NotifyIcon.Visible%2A> propriedade deve ser definida como `true`.  
  
 Se você estiver usando [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], você tem acesso a uma biblioteca grande de imagens padrão que você pode usar com o <xref:System.Windows.Forms.NotifyIcon> controle.  
  
## <a name="notifyicons-options"></a>Opções do NotifyIcons  
 Você pode associar as dicas de balão, menus de atalho e dicas de ferramenta com um <xref:System.Windows.Forms.NotifyIcon> para ajudar o usuário.  
  
 Você pode exibir dicas de balão para um <xref:System.Windows.Forms.NotifyIcon> chamando o <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> método especificando o intervalo de tempo você deseja a dica de balão a ser exibida. Você também pode especificar o texto, o ícone e o título da dica de balão com o <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> e <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectivamente. <xref:System.Windows.Forms.NotifyIcon> componentes também podem ter associadas menus de atalho e dicas de ferramenta. Para mais informação, consulte [Visão geral do componente ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md) e [Visão geral do componente ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.NotifyIcon>  
 [Componente NotifyIcon](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)
