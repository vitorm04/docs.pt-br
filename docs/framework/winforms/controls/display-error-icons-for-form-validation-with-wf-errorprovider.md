---
title: 'Como: Exibir ícones de erro para validação de formulário com o componente ErrorProvider do Windows Forms'
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
ms.openlocfilehash: 2af8d3b9ea97b678c493de8a58d439b62f448387
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053706"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>Como: Exibir ícones de erro para validação de formulário com o componente ErrorProvider do Windows Forms
Você pode usar um Windows Forms <xref:System.Windows.Forms.ErrorProvider> componente para exibir um ícone de erro quando o usuário insere dados inválidos. Você deve ter pelo menos dois controles no formulário para alternar entre eles e, portanto, invocar o código de validação.  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>Para exibir um ícone de erro quando o valor do controle é inválido  
  
1. Adicione dois controles, por exemplo, caixas de texto, a um Windows Form.  
  
2. Adicionar um <xref:System.Windows.Forms.ErrorProvider> componente para o formulário.  
  
3. Selecione o primeiro controle e adicione código ao seu <xref:System.Windows.Forms.Control.Validating> manipulador de eventos. Para que esse código seja executado corretamente, o procedimento deve estar conectado ao evento. Para obter mais informações, confira [Como: Criar manipuladores de eventos em tempo de execução para formulários do Windows](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     O código a seguir testa a validade dos dados que o usuário inseriu; Se os dados forem inválidos, o <xref:System.Windows.Forms.ErrorProvider.SetError%2A> método é chamado. O primeiro argumento do <xref:System.Windows.Forms.ErrorProvider.SetError%2A> método Especifica que o controle para exibir o ícone ao lado. O segundo argumento é o texto do erro a ser exibido.  
  
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
- [Como: Exibir erros dentro de um conjunto de dados com o componente do Windows Forms ErrorProvider](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
