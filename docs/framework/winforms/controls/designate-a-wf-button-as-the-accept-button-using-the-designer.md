---
title: Como projetar um botão dos Windows Forms como o botão Aceitar usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: ca049e86ab53fbd84cb24e81b0a850050ec2823f
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46702914"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>Como projetar um botão dos Windows Forms como o botão Aceitar usando o designer
Em qualquer formulário do Windows, você pode designar um <xref:System.Windows.Forms.Button> controle para ser o botão aceitar, também conhecido como botão padrão. Sempre que o usuário pressiona a tecla ENTER, o botão padrão é clicado, independentemente de qual outro controle no formulário tem o foco. As exceções a isso são quando o controle com o foco é outro botão — nesse caso, o botão com o foco será ser clicado — ou uma caixa de texto de várias linhas, ou um controle personalizado que intercepte a tecla ENTER.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-designate-the-accept-button"></a>Para designar o botão aceitar  
  
1.  Selecione o formulário no qual reside o botão.  
  
2.  No **propriedades** janela, defina o formulário <xref:System.Windows.Forms.Form.AcceptButton%2A> propriedade para o <xref:System.Windows.Forms.Button> nome do controle.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [Visão geral do controle de botão](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Formas de selecionar um controle de botão dos Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Como responder a cliques no botão dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Como projetar um botão do Windows Forms como o botão Cancelar usando o Designer](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [Controle de botão](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
