---
title: Definir recuos, recuos deslocados e parágrafos com marcadores com controle RichTextBox
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
ms.openlocfilehash: 4dcd5691f328eac6d94675c50ed41a7d7cc36596
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743011"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>Como definir recuos definidos, recuos deslocados e parágrafos com marcadores com o controle RichTextBox dos Windows Forms
O controle de <xref:System.Windows.Forms.RichTextBox> de Windows Forms tem várias opções para formatar o texto exibido. Você pode formatar os parágrafos selecionados como listas com marcadores definindo a propriedade <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>. Você também pode usar as propriedades <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>e <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> para definir o recuo de parágrafos em relação às bordas esquerda e direita do controle e à borda esquerda de outras linhas de texto.  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>Formatar um parágrafo como uma lista com marcadores  
  
1. Defina a propriedade <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> como `true`.  
  
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
  
1. Defina a propriedade <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> como um inteiro que representa a distância em pixels entre a borda esquerda do controle e a borda esquerda do texto.  
  
2. Defina a propriedade <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> como um inteiro que representa a distância em pixels entre a borda esquerda da primeira linha de texto no parágrafo e a borda esquerda das linhas subsequentes no mesmo parágrafo. O valor da propriedade <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> só se aplica a linhas em um parágrafo que tenha sido encapsulado abaixo da primeira linha.  
  
3. Defina a propriedade <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> como um inteiro que representa a distância em pixels entre a borda direita do controle e a borda direita do texto.  
  
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
    > Todas essas propriedades afetam todos os parágrafos que contêm o texto selecionado, bem como o texto digitado após o ponto de inserção atual. Por exemplo, quando um usuário seleciona uma palavra em um parágrafo e ajusta o recuo, as novas configurações serão aplicadas a todo o parágrafo que contém a palavra, bem como aos parágrafos subsequentemente inseridos depois do parágrafo selecionado. Para obter informações sobre como selecionar texto programaticamente, consulte <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.RichTextBox>
- [Controle RichTextBox](richtextbox-control-windows-forms.md)
- [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)
