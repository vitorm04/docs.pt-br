---
title: 'Como: Desabilitar ToolStripMenuItems usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: fd80a6543c83ae957cd9c51b068d0702559f0925
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040264"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="91bcc-102">Como: Desabilitar ToolStripMenuItems usando o designer</span><span class="sxs-lookup"><span data-stu-id="91bcc-102">How to: Disable ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="91bcc-103">Você pode limitar ou ampliar os comandos que um usuário pode fazer ao habilitar e desabilitar itens de menu em resposta a atividades do usuário.</span><span class="sxs-lookup"><span data-stu-id="91bcc-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="91bcc-104">Os itens de menu são habilitados por padrão quando são criados, mas isso pode ser ajustado <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> por meio da propriedade.</span><span class="sxs-lookup"><span data-stu-id="91bcc-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="91bcc-105">Você pode manipular essa propriedade em tempo de design na janela **Propriedades** ou programaticamente configurando ela no código.</span><span class="sxs-lookup"><span data-stu-id="91bcc-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span> <span data-ttu-id="91bcc-106">Para obter mais informações, confira [Como: Desabilite](how-to-disable-toolstripmenuitems.md)o ToolStripMenuItems.</span><span class="sxs-lookup"><span data-stu-id="91bcc-106">For more information, see [How to: Disable ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span></span>

## <a name="to-disable-a-menu-item-at-design-time"></a><span data-ttu-id="91bcc-107">Para desabilitar um item de menu em tempo de design</span><span class="sxs-lookup"><span data-stu-id="91bcc-107">To disable a menu item at design time</span></span>

1. <span data-ttu-id="91bcc-108">Com o item de menu selecionado no formulário, defina a <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> Propriedade como `false`.</span><span class="sxs-lookup"><span data-stu-id="91bcc-108">With the menu item selected on the form, set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>

    > [!TIP]
    >  <span data-ttu-id="91bcc-109">Desabilitar o primeiro item de menu ou o de nível superior em um menu desabilita todos os itens de menu contidos no menu.</span><span class="sxs-lookup"><span data-stu-id="91bcc-109">Disabling the first or top-level menu item in a menu disables all the menu items contained within the menu.</span></span> <span data-ttu-id="91bcc-110">Da mesma forma, desabilitar um item de menu que tenha itens de submenu desabilita os itens do submenu.</span><span class="sxs-lookup"><span data-stu-id="91bcc-110">Likewise, disabling a menu item that has submenu items disables the submenu items.</span></span> <span data-ttu-id="91bcc-111">Se todos os comandos em um determinado menu estiverem indisponíveis para o usuário, ocultar e desabilitar todo o menu será considerado uma boa prática de programação, pois isso apresenta uma interface do usuário mais enxuta.</span><span class="sxs-lookup"><span data-stu-id="91bcc-111">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="91bcc-112">Você deve ocultar e desabilitar o menu, pois apenas ocultar não impede o acesso a um comando de menu por meio de uma tecla de atalho.</span><span class="sxs-lookup"><span data-stu-id="91bcc-112">You should both hide and disable the menu, as hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="91bcc-113">Defina a <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade de um item de menu de nível superior `false` como para ocultar o menu inteiro.</span><span class="sxs-lookup"><span data-stu-id="91bcc-113">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>

## <a name="see-also"></a><span data-ttu-id="91bcc-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91bcc-114">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="91bcc-115">Como: Ocultar ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="91bcc-115">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="91bcc-116">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="91bcc-116">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
