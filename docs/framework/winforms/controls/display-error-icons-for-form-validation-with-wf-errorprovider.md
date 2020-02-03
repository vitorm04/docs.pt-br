---
title: Exibir ícones de erro para validação de formulário com o componente ErrorProvider
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error icons
- ErrorProvider component [Windows Forms], displaying error icons
- error messages [Windows Forms], displaying icons
ms.assetid: 3b681a32-9db4-497b-a34b-34980eabee46
ms.openlocfilehash: a1e346e332db489351f59c9a0c03ae731baf3dc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745913"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="69b35-102">Como exibir ícones de erro para validação do formulário com o componente ErrorProvider dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="69b35-102">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="69b35-103">Você pode usar um componente Windows Forms <xref:System.Windows.Forms.ErrorProvider> para exibir um ícone de erro quando o usuário insere dados inválidos.</span><span class="sxs-lookup"><span data-stu-id="69b35-103">You can use a Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to display an error icon when the user enters invalid data.</span></span> <span data-ttu-id="69b35-104">Você deve ter pelo menos dois controles no formulário para alternar entre eles e, portanto, invocar o código de validação.</span><span class="sxs-lookup"><span data-stu-id="69b35-104">You must have at least two controls on the form in order to tab between them and thereby invoke the validation code.</span></span>  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a><span data-ttu-id="69b35-105">Para exibir um ícone de erro quando o valor do controle é inválido</span><span class="sxs-lookup"><span data-stu-id="69b35-105">To display an error icon when a control's value is invalid</span></span>  
  
1. <span data-ttu-id="69b35-106">Adicione dois controles, por exemplo, caixas de texto, a um Windows Form.</span><span class="sxs-lookup"><span data-stu-id="69b35-106">Add two controls — for example, text boxes — to a Windows Form.</span></span>  
  
2. <span data-ttu-id="69b35-107">Adicione um componente <xref:System.Windows.Forms.ErrorProvider> ao formulário.</span><span class="sxs-lookup"><span data-stu-id="69b35-107">Add an <xref:System.Windows.Forms.ErrorProvider> component to the form.</span></span>  
  
3. <span data-ttu-id="69b35-108">Selecione o primeiro controle e adicione o código ao seu manipulador de eventos <xref:System.Windows.Forms.Control.Validating>.</span><span class="sxs-lookup"><span data-stu-id="69b35-108">Select the first control and add code to its <xref:System.Windows.Forms.Control.Validating> event handler.</span></span> <span data-ttu-id="69b35-109">Para que esse código seja executado corretamente, o procedimento deve estar conectado ao evento.</span><span class="sxs-lookup"><span data-stu-id="69b35-109">In order for this code to run properly, the procedure must be connected to the event.</span></span> <span data-ttu-id="69b35-110">Para saber mais, veja [Como criar manipuladores de eventos em tempo de execução para formulários dos Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="69b35-110">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="69b35-111">O código a seguir testa a validade dos dados que o usuário inseriu; Se os dados forem inválidos, o método <xref:System.Windows.Forms.ErrorProvider.SetError%2A> será chamado.</span><span class="sxs-lookup"><span data-stu-id="69b35-111">The following code tests the validity of the data the user has entered; if the data is invalid, the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method is called.</span></span> <span data-ttu-id="69b35-112">O primeiro argumento do método <xref:System.Windows.Forms.ErrorProvider.SetError%2A> especifica qual controle exibirá o ícone ao lado de.</span><span class="sxs-lookup"><span data-stu-id="69b35-112">The first argument of the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method specifies which control to display the icon next to.</span></span> <span data-ttu-id="69b35-113">O segundo argumento é o texto do erro a ser exibido.</span><span class="sxs-lookup"><span data-stu-id="69b35-113">The second argument is the error text to display.</span></span>  
  
    ```vb  
    Private Sub TextBox1_Validating(ByVal Sender As Object, _  
       ByVal e As System.ComponentModel.CancelEventArgs) Handles _  
       TextBox1.Validating  
          If Not IsNumeric(TextBox1.Text) Then  
             ErrorProvider1.SetError(TextBox1, "Not a numeric value.")  
          Else  
             ' Clear the error.  
             ErrorProvider1.SetError(TextBox1, "")  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void textBox1_Validating (object sender,  
       System.ComponentModel.CancelEventArgs e)  
    {  
       try  
       {  
          int x = Int32.Parse(textBox1.Text);  
          errorProvider1.SetError(textBox1, "");  
       }  
       catch (Exception ex)  
       {  
          errorProvider1.SetError(textBox1, "Not an integer value.");  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void textBox1_Validating(System::Object ^  sender,  
          System::ComponentModel::CancelEventArgs ^  e)  
       {  
          try  
          {  
             int x = Int32::Parse(textBox1->Text);  
             errorProvider1->SetError(textBox1, "");  
          }  
          catch (System::Exception ^ ex)  
          {  
             errorProvider1->SetError(textBox1, "Not an integer value.");  
          }  
       }  
    ```  
  
     <span data-ttu-id="69b35-114">(Visual C#, Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="69b35-114">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. <span data-ttu-id="69b35-115">Execute o projeto.</span><span class="sxs-lookup"><span data-stu-id="69b35-115">Run the project.</span></span> <span data-ttu-id="69b35-116">Digite dados inválidos (neste exemplo, não numéricos) no primeiro controle e alterne para o segundo.</span><span class="sxs-lookup"><span data-stu-id="69b35-116">Type invalid (in this example, non-numeric) data into the first control, and then tab to the second.</span></span> <span data-ttu-id="69b35-117">Quando o ícone de erro for exibido, aponte para ele com o ponteiro do mouse para ver o texto do erro.</span><span class="sxs-lookup"><span data-stu-id="69b35-117">When the error icon is displayed, point at it with the mouse pointer to see the error text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b35-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69b35-118">See also</span></span>

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [<span data-ttu-id="69b35-119">Visão geral do componente ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="69b35-119">ErrorProvider Component Overview</span></span>](errorprovider-component-overview-windows-forms.md)
- [<span data-ttu-id="69b35-120">Como exibir erros dentro de um DataSet com o componente ErrorProvider dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="69b35-120">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
