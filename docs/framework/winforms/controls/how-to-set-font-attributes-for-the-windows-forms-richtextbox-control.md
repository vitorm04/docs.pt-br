---
title: 'Como: Definir atributos de fonte para o controle RichTextBox do Windows Forms'
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
ms.openlocfilehash: 4919e94c23b1a67680ea0f360304ee0f75c7f425
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963217"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>Como: Definir atributos de fonte para o controle RichTextBox do Windows Forms
O controle <xref:System.Windows.Forms.RichTextBox> Windows Forms tem várias opções para formatar o texto exibido. Você pode tornar os caracteres selecionados em negrito, sublinhados ou itálicos usando a <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> propriedade. Você também pode usar essa propriedade para alterar o tamanho e a face de tipo dos caracteres selecionados. A <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> propriedade permite que você altere a cor dos caracteres selecionados.  
  
### <a name="to-change-the-appearance-of-characters"></a>Para alterar a aparência dos caracteres  
  
1. Defina a <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> Propriedade como uma fonte apropriada.  
  
     Para permitir que os usuários definam a família de fontes, o tamanho e a face de tipos em um aplicativo <xref:System.Windows.Forms.FontDialog> , você normalmente usaria o componente. Para obter uma visão geral, consulte [Visão geral do componente FontDialog](fontdialog-component-overview-windows-forms.md).  
  
2. Defina a <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Propriedade como uma cor apropriada.  
  
     Para permitir que os usuários definam a cor em um aplicativo, você normalmente usaria o <xref:System.Windows.Forms.ColorDialog> componente. Para obter uma visão geral, consulte [Visão geral do componente ColorDialog](colordialog-component-overview-windows-forms.md).  
  
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
    > Essas propriedades afetam apenas o texto selecionado ou, se nenhum texto estiver selecionado, o texto que é digitado no local atual do ponto de inserção. Para obter informações sobre como selecionar texto programaticamente, consulte <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.RichTextBox>
- [Controle RichTextBox](richtextbox-control-windows-forms.md)
- [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)
