---
title: 'Como: Designar um botão do Windows Forms como o botão Aceitar usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: e0eaa90c8450888ea325470db5d4adae555f8d82
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304162"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>Como: Designar um botão do Windows Forms como o botão Aceitar usando o designer
Em qualquer formulário do Windows, você pode designar um <xref:System.Windows.Forms.Button> controle para ser o botão aceitar, também conhecido como botão padrão. Sempre que o usuário pressiona a tecla ENTER, o botão padrão é clicado, independentemente de qual outro controle no formulário tem o foco. As exceções a isso são quando o controle com o foco é outro botão — nesse caso, o botão com o foco será ser clicado — ou uma caixa de texto de várias linhas, ou um controle personalizado que intercepte a tecla ENTER.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-designate-the-accept-button"></a>Para designar o botão aceitar  
  
1. Selecione o formulário no qual reside o botão.  
  
2. No **propriedades** janela, defina o formulário <xref:System.Windows.Forms.Form.AcceptButton%2A> propriedade para o <xref:System.Windows.Forms.Button> nome do controle.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Visão geral do controle de botão](button-control-overview-windows-forms.md)
- [Forma de selecionar um controle de botão dos Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Como: Responder a cliques no botão do Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Como: Designar um botão do Windows Forms como o botão Cancelar usando o designer](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Controle de botão](button-control-windows-forms.md)
