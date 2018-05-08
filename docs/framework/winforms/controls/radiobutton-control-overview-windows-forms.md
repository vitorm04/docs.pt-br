---
title: Visão geral do controle RadioButton (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
ms.openlocfilehash: 397808c055fd5ba5e8a73d47dfc7fee6c0cf2975
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="radiobutton-control-overview-windows-forms"></a>Visão geral do controle RadioButton (Windows Forms)
Windows Forms <xref:System.Windows.Forms.RadioButton> controles apresentam um conjunto de duas ou mais opções mutuamente exclusivas para o usuário. Embora os botões de opção e caixas de seleção pareçam funcionar da mesma forma, há uma diferença importante: quando um usuário seleciona um botão de opção, os outros botões de opção no mesmo grupo não podem ser selecionados juntamente. Por outro lado, qualquer número de caixas de seleção pode ser selecionado. Definir um grupo de botões de opção informa ao usuário: “Esse é um conjunto de opções, dentre as quais você pode escolher uma e apenas uma”.  
  
## <a name="using-the-control"></a>Usando o controle  
 Quando um <xref:System.Windows.Forms.RadioButton> controle é clicado, seu <xref:System.Windows.Forms.RadioButton.Checked%2A> está definida como `true` e <xref:System.Windows.Forms.Control.Click> manipulador de eventos é chamado. O <xref:System.Windows.Forms.RadioButton.CheckedChanged> é gerado quando o valor da <xref:System.Windows.Forms.RadioButton.Checked%2A> alterações de propriedade. Se o <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> está definida como `true` (o padrão), quando o botão de opção é selecionado automaticamente todos os outros no grupo estão desmarcados. Essa propriedade normalmente é definida apenas como `false` quando o código de validação é usado para verificar se o botão de opção selecionado é uma opção permitida. O texto exibido dentro do controle é definido com o <xref:System.Windows.Forms.Control.Text%2A> propriedade, que pode conter atalhos de chave de acesso. Uma tecla de acesso permite a um usuário “clicar” no controle pressionando a tecla ALT com a tecla de acesso. Para obter mais informações, consulte [Como criar teclas de acesso para controles dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) e [Como definir o texto exibido por um controle dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
 O <xref:System.Windows.Forms.RadioButton> controle pode aparecer como um botão de comando, que parece ter sido pressionado se selecionada, se o <xref:System.Windows.Forms.RadioButton.Appearance%2A> está definida como <xref:System.Windows.Forms.Appearance.Button>. Botões de opção também podem exibir imagens usando o <xref:System.Windows.Forms.ButtonBase.Image%2A> e <xref:System.Windows.Forms.ButtonBase.ImageList%2A> propriedades. Para obter mais informações, consulte [Como definir a imagem exibida por um controle dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.RadioButton>  
 [Visão geral do controle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [Visão geral do controle GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [Visão geral do controle CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [Como criar teclas de acesso para controles dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 [Como definir o texto exibido por um controle dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Como agrupar controles RadioButton do Windows Forms para funcionarem como um conjunto](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)  
 [Controle RadioButton](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
