---
title: 'Como: Bloquear controles nos Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f6dd079331c6c1883839efe5c6cb127044380fd2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987466"
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="ce243-102">Como: Bloquear controles para Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce243-102">How to: Lock controls to Windows Forms</span></span>

<span data-ttu-id="ce243-103">Ao projetar a interface do usuário do seu aplicativo do Windows, você pode bloquear os controles quando eles são posicionados corretamente, para que você não os mova nem os redimensione inadvertidamente ao configurar outras propriedades.</span><span class="sxs-lookup"><span data-stu-id="ce243-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>

<span data-ttu-id="ce243-104">Além disso, você pode bloquear e desbloquear todos os controles no formulário de uma vez, o que é útil para formulários com muitos controles ou você pode desbloquear controles individuais.</span><span class="sxs-lookup"><span data-stu-id="ce243-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="ce243-105">Depois de colocar todos os controles no local desejado no formulário, bloqueie-os no local para evitar a movimentação incorreta.</span><span class="sxs-lookup"><span data-stu-id="ce243-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>

## <a name="to-lock-a-control"></a><span data-ttu-id="ce243-106">Para bloquear um controle</span><span class="sxs-lookup"><span data-stu-id="ce243-106">To lock a control</span></span>

<span data-ttu-id="ce243-107">Na janela **Propriedades** do Visual Studio, selecione a propriedade **bloqueado** e, em seguida, selecione **verdadeiro**.</span><span class="sxs-lookup"><span data-stu-id="ce243-107">In the **Properties** window of Visual Studio, select the **Locked** property and then select **true**.</span></span> <span data-ttu-id="ce243-108">(Clicar duas vezes no nome alterna a configuração da propriedade.)</span><span class="sxs-lookup"><span data-stu-id="ce243-108">(Double-clicking the name toggles the property setting.)</span></span>

<span data-ttu-id="ce243-109">Como alternativa, clique com o botão direito do mouse no controle e escolha **Bloquear Controles**.</span><span class="sxs-lookup"><span data-stu-id="ce243-109">Alternatively, right-click the control and choose **Lock Controls**.</span></span>

> [!NOTE]
> <span data-ttu-id="ce243-110">O bloqueio dos controles evita que eles sejam arrastados para um novo tamanho ou local na superfície de design.</span><span class="sxs-lookup"><span data-stu-id="ce243-110">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="ce243-111">No entanto, você ainda pode alterar o tamanho ou local dos controles por meio da janela **Propriedades** ou no código.</span><span class="sxs-lookup"><span data-stu-id="ce243-111">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>

## <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="ce243-112">Para bloquear todos os controles em um formulário</span><span class="sxs-lookup"><span data-stu-id="ce243-112">To lock all the controls on a form</span></span>

<span data-ttu-id="ce243-113">No menu **Formatar**, escolha **Bloquear Controles**.</span><span class="sxs-lookup"><span data-stu-id="ce243-113">From the **Format** menu, choose **Lock Controls**.</span></span>

> [!NOTE]
> <span data-ttu-id="ce243-114">Esse comando bloqueia também o tamanho do formulário, pois um formulário é um controle.</span><span class="sxs-lookup"><span data-stu-id="ce243-114">This command locks the form's size as well, because a form is a control.</span></span>

## <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="ce243-115">Para desbloquear todos os controles bloqueados em um formulário</span><span class="sxs-lookup"><span data-stu-id="ce243-115">To unlock all locked controls on a form</span></span>

<span data-ttu-id="ce243-116">No menu **Formatar**, escolha **Bloquear Controles**.</span><span class="sxs-lookup"><span data-stu-id="ce243-116">From the **Format** menu, choose **Lock Controls**.</span></span>

<span data-ttu-id="ce243-117">Todos os controles bloqueados anteriormente no formulário agora estão desbloqueados.</span><span class="sxs-lookup"><span data-stu-id="ce243-117">All previously locked controls on the form are now unlocked.</span></span>

## <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="ce243-118">Para desbloquear controles bloqueados individualmente</span><span class="sxs-lookup"><span data-stu-id="ce243-118">To unlock locked controls individually</span></span>

<span data-ttu-id="ce243-119">Na janela **Propriedades** , selecione a propriedade **bloqueado** e, em seguida, selecione **falso**.</span><span class="sxs-lookup"><span data-stu-id="ce243-119">In the **Properties** window, select the **Locked** property and then select **false**.</span></span> <span data-ttu-id="ce243-120">(Clicar duas vezes no nome alterna a configuração da propriedade.)</span><span class="sxs-lookup"><span data-stu-id="ce243-120">(Double-clicking the name toggles the property setting.)</span></span>

## <a name="see-also"></a><span data-ttu-id="ce243-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce243-121">See also</span></span>

- [<span data-ttu-id="ce243-122">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce243-122">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="ce243-123">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="ce243-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="ce243-124">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce243-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="ce243-125">Controles dos Windows Forms por função</span><span class="sxs-lookup"><span data-stu-id="ce243-125">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
