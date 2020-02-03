---
title: Designar um botão como o botão aceitar usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 27a5de51f8c5b2c84cc205e09ac1a2179c315752
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746068"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>Como projetar um botão dos Windows Forms como o botão Aceitar usando o designer
Em qualquer formulário do Windows, você pode designar um controle de <xref:System.Windows.Forms.Button> para ser o botão aceitar, também conhecido como o botão padrão. Sempre que o usuário pressiona a tecla ENTER, o botão padrão é clicado, independentemente de qual outro controle no formulário tenha o foco. As exceções a isso são quando o controle com foco é outro botão — nesse caso, o botão com o foco será clicado — ou uma caixa de texto de várias linhas ou um controle personalizado que intercepta a tecla ENTER.

## <a name="to-designate-the-accept-button"></a>Para designar o botão aceitar

1. Selecione o formulário no qual o botão reside.

2. Na janela **Propriedades** , defina a propriedade <xref:System.Windows.Forms.Form.AcceptButton%2A> do formulário como o nome do controle de <xref:System.Windows.Forms.Button>.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Visão geral do controle de botão](button-control-overview-windows-forms.md)
- [Formas de selecionar um controle de botão dos Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Como responder a cliques no botão dos Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Como designar um botão dos Windows Forms como o botão Cancelar usando o Designer](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Controle de botão](button-control-windows-forms.md)
