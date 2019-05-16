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
ms.openlocfilehash: def109799ddfb25b6f56a4f18d52bb19f62842f5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645693"
---
# <a name="notifyicon-component-overview-windows-forms"></a><span data-ttu-id="cb6e1-102">Visão geral do componente NotifyIcon (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="cb6e1-102">NotifyIcon Component Overview (Windows Forms)</span></span>

<span data-ttu-id="cb6e1-103">Os formulários do Windows <xref:System.Windows.Forms.NotifyIcon> componente normalmente é usado para exibir ícones para processos que são executados em segundo plano e não mostram que um usuário de interface grande parte do tempo.</span><span class="sxs-lookup"><span data-stu-id="cb6e1-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component is typically used to display icons for processes that run in the background and do not show a user interface much of the time.</span></span> <span data-ttu-id="cb6e1-104">Por exemplo, um programa de proteção contra vírus que pode ser acessado clicando em um ícone na área de notificação de status da barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="cb6e1-104">An example would be a virus protection program that can be accessed by clicking an icon in the status notification area of the taskbar.</span></span>

## <a name="key-properties-of-notifyicons"></a><span data-ttu-id="cb6e1-105">Propriedades chave do NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="cb6e1-105">Key Properties of NotifyIcons</span></span>

<span data-ttu-id="cb6e1-106">Cada <xref:System.Windows.Forms.NotifyIcon> componente exibe um único ícone na área de status.</span><span class="sxs-lookup"><span data-stu-id="cb6e1-106">Each <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status area.</span></span> <span data-ttu-id="cb6e1-107">Se você tem três processos em segundo plano e desejar exibir um ícone para cada um, você deve adicionar três <xref:System.Windows.Forms.NotifyIcon> componentes para o formulário.</span><span class="sxs-lookup"><span data-stu-id="cb6e1-107">If you have three background processes and wish to display an icon for each, you must add three <xref:System.Windows.Forms.NotifyIcon> components to the form.</span></span> <span data-ttu-id="cb6e1-108">As propriedades da chave de <xref:System.Windows.Forms.NotifyIcon> componente estão <xref:System.Windows.Forms.NotifyIcon.Icon%2A> e <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb6e1-108">The key properties of the <xref:System.Windows.Forms.NotifyIcon> component are <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span></span> <span data-ttu-id="cb6e1-109">O <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriedade define o ícone que aparece na área de status.</span><span class="sxs-lookup"><span data-stu-id="cb6e1-109">The <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property sets the icon that appears in the status area.</span></span> <span data-ttu-id="cb6e1-110">Para que o ícone apareça, a <xref:System.Windows.Forms.NotifyIcon.Visible%2A> propriedade deve ser definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="cb6e1-110">In order for the icon to appear, the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property must be set to `true`.</span></span>

## <a name="notifyicons-options"></a><span data-ttu-id="cb6e1-111">Opções do NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="cb6e1-111">NotifyIcons Options</span></span>

<span data-ttu-id="cb6e1-112">Você pode associar dicas de balão, menus de atalho e dicas de ferramenta com um <xref:System.Windows.Forms.NotifyIcon> para auxiliar o usuário.</span><span class="sxs-lookup"><span data-stu-id="cb6e1-112">You can associate balloon tips, shortcut menus, and ToolTips with a <xref:System.Windows.Forms.NotifyIcon> to assist the user.</span></span>

<span data-ttu-id="cb6e1-113">Você pode exibir dicas de balão para um <xref:System.Windows.Forms.NotifyIcon> chamando o <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> método especificando o intervalo de tempo você deseja exibir a dica de balão.</span><span class="sxs-lookup"><span data-stu-id="cb6e1-113">You can display balloon tips for a <xref:System.Windows.Forms.NotifyIcon> by calling the <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> method specifying the time span you wish the balloon tip to display.</span></span> <span data-ttu-id="cb6e1-114">Você também pode especificar o texto, ícone e título da dica de balão com o <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> e <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="cb6e1-114">You can also specify the text, icon and title of the balloon tip with the <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> and <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectively.</span></span> <span data-ttu-id="cb6e1-115"><xref:System.Windows.Forms.NotifyIcon> componentes também podem ter associadas dicas de ferramentas e menus de atalho.</span><span class="sxs-lookup"><span data-stu-id="cb6e1-115"><xref:System.Windows.Forms.NotifyIcon> components can also have associated ToolTips and shortcut menus.</span></span> <span data-ttu-id="cb6e1-116">Para mais informação, consulte [Visão geral do componente ToolTip](tooltip-component-overview-windows-forms.md) e [Visão geral do componente ContextMenu](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cb6e1-116">For more information, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md) and [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cb6e1-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb6e1-117">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- [<span data-ttu-id="cb6e1-118">Componente NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="cb6e1-118">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
