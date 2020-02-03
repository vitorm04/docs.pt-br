---
title: Visão geral do controle RadioButton
ms.date: 03/30/2017
f1_keywords:
- RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
ms.openlocfilehash: bbc93046b69d39caadde4986ff56f067fc206a9e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741139"
---
# <a name="radiobutton-control-overview-windows-forms"></a>Visão geral do controle RadioButton (Windows Forms)
Windows Forms controles de <xref:System.Windows.Forms.RadioButton> apresentam um conjunto de duas ou mais opções mutuamente exclusivas para o usuário. Embora os botões de opção e caixas de seleção pareçam funcionar da mesma forma, há uma diferença importante: quando um usuário seleciona um botão de opção, os outros botões de opção no mesmo grupo não podem ser selecionados juntamente. Por outro lado, qualquer número de caixas de seleção pode ser selecionado. Definir um grupo de botões de opção informa ao usuário: “Esse é um conjunto de opções, dentre as quais você pode escolher uma e apenas uma”.  
  
## <a name="using-the-control"></a>Usando o controle  
 Quando um controle de <xref:System.Windows.Forms.RadioButton> é clicado, sua propriedade <xref:System.Windows.Forms.RadioButton.Checked%2A> é definida como `true` e o manipulador de eventos <xref:System.Windows.Forms.Control.Click> é chamado. O evento <xref:System.Windows.Forms.RadioButton.CheckedChanged> é gerado quando o valor da propriedade <xref:System.Windows.Forms.RadioButton.Checked%2A> é alterado. Se a propriedade <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> for definida como `true` (o padrão), quando o botão de opção for selecionado, todos os outros no grupo serão automaticamente apagados. Essa propriedade normalmente é definida apenas como `false` quando o código de validação é usado para verificar se o botão de opção selecionado é uma opção permitida. O texto exibido no controle é definido com a propriedade <xref:System.Windows.Forms.Control.Text%2A>, que pode conter atalhos de chave de acesso. Uma tecla de acesso permite a um usuário “clicar” no controle pressionando a tecla ALT com a tecla de acesso. Para obter mais informações, consulte [Como criar teclas de acesso para controles dos Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md) e [Como definir o texto exibido por um controle dos Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
 O controle <xref:System.Windows.Forms.RadioButton> pode aparecer como um botão de comando, que parece ter sido pressionado, se selecionado, se a propriedade <xref:System.Windows.Forms.RadioButton.Appearance%2A> estiver definida como <xref:System.Windows.Forms.Appearance.Button>. Os botões de opção também podem exibir imagens usando as propriedades <xref:System.Windows.Forms.ButtonBase.Image%2A> e <xref:System.Windows.Forms.ButtonBase.ImageList%2A>. Para obter mais informações, consulte [Como definir a imagem exibida por um controle dos Windows Forms](how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.RadioButton>
- [Visão geral do controle Panel](panel-control-overview-windows-forms.md)
- [Visão geral do controle GroupBox](groupbox-control-overview-windows-forms.md)
- [Visão geral do controle CheckBox](checkbox-control-overview-windows-forms.md)
- [Como criar teclas de acesso para controles dos Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md)
- [Como definir o texto exibido por um controle dos Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Como agrupar controles RadioButton dos Windows Forms para funcionarem como um conjunto](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)
- [Controle RadioButton](radiobutton-control-windows-forms.md)
