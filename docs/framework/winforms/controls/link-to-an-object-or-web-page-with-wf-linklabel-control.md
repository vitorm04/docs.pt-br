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
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a><span data-ttu-id="b0d2e-102">Como vincular a um objeto ou página da Web com o controle LinkLabel dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0d2e-102">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>

<span data-ttu-id="b0d2e-103">O controle de <xref:System.Windows.Forms.LinkLabel> de Windows Forms permite que você crie links de estilo da Web no formulário.</span><span class="sxs-lookup"><span data-stu-id="b0d2e-103">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to create Web-style links on your form.</span></span> <span data-ttu-id="b0d2e-104">Ao clicar no link, é possível alterar sua cor para indicar que o link foi visitado.</span><span class="sxs-lookup"><span data-stu-id="b0d2e-104">When the link is clicked, you can change its color to indicate the link has been visited.</span></span> <span data-ttu-id="b0d2e-105">Para obter mais informações sobre como alterar a cor, consulte [Como alterar a aparência do controle LinkLabel do Windows Forms](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span><span class="sxs-lookup"><span data-stu-id="b0d2e-105">For more information on changing the color, see [How to: Change the Appearance of the Windows Forms LinkLabel Control](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span></span>

## <a name="linking-to-another-form"></a><span data-ttu-id="b0d2e-106">Vinculando a outro formulário</span><span class="sxs-lookup"><span data-stu-id="b0d2e-106">Linking to Another Form</span></span>

#### <a name="to-link-to-another-form-with-a-linklabel-control"></a><span data-ttu-id="b0d2e-107">Vincular a outro formulário com um controle LinkLabel</span><span class="sxs-lookup"><span data-stu-id="b0d2e-107">To link to another form with a LinkLabel control</span></span>

1. <span data-ttu-id="b0d2e-108">Defina a propriedade <xref:System.Windows.Forms.LinkLabel.Text%2A> como uma legenda apropriada.</span><span class="sxs-lookup"><span data-stu-id="b0d2e-108">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>

2. <span data-ttu-id="b0d2e-109">Defina a propriedade <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> para determinar qual parte da legenda será indicada como um link.</span><span class="sxs-lookup"><span data-stu-id="b0d2e-109">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span> <span data-ttu-id="b0d2e-110">Como isso é indicado depende das propriedades relacionadas à aparência do rótulo do link.</span><span class="sxs-lookup"><span data-stu-id="b0d2e-110">How it is indicated depends on the appearance-related properties of the link label.</span></span> <span data-ttu-id="b0d2e-111">O valor <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> é representado por um objeto <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> contendo dois números, a posição do caractere inicial e o número de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b0d2e-111">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented by a <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> object containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="b0d2e-112">A propriedade <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> pode ser definida no janela Propriedades ou no código de uma maneira semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="b0d2e-112">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property can be set in the Properties window or in code in a manner similar to the following:</span></span>

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

3. <span data-ttu-id="b0d2e-113">No manipulador de eventos <xref:System.Windows.Forms.LinkLabel.LinkClicked>, invoque o método <xref:System.Windows.Forms.Form.Show%2A> para abrir outro formulário no projeto e defina a propriedade <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="b0d2e-113">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, invoke the <xref:System.Windows.Forms.Form.Show%2A> method to open another form in the project, and set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b0d2e-114">Uma instância da classe <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> transporta uma referência ao controle de <xref:System.Windows.Forms.LinkLabel> que foi clicado, portanto, não é necessário converter o objeto `sender`.</span><span class="sxs-lookup"><span data-stu-id="b0d2e-114">An instance of the <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> class carries a reference to the <xref:System.Windows.Forms.LinkLabel> control that was clicked, so there is no need to cast the `sender` object.</span></span>

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

## <a name="linking-to-a-web-page"></a><span data-ttu-id="b0d2e-115">Vinculando a uma página da Web</span><span class="sxs-lookup"><span data-stu-id="b0d2e-115">Linking to a Web Page</span></span>

<span data-ttu-id="b0d2e-116">O controle de <xref:System.Windows.Forms.LinkLabel> também pode ser usado para exibir uma página da Web com o navegador padrão.</span><span class="sxs-lookup"><span data-stu-id="b0d2e-116">The <xref:System.Windows.Forms.LinkLabel> control can also be used to display a Web page with the default browser.</span></span>

#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a><span data-ttu-id="b0d2e-117">Abrir o Internet Explorer e vincular a uma página da Web com um controle LinkLabel</span><span class="sxs-lookup"><span data-stu-id="b0d2e-117">To start Internet Explorer and link to a Web page with a LinkLabel control</span></span>

1. <span data-ttu-id="b0d2e-118">Defina a propriedade <xref:System.Windows.Forms.LinkLabel.Text%2A> como uma legenda apropriada.</span><span class="sxs-lookup"><span data-stu-id="b0d2e-118">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>

2. <span data-ttu-id="b0d2e-119">Defina a propriedade <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> para determinar qual parte da legenda será indicada como um link.</span><span class="sxs-lookup"><span data-stu-id="b0d2e-119">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>

3. <span data-ttu-id="b0d2e-120">No manipulador de eventos <xref:System.Windows.Forms.LinkLabel.LinkClicked>, no meio de um bloco de tratamento de exceções, chame um segundo procedimento que defina a propriedade <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> como `true` e use o método <xref:System.Diagnostics.Process.Start%2A> para iniciar o navegador padrão com uma URL.</span><span class="sxs-lookup"><span data-stu-id="b0d2e-120">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, in the midst of an exception-handling block, call a second procedure that sets the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true` and uses the <xref:System.Diagnostics.Process.Start%2A> method to start the default browser with a URL.</span></span> <span data-ttu-id="b0d2e-121">Para usar o método <xref:System.Diagnostics.Process.Start%2A>, você precisa adicionar uma referência ao namespace <xref:System.Diagnostics?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b0d2e-121">To use the <xref:System.Diagnostics.Process.Start%2A> method you need to add a reference to the <xref:System.Diagnostics?displayProperty=nameWithType> namespace.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b0d2e-122">Se o código abaixo for executado em um ambiente de confiança parcial (como em uma unidade compartilhada), o compilador JIT falhará quando o método `VisitLink` for chamado.</span><span class="sxs-lookup"><span data-stu-id="b0d2e-122">If the code below is run in a partial-trust environment (such as on a shared drive), the JIT compiler fails when the `VisitLink` method is called.</span></span> <span data-ttu-id="b0d2e-123">A instrução `System.Diagnostics.Process.Start` causa uma demanda de link que falha.</span><span class="sxs-lookup"><span data-stu-id="b0d2e-123">The `System.Diagnostics.Process.Start` statement causes a link demand that fails.</span></span> <span data-ttu-id="b0d2e-124">Ao capturar a exceção quando o método `VisitLink` é chamado, o código a seguir garante que, se o compilador JIT falhar, o erro será tratado normalmente.</span><span class="sxs-lookup"><span data-stu-id="b0d2e-124">By catching the exception when the `VisitLink` method is called, the code below ensures that if the JIT compiler fails, the error is handled gracefully.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b0d2e-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="b0d2e-125">See also</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b0d2e-126">Visão geral do controle LinkLabel</span><span class="sxs-lookup"><span data-stu-id="b0d2e-126">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="b0d2e-127">Como alterar a aparência do controle LinkLabel dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0d2e-127">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [<span data-ttu-id="b0d2e-128">Controle LinkLabel</span><span class="sxs-lookup"><span data-stu-id="b0d2e-128">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
