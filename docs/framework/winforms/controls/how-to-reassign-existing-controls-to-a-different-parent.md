---
title: Como reatribuir controles existentes a um pai diferente
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1767fcff1742f4ad630b4b996c709b7ded53a129
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459203"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="c1600-102">Como: Reatribuir controles existentes a um pai diferente</span><span class="sxs-lookup"><span data-stu-id="c1600-102">How to: Reassign existing controls to a different parent</span></span>

<span data-ttu-id="c1600-103">Você pode atribuir controles que existem no formulário a um novo controle de contêiner.</span><span class="sxs-lookup"><span data-stu-id="c1600-103">You can assign controls that exist on your form to a new container control.</span></span>

1. <span data-ttu-id="c1600-104">No Visual Studio, arraste três controles de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="c1600-104">In Visual Studio, drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span> <span data-ttu-id="c1600-105">Posicione-os próximo entre si, mas deixe-os desalinhados.</span><span class="sxs-lookup"><span data-stu-id="c1600-105">Position them near to each other, but leave them unaligned.</span></span>

2. <span data-ttu-id="c1600-106">Na **caixa de ferramentas**, clique no ícone controle de <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="c1600-106">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span> <span data-ttu-id="c1600-107">(Não arraste o ícone para o formulário.)</span><span class="sxs-lookup"><span data-stu-id="c1600-107">(Do not drag the icon onto the form.)</span></span>

3. <span data-ttu-id="c1600-108">Mova o ponteiro do mouse para perto dos três <xref:System.Windows.Forms.Button> controles.</span><span class="sxs-lookup"><span data-stu-id="c1600-108">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>

   <span data-ttu-id="c1600-109">O ponteiro muda para uma cruz com o ícone de controle de <xref:System.Windows.Forms.FlowLayoutPanel> anexado.</span><span class="sxs-lookup"><span data-stu-id="c1600-109">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>

4. <span data-ttu-id="c1600-110">Clique e mantenha o botão do mouse pressionado.</span><span class="sxs-lookup"><span data-stu-id="c1600-110">Click and hold the mouse button.</span></span>

5. <span data-ttu-id="c1600-111">Arraste o ponteiro do mouse para desenhar a estrutura de tópicos do controle de <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="c1600-111">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="c1600-112">Desenhe a estrutura de tópicos em torno dos três controles de <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="c1600-112">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>

7. <span data-ttu-id="c1600-113">Solte o botão do mouse.</span><span class="sxs-lookup"><span data-stu-id="c1600-113">Release the mouse button.</span></span>

   <span data-ttu-id="c1600-114">Os três controles de <xref:System.Windows.Forms.Button> agora são inseridos no controle de <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="c1600-114">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1600-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1600-115">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="c1600-116">Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c1600-116">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="c1600-117">Instruções passo a passo: organizando controles no Windows Forms usando guias de alinhamento</span><span class="sxs-lookup"><span data-stu-id="c1600-117">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
