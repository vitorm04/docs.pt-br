---
title: 'Como: Transferir controles existentes a um pai diferente'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: a65b3c2b596a2d88ce4236aeadd86993bb268aa6
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039782"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="410ae-102">Como: Transferir controles existentes a um pai diferente</span><span class="sxs-lookup"><span data-stu-id="410ae-102">How to: Reassign Existing Controls to a Different Parent</span></span>
<span data-ttu-id="410ae-103">Você pode atribuir controles que existem no formulário a um novo controle de contêiner.</span><span class="sxs-lookup"><span data-stu-id="410ae-103">You can assign controls that exist on your form to a new container control.</span></span>

## <a name="to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="410ae-104">Para reatribuir controles existentes a um pai diferente</span><span class="sxs-lookup"><span data-stu-id="410ae-104">To reassign existing controls to a different parent</span></span>

1. <span data-ttu-id="410ae-105">Arraste três <xref:System.Windows.Forms.Button> controles da **caixa de ferramentas** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="410ae-105">Drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span>

     <span data-ttu-id="410ae-106">Posicione-os próximo entre si, mas deixe-os desalinhados.</span><span class="sxs-lookup"><span data-stu-id="410ae-106">Position them near to each other, but leave them unaligned.</span></span>

2. <span data-ttu-id="410ae-107">Na **caixa de ferramentas**, clique <xref:System.Windows.Forms.FlowLayoutPanel> no ícone de controle.</span><span class="sxs-lookup"><span data-stu-id="410ae-107">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span>

     <span data-ttu-id="410ae-108">Não arraste o ícone para o formulário.</span><span class="sxs-lookup"><span data-stu-id="410ae-108">Do not drag the icon onto the form.</span></span>

3. <span data-ttu-id="410ae-109">Mova o ponteiro do mouse para perto dos <xref:System.Windows.Forms.Button> três controles.</span><span class="sxs-lookup"><span data-stu-id="410ae-109">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>

     <span data-ttu-id="410ae-110">O ponteiro muda para um cruzado com <xref:System.Windows.Forms.FlowLayoutPanel> o ícone de controle anexado.</span><span class="sxs-lookup"><span data-stu-id="410ae-110">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>

4. <span data-ttu-id="410ae-111">Clique e mantenha o botão do mouse pressionado.</span><span class="sxs-lookup"><span data-stu-id="410ae-111">Click and hold the mouse button.</span></span>

5. <span data-ttu-id="410ae-112">Arraste o ponteiro do mouse para desenhar a estrutura de <xref:System.Windows.Forms.FlowLayoutPanel> tópicos do controle.</span><span class="sxs-lookup"><span data-stu-id="410ae-112">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="410ae-113">Desenhe a estrutura de tópicos em <xref:System.Windows.Forms.Button> torno dos três controles.</span><span class="sxs-lookup"><span data-stu-id="410ae-113">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>

7. <span data-ttu-id="410ae-114">Solte o botão do mouse.</span><span class="sxs-lookup"><span data-stu-id="410ae-114">Release the mouse button.</span></span>

     <span data-ttu-id="410ae-115">Os três <xref:System.Windows.Forms.Button> controles agora são inseridos <xref:System.Windows.Forms.FlowLayoutPanel> no controle.</span><span class="sxs-lookup"><span data-stu-id="410ae-115">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="410ae-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="410ae-116">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="410ae-117">Organizando Controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="410ae-117">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="410ae-118">Passo a passo: Organizando controles em Windows Forms usando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="410ae-118">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="410ae-119">Passo a passo: Organizando controles em Windows Forms usando Snaplines</span><span class="sxs-lookup"><span data-stu-id="410ae-119">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
