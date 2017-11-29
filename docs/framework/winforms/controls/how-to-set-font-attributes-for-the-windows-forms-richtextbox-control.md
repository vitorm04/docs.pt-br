---
title: Como definir atributos de fonte para o controle RichTextBox dos Windows Forms
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
- cpp
helpviewer_keywords:
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0fe122f509890715c398bef728a98ff874b61817
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>Como definir atributos de fonte para o controle RichTextBox dos Windows Forms
Windows Forms <xref:System.Windows.Forms.RichTextBox> controle tem várias opções para formatar o texto é exibido. Você pode fazer os caracteres selecionados em negrito, sublinhado ou itálico, usando o <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> propriedade. Você também pode usar essa propriedade para alterar o tamanho e a face de tipo dos caracteres selecionados. O <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> propriedade permite que você altere a cor dos caracteres selecionados.  
  
### <a name="to-change-the-appearance-of-characters"></a>Para alterar a aparência dos caracteres  
  
1.  Definir o <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> propriedade para uma fonte apropriada.  
  
     Para habilitar usuários definir o tipo, tamanho e família de fontes em um aplicativo, normalmente você usaria o <xref:System.Windows.Forms.FontDialog> componente. Para obter uma visão geral, consulte [Visão geral do componente FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).  
  
2.  Definir o <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> propriedade para uma cor apropriada.  
  
     Para habilitar usuários definir a cor em um aplicativo, normalmente você usaria o <xref:System.Windows.Forms.ColorDialog> componente. Para obter uma visão geral, consulte [Visão geral do componente ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    >  Essas propriedades afetam apenas o texto selecionado ou, se nenhum texto estiver selecionado, o texto que é digitado no local atual do ponto de inserção. Para obter informações sobre a seleção de texto programaticamente, consulte <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.RichTextBox>  
 [Controle RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
