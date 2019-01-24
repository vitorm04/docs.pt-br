---
title: 'Como: Dar ao controle uma tela de fundo transparente'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: 20815518c2a683878e0d3adf6a4bdc9261b614d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644606"
---
# <a name="how-to-give-your-control-a-transparent-background"></a>Como: Dar ao controle uma tela de fundo transparente
Em versões anteriores do .NET Framework, controles não oferece suporte à configuração backcolors transparente sem primeiro definir o <xref:System.Windows.Forms.Control.SetStyle%2A> método no construtor de formulários. Na versão atual do framework, a cor de fundo para a maioria dos controles pode ser definido como <xref:System.Drawing.Color.Transparent%2A> no **propriedades** janela em tempo de design ou no código no construtor do formulário.  
  
> [!NOTE]
>  Controles de formulários do Windows não têm suporte para a verdadeira transparência. O plano de fundo de um controle Windows Forms transparente é pintado pelo pai.  
  
> [!NOTE]
>  O <xref:System.Windows.Controls.Button> controle não dá suporte a um backcolor transparente, mesmo quando o <xref:System.Windows.Forms.ButtonBase.BackColor%2A> estiver definida como <xref:System.Drawing.Color.Transparent%2A>.  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>Para dar ao controle uma backcolor transparente  
  
-   Na janela Propriedades, escolha o <xref:System.Windows.Forms.ButtonBase.BackColor%2A> propriedade e defina-o como <xref:System.Drawing.Color.Transparent%2A>  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Drawing.Color.FromArgb%2A>
- [Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [Usando Classes de Elementos Gráficos Gerenciadas](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
- [Como: Desenhar linhas opacas e semitransparentes](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
