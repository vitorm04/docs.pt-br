---
title: "Visão geral do controle FlowLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FlowLayoutPanel
helpviewer_keywords:
- forms [Windows Forms], dynamic layout
- layout [Windows Forms], dynamic
- Windows Forms, dynamic layout
- FlowLayoutPanel control [Windows Forms], about FlowLayoutPanel control
ms.assetid: 3883e024-f5a0-456d-9c27-b4dfa1cc9045
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7eafe31bec86a969a12661c9f5629b2d55e3e3d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="flowlayoutpanel-control-overview"></a><span data-ttu-id="15e8b-102">Visão geral do controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="15e8b-102">FlowLayoutPanel Control Overview</span></span>
<span data-ttu-id="15e8b-103">O <xref:System.Windows.Forms.FlowLayoutPanel> controle organiza seu conteúdo em uma direção de fluxo horizontal ou vertical.</span><span class="sxs-lookup"><span data-stu-id="15e8b-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control arranges its contents in a horizontal or vertical flow direction.</span></span> <span data-ttu-id="15e8b-104">Você pode encapsular o conteúdo do controle de uma linha para outra ou de uma coluna para a próxima.</span><span class="sxs-lookup"><span data-stu-id="15e8b-104">You can wrap the control's contents from one row to the next, or from one column to the next.</span></span> <span data-ttu-id="15e8b-105">Como alternativa, você pode recortar, em vez de encapsular seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="15e8b-105">Alternately, you can clip instead of wrap its contents.</span></span>  
  
 <span data-ttu-id="15e8b-106">Você pode especificar a direção de fluxo, definindo o valor da <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="15e8b-106">You can specify the flow direction by setting the value of the <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> property.</span></span> <span data-ttu-id="15e8b-107">O <xref:System.Windows.Forms.FlowLayoutPanel> controle corretamente inverte a direção de fluxo em layouts da direita para esquerda (RTL).</span><span class="sxs-lookup"><span data-stu-id="15e8b-107">The <xref:System.Windows.Forms.FlowLayoutPanel> control correctly reverses its flow direction in Right-to-Left (RTL) layouts.</span></span> <span data-ttu-id="15e8b-108">Você também pode especificar se o <xref:System.Windows.Forms.FlowLayoutPanel> conteúdo do controle é encapsulado ou recortado, definindo o valor da <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="15e8b-108">You can also specify whether the <xref:System.Windows.Forms.FlowLayoutPanel> control's contents are wrapped or clipped by setting the value of the <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> property.</span></span>  
  
 <span data-ttu-id="15e8b-109">O <xref:System.Windows.Forms.FlowLayoutPanel> controlar tamanhos para seu conteúdo automaticamente, quando você define o <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="15e8b-109">The <xref:System.Windows.Forms.FlowLayoutPanel> control automatically sizes to its contents when you set the <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="15e8b-110">Ele também fornece uma propriedade **FlowBreak** para seus controles filho.</span><span class="sxs-lookup"><span data-stu-id="15e8b-110">It also provides a **FlowBreak** property to its child controls.</span></span> <span data-ttu-id="15e8b-111">Definir o valor da propriedade FlowBreak para `true` faz com que o <xref:System.Windows.Forms.FlowLayoutPanel> controle parar dispor controles no contorno para a próxima linha ou coluna e direção do fluxo atual.</span><span class="sxs-lookup"><span data-stu-id="15e8b-111">Setting the value of the FlowBreak property to `true` causes the <xref:System.Windows.Forms.FlowLayoutPanel> control to stop laying out controls in the current flow direction and wrap to the next row or column.</span></span>  
  
 <span data-ttu-id="15e8b-112">Qualquer controle de formulários do Windows pode ser um filho de <xref:System.Windows.Forms.FlowLayoutPanel> controle, inclusive de outras instâncias de <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="15e8b-112">Any Windows Forms control can be a child of the <xref:System.Windows.Forms.FlowLayoutPanel> control, including other instances of <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="15e8b-113">Com esse capacidade, você pode criar layouts sofisticados que se adaptam às dimensões do formulário em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="15e8b-113">With this capability, you can construct sophisticated layouts that adapt to your form's dimensions at run time.</span></span>  
  
 <span data-ttu-id="15e8b-114">Consulte também [Explicação passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="15e8b-114">Also see [Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15e8b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15e8b-115">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="15e8b-116">Controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="15e8b-116">FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-windows-forms.md)
