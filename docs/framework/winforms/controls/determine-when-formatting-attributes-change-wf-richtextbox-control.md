---
title: 'Como: Determinar quando os atributos de formatação mudam no controle RichTextBox do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], determining font changes
- text boxes [Windows Forms], determining font changes
- SelChange event
ms.assetid: bdfed015-f77a-41e5-b38f-f8629b2fa166
ms.openlocfilehash: a90affde9de36f1c83d5b7c21b40580cdf53402e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308452"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>Como: Determinar quando os atributos de formatação mudam no controle RichTextBox do Windows Forms
Um uso comum dos formulários Windows <xref:System.Windows.Forms.RichTextBox> controle é formatar texto com atributos como opções de fonte ou estilos de parágrafo. Seu aplicativo pode precisar controlar as alterações no texto de formatação para fins de exibição de uma barra de ferramentas, como muitos aplicativos de processamento de texto.  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>Para responder a alterações em atributos de formatação  
  
1. Escrever código no <xref:System.Windows.Forms.RichTextBox.SelectionChanged> manipulador de eventos para executar a ação apropriada dependendo do valor do atributo. O exemplo a seguir altera a aparência de um botão de barra de ferramentas, dependendo do valor da <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> propriedade. O botão de barra de ferramentas será atualizado somente quando o ponto de inserção for movido no controle.  
  
     O exemplo a seguir supõe um formulário com um <xref:System.Windows.Forms.RichTextBox> controle e um <xref:System.Windows.Forms.ToolBar> controle que contém um botão de barra de ferramentas. Para obter mais informações sobre as barras de ferramentas e botões de barra de ferramentas, consulte [como: Adicionar botões a um controle de barra de ferramentas](how-to-add-buttons-to-a-toolbar-control.md).  
  
    ```vb  
    ' The following code assumes the existence of a toolbar control  
    ' with at least one toolbar button.  
    Private Sub RichTextBox1_SelectionChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles RichTextBox1.SelectionChanged  
       If RichTextBox1.SelectionBullet = True Then  
          ' Bullet button on toolbar should appear pressed  
          ToolBarButton1.Pushed = True  
       Else  
           ' Bullet button on toolbar should appear unpressed  
           ToolBarButton1.Pushed = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private void richTextBox1_SelectionChanged(object sender,  
    System.EventArgs e)  
    {  
       if (richTextBox1.SelectionBullet == true)   
       {  
          // Bullet button on toolbar should appear pressed  
          toolBarButton1.Pushed = true;  
       }  
       else   
       {  
          // Bullet button on toolbar should appear unpressed  
          toolBarButton1.Pushed = false;  
       }  
    }  
    ```  
  
    ```cpp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private:  
       System::Void richTextBox1_SelectionChanged(  
          System::Object ^  sender, System::EventArgs ^  e)  
       {  
          if (richTextBox1->SelectionBullet == true)  
          {  
             // Bullet button on toolbar should appear pressed  
             toolBarButton1->Pushed = true;  
          }  
          else  
          {  
             // Bullet button on toolbar should appear unpressed  
             toolBarButton1->Pushed = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.RichTextBox.SelectionChanged>
- <xref:System.Windows.Forms.RichTextBox>
- [Controle RichTextBox](richtextbox-control-windows-forms.md)
- [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)
