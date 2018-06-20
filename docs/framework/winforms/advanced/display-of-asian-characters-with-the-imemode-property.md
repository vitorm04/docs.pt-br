---
title: Exibição de caracteres asiáticos com a propriedade ImeMode
ms.date: 03/30/2017
helpviewer_keywords:
- Asian languages [Windows Forms], displaying with ImeMode
- Chinese characters [Windows Forms], displaying with ImeMode
- IME mode
- Japanese characters [Windows Forms], displaying with ImeMode
- international applications [Windows Forms], character display
- international characters
- Korean characters
- Asian languages
- Input Method Editor (IME), mode
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: c60ae399-0dab-4f07-9dea-6dbfb15ec0ae
ms.openlocfilehash: d3733f642d4218c851040582ee5637b5486a7804
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208547"
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a><span data-ttu-id="ee3ce-102">Exibição de caracteres asiáticos com a propriedade ImeMode</span><span class="sxs-lookup"><span data-stu-id="ee3ce-102">Display of Asian Characters with the ImeMode Property</span></span>
<span data-ttu-id="ee3ce-103">O <xref:System.Windows.Forms.Control.ImeMode%2A> propriedade é usada por formulários e controles para forçar um modo específico para um editor de método de entrada (IME).</span><span class="sxs-lookup"><span data-stu-id="ee3ce-103">The <xref:System.Windows.Forms.Control.ImeMode%2A> property is used by forms and controls to force a specific mode for an input method editor (IME).</span></span> <span data-ttu-id="ee3ce-104">O IME é um componente essencial para escrever scripts chinês, japonês e coreano, pois esses sistemas de escrita têm mais caracteres que podem ser codificados para um teclado normal.</span><span class="sxs-lookup"><span data-stu-id="ee3ce-104">The IME is an essential component for writing Chinese, Japanese, and Korean scripts, since these writing systems have more characters than can be encoded for a regular keyboard.</span></span> <span data-ttu-id="ee3ce-105">Por exemplo, convém permitir que apenas caracteres ASCII em uma caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="ee3ce-105">For example, you may want to allow only ASCII characters in a particular text box.</span></span> <span data-ttu-id="ee3ce-106">Nesse caso, você pode definir o <xref:System.Windows.Forms.Control.ImeMode%2A> propriedade <xref:System.Windows.Forms.ImeMode> e os usuários somente poderão inserir caracteres ASCII para a caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="ee3ce-106">In such a case you can set the <xref:System.Windows.Forms.Control.ImeMode%2A> property to <xref:System.Windows.Forms.ImeMode> and users will only be able to enter ASCII characters for that particular text box.</span></span> <span data-ttu-id="ee3ce-107">O valor padrão de <xref:System.Windows.Forms.Control.ImeMode%2A> é de propriedade <xref:System.Windows.Forms.ImeMode>, portanto, se você definir a propriedade de um formulário, todos os controles no formulário herdarão essa definição.</span><span class="sxs-lookup"><span data-stu-id="ee3ce-107">The default value of the <xref:System.Windows.Forms.Control.ImeMode%2A> property is <xref:System.Windows.Forms.ImeMode>, so if you set the property for a form, all controls on the form will inherit that setting.</span></span> <span data-ttu-id="ee3ce-108">Para obter mais informações, consulte <xref:System.Windows.Forms.Control.ImeMode%2A> ) e <xref:System.Windows.Forms.ImeMode>.</span><span class="sxs-lookup"><span data-stu-id="ee3ce-108">For more information, see <xref:System.Windows.Forms.Control.ImeMode%2A> ) and <xref:System.Windows.Forms.ImeMode>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee3ce-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee3ce-109">See also</span></span>

[<span data-ttu-id="ee3ce-110">Globalizando aplicativos do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ee3ce-110">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)
