---
title: 'Como: Exibir links em estilo da Web com o controle RichTextBox do Windows Forms'
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
ms.openlocfilehash: faaa48051c80b6dfd330f15f72a38297ff2d1b9f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59301874"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a>Como: Exibir links em estilo da Web com o controle RichTextBox do Windows Forms
Os formulários do Windows <xref:System.Windows.Forms.RichTextBox> controle pode exibir links da Web como coloridos e sublinhados. Você pode gravar o código que abre uma janela do navegador mostrando o site da Web especificado no texto do link quando o link é clicado.  
  
### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a>Para vincular a uma página da Web com o controle RichTextBox  
  
1. Defina as <xref:System.Windows.Forms.RichTextBox.Text%2A> propriedade para uma cadeia de caracteres que inclui uma URL válida (por exemplo, "http://www.microsoft.com/").  
  
2. Verifique se o <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> estiver definida como `true` (o padrão).  
  
3. Criar uma nova instância global do <xref:System.Diagnostics.Process> objeto.  
  
4. Escrever um manipulador de eventos para o <xref:System.Windows.Forms.RichTextBox.LinkClicked> eventos que envia ao navegador o texto desejado.  
  
     No exemplo a seguir, o <xref:System.Windows.Forms.RichTextBox.LinkClicked> evento abre uma instância do Internet Explorer para a URL especificada na <xref:System.Windows.Forms.RichTextBox.Text%2A> propriedade do <xref:System.Windows.Forms.RichTextBox> controle. Este exemplo pressupõe um formulário com um <xref:System.Windows.Forms.RichTextBox> controle.  
  
    > [!IMPORTANT]
    >  Na chamada a <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> método, você encontrará um <xref:System.Security.SecurityException> exceção se você estiver executando o código em um contexto de confiança parcial devido a privilégios insuficientes. Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../misc/code-access-security-basics.md).  
  
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
  
     ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]), Você deverá inicializar processo `p`, que pode ser feito incluindo a instrução a seguir no construtor do formulário:  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     (Visual c#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
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
- [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)
