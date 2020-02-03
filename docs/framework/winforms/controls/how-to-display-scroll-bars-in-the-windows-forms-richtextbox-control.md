---
title: Exibir barras de rolagem no controle RichTextBox
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
ms.openlocfilehash: 2185b572ef20765043d3df3dbfd8bf5b21cfac28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745554"
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>Como exibir barras de rolagem no controle RichTextBox dos Windows Forms
Por padrão, o controle de <xref:System.Windows.Forms.RichTextBox> de Windows Forms exibe barras de rolagem horizontais e verticais, conforme necessário. Há sete valores possíveis para a propriedade <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> do controle de <xref:System.Windows.Forms.RichTextBox>, que são descritos na tabela a seguir.  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>Exibir barras de rolagem em um controle RichTextBox  
  
1. Defina a propriedade <xref:System.Windows.Forms.RichTextBox.Multiline%2A> como `true`. Nenhum tipo de barra de rolagem, incluindo horizontal, será exibido se a propriedade <xref:System.Windows.Forms.RichTextBox.Multiline%2A> for definida como `false`.  
  
2. Defina a propriedade <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> como um valor apropriado da enumeração <xref:System.Windows.Forms.RichTextBoxScrollBars>.  
  
    |{1&gt;Valor&lt;1}|Descrição|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (padrão)|Exibe barras de rolagem horizontal, vertical ou ambas, mas apenas quando o texto excede a largura ou o comprimento do controle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|Nunca exibe nenhum tipo de barra de rolagem.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|Exibe uma barra de rolagem horizontal somente quando o texto excede a largura do controle. (Para que isso ocorra, a propriedade <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> deve ser definida como `false`.)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|Exibe uma barra de rolagem vertical somente quando o texto excede a altura do controle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|Exibe uma barra de rolagem horizontal quando a propriedade <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> é definida como `false`. A barra de rolagem aparece esmaecida quando o texto não excede a largura do controle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|Sempre exibe uma barra de rolagem vertical. A barra de rolagem aparece esmaecida quando o texto não excede o tamanho do controle.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|Sempre exibe uma barra de rolagem vertical. Exibe uma barra de rolagem horizontal quando a propriedade <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> é definida como `false`. A barra de rolagem aparece esmaecida quando o texto não excede a largura ou altura do controle.|  
  
3. Defina a propriedade <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> com um valor apropriado.  
  
    |{1&gt;Valor&lt;1}|Descrição|  
    |-----------|-----------------|  
    |`false`|O texto do controle não é ajustado automaticamente para caber na largura do controle, por isso rolará para a direita até atingir uma quebra de linha. Use esse valor se você escolher barras de rolagem horizontal ou ambas acima.|  
    |`true` (padrão)|O texto do controle é ajustado automaticamente para caber na largura do controle. A barra de rolagem horizontal não será exibida. Use esse valor se você escolher as barras de rolagem vertical ou nenhuma acima para exibir um ou mais parágrafos acima.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.RichTextBoxScrollBars>
- <xref:System.Windows.Forms.RichTextBox>
- [Controle RichTextBox](richtextbox-control-windows-forms.md)
- [Controles a serem usados no Windows Forms](controls-to-use-on-windows-forms.md)
