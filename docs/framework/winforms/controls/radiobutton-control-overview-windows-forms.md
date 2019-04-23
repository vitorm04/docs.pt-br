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
ms.openlocfilehash: 1210658226d9bcacbf4904fdc90a9908c34f5b73
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129110"
---
# <a name="radiobutton-control-overview-windows-forms"></a>Visão geral do controle RadioButton (Windows Forms)
Windows Forms <xref:System.Windows.Forms.RadioButton> controles apresentam um conjunto de duas ou mais opções mutuamente exclusivas para o usuário. Embora os botões de opção e caixas de seleção pareçam funcionar da mesma forma, há uma diferença importante: quando um usuário seleciona um botão de opção, os outros botões de opção no mesmo grupo não podem ser selecionados juntamente. Por outro lado, qualquer número de caixas de seleção pode ser selecionado. Definir um grupo de botões de opção informa ao usuário: “Esse é um conjunto de opções, dentre as quais você pode escolher uma e apenas uma”.  
  
## <a name="using-the-control"></a>Usando o controle  
 Quando um <xref:System.Windows.Forms.RadioButton> controle é clicado, seu <xref:System.Windows.Forms.RadioButton.Checked%2A> estiver definida como `true` e o <xref:System.Windows.Forms.Control.Click> manipulador de eventos é chamado. O <xref:System.Windows.Forms.RadioButton.CheckedChanged> é gerado quando o valor da <xref:System.Windows.Forms.RadioButton.Checked%2A> as alterações de propriedade. Se o <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> estiver definida como `true` (o padrão), quando o botão de opção é selecionado todos os outros no grupo são removidos automaticamente. Essa propriedade normalmente é definida apenas como `false` quando o código de validação é usado para verificar se o botão de opção selecionado é uma opção permitida. O texto exibido dentro do controle é definido com o <xref:System.Windows.Forms.Control.Text%2A> propriedade, que pode conter atalhos de tecla de acesso. Uma tecla de acesso permite a um usuário “clicar” no controle pressionando a tecla ALT com a tecla de acesso. Para obter mais informações, confira [Como: Criar chaves de acesso para controles do Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md) e [como: Definir o texto exibido pelo controle de um Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
 O <xref:System.Windows.Forms.RadioButton> controle pode aparecer como um botão de comando, que parece ter sido pressionado se selecionado, se o <xref:System.Windows.Forms.RadioButton.Appearance%2A> estiver definida como <xref:System.Windows.Forms.Appearance.Button>. Botões de opção também podem exibir imagens usando o <xref:System.Windows.Forms.ButtonBase.Image%2A> e <xref:System.Windows.Forms.ButtonBase.ImageList%2A> propriedades. Para obter mais informações, confira [Como: Definir a imagem exibida pelo controle de um Windows Forms](how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.RadioButton>
- [Visão geral do controle Panel](panel-control-overview-windows-forms.md)
- [Visão geral do controle GroupBox](groupbox-control-overview-windows-forms.md)
- [Visão geral do controle CheckBox](checkbox-control-overview-windows-forms.md)
- [Como: Criar chaves de acesso para controles dos Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md)
- [Como: Definir o texto exibido pelo controle de um Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Como: Controles de botão de opção do grupo Windows Forms para funcionarem como um conjunto](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)
- [Controle RadioButton](radiobutton-control-windows-forms.md)
