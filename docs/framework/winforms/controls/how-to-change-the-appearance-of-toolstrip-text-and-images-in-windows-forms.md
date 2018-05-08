---
title: Como alterar a aparência de texto e imagens de ToolStrip nos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
ms.openlocfilehash: d3f53291e24d6a57e798725b716a7fd56eb661b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>Como alterar a aparência de texto e imagens de ToolStrip nos Windows Forms
Você pode controlar se o texto e imagens são exibidas em uma <xref:System.Windows.Forms.ToolStripItem> e como eles são alinhados relativos entre si e o <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>Para definir o que é exibido em um ToolStripItem  
  
-   Definir o <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriedade para o valor desejado. As possibilidades são `Image`, `ImageAndText`, `None`, e `Text`. O padrão é `ImageAndText`.  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>Para alinhar o texto em um ToolStripItem  
  
-   Definir o <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> propriedade para o valor desejado. As possibilidades são qualquer combinação de parte superior, intermediária e inferior com esquerda, centro e direita. O padrão é `MiddleCenter`.  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>Para alinhar uma imagem em um ToolStripItem  
  
-   Definir o <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> propriedade para o valor desejado. As possibilidades são qualquer combinação de parte superior, intermediária e inferior com esquerda, centro e direita. O padrão é `MiddleLeft`.  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>Para definir como imagens e textos de ToolStripItem são exibidas em relação a outro  
  
-   Definir o <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> propriedade para o valor desejado. As possibilidades são `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage` e `TextBeforeImage`. O padrão é `ImageBeforeText`.  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolStrip>  
 [Visão geral do controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Arquitetura de controle do ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Resumo da tecnologia de ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
