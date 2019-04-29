---
title: 'Como: Criar uma caixa de texto somente leitura (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 72dc188993474ad4b39f0cfa74cadffdb99ff46f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746794"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Como: Criar uma caixa de texto somente leitura (Windows Forms)
Você pode transformar uma caixa de texto editável do Windows Forms em um controle somente leitura. Por exemplo, a caixa de texto pode exibir um valor que geralmente é editado, mas pode não ser no momento, devido ao estado do aplicativo.  
  
### <a name="to-create-a-read-only-text-box"></a>Para criar uma caixa de texto somente leitura  
  
1. Defina as <xref:System.Windows.Forms.TextBox> do controle <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> propriedade `true`. Com a propriedade definida como `true`, os usuários ainda podem rolar e realçar o texto em uma caixa de texto sem permitir alterações. Um **cópia** comando é funcional em uma caixa de texto, mas **Recortar** e **colar** comandos não são.  
  
    > [!NOTE]
    >  O <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> propriedade afeta somente a interação do usuário em tempo de execução. Você ainda pode alterar conteúdo da caixa de texto por meio de programação em tempo de execução, alterando o <xref:System.Windows.Forms.TextBox.Text%2A> propriedade da caixa de texto.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.TextBox>
- [Visão geral do controle TextBox](textbox-control-overview-windows-forms.md)
- [Como: Controlar o ponto de inserção em um controle TextBox dos Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Como: Criar uma caixa de texto de senha com o controle TextBox dos Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Como: Inserir aspas em uma cadeia de caracteres](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Como: Selecione o texto no controle TextBox de formulários do Windows](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Como: Exibir várias linhas no controle TextBox de formulários do Windows](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Controle TextBox](textbox-control-windows-forms.md)
