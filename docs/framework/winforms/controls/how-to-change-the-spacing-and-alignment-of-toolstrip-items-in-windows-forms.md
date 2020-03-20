---
title: 'Como: Alterar o espaçamento e o alinhamento dos itens toolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 550ac1660a077e8d766a01bfa8d102c07f0fbfeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182236"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Como alterar o espaçamento e o alinhamento de itens ToolStrip nos Windows Forms
O <xref:System.Windows.Forms.ToolStrip> controle suporta totalmente características de layout, como <xref:System.Windows.Forms.ToolStripItem> o dimensionamento, o espaçamento dos <xref:System.Windows.Forms.ToolStrip>controles em relação ao outro, <xref:System.Windows.Forms.ToolStrip>o arranjo de controles sobre o , e o espaçamento dos controles relativos ao .  
  
 Como o valor <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> padrão `true`da propriedade é, os controles <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> são `false`dimensionados automaticamente, a menos que você defina a propriedade para .  
  
### <a name="to-manually-size-a-toolstripitem"></a>Para dimensionar manualmente um ToolStripItem  
  
1. Defina <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> a `false` propriedade para o controle associado.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. Defina <xref:System.Windows.Forms.ToolStripItem.Size%2A> a propriedade da maneira <xref:System.Windows.Forms.ToolStripItem>que você quiser para o associado .  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>Para definir o espaçamento de um ToolStripItem  
  
1. Insira os valores desejados, <xref:System.Windows.Forms.ToolStripItem.Margin%2A> em pixels, na propriedade do controle associado.  
  
     Os valores <xref:System.Windows.Forms.ToolStripItem.Margin%2A> da propriedade especificam o espaçamento entre o item e os itens adjacentes nesta ordem: Esquerda, Superior, Direita e Inferior.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>Para alinhar um ToolStripItem à direita de ToolStrip  
  
1. Defina <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> a <xref:System.Windows.Forms.ToolStripItemAlignment.Right> propriedade para o controle associado. Por padrão, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> é <xref:System.Windows.Forms.ToolStripItemAlignment.Left>definido para , que alinha <xref:System.Windows.Forms.ToolStrip>os controles para o lado esquerdo do .  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>Para organizar itens de ToolStrip no ToolStrip  
  
- Defina <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> a propriedade <xref:System.Windows.Forms.ToolStripLayoutStyle> para o valor do que você deseja.  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [Visão geral do controle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Arquitetura de controle ToolStrip](toolstrip-control-architecture.md)
- [Resumo da tecnologia de ToolStrip](toolstrip-technology-summary.md)
