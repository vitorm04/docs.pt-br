---
title: Visão geral do controle NumericUpDown
ms.date: 03/30/2017
f1_keywords:
- NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
ms.openlocfilehash: 3e24fa543df9028e9866d91ec60c3cf88578ac56
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740804"
---
# <a name="numericupdown-control-overview-windows-forms"></a>Visão geral do controle NumericUpDown (Windows Forms)
O controle <xref:System.Windows.Forms.NumericUpDown> se parece com uma combinação de uma caixa de texto e um par de setas que o usuário pode clicar para ajustar um valor. O controle exibe e define um único valor numérico de uma lista de opções fixas. O usuário pode aumentar e diminuir o número clicando nas setas para cima e para baixo, pressionando as teclas de direção para cima ou para baixo ou digitando um número na parte de caixa de texto do controle. Clicar na seta para cima move o número em direção ao máximo; clicar na seta para baixo move o número em direção ao mínimo.  
  
 Devido à sua funcionalidade versátil, esse controle é uma opção óbvia, por exemplo, se você quiser criar um controle de volume para aplicativo de player de música. O controle <xref:System.Windows.Forms.NumericUpDown> é usado em muitos aplicativos do painel de controle do Windows.  
  
## <a name="key-properties-and-methods"></a>Propriedades e métodos de tecla  
 Os números exibidos na caixa de texto do controle podem estar em uma variedade de formatos, incluindo hexadecimais. Para obter mais informações, consulte [Como definir o formato para o controle NumericUpDown dos Windows Forms](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md). As propriedades de chave do controle são <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (valor padrão 100), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (valor padrão 0) e <xref:System.Windows.Forms.NumericUpDown.Increment%2A> (valor padrão 1). A propriedade <xref:System.Windows.Forms.NumericUpDown.Value%2A> define o número atual selecionado no controle. A propriedade <xref:System.Windows.Forms.NumericUpDown.Increment%2A> define o valor pelo qual o número é ajustado quando o usuário clica em uma seta para cima ou para baixo. Quando o foco é movido para fora do controle, qualquer entrada digitada será validada em relação aos valores numéricos mínimo e máximo. Você pode aumentar a velocidade com que o controle se move por números, quando o usuário pressiona continuamente a seta para cima ou para baixo, com a propriedade <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A>. Os principais métodos do controle são <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> e <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.NumericUpDown>
- [Controle NumericUpDown](numericupdown-control-windows-forms.md)
- [How to: Set the Format for the Windows Forms NumericUpDown Control](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md) (Como definir o formato para o controle NumericUpDown dos Windows Forms)
- [Controle TextBox](textbox-control-windows-forms.md)
