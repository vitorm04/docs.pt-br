---
title: Visão geral do controle Divisor
ms.date: 03/30/2017
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
ms.openlocfilehash: 3d6da8daf9bb0e8df4f69554a87725a7ddb65acb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742888"
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="c74e2-102">Visão geral do controle divisor (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c74e2-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="c74e2-103">Embora <xref:System.Windows.Forms.SplitContainer> substitua e adicione funcionalidade ao controle <xref:System.Windows.Forms.Splitter> de versões anteriores, <xref:System.Windows.Forms.Splitter> é mantido para compatibilidade com versões anteriores e uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="c74e2-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="c74e2-104">Windows Forms <xref:System.Windows.Forms.Splitter> controles são usados para redimensionar controles encaixados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c74e2-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="c74e2-105">O controle de <xref:System.Windows.Forms.Splitter> geralmente é usado em formulários com controles que têm tamanhos variáveis de dados a serem apresentados, como o Windows Explorer, cujos painéis de dados contêm informações de larguras variadas em momentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="c74e2-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="c74e2-106">Trabalhando com o controle Splitter</span><span class="sxs-lookup"><span data-stu-id="c74e2-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="c74e2-107">Quando o usuário aponta o ponteiro do mouse na borda não encaixada de um controle que pode ser redimensionado por um controle splitter, o ponteiro muda de aparência para indicar que o controle pode ser redimensionado.</span><span class="sxs-lookup"><span data-stu-id="c74e2-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="c74e2-108">Com o controle Splitter, o usuário pode redimensionar o controle encaixado que esteja imediatamente antes dele.</span><span class="sxs-lookup"><span data-stu-id="c74e2-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="c74e2-109">Portanto, para permitir que o usuário redimensione um controle encaixado em tempo de execução, encaixe o controle a ser redimensionado em uma borda de um contêiner e, em seguida, encaixe um controle Splitter no mesmo lado do contêiner.</span><span class="sxs-lookup"><span data-stu-id="c74e2-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c74e2-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="c74e2-110">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="c74e2-111">Como encaixar controles no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c74e2-111">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="c74e2-112">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c74e2-112">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
