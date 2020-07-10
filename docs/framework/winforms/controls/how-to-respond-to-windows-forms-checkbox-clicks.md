---
title: responder a cliques em caixa de seleção
description: Saiba como programar seu aplicativo Windows Forms para executar alguma ação, dependendo do estado da caixa de seleção.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Click event [Windows Forms], CheckBox control
- CheckBox control [Windows Forms], Click events
- events [Windows Forms], Click events
- double-clicks
- check boxes [Windows Forms], responding to events
ms.assetid: c39f901e-8899-43b6-aa31-939cbf7089fb
ms.openlocfilehash: 58944bc421f990343b6c58484aaab3d79c8bda5e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174491"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="7e341-103">Como responder a cliques CheckBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e341-103">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="7e341-104">Sempre que um usuário clicar em um controle de Windows Forms <xref:System.Windows.Forms.CheckBox> , o <xref:System.Windows.Forms.Control.Click> evento ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="7e341-104">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="7e341-105">Você pode programar seu aplicativo para realizar alguma ação dependendo do estado da caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="7e341-105">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="7e341-106">Para responder a cliques na caixa de seleção</span><span class="sxs-lookup"><span data-stu-id="7e341-106">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="7e341-107">No <xref:System.Windows.Forms.Control.Click> manipulador de eventos, use a <xref:System.Windows.Forms.CheckBox.Checked%2A> propriedade para determinar o estado do controle e execute qualquer ação necessária.</span><span class="sxs-lookup"><span data-stu-id="7e341-107">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       ' The CheckBox control's Text property is changed each time the
       ' control is clicked, indicating a checked or unchecked state.  
       If CheckBox1.Checked = True Then  
          CheckBox1.Text = "Checked"  
       Else  
          CheckBox1.Text = "Unchecked"  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       // The CheckBox control's Text property is changed each time the
       // control is clicked, indicating a checked or unchecked state.  
       if (checkBox1.Checked)  
       {  
          checkBox1.Text = "Checked";  
       }  
       else  
       {  
          checkBox1.Text = "Unchecked";  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if (checkBox1->Checked)  
          {  
             checkBox1->Text = "Checked";  
          }  
          else  
          {  
             checkBox1->Text = "Unchecked";  
          }  
       }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="7e341-108">Se o usuário tentar clicar duas vezes no <xref:System.Windows.Forms.CheckBox> controle, cada clique será processado separadamente; ou seja, o controle não <xref:System.Windows.Forms.CheckBox> oferece suporte ao evento de clique duplo.</span><span class="sxs-lookup"><span data-stu-id="7e341-108">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7e341-109">Quando a <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> propriedade é `true` (o padrão), <xref:System.Windows.Forms.CheckBox> é selecionada ou desmarcada automaticamente quando clicada.</span><span class="sxs-lookup"><span data-stu-id="7e341-109">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="7e341-110">Caso contrário, você deve definir manualmente a <xref:System.Windows.Forms.CheckBox.Checked%2A> propriedade quando o <xref:System.Windows.Forms.Control.Click> evento ocorrer.</span><span class="sxs-lookup"><span data-stu-id="7e341-110">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="7e341-111">Você também pode usar o <xref:System.Windows.Forms.CheckBox> controle para determinar um curso de ação.</span><span class="sxs-lookup"><span data-stu-id="7e341-111">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="7e341-112">Para determinar um curso de ação quando uma caixa de seleção é clicada</span><span class="sxs-lookup"><span data-stu-id="7e341-112">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="7e341-113">Use uma instrução Case para consultar o valor da <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriedade para determinar um curso de ação.</span><span class="sxs-lookup"><span data-stu-id="7e341-113">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="7e341-114">Quando a <xref:System.Windows.Forms.CheckBox.ThreeState%2A> propriedade é definida como `true` , a <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriedade pode retornar três valores possíveis, que representam a caixa que está sendo marcada, a caixa que está sendo desmarcada ou um terceiro estado indeterminado no qual a caixa é exibida com uma aparência esmaecida para indicar que a opção não está disponível.</span><span class="sxs-lookup"><span data-stu-id="7e341-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       Select Case CheckBox1.CheckState  
          Case CheckState.Checked  
             ' Code for checked state.  
          Case CheckState.Unchecked  
             ' Code for unchecked state.  
          Case CheckState.Indeterminate  
             ' Code for indeterminate state.  
       End Select
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       switch(checkBox1.CheckState)  
       {  
          case CheckState.Checked:  
             // Code for checked state.  
             break;  
          case CheckState.Unchecked:  
             // Code for unchecked state.  
             break;  
          case CheckState.Indeterminate:  
             // Code for indeterminate state.  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          switch(checkBox1->CheckState) {  
             case CheckState::Checked:  
                // Code for checked state.  
                break;  
             case CheckState::Unchecked:  
                // Code for unchecked state.  
                break;  
             case CheckState::Indeterminate:  
                // Code for indeterminate state.  
                break;  
          }  
       }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="7e341-115">Quando a <xref:System.Windows.Forms.CheckBox.ThreeState%2A> propriedade é definida como `true` , a <xref:System.Windows.Forms.CheckBox.Checked%2A> propriedade retorna `true` para <xref:System.Windows.Forms.CheckState.Checked> e <xref:System.Windows.Forms.CheckState.Indeterminate> .</span><span class="sxs-lookup"><span data-stu-id="7e341-115">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e341-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="7e341-116">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="7e341-117">Visão geral do controle CheckBox</span><span class="sxs-lookup"><span data-stu-id="7e341-117">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="7e341-118">Como definir opções com controles CheckBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e341-118">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="7e341-119">Controle de caixa de seleção</span><span class="sxs-lookup"><span data-stu-id="7e341-119">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
