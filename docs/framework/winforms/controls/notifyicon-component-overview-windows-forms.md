---
title: "Visão geral do componente NotifyIcon (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d951d45232437026cc41d8e40284207ea1c64ab9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="notifyicon-component-overview-windows-forms"></a><span data-ttu-id="b3397-102">Visão geral do componente NotifyIcon (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b3397-102">NotifyIcon Component Overview (Windows Forms)</span></span>
<span data-ttu-id="b3397-103">Windows Forms <xref:System.Windows.Forms.NotifyIcon> componente normalmente é usado para exibir ícones para processos que são executados em segundo plano e não mostram um usuário da interface grande parte do tempo.</span><span class="sxs-lookup"><span data-stu-id="b3397-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component is typically used to display icons for processes that run in the background and do not show a user interface much of the time.</span></span> <span data-ttu-id="b3397-104">Por exemplo, um programa de proteção contra vírus que pode ser acessado clicando em um ícone na área de notificação de status da barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="b3397-104">An example would be a virus protection program that can be accessed by clicking an icon in the status notification area of the taskbar.</span></span>  
  
## <a name="key-properties-of-notifyicons"></a><span data-ttu-id="b3397-105">Propriedades chave do NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="b3397-105">Key Properties of NotifyIcons</span></span>  
 <span data-ttu-id="b3397-106">Cada <xref:System.Windows.Forms.NotifyIcon> componente exibe um único ícone na área de status.</span><span class="sxs-lookup"><span data-stu-id="b3397-106">Each <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status area.</span></span> <span data-ttu-id="b3397-107">Se você tiver três processos de plano de fundo e deseja exibir um ícone para cada um, você deve adicionar três <xref:System.Windows.Forms.NotifyIcon> componentes para o formulário.</span><span class="sxs-lookup"><span data-stu-id="b3397-107">If you have three background processes and wish to display an icon for each, you must add three <xref:System.Windows.Forms.NotifyIcon> components to the form.</span></span> <span data-ttu-id="b3397-108">Propriedades de chave do <xref:System.Windows.Forms.NotifyIcon> componente são <xref:System.Windows.Forms.NotifyIcon.Icon%2A> e <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span><span class="sxs-lookup"><span data-stu-id="b3397-108">The key properties of the <xref:System.Windows.Forms.NotifyIcon> component are <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span></span> <span data-ttu-id="b3397-109">O <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriedade define o ícone que aparece na área de status.</span><span class="sxs-lookup"><span data-stu-id="b3397-109">The <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property sets the icon that appears in the status area.</span></span> <span data-ttu-id="b3397-110">Para que o ícone a ser exibido, o <xref:System.Windows.Forms.NotifyIcon.Visible%2A> propriedade deve ser definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="b3397-110">In order for the icon to appear, the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property must be set to `true`.</span></span>  
  
 <span data-ttu-id="b3397-111">Se você estiver usando [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], você tem acesso a uma biblioteca grande de imagens padrão que você pode usar com o <xref:System.Windows.Forms.NotifyIcon> controle.</span><span class="sxs-lookup"><span data-stu-id="b3397-111">If you are using [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], you have access to a large library of standard images that you can use with the <xref:System.Windows.Forms.NotifyIcon> control.</span></span>  
  
## <a name="notifyicons-options"></a><span data-ttu-id="b3397-112">Opções do NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="b3397-112">NotifyIcons Options</span></span>  
 <span data-ttu-id="b3397-113">Você pode associar as dicas de balão, menus de atalho e dicas de ferramenta com um <xref:System.Windows.Forms.NotifyIcon> para ajudar o usuário.</span><span class="sxs-lookup"><span data-stu-id="b3397-113">You can associate balloon tips, shortcut menus, and ToolTips with a <xref:System.Windows.Forms.NotifyIcon> to assist the user.</span></span>  
  
 <span data-ttu-id="b3397-114">Você pode exibir dicas de balão para um <xref:System.Windows.Forms.NotifyIcon> chamando o <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> método especificando o intervalo de tempo você deseja a dica de balão a ser exibida.</span><span class="sxs-lookup"><span data-stu-id="b3397-114">You can display balloon tips for a <xref:System.Windows.Forms.NotifyIcon> by calling the <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> method specifying the time span you wish the balloon tip to display.</span></span> <span data-ttu-id="b3397-115">Você também pode especificar o texto, o ícone e o título da dica de balão com o <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> e <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="b3397-115">You can also specify the text, icon and title of the balloon tip with the <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> and <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectively.</span></span> <span data-ttu-id="b3397-116"><xref:System.Windows.Forms.NotifyIcon>componentes também podem ter associadas menus de atalho e dicas de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="b3397-116"><xref:System.Windows.Forms.NotifyIcon> components can also have associated ToolTips and shortcut menus.</span></span> <span data-ttu-id="b3397-117">Para mais informação, consulte [Visão geral do componente ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md) e [Visão geral do componente ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b3397-117">For more information, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md) and [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3397-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3397-118">See Also</span></span>  
 <xref:System.Windows.Forms.NotifyIcon>  
 [<span data-ttu-id="b3397-119">Componente NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="b3397-119">NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)
