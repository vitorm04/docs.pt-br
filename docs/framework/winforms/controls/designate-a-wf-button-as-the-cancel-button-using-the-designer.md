---
title: Designar um botão como o botão de cancelamento usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: 95d1139b6e339055f944ad0b0967a6d91283d49e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746058"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>Como projetar um botão dos Windows Forms como o botão Cancelar usando o designer
Em qualquer formulário do Windows, você pode designar um controle de <xref:System.Windows.Forms.Button> para ser o botão Cancelar. Um botão Cancelar é clicado sempre que o usuário pressiona a tecla ESC, independentemente de qual outro controle no formulário tem o foco. Esse botão geralmente é programado para permitir que o usuário saia rapidamente de uma operação sem confirmar qualquer ação.

## <a name="to-designate-the-cancel-button"></a>Para designar o botão Cancelar

1. Selecione o formulário no qual o botão reside.

2. Na janela **Propriedades** , defina a propriedade <xref:System.Windows.Forms.Form.CancelButton%2A> do formulário como o nome do controle de <xref:System.Windows.Forms.Button>.

## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Visão geral do controle de botão](button-control-overview-windows-forms.md)
- [Formas de selecionar um controle de botão dos Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Como responder a cliques no botão dos Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Como designar um botão do Windows Forms como o botão Aceitar usando o Designer](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Controle de botão](button-control-windows-forms.md)
