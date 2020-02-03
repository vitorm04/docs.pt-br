---
title: Exibir links de estilo da Web com controle RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying Web links
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], linking to Web pages
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
ms.openlocfilehash: 78a07a250744018f121b03f2973b1661ed6bf764
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745535"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a>Como exibir links em estilo da Web com o controle RichTextBox dos Windows Forms

O controle de <xref:System.Windows.Forms.RichTextBox> de Windows Forms pode exibir links da Web como coloridos e sublinhados. Você pode gravar o código que abre uma janela do navegador mostrando o site da Web especificado no texto do link quando o link é clicado.

### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a>Para vincular a uma página da Web com o controle RichTextBox

1. Defina a propriedade <xref:System.Windows.Forms.RichTextBox.Text%2A> como uma cadeia de caracteres que inclua uma URL válida (por exemplo, "http://www.microsoft.com/").

2. Verifique se a propriedade <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> está definida como `true` (o padrão).

3. Crie uma nova instância global do objeto <xref:System.Diagnostics.Process>.

4. Escreva um manipulador de eventos para o evento <xref:System.Windows.Forms.RichTextBox.LinkClicked> que envia ao navegador o texto desejado.

    No exemplo a seguir, o evento <xref:System.Windows.Forms.RichTextBox.LinkClicked> abre uma instância do Internet Explorer para a URL especificada na propriedade <xref:System.Windows.Forms.RichTextBox.Text%2A> do controle de <xref:System.Windows.Forms.RichTextBox>. Este exemplo assume um formulário com um controle de <xref:System.Windows.Forms.RichTextBox>.

    > [!IMPORTANT]
    > Ao chamar o método <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>, você encontrará uma exceção de <xref:System.Security.SecurityException> se estiver executando o código em um contexto de confiança parcial devido a privilégios insuficientes. Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../misc/code-access-security-basics.md).

    ```vb
    Public p As New System.Diagnostics.Process
    Private Sub RichTextBox1_LinkClicked _
       (ByVal sender As Object, ByVal e As _
       System.Windows.Forms.LinkClickedEventArgs) _
       Handles RichTextBox1.LinkClicked
          ' Call Process.Start method to open a browser
          ' with link text as URL.
          p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText)
    End Sub
    ```

    ```csharp
    public System.Diagnostics.Process p = new System.Diagnostics.Process();

    private void richTextBox1_LinkClicked(object sender,
    System.Windows.Forms.LinkClickedEventArgs e)
    {
       // Call Process.Start method to open a browser
       // with link text as URL.
       p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText);
    }
    ```

    ```cpp
    public:
       System::Diagnostics::Process ^ p;

    private:
       void richTextBox1_LinkClicked(System::Object ^  sender,
          System::Windows::Forms::LinkClickedEventArgs ^  e)
       {
          // Call Process.Start method to open a browser
          // with link text as URL.
          p = System::Diagnostics::Process::Start("IExplore.exe",
             e->LinkText);
       }
    ```

    (Visual C++) Você deve inicializar o processo `p`, que pode ser feito incluindo a seguinte instrução no construtor do seu formulário:

    ```cpp
    p = gcnew System::Diagnostics::Process();
    ```

    (Visual C#, Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.

    ```csharp
    this.richTextBox1.LinkClicked += new
       System.Windows.Forms.LinkClickedEventHandler
       (this.richTextBox1_LinkClicked);
    ```

    ```cpp
    this->richTextBox1->LinkClicked += gcnew
       System::Windows::Forms::LinkClickedEventHandler
       (this, &Form1::richTextBox1_LinkClicked);
    ```

    É importante parar imediatamente o processo que você criou quando terminar de trabalhar com ele. No que se refere ao código apresentado acima, o código para interromper o processo pode se parecer com isso:

    ```vb
    Public Sub StopWebProcess()
       p.Kill()
    End Sub
    ```

    ```csharp
    public void StopWebProcess()
    {
       p.Kill();
    }
    ```

    ```cpp
    public: void StopWebProcess()
    {
       p->Kill();
    }
    ```

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [Controle RichTextBox](richtextbox-control-windows-forms.md)
- [Controles a serem usados no Windows Forms](controls-to-use-on-windows-forms.md)
