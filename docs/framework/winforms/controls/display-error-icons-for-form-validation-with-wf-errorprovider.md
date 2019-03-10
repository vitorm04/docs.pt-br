---
title: 'Como: Exibir ícones de erro para validação do formulário com o componente do Windows Forms ErrorProvider'
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
ms.openlocfilehash: f676454849c37da8c0a5f944be05c3f6c95887b4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707632"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="9ccea-102">Como: Exibir ícones de erro para validação do formulário com o componente do Windows Forms ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="9ccea-102">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="9ccea-103">Você pode usar um Windows Forms <xref:System.Windows.Forms.ErrorProvider> componente para exibir um ícone de erro quando o usuário insere dados inválidos.</span><span class="sxs-lookup"><span data-stu-id="9ccea-103">You can use a Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to display an error icon when the user enters invalid data.</span></span> <span data-ttu-id="9ccea-104">Você deve ter pelo menos dois controles no formulário para alternar entre eles e, portanto, invocar o código de validação.</span><span class="sxs-lookup"><span data-stu-id="9ccea-104">You must have at least two controls on the form in order to tab between them and thereby invoke the validation code.</span></span>  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a><span data-ttu-id="9ccea-105">Para exibir um ícone de erro quando o valor do controle é inválido</span><span class="sxs-lookup"><span data-stu-id="9ccea-105">To display an error icon when a control's value is invalid</span></span>  
  
1.  <span data-ttu-id="9ccea-106">Adicione dois controles, por exemplo, caixas de texto, a um Windows Form.</span><span class="sxs-lookup"><span data-stu-id="9ccea-106">Add two controls — for example, text boxes — to a Windows Form.</span></span>  
  
2.  <span data-ttu-id="9ccea-107">Adicionar um <xref:System.Windows.Forms.ErrorProvider> componente para o formulário.</span><span class="sxs-lookup"><span data-stu-id="9ccea-107">Add an <xref:System.Windows.Forms.ErrorProvider> component to the form.</span></span>  
  
3.  <span data-ttu-id="9ccea-108">Selecione o primeiro controle e adicione código ao seu <xref:System.Windows.Forms.Control.Validating> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="9ccea-108">Select the first control and add code to its <xref:System.Windows.Forms.Control.Validating> event handler.</span></span> <span data-ttu-id="9ccea-109">Para que esse código seja executado corretamente, o procedimento deve estar conectado ao evento.</span><span class="sxs-lookup"><span data-stu-id="9ccea-109">In order for this code to run properly, the procedure must be connected to the event.</span></span> <span data-ttu-id="9ccea-110">Para obter mais informações, confira [Como: Criar manipuladores de eventos em tempo de execução para formulários do Windows](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9ccea-110">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="9ccea-111">O código a seguir testa a validade dos dados que o usuário inseriu; Se os dados forem inválidos, o <xref:System.Windows.Forms.ErrorProvider.SetError%2A> método é chamado.</span><span class="sxs-lookup"><span data-stu-id="9ccea-111">The following code tests the validity of the data the user has entered; if the data is invalid, the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method is called.</span></span> <span data-ttu-id="9ccea-112">O primeiro argumento do <xref:System.Windows.Forms.ErrorProvider.SetError%2A> método Especifica que o controle para exibir o ícone ao lado.</span><span class="sxs-lookup"><span data-stu-id="9ccea-112">The first argument of the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method specifies which control to display the icon next to.</span></span> <span data-ttu-id="9ccea-113">O segundo argumento é o texto do erro a ser exibido.</span><span class="sxs-lookup"><span data-stu-id="9ccea-113">The second argument is the error text to display.</span></span>  
  
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
  
     <span data-ttu-id="9ccea-114">(Visual c#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="9ccea-114">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4.  <span data-ttu-id="9ccea-115">Execute o projeto.</span><span class="sxs-lookup"><span data-stu-id="9ccea-115">Run the project.</span></span> <span data-ttu-id="9ccea-116">Digite dados inválidos (neste exemplo, não numéricos) no primeiro controle e alterne para o segundo.</span><span class="sxs-lookup"><span data-stu-id="9ccea-116">Type invalid (in this example, non-numeric) data into the first control, and then tab to the second.</span></span> <span data-ttu-id="9ccea-117">Quando o ícone de erro for exibido, aponte para ele com o ponteiro do mouse para ver o texto do erro.</span><span class="sxs-lookup"><span data-stu-id="9ccea-117">When the error icon is displayed, point at it with the mouse pointer to see the error text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ccea-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ccea-118">See also</span></span>
- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [<span data-ttu-id="9ccea-119">Visão geral do componente ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="9ccea-119">ErrorProvider Component Overview</span></span>](errorprovider-component-overview-windows-forms.md)
- [<span data-ttu-id="9ccea-120">Como: Exibir erros dentro de um conjunto de dados com o componente do Windows Forms ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="9ccea-120">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
