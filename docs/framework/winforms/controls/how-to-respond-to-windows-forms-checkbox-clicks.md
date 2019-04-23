---
title: 'Como: Responder a cliques CheckBox do Windows Forms'
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
ms.openlocfilehash: ce616f45ceaa3db117c6981d2987ac09bba7b3fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319892"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="01bfa-102">Como: Responder a cliques CheckBox do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01bfa-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="01bfa-103">Sempre que um usuário clica em um Windows Forms <xref:System.Windows.Forms.CheckBox> controle, o <xref:System.Windows.Forms.Control.Click> evento ocorre.</span><span class="sxs-lookup"><span data-stu-id="01bfa-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="01bfa-104">Você pode programar seu aplicativo para realizar alguma ação dependendo do estado da caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="01bfa-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="01bfa-105">Para responder a cliques na caixa de seleção</span><span class="sxs-lookup"><span data-stu-id="01bfa-105">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="01bfa-106">No <xref:System.Windows.Forms.Control.Click> manipulador de eventos, use o <xref:System.Windows.Forms.CheckBox.Checked%2A> propriedade para determinar o estado do controle e executar qualquer ação necessária.</span><span class="sxs-lookup"><span data-stu-id="01bfa-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    >  <span data-ttu-id="01bfa-107">Se o usuário tentar clicar duas vezes o <xref:System.Windows.Forms.CheckBox> controle, cada clique será processado separadamente; ou seja, o <xref:System.Windows.Forms.CheckBox> controle não dá suporte para o evento de clique duplo.</span><span class="sxs-lookup"><span data-stu-id="01bfa-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="01bfa-108">Quando o <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> é de propriedade `true` (o padrão), o <xref:System.Windows.Forms.CheckBox> é automaticamente selecionada ou desmarcada quando ele for clicado.</span><span class="sxs-lookup"><span data-stu-id="01bfa-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="01bfa-109">Caso contrário, você deve definir manualmente as <xref:System.Windows.Forms.CheckBox.Checked%2A> propriedade quando o <xref:System.Windows.Forms.Control.Click> evento ocorre.</span><span class="sxs-lookup"><span data-stu-id="01bfa-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="01bfa-110">Você também pode usar o <xref:System.Windows.Forms.CheckBox> controle para determinar um curso de ação.</span><span class="sxs-lookup"><span data-stu-id="01bfa-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="01bfa-111">Para determinar um curso de ação quando uma caixa de seleção é clicada</span><span class="sxs-lookup"><span data-stu-id="01bfa-111">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="01bfa-112">Use uma instrução case para consultar o valor da <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriedade para determinar um curso de ação.</span><span class="sxs-lookup"><span data-stu-id="01bfa-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="01bfa-113">Quando o <xref:System.Windows.Forms.CheckBox.ThreeState%2A> estiver definida como `true`, o <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriedade pode retornar três valores possíveis, que representam a caixa que está sendo verificada, a caixa desmarcada ou um terceiro estado indeterminado no qual a caixa é exibida com um esmaecido aparência para indicar que a opção não está disponível.</span><span class="sxs-lookup"><span data-stu-id="01bfa-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    >  <span data-ttu-id="01bfa-114">Quando o <xref:System.Windows.Forms.CheckBox.ThreeState%2A> estiver definida como `true`, o <xref:System.Windows.Forms.CheckBox.Checked%2A> propriedade retorna `true` para ambos <xref:System.Windows.Forms.CheckState.Checked> e <xref:System.Windows.Forms.CheckState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="01bfa-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01bfa-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01bfa-115">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="01bfa-116">Visão geral do controle CheckBox</span><span class="sxs-lookup"><span data-stu-id="01bfa-116">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="01bfa-117">Como: Definir opções com controles CheckBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01bfa-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="01bfa-118">Controle CheckBox</span><span class="sxs-lookup"><span data-stu-id="01bfa-118">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
