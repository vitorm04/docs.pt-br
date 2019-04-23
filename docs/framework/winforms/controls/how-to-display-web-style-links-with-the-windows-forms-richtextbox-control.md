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
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="13b45-102">Como: Exibir links em estilo da Web com o controle RichTextBox do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="13b45-102">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="13b45-103">Os formulários do Windows <xref:System.Windows.Forms.RichTextBox> controle pode exibir links da Web como coloridos e sublinhados.</span><span class="sxs-lookup"><span data-stu-id="13b45-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display Web links as colored and underlined.</span></span> <span data-ttu-id="13b45-104">Você pode gravar o código que abre uma janela do navegador mostrando o site da Web especificado no texto do link quando o link é clicado.</span><span class="sxs-lookup"><span data-stu-id="13b45-104">You can write code that opens a browser window showing the Web site specified in the link text when the link is clicked.</span></span>  
  
### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a><span data-ttu-id="13b45-105">Para vincular a uma página da Web com o controle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="13b45-105">To link to a Web page with the RichTextBox control</span></span>  
  
1. <span data-ttu-id="13b45-106">Defina as <xref:System.Windows.Forms.RichTextBox.Text%2A> propriedade para uma cadeia de caracteres que inclui uma URL válida (por exemplo, "http://www.microsoft.com/").</span><span class="sxs-lookup"><span data-stu-id="13b45-106">Set the <xref:System.Windows.Forms.RichTextBox.Text%2A> property to a string that includes a valid URL (for example, "http://www.microsoft.com/").</span></span>  
  
2. <span data-ttu-id="13b45-107">Verifique se o <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> estiver definida como `true` (o padrão).</span><span class="sxs-lookup"><span data-stu-id="13b45-107">Make sure the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property is set to `true` (the default).</span></span>  
  
3. <span data-ttu-id="13b45-108">Criar uma nova instância global do <xref:System.Diagnostics.Process> objeto.</span><span class="sxs-lookup"><span data-stu-id="13b45-108">Create a new global instance of the <xref:System.Diagnostics.Process> object.</span></span>  
  
4. <span data-ttu-id="13b45-109">Escrever um manipulador de eventos para o <xref:System.Windows.Forms.RichTextBox.LinkClicked> eventos que envia ao navegador o texto desejado.</span><span class="sxs-lookup"><span data-stu-id="13b45-109">Write an event handler for the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event that sends the browser the desired text.</span></span>  
  
     <span data-ttu-id="13b45-110">No exemplo a seguir, o <xref:System.Windows.Forms.RichTextBox.LinkClicked> evento abre uma instância do Internet Explorer para a URL especificada na <xref:System.Windows.Forms.RichTextBox.Text%2A> propriedade do <xref:System.Windows.Forms.RichTextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="13b45-110">In the example below, the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event opens an instance of Internet Explorer to the URL specified in the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="13b45-111">Este exemplo pressupõe um formulário com um <xref:System.Windows.Forms.RichTextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="13b45-111">This example assumes a form with a <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="13b45-112">Na chamada a <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> método, você encontrará um <xref:System.Security.SecurityException> exceção se você estiver executando o código em um contexto de confiança parcial devido a privilégios insuficientes.</span><span class="sxs-lookup"><span data-stu-id="13b45-112">In calling the <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> method, you will encounter a <xref:System.Security.SecurityException> exception if you are running the code in a partial-trust context because of insufficient privileges.</span></span> <span data-ttu-id="13b45-113">Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="13b45-113">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>  
  
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
  
     <span data-ttu-id="13b45-114">([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]), Você deverá inicializar processo `p`, que pode ser feito incluindo a instrução a seguir no construtor do formulário:</span><span class="sxs-lookup"><span data-stu-id="13b45-114">([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) You must initialize process `p`, which you can do by including the following statement in the constructor of your form:</span></span>  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     <span data-ttu-id="13b45-115">(Visual c#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="13b45-115">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="13b45-116">É importante parar imediatamente o processo que você criou quando terminar de trabalhar com ele.</span><span class="sxs-lookup"><span data-stu-id="13b45-116">It is important to immediately stop the process you have created once you have finished working with it.</span></span> <span data-ttu-id="13b45-117">No que se refere ao código apresentado acima, o código para interromper o processo pode se parecer com isso:</span><span class="sxs-lookup"><span data-stu-id="13b45-117">Referring to the code presented above, your code to stop the process might look like this:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="13b45-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13b45-118">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="13b45-119">Controle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="13b45-119">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="13b45-120">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="13b45-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
