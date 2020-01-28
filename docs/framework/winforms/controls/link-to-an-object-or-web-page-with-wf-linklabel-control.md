---
title: Link para um objeto ou página da Web com controle LinkLabel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Windows Forms, linking to objects
- Web page link control
- linking [Windows Forms], to other forms
- Windows Forms, linking to Web pages
- links [Windows Forms], to other forms
- LinkLabel control [Windows Forms], linking to object or Web page
- LinkLabel control [Windows Forms], examples
ms.assetid: 6c91c975-3cb7-4504-82f0-fc6255f8fb85
ms.openlocfilehash: 1669a9d6aba39b02d228c735701ca4e31c8f8291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745214"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>Como vincular a um objeto ou página da Web com o controle LinkLabel dos Windows Forms

O controle de <xref:System.Windows.Forms.LinkLabel> de Windows Forms permite que você crie links de estilo da Web no formulário. Ao clicar no link, é possível alterar sua cor para indicar que o link foi visitado. Para obter mais informações sobre como alterar a cor, consulte [Como alterar a aparência do controle LinkLabel do Windows Forms](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).

## <a name="linking-to-another-form"></a>Vinculando a outro formulário

#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>Vincular a outro formulário com um controle LinkLabel

1. Defina a propriedade <xref:System.Windows.Forms.LinkLabel.Text%2A> como uma legenda apropriada.

2. Defina a propriedade <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> para determinar qual parte da legenda será indicada como um link. Como isso é indicado depende das propriedades relacionadas à aparência do rótulo do link. O valor <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> é representado por um objeto <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> contendo dois números, a posição do caractere inicial e o número de caracteres. A propriedade <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> pode ser definida no janela Propriedades ou no código de uma maneira semelhante à seguinte:

    ```vb
    ' In this code example, the link area has been set to begin
    ' at the first character and extend for eight characters.
    ' You may need to modify this based on the text entered in Step 1.
    LinkLabel1.LinkArea = New LinkArea(0, 8)
    ```

    ```csharp
    // In this code example, the link area has been set to begin
    // at the first character and extend for eight characters.
    // You may need to modify this based on the text entered in Step 1.
    linkLabel1.LinkArea = new LinkArea(0,8);
    ```

    ```cpp
    // In this code example, the link area has been set to begin
    // at the first character and extend for eight characters.
    // You may need to modify this based on the text entered in Step 1.
    linkLabel1->LinkArea = LinkArea(0,8);
    ```

3. No manipulador de eventos <xref:System.Windows.Forms.LinkLabel.LinkClicked>, invoque o método <xref:System.Windows.Forms.Form.Show%2A> para abrir outro formulário no projeto e defina a propriedade <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> como `true`.

    > [!NOTE]
    > Uma instância da classe <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> transporta uma referência ao controle de <xref:System.Windows.Forms.LinkLabel> que foi clicado, portanto, não é necessário converter o objeto `sender`.

    ```vb
    Protected Sub LinkLabel1_LinkClicked(ByVal Sender As System.Object, _
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _
       Handles LinkLabel1.LinkClicked
       ' Show another form.
       Dim f2 As New Form()
       f2.Show
       LinkLabel1.LinkVisited = True
    End Sub
    ```

    ```csharp
    protected void linkLabel1_LinkClicked(object sender, System. Windows.Forms.LinkLabelLinkClickedEventArgs e)
    {
       // Show another form.
       Form f2 = new Form();
       f2.Show();
       linkLabel1.LinkVisited = true;
    }
    ```

    ```cpp
    private:
       void linkLabel1_LinkClicked(System::Object ^  sender,
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)
       {
          // Show another form.
          Form ^ f2 = new Form();
          f2->Show();
          linkLabel1->LinkVisited = true;
       }
    ```

## <a name="linking-to-a-web-page"></a>Vinculando a uma página da Web

O controle de <xref:System.Windows.Forms.LinkLabel> também pode ser usado para exibir uma página da Web com o navegador padrão.

#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>Abrir o Internet Explorer e vincular a uma página da Web com um controle LinkLabel

1. Defina a propriedade <xref:System.Windows.Forms.LinkLabel.Text%2A> como uma legenda apropriada.

2. Defina a propriedade <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> para determinar qual parte da legenda será indicada como um link.

3. No manipulador de eventos <xref:System.Windows.Forms.LinkLabel.LinkClicked>, no meio de um bloco de tratamento de exceções, chame um segundo procedimento que defina a propriedade <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> como `true` e use o método <xref:System.Diagnostics.Process.Start%2A> para iniciar o navegador padrão com uma URL. Para usar o método <xref:System.Diagnostics.Process.Start%2A>, você precisa adicionar uma referência ao namespace <xref:System.Diagnostics?displayProperty=nameWithType>.

    > [!IMPORTANT]
    > Se o código abaixo for executado em um ambiente de confiança parcial (como em uma unidade compartilhada), o compilador JIT falhará quando o método `VisitLink` for chamado. A instrução `System.Diagnostics.Process.Start` causa uma demanda de link que falha. Ao capturar a exceção quando o método `VisitLink` é chamado, o código a seguir garante que, se o compilador JIT falhar, o erro será tratado normalmente.

    ```vb
    Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, _
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _
       Handles LinkLabel1.LinkClicked
       Try
          VisitLink()
       Catch ex As Exception
          ' The error message
          MessageBox.Show("Unable to open link that was clicked.")
       End Try
    End Sub

    Sub VisitLink()
       ' Change the color of the link text by setting LinkVisited
       ' to True.
       LinkLabel1.LinkVisited = True
       ' Call the Process.Start method to open the default browser
       ' with a URL:
       System.Diagnostics.Process.Start("http://www.microsoft.com")
    End Sub
    ```

    ```csharp
    private void linkLabel1_LinkClicked(object sender, System.Windows.Forms.LinkLabelLinkClickedEventArgs e)
    {
       try
       {
          VisitLink();
       }
       catch (Exception ex )
       {
          MessageBox.Show("Unable to open link that was clicked.");
       }
    }

    private void VisitLink()
    {
       // Change the color of the link text by setting LinkVisited
       // to true.
       linkLabel1.LinkVisited = true;
       //Call the Process.Start method to open the default browser
       //with a URL:
       System.Diagnostics.Process.Start("http://www.microsoft.com");
    }
    ```

    ```cpp
    private:
       void linkLabel1_LinkClicked(System::Object ^  sender,
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)
       {
          try
          {
             VisitLink();
          }
          catch (Exception ^ ex)
          {
             MessageBox::Show("Unable to open link that was clicked.");
          }
       }
    private:
       void VisitLink()
       {
          // Change the color of the link text by setting LinkVisited
          // to true.
          linkLabel1->LinkVisited = true;
          // Call the Process.Start method to open the default browser
          // with a URL:
          System::Diagnostics::Process::Start("http://www.microsoft.com");
       }
    ```

## <a name="see-also"></a>Veja também

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- [Visão geral do controle LinkLabel](linklabel-control-overview-windows-forms.md)
- [Como alterar a aparência do controle LinkLabel dos Windows Forms](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [Controle LinkLabel](linklabel-control-windows-forms.md)
