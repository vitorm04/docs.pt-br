---
title: 'Como: Dar ao controle um segundo plano transparente'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: a82807ea3873b2217d1f05f6c720c599ea79abdd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966647"
---
# <a name="how-to-give-your-control-a-transparent-background"></a><span data-ttu-id="9927e-102">Como: Dar ao controle um segundo plano transparente</span><span class="sxs-lookup"><span data-stu-id="9927e-102">How to: Give Your Control a Transparent Background</span></span>
<span data-ttu-id="9927e-103">Em versões anteriores do .NET Framework, os controles não suportavam definir cores de BackColor transparente sem <xref:System.Windows.Forms.Control.SetStyle%2A> primeiro definir o método no construtor do formulário.</span><span class="sxs-lookup"><span data-stu-id="9927e-103">In earlier versions of the .NET Framework, controls didn't support setting transparent backcolors without first setting the <xref:System.Windows.Forms.Control.SetStyle%2A> method in the forms's constructor.</span></span> <span data-ttu-id="9927e-104">Na versão atual do Framework, a BackColor para a maioria dos controles pode ser <xref:System.Drawing.Color.Transparent%2A> definida como na janela **Propriedades** em tempo de design ou no código do construtor do formulário.</span><span class="sxs-lookup"><span data-stu-id="9927e-104">In the current framework version, the backcolor for most controls can be set to <xref:System.Drawing.Color.Transparent%2A> in the **Properties** window at design time, or in code in the form's constructor.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9927e-105">Os controles de Windows Forms não dão suporte à transparência real.</span><span class="sxs-lookup"><span data-stu-id="9927e-105">Windows Forms controls do not support true transparency.</span></span> <span data-ttu-id="9927e-106">O plano de fundo de um controle de Windows Forms transparente é pintado por seu pai.</span><span class="sxs-lookup"><span data-stu-id="9927e-106">The background of a transparent Windows Forms control is painted by its parent.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9927e-107">O <xref:System.Windows.Controls.Button> controle não dá suporte a um BackColor transparente mesmo <xref:System.Windows.Forms.ButtonBase.BackColor%2A> quando a propriedade é <xref:System.Drawing.Color.Transparent%2A>definida como.</span><span class="sxs-lookup"><span data-stu-id="9927e-107">The <xref:System.Windows.Controls.Button> control doesn't support a transparent backcolor even when the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property is set to <xref:System.Drawing.Color.Transparent%2A>.</span></span>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a><span data-ttu-id="9927e-108">Para dar ao seu controle um BackColor transparente</span><span class="sxs-lookup"><span data-stu-id="9927e-108">To give your control a transparent backcolor</span></span>  
  
- <span data-ttu-id="9927e-109">Na janela Propriedades, escolha a <xref:System.Windows.Forms.ButtonBase.BackColor%2A> Propriedade e defina-a como<xref:System.Drawing.Color.Transparent%2A></span><span class="sxs-lookup"><span data-stu-id="9927e-109">In the Properties window, choose the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property and set it to <xref:System.Drawing.Color.Transparent%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9927e-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9927e-110">See also</span></span>

- <xref:System.Drawing.Color.FromArgb%2A>
- [<span data-ttu-id="9927e-111">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9927e-111">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="9927e-112">Usando Classes de Elementos Gráficos Gerenciadas</span><span class="sxs-lookup"><span data-stu-id="9927e-112">Using Managed Graphics Classes</span></span>](../advanced/using-managed-graphics-classes.md)
- [<span data-ttu-id="9927e-113">Como: Desenhar linhas opacas e semitransparentes</span><span class="sxs-lookup"><span data-stu-id="9927e-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
