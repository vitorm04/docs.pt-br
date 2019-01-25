---
title: 'Como: Alterar o espaçamento e alinhamento de itens de ToolStrip nos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 2c9c60a3bfd78b7111b9cdff6a791d70c8e53c82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685057"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Como: Alterar o espaçamento e alinhamento de itens de ToolStrip nos Windows Forms
O <xref:System.Windows.Forms.ToolStrip> totalmente o controle dá suporte a recursos de layout como dimensionamento, espaçamento de <xref:System.Windows.Forms.ToolStripItem> controles relativos uns aos outros, a organização dos controles na <xref:System.Windows.Forms.ToolStrip>e o espaçamento dos controles relativo para o <xref:System.Windows.Forms.ToolStrip>.  
  
 Porque o valor padrão do <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> é de propriedade `true`, controles são dimensionados automaticamente a menos que você defina o <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> propriedade `false`.  
  
### <a name="to-manually-size-a-toolstripitem"></a>Para dimensionar manualmente um ToolStripItem  
  
1.  Defina as <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> propriedade para `false` para o controle associado.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2.  Defina as <xref:System.Windows.Forms.ToolStripItem.Size%2A> propriedade da maneira desejada para associado <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>Para definir o espaçamento de um ToolStripItem  
  
1.  Insira os valores desejados, em pixels, o <xref:System.Windows.Forms.ToolStripItem.Margin%2A> propriedade do controle associado.  
  
     Os valores da <xref:System.Windows.Forms.ToolStripItem.Margin%2A> propriedade especificam o espaçamento entre o item e itens adjacentes nesta ordem: À esquerda, superior, direita e inferior.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>Para alinhar um ToolStripItem à direita de ToolStrip  
  
1.  Defina as <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> propriedade para <xref:System.Windows.Forms.ToolStripItemAlignment.Right> para o controle associado. Por padrão, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> é definido como <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, que alinha os controles à esquerda do <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>Para organizar itens de ToolStrip no ToolStrip  
  
-   Defina as <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> propriedade para o valor de <xref:System.Windows.Forms.ToolStripLayoutStyle> que você deseja.  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [Visão geral do controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
- [Arquitetura de controle do ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
- [Resumo da tecnologia de ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
