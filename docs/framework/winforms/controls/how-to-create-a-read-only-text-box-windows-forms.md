---
title: Como criar uma caixa de texto somente leitura (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 06e03f67bd1f084b30bce85c3d81ad7b8c97a1b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530140"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Como criar uma caixa de texto somente leitura (Windows Forms)
Você pode transformar uma caixa de texto Windows Forms editável em um controle somente leitura. Por exemplo, a caixa de texto pode exibir um valor que não estejam no momento, devido ao estado do aplicativo, mas geralmente é editado.  
  
### <a name="to-create-a-read-only-text-box"></a>Para criar uma caixa de texto somente leitura  
  
1.  Definir o <xref:System.Windows.Forms.TextBox> do controle <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> propriedade `true`. Com a propriedade definida como `true`, os usuários ainda podem rolar e realce o texto em uma caixa de texto sem permitir alterações. Um **cópia** comando está funcionando em uma caixa de texto, mas **Recortar** e **colar** comandos não são.  
  
    > [!NOTE]
    >  O <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> propriedade afeta apenas a interação do usuário em tempo de execução. Você ainda pode alterar conteúdo da caixa de texto programaticamente no tempo de execução alterando o <xref:System.Windows.Forms.TextBox.Text%2A> propriedade da caixa de texto.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.TextBox>  
 [Visão geral do controle TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Como controlar o ponto de inserção em um controle TextBox dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Como criar uma caixa de texto de senha com o controle TextBox dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Como inserir aspas em uma cadeia de caracteres](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Como selecionar texto no controle TextBox dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Como exibir várias linhas no controle TextBox dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [Controle TextBox](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
