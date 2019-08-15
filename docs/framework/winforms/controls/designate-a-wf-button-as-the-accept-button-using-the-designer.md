---
title: 'Como: Designar um botão do Windows Forms como o botão Aceitar usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 27ecb26c493232bcfb996d012f9760b7ef91e5b2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039652"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>Como: Designar um botão do Windows Forms como o botão Aceitar usando o designer
Em qualquer formulário do Windows, você pode designar <xref:System.Windows.Forms.Button> um controle para ser o botão aceitar, também conhecido como o botão padrão. Sempre que o usuário pressiona a tecla ENTER, o botão padrão é clicado, independentemente de qual outro controle no formulário tenha o foco. As exceções a isso são quando o controle com foco é outro botão — nesse caso, o botão com o foco será clicado — ou uma caixa de texto de várias linhas ou um controle personalizado que intercepta a tecla ENTER.

## <a name="to-designate-the-accept-button"></a>Para designar o botão aceitar

1. Selecione o formulário no qual o botão reside.

2. Na janela **Propriedades** , defina a propriedade do <xref:System.Windows.Forms.Form.AcceptButton%2A> formulário como o <xref:System.Windows.Forms.Button> nome do controle.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Visão geral do controle de botão](button-control-overview-windows-forms.md)
- [Formas de selecionar um controle de botão dos Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Como: Responder a Windows Forms cliques de botão](how-to-respond-to-windows-forms-button-clicks.md)
- [Como: Designar um botão de Windows Forms como o botão de cancelamento usando o designer](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Controle de botão](button-control-windows-forms.md)
