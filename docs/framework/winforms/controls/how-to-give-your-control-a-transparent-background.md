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
# <a name="how-to-give-your-control-a-transparent-background"></a>Como: Dar ao controle um segundo plano transparente
Em versões anteriores do .NET Framework, os controles não suportavam definir cores de BackColor transparente sem <xref:System.Windows.Forms.Control.SetStyle%2A> primeiro definir o método no construtor do formulário. Na versão atual do Framework, a BackColor para a maioria dos controles pode ser <xref:System.Drawing.Color.Transparent%2A> definida como na janela **Propriedades** em tempo de design ou no código do construtor do formulário.  
  
> [!NOTE]
> Os controles de Windows Forms não dão suporte à transparência real. O plano de fundo de um controle de Windows Forms transparente é pintado por seu pai.  
  
> [!NOTE]
> O <xref:System.Windows.Controls.Button> controle não dá suporte a um BackColor transparente mesmo <xref:System.Windows.Forms.ButtonBase.BackColor%2A> quando a propriedade é <xref:System.Drawing.Color.Transparent%2A>definida como.  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>Para dar ao seu controle um BackColor transparente  
  
- Na janela Propriedades, escolha a <xref:System.Windows.Forms.ButtonBase.BackColor%2A> Propriedade e defina-a como<xref:System.Drawing.Color.Transparent%2A>  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Color.FromArgb%2A>
- [Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](developing-custom-windows-forms-controls.md)
- [Usando Classes de Elementos Gráficos Gerenciadas](../advanced/using-managed-graphics-classes.md)
- [Como: Desenhar linhas opacas e semitransparentes](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
