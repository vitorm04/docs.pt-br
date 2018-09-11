---
title: Visão geral do controle FlowLayoutPanel
ms.date: 03/30/2017
f1_keywords:
- FlowLayoutPanel
helpviewer_keywords:
- forms [Windows Forms], dynamic layout
- layout [Windows Forms], dynamic
- Windows Forms, dynamic layout
- FlowLayoutPanel control [Windows Forms], about FlowLayoutPanel control
ms.assetid: 3883e024-f5a0-456d-9c27-b4dfa1cc9045
ms.openlocfilehash: 73767114da1c04222fb8ceaf812153421c4597aa
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44270560"
---
# <a name="flowlayoutpanel-control-overview"></a><span data-ttu-id="5784d-102">Visão geral do controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5784d-102">FlowLayoutPanel Control Overview</span></span>
<span data-ttu-id="5784d-103">O <xref:System.Windows.Forms.FlowLayoutPanel> controle organiza seu conteúdo em uma direção de fluxo horizontal ou vertical.</span><span class="sxs-lookup"><span data-stu-id="5784d-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control arranges its contents in a horizontal or vertical flow direction.</span></span> <span data-ttu-id="5784d-104">Você pode encapsular o conteúdo do controle de uma linha para outra ou de uma coluna para a próxima.</span><span class="sxs-lookup"><span data-stu-id="5784d-104">You can wrap the control's contents from one row to the next, or from one column to the next.</span></span> <span data-ttu-id="5784d-105">Como alternativa, você pode recortar, em vez de encapsular seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="5784d-105">Alternately, you can clip instead of wrap its contents.</span></span>  
  
 <span data-ttu-id="5784d-106">Você pode especificar a direção do fluxo, definindo o valor da <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5784d-106">You can specify the flow direction by setting the value of the <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> property.</span></span> <span data-ttu-id="5784d-107">O <xref:System.Windows.Forms.FlowLayoutPanel> controle corretamente inverte a direção de seu fluxo em layouts da direita para esquerda (RTL).</span><span class="sxs-lookup"><span data-stu-id="5784d-107">The <xref:System.Windows.Forms.FlowLayoutPanel> control correctly reverses its flow direction in Right-to-Left (RTL) layouts.</span></span> <span data-ttu-id="5784d-108">Você também pode especificar se o <xref:System.Windows.Forms.FlowLayoutPanel> conteúdo do controle é encapsulado ou recortado Configurando o valor da <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5784d-108">You can also specify whether the <xref:System.Windows.Forms.FlowLayoutPanel> control's contents are wrapped or clipped by setting the value of the <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> property.</span></span>  
  
 <span data-ttu-id="5784d-109">O <xref:System.Windows.Forms.FlowLayoutPanel> controlar tamanhos para seu conteúdo automaticamente, quando você define o <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="5784d-109">The <xref:System.Windows.Forms.FlowLayoutPanel> control automatically sizes to its contents when you set the <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="5784d-110">Ele também fornece uma propriedade **FlowBreak** para seus controles filho.</span><span class="sxs-lookup"><span data-stu-id="5784d-110">It also provides a **FlowBreak** property to its child controls.</span></span> <span data-ttu-id="5784d-111">Definindo o valor da propriedade FlowBreak como `true` faz com que o <xref:System.Windows.Forms.FlowLayoutPanel> controle para interromper o layout de controles na direção do fluxo atual e quebra automática de linha para a próxima linha ou coluna.</span><span class="sxs-lookup"><span data-stu-id="5784d-111">Setting the value of the FlowBreak property to `true` causes the <xref:System.Windows.Forms.FlowLayoutPanel> control to stop laying out controls in the current flow direction and wrap to the next row or column.</span></span>  
  
 <span data-ttu-id="5784d-112">Qualquer controle dos Windows Forms pode ser um filho de <xref:System.Windows.Forms.FlowLayoutPanel> controle, incluindo outra instâncias de <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="5784d-112">Any Windows Forms control can be a child of the <xref:System.Windows.Forms.FlowLayoutPanel> control, including other instances of <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="5784d-113">Com esse capacidade, você pode criar layouts sofisticados que se adaptam às dimensões do formulário em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5784d-113">With this capability, you can construct sophisticated layouts that adapt to your form's dimensions at run time.</span></span>  
  
 <span data-ttu-id="5784d-114">Consulte também [Explicação passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="5784d-114">Also see [Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5784d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5784d-115">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="5784d-116">Controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5784d-116">FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-windows-forms.md)
