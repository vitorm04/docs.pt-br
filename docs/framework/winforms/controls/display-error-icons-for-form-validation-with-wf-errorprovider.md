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
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>Como exibir ícones de erro para validação do formulário com o componente ErrorProvider dos Windows Forms
Você pode usar um componente Windows Forms <xref:System.Windows.Forms.ErrorProvider> para exibir um ícone de erro quando o usuário insere dados inválidos. Você deve ter pelo menos dois controles no formulário para alternar entre eles e, portanto, invocar o código de validação.  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>Para exibir um ícone de erro quando o valor do controle é inválido  
  
1. Adicione dois controles, por exemplo, caixas de texto, a um Windows Form.  
  
2. Adicione um componente <xref:System.Windows.Forms.ErrorProvider> ao formulário.  
  
3. Selecione o primeiro controle e adicione o código ao seu manipulador de eventos <xref:System.Windows.Forms.Control.Validating>. Para que esse código seja executado corretamente, o procedimento deve estar conectado ao evento. Para saber mais, veja [Como criar manipuladores de eventos em tempo de execução para formulários dos Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     O código a seguir testa a validade dos dados que o usuário inseriu; Se os dados forem inválidos, o método <xref:System.Windows.Forms.ErrorProvider.SetError%2A> será chamado. O primeiro argumento do método <xref:System.Windows.Forms.ErrorProvider.SetError%2A> especifica qual controle exibirá o ícone ao lado de. O segundo argumento é o texto do erro a ser exibido.  
  
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
  
     (Visual C#, Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. Execute o projeto. Digite dados inválidos (neste exemplo, não numéricos) no primeiro controle e alterne para o segundo. Quando o ícone de erro for exibido, aponte para ele com o ponteiro do mouse para ver o texto do erro.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [Visão geral do componente ErrorProvider](errorprovider-component-overview-windows-forms.md)
- [Como exibir erros dentro de um DataSet com o componente ErrorProvider dos Windows Forms](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
