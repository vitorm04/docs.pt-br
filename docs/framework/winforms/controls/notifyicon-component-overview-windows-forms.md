---
title: Visão geral do componente NotifyIcon
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: 587bf514db853f1122ed16abc05a195985c5ce8d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742129"
---
# <a name="notifyicon-component-overview-windows-forms"></a>Visão geral do componente NotifyIcon (Windows Forms)

O Windows Forms <xref:System.Windows.Forms.NotifyIcon> componente é normalmente usado para exibir ícones para processos que são executados em segundo plano e não mostram a interface do usuário a maior parte do tempo. Por exemplo, um programa de proteção contra vírus que pode ser acessado clicando em um ícone na área de notificação de status da barra de tarefas.

## <a name="key-properties-of-notifyicons"></a>Propriedades chave do NotifyIcons

Cada componente de <xref:System.Windows.Forms.NotifyIcon> exibe um único ícone na área de status. Se você tiver três processos em segundo plano e desejar exibir um ícone para cada um deles, será necessário adicionar três <xref:System.Windows.Forms.NotifyIcon> componentes ao formulário. As propriedades de chave do componente <xref:System.Windows.Forms.NotifyIcon> são <xref:System.Windows.Forms.NotifyIcon.Icon%2A> e <xref:System.Windows.Forms.NotifyIcon.Visible%2A>. A propriedade <xref:System.Windows.Forms.NotifyIcon.Icon%2A> define o ícone que aparece na área de status. Para que o ícone apareça, a propriedade <xref:System.Windows.Forms.NotifyIcon.Visible%2A> deve ser definida como `true`.

## <a name="notifyicons-options"></a>Opções do NotifyIcons

Você pode associar dicas de balão, menus de atalho e dicas de ferramenta com um <xref:System.Windows.Forms.NotifyIcon> para auxiliar o usuário.

Você pode exibir dicas de balão para um <xref:System.Windows.Forms.NotifyIcon> chamando o método <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> especificando o período de tempo que deseja que a dica de balão seja exibida. Você também pode especificar o texto, o ícone e o título da dica de balão com a <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> e <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectivamente. <xref:System.Windows.Forms.NotifyIcon> componentes também podem ter dicas de ferramentas e menus de atalho associados. Para mais informação, consulte [Visão geral do componente ToolTip](tooltip-component-overview-windows-forms.md) e [Visão geral do componente ContextMenu](contextmenu-component-overview-windows-forms.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.NotifyIcon>
- [Componente NotifyIcon](notifyicon-component-windows-forms.md)
