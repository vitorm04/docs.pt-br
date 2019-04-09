---
title: 'Como: Bloquear controles nos Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: ac02e825218f14f8479e67a79da0c86e1c9ffe11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117917"
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="d05bb-102">Como: Bloquear controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d05bb-102">How to: Lock Controls to Windows Forms</span></span>
<span data-ttu-id="d05bb-103">Ao projetar a interface do usuário do seu aplicativo do Windows, você pode bloquear os controles quando eles são posicionados corretamente, para que você não os mova nem os redimensione inadvertidamente ao configurar outras propriedades.</span><span class="sxs-lookup"><span data-stu-id="d05bb-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>  
  
 <span data-ttu-id="d05bb-104">Além disso, você pode bloquear e desbloquear todos os controles no formulário de uma vez, o que é útil para formulários com muitos controles ou você pode desbloquear controles individuais.</span><span class="sxs-lookup"><span data-stu-id="d05bb-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="d05bb-105">Depois de colocar todos os controles no local desejado no formulário, bloqueie-os no local para evitar a movimentação incorreta.</span><span class="sxs-lookup"><span data-stu-id="d05bb-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d05bb-106">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="d05bb-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d05bb-107">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="d05bb-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d05bb-108">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d05bb-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-lock-a-control"></a><span data-ttu-id="d05bb-109">Para bloquear um controle</span><span class="sxs-lookup"><span data-stu-id="d05bb-109">To lock a control</span></span>  
  
1.  <span data-ttu-id="d05bb-110">Na janela **Propriedades**, clique na propriedade **Bloqueado** e selecione `true`.</span><span class="sxs-lookup"><span data-stu-id="d05bb-110">In the **Properties** window, click the **Locked** property and select `true`.</span></span> <span data-ttu-id="d05bb-111">(Clicar duas vezes no nome alterna a configuração da propriedade.)</span><span class="sxs-lookup"><span data-stu-id="d05bb-111">(Double-clicking the name toggles the property setting.)</span></span>  
  
     <span data-ttu-id="d05bb-112">Como alternativa, clique com o botão direito do mouse no controle e escolha **Bloquear Controles**.</span><span class="sxs-lookup"><span data-stu-id="d05bb-112">Alternatively, right-click the control and choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d05bb-113">O bloqueio dos controles evita que eles sejam arrastados para um novo tamanho ou local na superfície de design.</span><span class="sxs-lookup"><span data-stu-id="d05bb-113">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="d05bb-114">No entanto, você ainda pode alterar o tamanho ou local dos controles por meio da janela **Propriedades** ou no código.</span><span class="sxs-lookup"><span data-stu-id="d05bb-114">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>  
  
### <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="d05bb-115">Para bloquear todos os controles em um formulário</span><span class="sxs-lookup"><span data-stu-id="d05bb-115">To lock all the controls on a form</span></span>  
  
1.  <span data-ttu-id="d05bb-116">No menu **Formatar**, escolha **Bloquear Controles**.</span><span class="sxs-lookup"><span data-stu-id="d05bb-116">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d05bb-117">Esse comando bloqueia também o tamanho do formulário, pois um formulário é um controle.</span><span class="sxs-lookup"><span data-stu-id="d05bb-117">This command locks the form's size as well, because a form is a control.</span></span>  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="d05bb-118">Para desbloquear todos os controles bloqueados em um formulário</span><span class="sxs-lookup"><span data-stu-id="d05bb-118">To unlock all locked controls on a form</span></span>  
  
1.  <span data-ttu-id="d05bb-119">No menu **Formatar**, escolha **Bloquear Controles**.</span><span class="sxs-lookup"><span data-stu-id="d05bb-119">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
     <span data-ttu-id="d05bb-120">Todos os controles bloqueados anteriormente no formulário agora estão desbloqueados.</span><span class="sxs-lookup"><span data-stu-id="d05bb-120">All previously locked controls on the form are now unlocked.</span></span>  
  
### <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="d05bb-121">Para desbloquear controles bloqueados individualmente</span><span class="sxs-lookup"><span data-stu-id="d05bb-121">To unlock locked controls individually</span></span>  
  
1.  <span data-ttu-id="d05bb-122">Na janela **Propriedades**, clique na propriedade **Bloqueado** e selecione `false`.</span><span class="sxs-lookup"><span data-stu-id="d05bb-122">In the **Properties** window, click the **Locked** property and select `false`.</span></span> <span data-ttu-id="d05bb-123">(Clicar duas vezes no nome alterna a configuração da propriedade.)</span><span class="sxs-lookup"><span data-stu-id="d05bb-123">(Double-clicking the name toggles the property setting.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d05bb-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d05bb-124">See also</span></span>

- [<span data-ttu-id="d05bb-125">Controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d05bb-125">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="d05bb-126">Organizando controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d05bb-126">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="d05bb-127">Identificando controles dos Windows Forms individuais e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="d05bb-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="d05bb-128">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d05bb-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="d05bb-129">Controles dos Windows Forms por função</span><span class="sxs-lookup"><span data-stu-id="d05bb-129">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
