---
title: 'Como: Dar ao controle um segundo plano transparente'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: 8a03d9afec5340cd77af465c4470b7484b8926be
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609711"
---
# <a name="how-to-give-your-control-a-transparent-background"></a>Como: Dar ao controle um segundo plano transparente
Em versões anteriores do .NET Framework, controles não oferece suporte à configuração backcolors transparente sem primeiro definir o <xref:System.Windows.Forms.Control.SetStyle%2A> método no construtor de formulários. Na versão atual do framework, a cor de fundo para a maioria dos controles pode ser definido como <xref:System.Drawing.Color.Transparent%2A> no **propriedades** janela em tempo de design ou no código no construtor do formulário.  
  
> [!NOTE]
>  Controles de formulários do Windows não têm suporte para a verdadeira transparência. O plano de fundo de um controle Windows Forms transparente é pintado pelo pai.  
  
> [!NOTE]
>  O <xref:System.Windows.Controls.Button> controle não dá suporte a um backcolor transparente, mesmo quando o <xref:System.Windows.Forms.ButtonBase.BackColor%2A> estiver definida como <xref:System.Drawing.Color.Transparent%2A>.  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>Para dar ao controle uma backcolor transparente  
  
- Na janela Propriedades, escolha o <xref:System.Windows.Forms.ButtonBase.BackColor%2A> propriedade e defina-o como <xref:System.Drawing.Color.Transparent%2A>  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Color.FromArgb%2A>
- [Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](developing-custom-windows-forms-controls.md)
- [Usando Classes de Elementos Gráficos Gerenciadas](../advanced/using-managed-graphics-classes.md)
- [Como: Desenhar linhas opacas e semitransparentes](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
