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
ms.openlocfilehash: 25602e1a878443bd54411dfd6481581abebda5c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755474"
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a><span data-ttu-id="25c31-102">Exibição de caracteres asiáticos com a propriedade ImeMode</span><span class="sxs-lookup"><span data-stu-id="25c31-102">Display of Asian Characters with the ImeMode Property</span></span>
<span data-ttu-id="25c31-103">O <xref:System.Windows.Forms.Control.ImeMode%2A> por formulários e controles, a propriedade é usada para forçar um modo específico para um editor de método de entrada (IME).</span><span class="sxs-lookup"><span data-stu-id="25c31-103">The <xref:System.Windows.Forms.Control.ImeMode%2A> property is used by forms and controls to force a specific mode for an input method editor (IME).</span></span> <span data-ttu-id="25c31-104">O IME é um componente essencial para escrever scripts de chinês, japonês e coreano, já que esses sistemas de escrita têm mais caracteres que podem ser codificados para um teclado normal.</span><span class="sxs-lookup"><span data-stu-id="25c31-104">The IME is an essential component for writing Chinese, Japanese, and Korean scripts, since these writing systems have more characters than can be encoded for a regular keyboard.</span></span> <span data-ttu-id="25c31-105">Por exemplo, você talvez queira permitir que apenas caracteres ASCII em uma caixa de texto específica.</span><span class="sxs-lookup"><span data-stu-id="25c31-105">For example, you may want to allow only ASCII characters in a particular text box.</span></span> <span data-ttu-id="25c31-106">Nesse caso, você pode definir as <xref:System.Windows.Forms.Control.ImeMode%2A> propriedade para <xref:System.Windows.Forms.ImeMode> e os usuários somente poderão inserir caracteres ASCII para a caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="25c31-106">In such a case you can set the <xref:System.Windows.Forms.Control.ImeMode%2A> property to <xref:System.Windows.Forms.ImeMode> and users will only be able to enter ASCII characters for that particular text box.</span></span> <span data-ttu-id="25c31-107">O valor padrão de <xref:System.Windows.Forms.Control.ImeMode%2A> é de propriedade <xref:System.Windows.Forms.ImeMode>, portanto, se você definir a propriedade de um formulário, todos os controles no formulário herdarão essa definição.</span><span class="sxs-lookup"><span data-stu-id="25c31-107">The default value of the <xref:System.Windows.Forms.Control.ImeMode%2A> property is <xref:System.Windows.Forms.ImeMode>, so if you set the property for a form, all controls on the form will inherit that setting.</span></span> <span data-ttu-id="25c31-108">Para obter mais informações, consulte <xref:System.Windows.Forms.Control.ImeMode%2A> ) e <xref:System.Windows.Forms.ImeMode>.</span><span class="sxs-lookup"><span data-stu-id="25c31-108">For more information, see <xref:System.Windows.Forms.Control.ImeMode%2A> ) and <xref:System.Windows.Forms.ImeMode>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25c31-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25c31-109">See also</span></span>

- [<span data-ttu-id="25c31-110">Globalizando aplicativos dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25c31-110">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)
