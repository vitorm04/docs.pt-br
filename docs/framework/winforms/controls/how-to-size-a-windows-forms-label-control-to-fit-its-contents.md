---
title: 'Como: Dimensionar um controle de rótulo do Windows Forms para encaixar o conteúdo'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 110aab0c0826bb4b06e22158afd6af37b5406be4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312183"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="eb38f-102">Como: Dimensionar um controle de rótulo do Windows Forms para encaixar o conteúdo</span><span class="sxs-lookup"><span data-stu-id="eb38f-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="eb38f-103">Os formulários do Windows <xref:System.Windows.Forms.Label> controle pode ser uma linha ou várias linhas, e podem ser fixas de tamanho ou pode redimensionar automaticamente para acomodar sua legenda.</span><span class="sxs-lookup"><span data-stu-id="eb38f-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="eb38f-104">O <xref:System.Windows.Forms.Label.AutoSize%2A> propriedade ajuda você a dimensionar os controles para ajustar as legendas de maiores ou menores, que é particularmente útil se a legenda será alterado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="eb38f-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="eb38f-105">Para fazer com que um controle de rótulo redimensionar dinamicamente para ajustar seu conteúdo</span><span class="sxs-lookup"><span data-stu-id="eb38f-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1. <span data-ttu-id="eb38f-106">Defina suas <xref:System.Windows.Forms.Label.AutoSize%2A> propriedade para `true`.</span><span class="sxs-lookup"><span data-stu-id="eb38f-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="eb38f-107">Se <xref:System.Windows.Forms.Label.AutoSize%2A> é definido como `false`, palavras especificadas no <xref:System.Windows.Forms.Label.Text%2A> propriedade será encapsulado para a próxima linha se possível, mas o controle não crescerá.</span><span class="sxs-lookup"><span data-stu-id="eb38f-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb38f-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb38f-108">See also</span></span>

- [<span data-ttu-id="eb38f-109">Como: Criar chaves de acesso com controles de rótulo dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eb38f-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [<span data-ttu-id="eb38f-110">Visão geral do controle Label</span><span class="sxs-lookup"><span data-stu-id="eb38f-110">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="eb38f-111">Controle de rótulo</span><span class="sxs-lookup"><span data-stu-id="eb38f-111">Label Control</span></span>](label-control-windows-forms.md)
