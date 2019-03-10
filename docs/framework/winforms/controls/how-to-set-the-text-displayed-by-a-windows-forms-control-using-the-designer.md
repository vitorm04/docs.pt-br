---
title: 'Como: Definir o texto exibido por um Windows Forms usando o Designer de controle'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
ms.openlocfilehash: 4d3f12bd2606e40b5ceeef716d8f5d264bc46622
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707372"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a><span data-ttu-id="bc814-102">Como: Definir o texto exibido por um Windows Forms usando o Designer de controle</span><span class="sxs-lookup"><span data-stu-id="bc814-102">How to: Set the Text Displayed by a Windows Forms Control Using the Designer</span></span>
<span data-ttu-id="bc814-103">Controles dos Windows Forms normalmente exibem algum texto que está relacionado à função primária do controle.</span><span class="sxs-lookup"><span data-stu-id="bc814-103">Windows Forms controls typically display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="bc814-104">Por exemplo, um <xref:System.Windows.Forms.Button> controle normalmente exibe uma legenda que indica qual ação será executada quando o botão é clicado.</span><span class="sxs-lookup"><span data-stu-id="bc814-104">For example, a <xref:System.Windows.Forms.Button> control typically displays a caption that indicates what action will be performed when the button is clicked.</span></span> <span data-ttu-id="bc814-105">Para todos os controles, você pode definir ou retornar o texto usando o <xref:System.Windows.Forms.Control.Text%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="bc814-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="bc814-106">Você pode alterar a fonte usando o <xref:System.Windows.Forms.Control.Font%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="bc814-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a><span data-ttu-id="bc814-107">Para definir o texto e a fonte com o designer</span><span class="sxs-lookup"><span data-stu-id="bc814-107">To set the text and font with the designer</span></span>  
  
1.  <span data-ttu-id="bc814-108">Na janela Propriedades, defina o <xref:System.Windows.Forms.Control.Text%2A> propriedade do controle para uma cadeia de caracteres apropriada.</span><span class="sxs-lookup"><span data-stu-id="bc814-108">In the Properties window, set the <xref:System.Windows.Forms.Control.Text%2A> property of the control to an appropriate string.</span></span>  
  
     <span data-ttu-id="bc814-109">Para criar uma tecla de atalho sublinhada, inclua um e comercial (&) antes da letra que será a tecla de atalho.</span><span class="sxs-lookup"><span data-stu-id="bc814-109">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>  
  
2.  <span data-ttu-id="bc814-110">Na janela Propriedades, clique no botão de reticências (![captura de tela VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de <xref:System.Windows.Forms.Control.Font%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="bc814-110">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
     <span data-ttu-id="bc814-111">Na caixa de diálogo de fonte padrão, escolha a fonte, o estilo da fonte, o tamanho, efeitos (como riscado ou sublinhado) e o script que você deseja.</span><span class="sxs-lookup"><span data-stu-id="bc814-111">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc814-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc814-112">See also</span></span>
- [<span data-ttu-id="bc814-113">Como: Definir o texto exibido pelo controle de um Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bc814-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="bc814-114">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="bc814-114">Using Fonts and Text</span></span>](../advanced/using-fonts-and-text.md)
- [<span data-ttu-id="bc814-115">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="bc814-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
