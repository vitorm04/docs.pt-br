---
title: 'Como: Definir recuos, recuos deslocados e parágrafos com marcadores com o controle RichTextBox dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
ms.openlocfilehash: ad5dd1cc3839fbe29d39f6ab38b0e865e7b0a335
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492400"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>Como: Definir recuos, recuos deslocados e parágrafos com marcadores com o controle RichTextBox dos Windows Forms
Os formulários do Windows <xref:System.Windows.Forms.RichTextBox> controle tem várias opções para formatar o texto que ele exibe. Você pode formatar parágrafos selecionados como listas com marcadores, definindo o <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> propriedade. Você também pode usar o <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, e <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> propriedades para definir o recuo de parágrafos em relação à esquerda e direita bordas do controle e a borda esquerda de outras linhas de texto.  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>Formatar um parágrafo como uma lista com marcadores  
  
1.  Defina a propriedade <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> como `true`.  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a>Para recuar um parágrafo  
  
1.  Defina o <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> propriedade em um inteiro que representa a distância em pixels entre a borda esquerda do controle e a borda esquerda do texto.  
  
2.  Defina o <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> propriedade em um inteiro que representa a distância em pixels entre a borda esquerda da primeira linha do texto no parágrafo e a borda esquerda das linhas subsequentes do mesmo parágrafo. O valor da <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> propriedade só se aplica a linhas em um parágrafo que foram encapsuladas abaixo da primeira linha.  
  
3.  Defina o <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> propriedade em um inteiro que representa a distância em pixels entre a borda direita do controle e a borda direita do texto.  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    >  Todas essas propriedades afetam todos os parágrafos que contêm o texto selecionado, bem como o texto digitado após o ponto de inserção atual. Por exemplo, quando um usuário seleciona uma palavra em um parágrafo e ajusta o recuo, as novas configurações serão aplicadas a todo o parágrafo que contém a palavra, bem como aos parágrafos subsequentemente inseridos depois do parágrafo selecionado. Para obter informações sobre como selecionar texto por meio de programação, consulte <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.RichTextBox>
- [Controle RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)
- [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
