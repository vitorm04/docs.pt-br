---
title: 'Como: Designar um botão do Windows Forms como o botão Cancelar usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: cc352f15fb1e8b531cd0f9b298b2db4ce649d3cf
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039643"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>Como: Designar um botão do Windows Forms como o botão Cancelar usando o designer
Em qualquer formulário do Windows, você pode designar <xref:System.Windows.Forms.Button> um controle para ser o botão Cancelar. Um botão Cancelar é clicado sempre que o usuário pressiona a tecla ESC, independentemente de qual outro controle no formulário tem o foco. Esse botão geralmente é programado para permitir que o usuário saia rapidamente de uma operação sem confirmar qualquer ação.

## <a name="to-designate-the-cancel-button"></a>Para designar o botão Cancelar

1. Selecione o formulário no qual o botão reside.

2. Na janela **Propriedades** , defina a propriedade do <xref:System.Windows.Forms.Form.CancelButton%2A> formulário como o <xref:System.Windows.Forms.Button> nome do controle.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Visão geral do controle de botão](button-control-overview-windows-forms.md)
- [Formas de selecionar um controle de botão dos Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Como: Responder a Windows Forms cliques de botão](how-to-respond-to-windows-forms-button-clicks.md)
- [Como: Designar um botão de Windows Forms como o botão aceitar usando o designer](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Controle de botão](button-control-windows-forms.md)
