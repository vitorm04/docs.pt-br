---
title: definir opções com controles de caixa de seleção
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- checked
helpviewer_keywords:
- CheckBox control [Windows Forms], checked state
- check boxes [Windows Forms], using to set options
- CheckBox control [Windows Forms], using to set options
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
ms.openlocfilehash: 00b467836d8e60aeee51a010a6384abf7dd73c56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141842"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a><span data-ttu-id="853c8-102">Como definir opções com controles CheckBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="853c8-102">How to: Set Options with Windows Forms CheckBox Controls</span></span>
<span data-ttu-id="853c8-103">Um controle <xref:System.Windows.Forms.CheckBox> do Windows Forms é usado para dar aos usuários opções True/False ou Yes/No.</span><span class="sxs-lookup"><span data-stu-id="853c8-103">A Windows Forms <xref:System.Windows.Forms.CheckBox> control is used to give users True/False or Yes/No options.</span></span> <span data-ttu-id="853c8-104">O controle exibe uma marca de seleção quando é selecionada.</span><span class="sxs-lookup"><span data-stu-id="853c8-104">The control displays a check mark when it is selected.</span></span>  
  
### <a name="to-set-options-with-checkbox-controls"></a><span data-ttu-id="853c8-105">Para definir opções com controles do CheckBox</span><span class="sxs-lookup"><span data-stu-id="853c8-105">To set options with CheckBox controls</span></span>  
  
1. <span data-ttu-id="853c8-106">Examine o valor <xref:System.Windows.Forms.CheckBox.Checked%2A> da propriedade para determinar seu estado e use esse valor para definir uma opção.</span><span class="sxs-lookup"><span data-stu-id="853c8-106">Examine the value of the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine its state, and use that value to set an option.</span></span>  
  
     <span data-ttu-id="853c8-107">Na amostra de código <xref:System.Windows.Forms.CheckBox> abaixo, <xref:System.Windows.Forms.CheckBox.CheckedChanged> quando o evento do controle <xref:System.Windows.Forms.Control.AllowDrop%2A> é levantado, a propriedade do formulário é definida para `false` se a caixa de seleção for verificada.</span><span class="sxs-lookup"><span data-stu-id="853c8-107">In the code sample below, when the <xref:System.Windows.Forms.CheckBox> control's <xref:System.Windows.Forms.CheckBox.CheckedChanged> event is raised, the form's <xref:System.Windows.Forms.Control.AllowDrop%2A> property is set to `false` if the check box is checked.</span></span> <span data-ttu-id="853c8-108">Isso é útil para situações em que você deseja restringir a interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="853c8-108">This is useful for situations where you want to restrict user interaction.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="853c8-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="853c8-109">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="853c8-110">Visão geral do controle CheckBox</span><span class="sxs-lookup"><span data-stu-id="853c8-110">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="853c8-111">Como responder a cliques em CheckBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="853c8-111">How to: Respond to Windows Forms CheckBox Clicks</span></span>](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [<span data-ttu-id="853c8-112">Controle da caixa de seleção</span><span class="sxs-lookup"><span data-stu-id="853c8-112">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
