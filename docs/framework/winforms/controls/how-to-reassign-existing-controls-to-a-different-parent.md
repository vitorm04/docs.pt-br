---
title: 'Como: Transferir controles existentes a um pai diferente'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 84e662e0bd2689115abe128c6442e4462eed3e18
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987034"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="d2ff3-102">Como: Reatribuir controles existentes a um pai diferente</span><span class="sxs-lookup"><span data-stu-id="d2ff3-102">How to: Reassign existing controls to a different parent</span></span>

<span data-ttu-id="d2ff3-103">Você pode atribuir controles que existem no formulário a um novo controle de contêiner.</span><span class="sxs-lookup"><span data-stu-id="d2ff3-103">You can assign controls that exist on your form to a new container control.</span></span>

1. <span data-ttu-id="d2ff3-104">No Visual Studio, arraste três <xref:System.Windows.Forms.Button> controles da **caixa de ferramentas** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="d2ff3-104">In Visual Studio, drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span> <span data-ttu-id="d2ff3-105">Posicione-os próximo entre si, mas deixe-os desalinhados.</span><span class="sxs-lookup"><span data-stu-id="d2ff3-105">Position them near to each other, but leave them unaligned.</span></span>

2. <span data-ttu-id="d2ff3-106">Na **caixa de ferramentas**, clique <xref:System.Windows.Forms.FlowLayoutPanel> no ícone de controle.</span><span class="sxs-lookup"><span data-stu-id="d2ff3-106">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span> <span data-ttu-id="d2ff3-107">(Não arraste o ícone para o formulário.)</span><span class="sxs-lookup"><span data-stu-id="d2ff3-107">(Do not drag the icon onto the form.)</span></span>

3. <span data-ttu-id="d2ff3-108">Mova o ponteiro do mouse para perto dos <xref:System.Windows.Forms.Button> três controles.</span><span class="sxs-lookup"><span data-stu-id="d2ff3-108">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>

   <span data-ttu-id="d2ff3-109">O ponteiro muda para um cruzado com <xref:System.Windows.Forms.FlowLayoutPanel> o ícone de controle anexado.</span><span class="sxs-lookup"><span data-stu-id="d2ff3-109">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>

4. <span data-ttu-id="d2ff3-110">Clique e mantenha o botão do mouse pressionado.</span><span class="sxs-lookup"><span data-stu-id="d2ff3-110">Click and hold the mouse button.</span></span>

5. <span data-ttu-id="d2ff3-111">Arraste o ponteiro do mouse para desenhar a estrutura de <xref:System.Windows.Forms.FlowLayoutPanel> tópicos do controle.</span><span class="sxs-lookup"><span data-stu-id="d2ff3-111">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="d2ff3-112">Desenhe a estrutura de tópicos em <xref:System.Windows.Forms.Button> torno dos três controles.</span><span class="sxs-lookup"><span data-stu-id="d2ff3-112">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>

7. <span data-ttu-id="d2ff3-113">Solte o botão do mouse.</span><span class="sxs-lookup"><span data-stu-id="d2ff3-113">Release the mouse button.</span></span>

   <span data-ttu-id="d2ff3-114">Os três <xref:System.Windows.Forms.Button> controles agora são inseridos <xref:System.Windows.Forms.FlowLayoutPanel> no controle.</span><span class="sxs-lookup"><span data-stu-id="d2ff3-114">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2ff3-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2ff3-115">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="d2ff3-116">Passo a passo: Organizando controles em Windows Forms usando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d2ff3-116">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="d2ff3-117">Passo a passo: Organizando controles em Windows Forms usando Snaplines</span><span class="sxs-lookup"><span data-stu-id="d2ff3-117">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
