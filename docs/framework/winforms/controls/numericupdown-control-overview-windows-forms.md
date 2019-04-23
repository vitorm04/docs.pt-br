---
title: Visão geral do controle NumericUpDown (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
ms.openlocfilehash: 218eb685e546acac76a18450612a1601ab87276b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109870"
---
# <a name="numericupdown-control-overview-windows-forms"></a>Visão geral do controle NumericUpDown (Windows Forms)
O <xref:System.Windows.Forms.NumericUpDown> controle se parece com uma combinação de uma caixa de texto e um par de setas em que o usuário pode clicar para ajustar um valor. O controle exibe e define um único valor numérico de uma lista de opções fixas. O usuário pode aumentar e diminuir o número clicando nas setas para cima e para baixo, pressionando as teclas de direção para cima ou para baixo ou digitando um número na parte de caixa de texto do controle. Clicar na seta para cima move o número em direção ao máximo; clicar na seta para baixo move o número em direção ao mínimo.  
  
 Devido à sua funcionalidade versátil, esse controle é uma opção óbvia, por exemplo, se você quiser criar um controle de volume para aplicativo de player de música. O <xref:System.Windows.Forms.NumericUpDown> controle é usado em muitos aplicativos de painel de controle do Windows.  
  
## <a name="key-properties-and-methods"></a>Propriedades e métodos de tecla  
 Os números exibidos na caixa de texto do controle podem estar em uma variedade de formatos, incluindo hexadecimais. Para obter mais informações, confira [Como: Defina o formato para o Windows Forms NumericUpDown controle](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md). As principais propriedades do controle são <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (valor padrão 100), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (valor 0 do padrão), e <xref:System.Windows.Forms.NumericUpDown.Increment%2A> (valor 1 padrão). O <xref:System.Windows.Forms.NumericUpDown.Value%2A> propriedade define o número atual selecionado no controle. O <xref:System.Windows.Forms.NumericUpDown.Increment%2A> propriedade define a quantidade que o número é ajustado pelo quando o usuário clica em cima ou seta para baixo. Quando o foco é movido para fora do controle, qualquer entrada digitada será validada em relação aos valores numéricos mínimo e máximo. Você pode aumentar a velocidade em que o controle se move pelos números quando o usuário pressiona continuamente cima ou seta para baixo, com o <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A> propriedade. Os principais métodos do controle são <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> e <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.NumericUpDown>
- [Controle NumericUpDown](numericupdown-control-windows-forms.md)
- [Como: Defina o formato para o controle do Windows Forms NumericUpDown](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)
- [Controle TextBox](textbox-control-windows-forms.md)
