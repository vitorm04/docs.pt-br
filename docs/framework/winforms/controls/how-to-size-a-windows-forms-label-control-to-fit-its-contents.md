---
title: Dimensionar um controle rótulo para ajustar seu conteúdo
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 6a563693feaa5074f5d13f0b82cc4d0305a79c23
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743780"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="cd8c3-102">Como dimensionar um controle de rótulo dos Windows Forms para encaixar o conteúdo</span><span class="sxs-lookup"><span data-stu-id="cd8c3-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="cd8c3-103">O controle de <xref:System.Windows.Forms.Label> de Windows Forms pode ser de linha única ou de várias linhas e pode ser corrigido em tamanho ou pode ser redimensionado automaticamente para acomodar sua legenda.</span><span class="sxs-lookup"><span data-stu-id="cd8c3-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="cd8c3-104">A propriedade <xref:System.Windows.Forms.Label.AutoSize%2A> ajuda a dimensionar os controles para se ajustar a legendas maiores ou menores, o que é particularmente útil se a legenda for alterada em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cd8c3-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="cd8c3-105">Para fazer com que um controle de rótulo redimensione dinamicamente para se ajustar ao seu conteúdo</span><span class="sxs-lookup"><span data-stu-id="cd8c3-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1. <span data-ttu-id="cd8c3-106">Defina sua propriedade <xref:System.Windows.Forms.Label.AutoSize%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="cd8c3-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="cd8c3-107">Se <xref:System.Windows.Forms.Label.AutoSize%2A> for definido como `false`, as palavras especificadas na propriedade <xref:System.Windows.Forms.Label.Text%2A> serão encapsuladas na próxima linha, se possível, mas o controle não será aumentado.</span><span class="sxs-lookup"><span data-stu-id="cd8c3-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd8c3-108">Veja também</span><span class="sxs-lookup"><span data-stu-id="cd8c3-108">See also</span></span>

- [<span data-ttu-id="cd8c3-109">Como criar teclas de acesso com controles de rótulo dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd8c3-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [<span data-ttu-id="cd8c3-110">Visão geral do controle Label</span><span class="sxs-lookup"><span data-stu-id="cd8c3-110">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="cd8c3-111">Controle de rótulo</span><span class="sxs-lookup"><span data-stu-id="cd8c3-111">Label Control</span></span>](label-control-windows-forms.md)
