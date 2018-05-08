---
title: Como exibir várias linhas no controle TextBox dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
ms.openlocfilehash: c826a519d8be05430eb6e2434209424514347b5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>Como exibir várias linhas no controle TextBox dos Windows Forms
Por padrão, o Windows Forms <xref:System.Windows.Forms.TextBox> controle exibe uma única linha de texto e não exibe barras de rolagem. Se o texto for maior que o espaço disponível, apenas parte do texto ficará visível. Você pode alterar esse comportamento padrão definindo o <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, e <xref:System.Windows.Forms.TextBox.ScrollBars%2A> propriedades com valores apropriados.  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>Exibir um retorno de carro no controle TextBox  
  
-   Para exibir um retorno de carro em uma multilinha <xref:System.Windows.Forms.TextBox>, use o <xref:System.Environment.NewLine%2A> propriedade.  
  
     Lembre-se que a interpretação de caracteres de escape (\\) é específica a um idioma. O Visual Basic usa `Chr$(13) & Chr$(10)` para a combinação de retorno de carro e caracteres de avanço de linha.  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>Exibir várias linhas no controle TextBox  
  
1.  Defina a propriedade <xref:System.Windows.Forms.TextBox.Multiline%2A> como `true`. Se <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> é `true` (o padrão), em seguida, o texto no controle aparecerá como um ou mais parágrafos; caso contrário, ele aparecerá como uma lista, no qual algumas linhas podem ser cortadas na borda do controle.  
  
2.  Definir o <xref:System.Windows.Forms.TextBox.ScrollBars%2A> propriedade para um valor apropriado.  
  
    |Valor|Descrição|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|Use esse valor se o texto será um parágrafo que quase sempre se ajusta ao controle. O usuário poderá usar o ponteiro do mouse para mover-se dentro do controle se o texto for grande demais para ser exibido totalmente ao mesmo tempo.|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|Use esse valor se você deseja exibir uma lista de linhas, algumas das quais podem ser maiores que a largura do <xref:System.Windows.Forms.TextBox> controle.|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|Use esse valor se a lista pode ser maior que a altura do controle.|  
  
3.  Definir o <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> propriedade para um valor apropriado.  
  
    |Valor|Descrição|  
    |-----------|-----------------|  
    |`false`|O texto no controle não será encapsulado automaticamente, portanto ele rolará para a direita até atingir uma quebra de linha. Use esse valor se você escolheu <xref:System.Windows.Forms.ScrollBars.Horizontal> barras de rolagem ou <xref:System.Windows.Forms.ScrollBars.Both>acima.|  
    |`true` (padrão)|A barra de rolagem horizontal não será exibida. Use esse valor se você escolheu <xref:System.Windows.Forms.ScrollBars.Vertical> barras de rolagem ou <xref:System.Windows.Forms.ScrollBars.None>acima, para exibir um ou mais parágrafos.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.TextBox>  
 [Visão geral do controle TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Como controlar o ponto de inserção em um controle TextBox dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Como criar uma caixa de texto de senha com o controle TextBox dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Como criar uma caixa de texto somente leitura](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Como inserir aspas em uma cadeia de caracteres](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Como selecionar texto no controle TextBox dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Controle TextBox](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
