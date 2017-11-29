---
title: "Como definir recuos definidos, recuos deslocados e parágrafos com marcadores com o controle RichTextBox dos Windows Forms"
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
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9b1398c0438f9ebe528e9394014f5f6529ea8f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>Como definir recuos definidos, recuos deslocados e parágrafos com marcadores com o controle RichTextBox dos Windows Forms
Windows Forms <xref:System.Windows.Forms.RichTextBox> controle tem várias opções para formatar o texto é exibido. Você pode formatar parágrafos selecionados como listas de marcadores, definindo o <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> propriedade. Você também pode usar o <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, e <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> propriedades para definir o recuo de parágrafos em relação à esquerda e direita bordas do controle e a borda esquerda de outras linhas de texto.  
  
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
  
1.  Definir o <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> propriedade como um inteiro que representa a distância em pixels entre a borda esquerda do controle e a borda esquerda do texto.  
  
2.  Definir o <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> propriedade como um inteiro que representa a distância em pixels entre a borda esquerda da primeira linha do texto no parágrafo e a borda esquerda das linhas subsequentes no mesmo paragraph. O valor de <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> propriedade só se aplica a linhas em um parágrafo que encapsulados abaixo da primeira linha.  
  
3.  Definir o <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> propriedade como um inteiro que representa a distância em pixels entre a borda direita do controle e a borda direita do texto.  
  
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
    >  Todas essas propriedades afetam todos os parágrafos que contêm o texto selecionado, bem como o texto digitado após o ponto de inserção atual. Por exemplo, quando um usuário seleciona uma palavra em um parágrafo e ajusta o recuo, as novas configurações serão aplicadas a todo o parágrafo que contém a palavra, bem como aos parágrafos subsequentemente inseridos depois do parágrafo selecionado. Para obter informações sobre como selecionar texto programaticamente, consulte <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.RichTextBox>  
 [Controle RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
