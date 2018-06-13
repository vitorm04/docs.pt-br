---
title: Como determinar quando os atributos de formatação mudam no controle RichTextBox dos Windows Forms
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
ms.openlocfilehash: 789a0a25c65185b101ef427ff62871fa490c7f1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525208"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a><span data-ttu-id="c9c28-102">Como determinar quando os atributos de formatação mudam no controle RichTextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c9c28-102">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="c9c28-103">Um uso comum de Windows Forms <xref:System.Windows.Forms.RichTextBox> controle está formatando texto com atributos como opções de fonte ou estilos de parágrafo.</span><span class="sxs-lookup"><span data-stu-id="c9c28-103">A common use of the Windows Forms <xref:System.Windows.Forms.RichTextBox> control is formatting text with attributes such as font options or paragraph styles.</span></span> <span data-ttu-id="c9c28-104">Seu aplicativo pode precisar controlar as alterações no texto de formatação para fins de exibição de uma barra de ferramentas, como muitos aplicativos de processamento de texto.</span><span class="sxs-lookup"><span data-stu-id="c9c28-104">Your application may need to keep track of any changes in text formatting for the purpose of displaying a toolbar, as in many word-processing applications.</span></span>  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a><span data-ttu-id="c9c28-105">Para responder a alterações em atributos de formatação</span><span class="sxs-lookup"><span data-stu-id="c9c28-105">To respond to changes in formatting attributes</span></span>  
  
1.  <span data-ttu-id="c9c28-106">Escrever código de <xref:System.Windows.Forms.RichTextBox.SelectionChanged> manipulador de eventos para executar a ação apropriada dependendo do valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="c9c28-106">Write code in the <xref:System.Windows.Forms.RichTextBox.SelectionChanged> event handler to perform an appropriate action depending on the value of the attribute.</span></span> <span data-ttu-id="c9c28-107">O exemplo a seguir altera a aparência de um botão de barra de ferramentas, dependendo do valor da <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c9c28-107">The following example changes the appearance of a toolbar button depending on the value of the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="c9c28-108">O botão de barra de ferramentas será atualizado somente quando o ponto de inserção for movido no controle.</span><span class="sxs-lookup"><span data-stu-id="c9c28-108">The toolbar button will only be updated when the insertion point is moved in the control.</span></span>  
  
     <span data-ttu-id="c9c28-109">O exemplo a seguir assume uma forma com um <xref:System.Windows.Forms.RichTextBox> controle e um <xref:System.Windows.Forms.ToolBar> controle que contém um botão de barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="c9c28-109">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control and a <xref:System.Windows.Forms.ToolBar> control that contains a toolbar button.</span></span> <span data-ttu-id="c9c28-110">Para obter mais informações sobre barras de ferramentas e botões de barra de ferramentas, veja [Como adicionar botões a um controle de barra de ferramentas](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md).</span><span class="sxs-lookup"><span data-stu-id="c9c28-110">For more information about toolbars and toolbar buttons, see [How to: Add Buttons to a ToolBar Control](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c9c28-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9c28-111">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox.SelectionChanged>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="c9c28-112">Controle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="c9c28-112">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="c9c28-113">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c9c28-113">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
