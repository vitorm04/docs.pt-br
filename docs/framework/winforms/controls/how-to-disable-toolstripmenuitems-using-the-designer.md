---
title: 'Como: Desabilitar ToolStripMenuItems usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: 9965825458afcd50b29699c3b89ed506078e04d9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338053"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="7571b-102">Como: Desabilitar ToolStripMenuItems usando o designer</span><span class="sxs-lookup"><span data-stu-id="7571b-102">How to: Disable ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="7571b-103">Você pode limitar ou ampliar os comandos que um usuário pode fazer ao habilitar e desabilitar itens de menu em resposta a atividades do usuário.</span><span class="sxs-lookup"><span data-stu-id="7571b-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="7571b-104">Itens de menu são habilitados por padrão, quando eles são criados, mas isso pode ser ajustado por meio de <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="7571b-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="7571b-105">Você pode manipular essa propriedade em tempo de design na janela **Propriedades** ou programaticamente configurando ela no código.</span><span class="sxs-lookup"><span data-stu-id="7571b-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span> <span data-ttu-id="7571b-106">Para obter mais informações, confira [Como: Desabilitar ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span><span class="sxs-lookup"><span data-stu-id="7571b-106">For more information, see [How to: Disable ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7571b-107">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="7571b-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7571b-108">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="7571b-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7571b-109">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="7571b-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-disable-a-menu-item-at-design-time"></a><span data-ttu-id="7571b-110">Para desabilitar um item de menu em tempo de design</span><span class="sxs-lookup"><span data-stu-id="7571b-110">To disable a menu item at design time</span></span>  
  
1. <span data-ttu-id="7571b-111">Com o item de menu selecionado no formulário, defina as <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriedade para `false`.</span><span class="sxs-lookup"><span data-stu-id="7571b-111">With the menu item selected on the form, set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="7571b-112">Desabilitar o primeiro item de menu ou o de nível superior em um menu desabilita todos os itens de menu contidos no menu.</span><span class="sxs-lookup"><span data-stu-id="7571b-112">Disabling the first or top-level menu item in a menu disables all the menu items contained within the menu.</span></span> <span data-ttu-id="7571b-113">Da mesma forma, desabilitar um item de menu que tenha itens de submenu desabilita os itens do submenu.</span><span class="sxs-lookup"><span data-stu-id="7571b-113">Likewise, disabling a menu item that has submenu items disables the submenu items.</span></span> <span data-ttu-id="7571b-114">Se todos os comandos em um determinado menu estiverem indisponíveis para o usuário, ocultar e desabilitar todo o menu será considerado uma boa prática de programação, pois isso apresenta uma interface do usuário mais enxuta.</span><span class="sxs-lookup"><span data-stu-id="7571b-114">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="7571b-115">Você deve ocultar e desabilitar o menu, pois apenas ocultar não impede o acesso a um comando de menu por meio de uma tecla de atalho.</span><span class="sxs-lookup"><span data-stu-id="7571b-115">You should both hide and disable the menu, as hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="7571b-116">Defina as <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade de um item de menu de nível superior para `false` para ocultar o menu inteiro.</span><span class="sxs-lookup"><span data-stu-id="7571b-116">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7571b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7571b-117">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="7571b-118">Como: Ocultar ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="7571b-118">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="7571b-119">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="7571b-119">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
