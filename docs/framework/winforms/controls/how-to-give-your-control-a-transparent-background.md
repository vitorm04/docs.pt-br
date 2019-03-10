---
title: 'Como: Dar ao controle uma tela de fundo transparente'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: 5a54b76eb92c7d3f518b9bf13e154e6faf58de63
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718162"
---
# <a name="how-to-give-your-control-a-transparent-background"></a><span data-ttu-id="d4fb6-102">Como: Dar ao controle uma tela de fundo transparente</span><span class="sxs-lookup"><span data-stu-id="d4fb6-102">How to: Give Your Control a Transparent Background</span></span>
<span data-ttu-id="d4fb6-103">Em versões anteriores do .NET Framework, controles não oferece suporte à configuração backcolors transparente sem primeiro definir o <xref:System.Windows.Forms.Control.SetStyle%2A> método no construtor de formulários.</span><span class="sxs-lookup"><span data-stu-id="d4fb6-103">In earlier versions of the .NET Framework, controls didn't support setting transparent backcolors without first setting the <xref:System.Windows.Forms.Control.SetStyle%2A> method in the forms's constructor.</span></span> <span data-ttu-id="d4fb6-104">Na versão atual do framework, a cor de fundo para a maioria dos controles pode ser definido como <xref:System.Drawing.Color.Transparent%2A> no **propriedades** janela em tempo de design ou no código no construtor do formulário.</span><span class="sxs-lookup"><span data-stu-id="d4fb6-104">In the current framework version, the backcolor for most controls can be set to <xref:System.Drawing.Color.Transparent%2A> in the **Properties** window at design time, or in code in the form's constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4fb6-105">Controles de formulários do Windows não têm suporte para a verdadeira transparência.</span><span class="sxs-lookup"><span data-stu-id="d4fb6-105">Windows Forms controls do not support true transparency.</span></span> <span data-ttu-id="d4fb6-106">O plano de fundo de um controle Windows Forms transparente é pintado pelo pai.</span><span class="sxs-lookup"><span data-stu-id="d4fb6-106">The background of a transparent Windows Forms control is painted by its parent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4fb6-107">O <xref:System.Windows.Controls.Button> controle não dá suporte a um backcolor transparente, mesmo quando o <xref:System.Windows.Forms.ButtonBase.BackColor%2A> estiver definida como <xref:System.Drawing.Color.Transparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="d4fb6-107">The <xref:System.Windows.Controls.Button> control doesn't support a transparent backcolor even when the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property is set to <xref:System.Drawing.Color.Transparent%2A>.</span></span>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a><span data-ttu-id="d4fb6-108">Para dar ao controle uma backcolor transparente</span><span class="sxs-lookup"><span data-stu-id="d4fb6-108">To give your control a transparent backcolor</span></span>  
  
-   <span data-ttu-id="d4fb6-109">Na janela Propriedades, escolha o <xref:System.Windows.Forms.ButtonBase.BackColor%2A> propriedade e defina-o como <xref:System.Drawing.Color.Transparent%2A></span><span class="sxs-lookup"><span data-stu-id="d4fb6-109">In the Properties window, choose the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property and set it to <xref:System.Drawing.Color.Transparent%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4fb6-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4fb6-110">See also</span></span>
- <xref:System.Drawing.Color.FromArgb%2A>
- [<span data-ttu-id="d4fb6-111">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d4fb6-111">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="d4fb6-112">Usando Classes de Elementos Gráficos Gerenciadas</span><span class="sxs-lookup"><span data-stu-id="d4fb6-112">Using Managed Graphics Classes</span></span>](../advanced/using-managed-graphics-classes.md)
- [<span data-ttu-id="d4fb6-113">Como: Desenhar linhas opacas e semitransparentes</span><span class="sxs-lookup"><span data-stu-id="d4fb6-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
