---
title: 'Como: Definir atributos de fonte para o controle RichTextBox dos Windows Forms'
ms.date: 03/30/2017
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
ms.openlocfilehash: 3793c33d378ee242656889434c7b29c415e9ec9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496199"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>Como: Definir atributos de fonte para o controle RichTextBox dos Windows Forms
Os formulários do Windows <xref:System.Windows.Forms.RichTextBox> controle tem várias opções para formatar o texto que ele exibe. Você pode fazer os caracteres selecionados em negrito, sublinhado ou itálico, usando o <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> propriedade. Você também pode usar essa propriedade para alterar o tamanho e a face de tipo dos caracteres selecionados. O <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> propriedade permite que você alterar a cor dos caracteres selecionados.  
  
### <a name="to-change-the-appearance-of-characters"></a>Para alterar a aparência dos caracteres  
  
1.  Defina o <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> propriedade para uma fonte apropriada.  
  
     Para permitir que os usuários definam a família de fontes, tamanho e face de tipos em um aplicativo, você normalmente usaria o <xref:System.Windows.Forms.FontDialog> componente. Para obter uma visão geral, consulte [Visão geral do componente FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).  
  
2.  Defina o <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> propriedade como uma cor apropriada.  
  
     Para permitir que os usuários definam a cor em um aplicativo, você normalmente usaria o <xref:System.Windows.Forms.ColorDialog> componente. Para obter uma visão geral, consulte [Visão geral do componente ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).  
  
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
    >  Essas propriedades afetam apenas o texto selecionado ou, se nenhum texto estiver selecionado, o texto que é digitado no local atual do ponto de inserção. Para obter informações sobre como selecionar texto de forma programática, consulte <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.RichTextBox>
- [Controle RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)
- [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
