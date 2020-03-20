---
title: 'Instruções passo a passo: trabalhando com o controle MaskedTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- input [Windows Forms], controlling to ensure validity
- MaskedTextBox control [Windows Forms], walkthroughs
- MaskedTextBox control [Windows Forms], validation
- user input [Windows Forms], controlling
- text [Windows Forms], controls for input
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
ms.openlocfilehash: db32b3ec88a07747ea3e286af9f04edce3f1ba3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182069"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a>Instruções passo a passo: trabalhando com o controle MaskedTextBox
As tarefas ilustradas neste passo a passo incluem:  
  
- Inicializando <xref:System.Windows.Forms.MaskedTextBox> o controle  
  
- Usando <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> o manipulador de eventos para alertar o usuário quando um caractere não está de acordo com a máscara  
  
- Atribuir um tipo <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> à propriedade <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> e usar o manipulador de eventos para alertar o usuário quando o valor que ele está tentando comprometer não é válido para o tipo  
  
## <a name="creating-the-project-and-adding-a-control"></a>Criar o projeto e adicionar um controle  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a>Adicionar um controle MaskedTextBox ao seu formulário  
  
1. Abra o formulário no qual <xref:System.Windows.Forms.MaskedTextBox> deseja colocar o controle.  
  
2. Arraste <xref:System.Windows.Forms.MaskedTextBox> um controle da **caixa de ferramentas** para o seu formulário.  
  
3. Clique com o botão direito do mouse no controle e escolha **Propriedades**. Na janela **Propriedades**, selecione a propriedade **Máscara** e clique no botão de reticências **...** ao lado do nome da propriedade.  
  
4. Na caixa de diálogo **Máscara de Entrada**, selecione a máscara **Data abreviada** e clique em **OK**.  
  
5. Na janela **Propriedades,** defina a <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> propriedade como `true`. Essa propriedade faz com que um aviso sonoro curto soe sempre que o usuário tentar inserir um caractere que viola a definição da máscara.  
  
 Para obter um resumo dos caracteres que a propriedade Máscara suporta, consulte a seção Observações da <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriedade.  
  
## <a name="alert-the-user-to-input-errors"></a>Alertar o usuário de erros de entrada  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a>Adicionar uma dica de balão para entrada de máscara rejeitada  
  
1. Retorne à **caixa de** <xref:System.Windows.Forms.ToolTip> ferramentas e adicione um ao seu formulário.  
  
2. Crie um manipulador <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> de eventos <xref:System.Windows.Forms.ToolTip> para o evento que levanta o momento em que ocorre um erro de entrada. A dica de balão permanece visível por cinco segundos ou até que o usuário clique nele.  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
    ```  
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a>Alertar o usuário que um tipo que não é válido  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a>Adicionar uma dica de balão para tipos de dados inválidos  
  
1. No manipulador de <xref:System.Windows.Forms.Form.Load> eventos do formulário, <xref:System.Type> atribua um objeto representando o <xref:System.DateTime> tipo à propriedade do <xref:System.Windows.Forms.MaskedTextBox> <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> controle:  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2. Adicione um manipulador de eventos ao evento <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted>:  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.MaskedTextBox>
- [Controle MaskedTextBox](maskedtextbox-control-windows-forms.md)
