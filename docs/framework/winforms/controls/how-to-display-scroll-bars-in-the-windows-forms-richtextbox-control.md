---
title: 'Como: Controle RichTextBox do exibir barras de rolagem do Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
ms.openlocfilehash: 119cf736dfa7b8b8fce57b7e8fcb24dd09f01ce0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716485"
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>Como: Controle RichTextBox do exibir barras de rolagem do Windows Forms
Por padrão, os formulários do Windows <xref:System.Windows.Forms.RichTextBox> controle exibe barras de rolagem horizontal e vertical conforme necessário. Há sete valores possíveis para o <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> propriedade do <xref:System.Windows.Forms.RichTextBox> controle, que são descritos na tabela a seguir.  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>Exibir barras de rolagem em um controle RichTextBox  
  
1.  Defina a propriedade <xref:System.Windows.Forms.RichTextBox.Multiline%2A> como `true`. Nenhum tipo de barra, inclusive de rolagem horizontal, será exibida se o <xref:System.Windows.Forms.RichTextBox.Multiline%2A> estiver definida como `false`.  
  
2.  Defina a <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> propriedade para um valor apropriado igual a <xref:System.Windows.Forms.RichTextBoxScrollBars> enumeração.  
  
    |Valor|Descrição|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (padrão)|Exibe barras de rolagem horizontal, vertical ou ambas, mas apenas quando o texto excede a largura ou o comprimento do controle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|Nunca exibe nenhum tipo de barra de rolagem.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|Exibe uma barra de rolagem horizontal somente quando o texto excede a largura do controle. (Para isso ocorrer, o <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> propriedade deve ser definida como `false`.)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|Exibe uma barra de rolagem vertical somente quando o texto excede a altura do controle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|Exibe uma rolagem horizontal da barra quando o <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> estiver definida como `false`. A barra de rolagem aparece esmaecida quando o texto não excede a largura do controle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|Sempre exibe uma barra de rolagem vertical. A barra de rolagem aparece esmaecida quando o texto não excede o tamanho do controle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|Sempre exibe uma barra de rolagem vertical. Exibe uma rolagem horizontal da barra quando o <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> estiver definida como `false`. A barra de rolagem aparece esmaecida quando o texto não excede a largura ou altura do controle.|  
  
3.  Defina o <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> propriedade para um valor apropriado.  
  
    |Valor|Descrição|  
    |-----------|-----------------|  
    |`false`|O texto do controle não é ajustado automaticamente para caber na largura do controle, por isso rolará para a direita até atingir uma quebra de linha. Use esse valor se você escolher barras de rolagem horizontal ou ambas acima.|  
    |`true` (padrão)|O texto do controle é ajustado automaticamente para caber na largura do controle. A barra de rolagem horizontal não será exibida. Use esse valor se você escolher as barras de rolagem vertical ou nenhuma acima para exibir um ou mais parágrafos acima.|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.RichTextBoxScrollBars>
- <xref:System.Windows.Forms.RichTextBox>
- [Controle RichTextBox](richtextbox-control-windows-forms.md)
- [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)
