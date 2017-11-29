---
title: Como criar uma caixa de texto somente leitura (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9cf6064442c3b648116f98f98f169dac12e5e88c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
