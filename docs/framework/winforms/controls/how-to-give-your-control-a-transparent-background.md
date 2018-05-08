---
title: Como dar ao controle uma tela de fundo transparente
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: ad814c9179fd33955fe4df2666f8a47606bfbff0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-give-your-control-a-transparent-background"></a>Como dar ao controle uma tela de fundo transparente
Em versões anteriores do .NET Framework, os controles não oferece suporte à configuração transparente backcolors sem primeiro definir o <xref:System.Windows.Forms.Control.SetStyle%2A> método no construtor de formulários. A cor de fundo para a maioria dos controles na versão atual do framework, pode ser definido como <xref:System.Drawing.Color.Transparent%2A> no **propriedades** janela no tempo de design ou em código no construtor do formulário.  
  
> [!NOTE]
>  Controles de formulários do Windows não dão suporte a transparência de verdade. O plano de fundo de um controle de formulários do Windows transparente é pintado pelo pai.  
  
> [!NOTE]
>  O <xref:System.Windows.Controls.Button> controle não dá suporte a backcolor transparente, mesmo quando o <xref:System.Windows.Forms.ButtonBase.BackColor%2A> está definida como <xref:System.Drawing.Color.Transparent%2A>.  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>Para dar ao controle a backcolor transparente  
  
-   Na janela Propriedades, escolha o <xref:System.Windows.Forms.ButtonBase.BackColor%2A> propriedade e defina-a como <xref:System.Drawing.Color.Transparent%2A>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Usando Classes de Elementos Gráficos Gerenciadas](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 [Como Desenhar Linhas Opacas e Semitransparentes](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
