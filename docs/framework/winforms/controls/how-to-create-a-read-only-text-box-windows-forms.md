---
title: 'Como: Criar uma caixa de texto somente leitura (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 18d2f5ed2530957487ac25c3eb6240f8bc50a938
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971939"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Como: Criar uma caixa de texto somente leitura (Windows Forms)

Você pode transformar uma caixa de texto Windows Forms editável em um controle somente leitura. Por exemplo, a caixa de texto pode exibir um valor que geralmente é editado, mas pode não estar no momento, devido ao estado do aplicativo.

## <a name="to-create-a-read-only-text-box"></a>Para criar uma caixa de texto somente leitura

1. Defina a <xref:System.Windows.Forms.TextBox> Propriedade do <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> controle como `true`. Com a propriedade definida como `true`, os usuários ainda podem rolar e realçar o texto em uma caixa de texto sem permitir alterações. Um comando de **cópia** é funcional em uma caixa de texto, mas os comandos Recortar e **colar** não são.

    > [!NOTE]
    > A <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> propriedade afeta apenas a interação do usuário em tempo de execução. Você ainda pode alterar o conteúdo da caixa de texto programaticamente em <xref:System.Windows.Forms.TextBox.Text%2A> tempo de execução alterando a propriedade da caixa de texto.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.TextBox>
- [Visão geral do controle TextBox](textbox-control-overview-windows-forms.md)
- [Como: Controlar o ponto de inserção em um controle de caixa de texto Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Como: Criar uma caixa de texto de senha com o controle caixa de texto Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Como: Colocar aspas em uma cadeia de caracteres](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Como: Selecionar texto no controle de caixa de texto Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Como: Exibir várias linhas no controle de caixa de texto Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Controle TextBox](textbox-control-windows-forms.md)
