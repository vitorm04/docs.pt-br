---
title: Como alterar a aparência de texto e imagens de ToolStrip
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
ms.openlocfilehash: 7816e138e44554683c201895ece1f886ace8bfa6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746599"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>Como alterar a aparência de texto e imagens de ToolStrip nos Windows Forms
Você pode controlar se o texto e as imagens são exibidos em um <xref:System.Windows.Forms.ToolStripItem> e como eles são alinhados em relação uns aos outros e ao <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>Para definir o que é exibido em um ToolStripItem  
  
- Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> para o valor desejado. As possibilidades são `Image`, `ImageAndText`, `None`e `Text`. O padrão é `ImageAndText`.  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>Para alinhar texto em um ToolStripItem  
  
- Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> para o valor desejado. As possibilidades são qualquer combinação de superior, meio e inferior com esquerda, centro e direita. O padrão é `MiddleCenter`.  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>Para alinhar uma imagem em um ToolStripItem  
  
- Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> para o valor desejado. As possibilidades são qualquer combinação de superior, meio e inferior com esquerda, centro e direita. O padrão é `MiddleLeft`.  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>Para definir como as imagens e o texto de ToolStripItem são exibidos em relação umas às outras  
  
- Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> para o valor desejado. As possibilidades são `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage` e `TextBeforeImage`. O padrão é `ImageBeforeText`.  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.ToolStrip>
- [Visão geral do controle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Arquitetura de controle do ToolStrip](toolstrip-control-architecture.md)
- [Resumo da tecnologia de ToolStrip](toolstrip-technology-summary.md)
