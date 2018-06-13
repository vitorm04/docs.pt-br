---
title: Como exibir barras de rolagem no controle RichTextBox dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
ms.openlocfilehash: 5588aad5b2e38716c628947c6e06365e7053eb5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532737"
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>Como exibir barras de rolagem no controle RichTextBox dos Windows Forms
Por padrão, o Windows Forms <xref:System.Windows.Forms.RichTextBox> controle exibe barras de rolagem horizontal e vertical conforme necessário. Há sete valores possíveis para a <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> propriedade o <xref:System.Windows.Forms.RichTextBox> controle, que são descritas na tabela a seguir.  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>Exibir barras de rolagem em um controle RichTextBox  
  
1.  Defina a propriedade <xref:System.Windows.Forms.RichTextBox.Multiline%2A> como `true`. Nenhum tipo de barra, inclusive de rolagem horizontal, será exibida se o <xref:System.Windows.Forms.RichTextBox.Multiline%2A> está definida como `false`.  
  
2.  Definir o <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> propriedade para um valor apropriado igual a <xref:System.Windows.Forms.RichTextBoxScrollBars> enumeração.  
  
    |Valor|Descrição|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (padrão)|Exibe barras de rolagem horizontal, vertical ou ambas, mas apenas quando o texto excede a largura ou o comprimento do controle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|Nunca exibe nenhum tipo de barra de rolagem.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|Exibe uma barra de rolagem horizontal somente quando o texto excede a largura do controle. (Para que isso ocorra, o <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> propriedade deve ser definida como `false`.)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|Exibe uma barra de rolagem vertical somente quando o texto excede a altura do controle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|Exibe quando da barra de rolagem de uma horizontal de <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> está definida como `false`. A barra de rolagem aparece esmaecida quando o texto não excede a largura do controle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|Sempre exibe uma barra de rolagem vertical. A barra de rolagem aparece esmaecida quando o texto não excede o tamanho do controle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|Sempre exibe uma barra de rolagem vertical. Exibe quando da barra de rolagem de uma horizontal de <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> está definida como `false`. A barra de rolagem aparece esmaecida quando o texto não excede a largura ou altura do controle.|  
  
3.  Definir o <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> propriedade para um valor apropriado.  
  
    |Valor|Descrição|  
    |-----------|-----------------|  
    |`false`|O texto do controle não é ajustado automaticamente para caber na largura do controle, por isso rolará para a direita até atingir uma quebra de linha. Use esse valor se você escolher barras de rolagem horizontal ou ambas acima.|  
    |`true` (padrão)|O texto do controle é ajustado automaticamente para caber na largura do controle. A barra de rolagem horizontal não será exibida. Use esse valor se você escolher as barras de rolagem vertical ou nenhuma acima para exibir um ou mais parágrafos acima.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.RichTextBoxScrollBars>  
 <xref:System.Windows.Forms.RichTextBox>  
 [Controle RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
