---
title: "Como alterar o espaçamento e o alinhamento de itens ToolStrip nos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42ae53e143942201359baebdfa8929647e7e35cd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Como alterar o espaçamento e o alinhamento de itens ToolStrip nos Windows Forms
O <xref:System.Windows.Forms.ToolStrip> totalmente o controle oferece suporte para recursos de layout, como dimensionamento, o espaçamento de <xref:System.Windows.Forms.ToolStripItem> controles relativos uns aos outros, a organização dos controles no <xref:System.Windows.Forms.ToolStrip>e o espaçamento de controles relativo a <xref:System.Windows.Forms.ToolStrip>.  
  
 Porque o valor padrão a <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> é de propriedade `true`, controles são dimensionados automaticamente a menos que você defina o <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> propriedade `false`.  
  
### <a name="to-manually-size-a-toolstripitem"></a>Para dimensionar manualmente um ToolStripItem  
  
1.  Definir o <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> propriedade `false` para o controle associado.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2.  Definir o <xref:System.Windows.Forms.ToolStripItem.Size%2A> da maneira desejada para o associado de propriedade <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>Para definir o espaçamento de um ToolStripItem  
  
1.  Insira os valores desejados, em pixels, do <xref:System.Windows.Forms.ToolStripItem.Margin%2A> propriedade do controle associado.  
  
     Os valores de <xref:System.Windows.Forms.ToolStripItem.Margin%2A> propriedade especifica o espaçamento entre o item e itens adjacentes nesta ordem: esquerda, superior, direita e inferior.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>Para alinhar um ToolStripItem à direita de ToolStrip  
  
1.  Definir o <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> propriedade <xref:System.Windows.Forms.ToolStripItemAlignment.Right> para o controle associado. Por padrão, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> é definido como <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, que alinha os controles para o lado esquerdo do <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>Para organizar itens de ToolStrip no ToolStrip  
  
-   Definir o <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> o valor da propriedade <xref:System.Windows.Forms.ToolStripLayoutStyle> que você deseja.  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.Control.Layout>  
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>  
 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [Visão geral do controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Arquitetura de controle do ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Resumo da tecnologia de ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
