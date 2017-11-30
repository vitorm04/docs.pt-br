---
title: Como dar ao controle uma tela de fundo transparente
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5ec2c353a960626c54c05009393bcd80dac1b38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-give-your-control-a-transparent-background"></a><span data-ttu-id="3d3a6-102">Como dar ao controle uma tela de fundo transparente</span><span class="sxs-lookup"><span data-stu-id="3d3a6-102">How to: Give Your Control a Transparent Background</span></span>
<span data-ttu-id="3d3a6-103">Em versões anteriores do .NET Framework, os controles não oferece suporte à configuração transparente backcolors sem primeiro definir o <xref:System.Windows.Forms.Control.SetStyle%2A> método no construtor de formulários.</span><span class="sxs-lookup"><span data-stu-id="3d3a6-103">In earlier versions of the .NET Framework, controls didn't support setting transparent backcolors without first setting the <xref:System.Windows.Forms.Control.SetStyle%2A> method in the forms's constructor.</span></span> <span data-ttu-id="3d3a6-104">A cor de fundo para a maioria dos controles na versão atual do framework, pode ser definido como <xref:System.Drawing.Color.Transparent%2A> no **propriedades** janela no tempo de design ou em código no construtor do formulário.</span><span class="sxs-lookup"><span data-stu-id="3d3a6-104">In the current framework version, the backcolor for most controls can be set to <xref:System.Drawing.Color.Transparent%2A> in the **Properties** window at design time, or in code in the form's constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d3a6-105">Controles de formulários do Windows não dão suporte a transparência de verdade.</span><span class="sxs-lookup"><span data-stu-id="3d3a6-105">Windows Forms controls do not support true transparency.</span></span> <span data-ttu-id="3d3a6-106">O plano de fundo de um controle de formulários do Windows transparente é pintado pelo pai.</span><span class="sxs-lookup"><span data-stu-id="3d3a6-106">The background of a transparent Windows Forms control is painted by its parent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d3a6-107">O <xref:System.Windows.Controls.Button> controle não dá suporte a backcolor transparente, mesmo quando o <xref:System.Windows.Forms.ButtonBase.BackColor%2A> está definida como <xref:System.Drawing.Color.Transparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="3d3a6-107">The <xref:System.Windows.Controls.Button> control doesn't support a transparent backcolor even when the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property is set to <xref:System.Drawing.Color.Transparent%2A>.</span></span>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a><span data-ttu-id="3d3a6-108">Para dar ao controle a backcolor transparente</span><span class="sxs-lookup"><span data-stu-id="3d3a6-108">To give your control a transparent backcolor</span></span>  
  
-   <span data-ttu-id="3d3a6-109">Na janela Propriedades, escolha o <xref:System.Windows.Forms.ButtonBase.BackColor%2A> propriedade e defina-a como<xref:System.Drawing.Color.Transparent%2A></span><span class="sxs-lookup"><span data-stu-id="3d3a6-109">In the Properties window, choose the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property and set it to <xref:System.Drawing.Color.Transparent%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d3a6-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d3a6-110">See Also</span></span>  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [<span data-ttu-id="3d3a6-111">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3d3a6-111">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="3d3a6-112">Usando Classes de Elementos Gráficos Gerenciadas</span><span class="sxs-lookup"><span data-stu-id="3d3a6-112">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 [<span data-ttu-id="3d3a6-113">Como Desenhar Linhas Opacas e Semitransparentes</span><span class="sxs-lookup"><span data-stu-id="3d3a6-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
