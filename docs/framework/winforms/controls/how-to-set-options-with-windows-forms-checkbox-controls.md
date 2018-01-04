---
title: "Como definir opções com controles CheckBox dos Windows Forms"
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
f1_keywords: checked
helpviewer_keywords:
- CheckBox control [Windows Forms], checked state
- check boxes [Windows Forms], using to set options
- CheckBox control [Windows Forms], using to set options
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4059e3b4ad4c687234f2bc0c66c680b2c857cfe7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a><span data-ttu-id="36dcf-102">Como definir opções com controles CheckBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36dcf-102">How to: Set Options with Windows Forms CheckBox Controls</span></span>
<span data-ttu-id="36dcf-103">Um Windows Forms <xref:System.Windows.Forms.CheckBox> controle é usado para fornecer aos usuários True/False ou Yes/No opções.</span><span class="sxs-lookup"><span data-stu-id="36dcf-103">A Windows Forms <xref:System.Windows.Forms.CheckBox> control is used to give users True/False or Yes/No options.</span></span> <span data-ttu-id="36dcf-104">O controle exibe uma marca de seleção quando ele é selecionado.</span><span class="sxs-lookup"><span data-stu-id="36dcf-104">The control displays a check mark when it is selected.</span></span>  
  
### <a name="to-set-options-with-checkbox-controls"></a><span data-ttu-id="36dcf-105">Para definir opções com controles CheckBox</span><span class="sxs-lookup"><span data-stu-id="36dcf-105">To set options with CheckBox controls</span></span>  
  
1.  <span data-ttu-id="36dcf-106">Examinar o valor da <xref:System.Windows.Forms.CheckBox.Checked%2A> propriedade para determinar o estado e usar esse valor para definir uma opção.</span><span class="sxs-lookup"><span data-stu-id="36dcf-106">Examine the value of the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine its state, and use that value to set an option.</span></span>  
  
     <span data-ttu-id="36dcf-107">No exemplo de código a seguir, quando o <xref:System.Windows.Forms.CheckBox> do controle <xref:System.Windows.Forms.CheckBox.CheckedChanged> é gerado, o formulário <xref:System.Windows.Forms.Control.AllowDrop%2A> está definida como `false` se a caixa de seleção estiver marcada.</span><span class="sxs-lookup"><span data-stu-id="36dcf-107">In the code sample below, when the <xref:System.Windows.Forms.CheckBox> control's <xref:System.Windows.Forms.CheckBox.CheckedChanged> event is raised, the form's <xref:System.Windows.Forms.Control.AllowDrop%2A> property is set to `false` if the check box is checked.</span></span> <span data-ttu-id="36dcf-108">Isso é útil para situações em que você deseja restringir a interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="36dcf-108">This is useful for situations where you want to restrict user interaction.</span></span>  
  
    ```vb  
    Private Sub CheckBox1_CheckedChanged(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles CheckBox1.CheckedChanged  
       ' Determine the CheckState of the check box.  
       If CheckBox1.CheckState = CheckState.Checked Then  
          ' If checked, do not allow items to be dragged onto the form.  
          Me.AllowDrop = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_CheckedChanged(object sender, System.EventArgs e)  
    {  
       // Determine the CheckState of the check box.  
       if (checkBox1.CheckState == CheckState.Checked)   
       {  
          // If checked, do not allow items to be dragged onto the form.  
          this.AllowDrop = false;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Determine the CheckState of the check box.  
          if (checkBox1->CheckState == CheckState::Checked)   
          {  
             // If checked, do not allow items to be dragged onto the form.  
             this->AllowDrop = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="36dcf-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36dcf-109">See Also</span></span>  
 <xref:System.Windows.Forms.CheckBox>  
 [<span data-ttu-id="36dcf-110">Visão geral do controle CheckBox</span><span class="sxs-lookup"><span data-stu-id="36dcf-110">CheckBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="36dcf-111">Como responder a cliques em CheckBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36dcf-111">How to: Respond to Windows Forms CheckBox Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [<span data-ttu-id="36dcf-112">Controle CheckBox</span><span class="sxs-lookup"><span data-stu-id="36dcf-112">CheckBox Control</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
