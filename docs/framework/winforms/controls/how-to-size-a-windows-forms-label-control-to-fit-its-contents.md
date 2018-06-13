---
title: Como dimensionar um controle de rótulo dos Windows Forms para encaixar o conteúdo
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: e067966b606d77ceb9d11d2784c0d5f73ad332a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533722"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="321e0-102">Como dimensionar um controle de rótulo dos Windows Forms para encaixar o conteúdo</span><span class="sxs-lookup"><span data-stu-id="321e0-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="321e0-103">Windows Forms <xref:System.Windows.Forms.Label> controle pode ser de linha única ou multilinha, e podem ser fixas no tamanho ou pode redimensionar automaticamente para acomodar a legenda.</span><span class="sxs-lookup"><span data-stu-id="321e0-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="321e0-104">O <xref:System.Windows.Forms.Label.AutoSize%2A> propriedade ajuda a dimensionar os controles para caber legendas maiores ou menores, que é especialmente útil se a legenda será alterado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="321e0-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="321e0-105">Para fazer com que um controle de rótulo redimensionar dinamicamente para acomodar seu conteúdo</span><span class="sxs-lookup"><span data-stu-id="321e0-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1.  <span data-ttu-id="321e0-106">Definir seu <xref:System.Windows.Forms.Label.AutoSize%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="321e0-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="321e0-107">Se <xref:System.Windows.Forms.Label.AutoSize%2A> é definido como `false`, palavras especificadas no <xref:System.Windows.Forms.Label.Text%2A> propriedade ajustarão para a próxima linha se possível, mas o controle não aumentará.</span><span class="sxs-lookup"><span data-stu-id="321e0-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="321e0-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="321e0-108">See Also</span></span>  
 [<span data-ttu-id="321e0-109">Como criar teclas de acesso com controles de rótulo dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="321e0-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 [<span data-ttu-id="321e0-110">Visão geral do controle Label</span><span class="sxs-lookup"><span data-stu-id="321e0-110">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="321e0-111">Controle de rótulo</span><span class="sxs-lookup"><span data-stu-id="321e0-111">Label Control</span></span>](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
