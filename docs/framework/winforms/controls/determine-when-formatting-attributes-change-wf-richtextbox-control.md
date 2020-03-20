---
title: Determine quando a formatação de atributos altera no controle RichTextBox
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
ms.openlocfilehash: a190c3479b58464763e0eefdd32d14e88a1f05e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142258"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>Como determinar quando os atributos de formatação mudam no controle RichTextBox dos Windows Forms
Um uso comum <xref:System.Windows.Forms.RichTextBox> do controle do Windows Forms é a formatação de texto com atributos como opções de fonte ou estilos de parágrafo. Seu aplicativo pode precisar controlar as alterações no texto de formatação para fins de exibição de uma barra de ferramentas, como muitos aplicativos de processamento de texto.  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>Para responder a alterações em atributos de formatação  
  
1. Escreva código <xref:System.Windows.Forms.RichTextBox.SelectionChanged> no manipulador de eventos para executar uma ação apropriada, dependendo do valor do atributo. O exemplo a seguir altera a aparência de um <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> botão de barra de ferramentas, dependendo do valor da propriedade. O botão de barra de ferramentas será atualizado somente quando o ponto de inserção for movido no controle.  
  
     O exemplo abaixo assume um <xref:System.Windows.Forms.RichTextBox> formulário <xref:System.Windows.Forms.ToolBar> com um controle e um controle que contém um botão de barra de ferramentas. Para obter mais informações sobre barras de ferramentas e botões de barra de ferramentas, veja [Como adicionar botões a um controle de barra de ferramentas](how-to-add-buttons-to-a-toolbar-control.md).  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.RichTextBox.SelectionChanged>
- <xref:System.Windows.Forms.RichTextBox>
- [Controle RichTextBox](richtextbox-control-windows-forms.md)
- [Controles para usar em formulários windows](controls-to-use-on-windows-forms.md)
