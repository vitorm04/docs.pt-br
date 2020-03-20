---
title: Habilite operações de arrastar e soltar com controle RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- drag and drop [Windows Forms], richTextBox control
- text boxes [Windows Forms], drag-and-drop operations
- RichTextBox control [Windows Forms], drag-and-drop operations
ms.assetid: ca167d1c-2014-4cf0-96a0-20598470be3b
ms.openlocfilehash: 27e5c18598552c465ef17f5e58069bc10e401c09
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182344"
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="eb681-102">Como habilitar operações arrastar e soltar com o controle RichTextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eb681-102">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="eb681-103">As operações de arrastar e <xref:System.Windows.Forms.RichTextBox> soltar com o <xref:System.Windows.Forms.RichTextBox.DragEnter> controle <xref:System.Windows.Forms.RichTextBox.DragDrop> do Windows Forms são feitas manuseando os eventos.</span><span class="sxs-lookup"><span data-stu-id="eb681-103">Drag-and-drop operations with the Windows Forms <xref:System.Windows.Forms.RichTextBox> control are done by handling the <xref:System.Windows.Forms.RichTextBox.DragEnter> and <xref:System.Windows.Forms.RichTextBox.DragDrop> events.</span></span> <span data-ttu-id="eb681-104">Assim, as operações de arrastar e <xref:System.Windows.Forms.RichTextBox> soltar são extremamente simples com o controle.</span><span class="sxs-lookup"><span data-stu-id="eb681-104">Thus, drag-and-drop operations are extremely simple with the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a><span data-ttu-id="eb681-105">Habilitar operações de arrastar em um controle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="eb681-105">To enable drag operations in a RichTextBox control</span></span>  
  
1. <span data-ttu-id="eb681-106">Defina <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> a <xref:System.Windows.Forms.RichTextBox> propriedade `true`do controle para .</span><span class="sxs-lookup"><span data-stu-id="eb681-106">Set the <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> property of the <xref:System.Windows.Forms.RichTextBox> control to `true`.</span></span>  
  
2. <span data-ttu-id="eb681-107">Escreva código no manipulador <xref:System.Windows.Forms.RichTextBox.DragEnter> de eventos do evento.</span><span class="sxs-lookup"><span data-stu-id="eb681-107">Write code in the event handler of the <xref:System.Windows.Forms.RichTextBox.DragEnter> event.</span></span> <span data-ttu-id="eb681-108">Use uma instrução `if` para garantir que os dados que são arrastados pertencem a um tipo aceitável (neste caso, texto).</span><span class="sxs-lookup"><span data-stu-id="eb681-108">Use an `if` statement to ensure that the data being dragged is of an acceptable type (in this case, text).</span></span> <span data-ttu-id="eb681-109">A <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> propriedade pode ser definida <xref:System.Windows.Forms.DragDropEffects> para qualquer valor da enumeração.</span><span class="sxs-lookup"><span data-stu-id="eb681-109">The <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> property can be set to any value of the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span>  
  
    ```vb  
    Private Sub RichTextBox1_DragEnter(ByVal sender As Object, _
       ByVal e As System.Windows.Forms.DragEventArgs) _
       Handles RichTextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
          e.Effect = DragDropEffects.Copy  
       Else  
          e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragEnter(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    ```cpp  
    private:  
       void richTextBox1_DragEnter(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          if (e->Data->GetDataPresent(DataFormats::Text))  
             e->Effect = DragDropEffects::Copy;  
          else  
             e->Effect = DragDropEffects::None;  
       }  
    ```  
  
     <span data-ttu-id="eb681-110">(Visual C# e Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="eb681-110">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.richTextBox1.DragEnter += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragEnter);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragEnter += gcnew  
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragEnter);  
    ```  
  
3. <span data-ttu-id="eb681-111">Escreva código para <xref:System.Windows.Forms.RichTextBox.DragDrop> lidar com o evento.</span><span class="sxs-lookup"><span data-stu-id="eb681-111">Write code to handle the <xref:System.Windows.Forms.RichTextBox.DragDrop> event.</span></span> <span data-ttu-id="eb681-112">Use <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> o método para recuperar os dados que estão sendo arrastados.</span><span class="sxs-lookup"><span data-stu-id="eb681-112">Use the <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> method to retrieve the data being dragged.</span></span>  
  
     <span data-ttu-id="eb681-113">No exemplo abaixo, o <xref:System.Windows.Forms.RichTextBox.Text%2A> código define <xref:System.Windows.Forms.RichTextBox> a propriedade do controle igual aos dados que estão sendo arrastados.</span><span class="sxs-lookup"><span data-stu-id="eb681-113">In the example below, the code sets the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control equal to the data being dragged.</span></span> <span data-ttu-id="eb681-114">Se já houver texto <xref:System.Windows.Forms.RichTextBox> no controle, o texto arrastado será inserido no ponto de inserção.</span><span class="sxs-lookup"><span data-stu-id="eb681-114">If there is already text in the <xref:System.Windows.Forms.RichTextBox> control, the dragged text is inserted at the insertion point.</span></span>  
  
    ```vb  
    Private Sub RichTextBox1_DragDrop(ByVal sender As Object, _
       ByVal e As System.Windows.Forms.DragEventArgs) _
       Handles RichTextBox1.DragDrop  
       Dim i As Int16
       Dim s As String  
  
       ' Get start position to drop the text.  
       i = RichTextBox1.SelectionStart  
       s = RichTextBox1.Text.Substring(i)  
       RichTextBox1.Text = RichTextBox1.Text.Substring(0, i)  
  
       ' Drop the text on to the RichTextBox.  
       RichTextBox1.Text = RichTextBox1.Text + _  
          e.Data.GetData(DataFormats.Text).ToString()  
       RichTextBox1.Text = RichTextBox1.Text + s  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragDrop(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       int i;  
       String s;  
  
       // Get start position to drop the text.  
       i = richTextBox1.SelectionStart;  
       s = richTextBox1.Text.Substring(i);  
       richTextBox1.Text = richTextBox1.Text.Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       richTextBox1.Text = richTextBox1.Text +
          e.Data.GetData(DataFormats.Text).ToString();  
       richTextBox1.Text = richTextBox1.Text + s;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void richTextBox1_DragDrop(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          int i;  
          String ^s;  
  
       // Get start position to drop the text.  
       i = richTextBox1->SelectionStart;  
       s = richTextBox1->Text->Substring(i);  
       richTextBox1->Text = richTextBox1->Text->Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       String ^str = String::Concat(richTextBox1->Text, e->Data  
       ->GetData(DataFormats->Text)->ToString());
       richTextBox1->Text = String::Concat(str, s);  
       }  
    ```  
  
     <span data-ttu-id="eb681-115">(Visual C# e Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="eb681-115">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.richTextBox1.DragDrop += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragDrop);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragDrop += gcnew
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragDrop);  
    ```  
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a><span data-ttu-id="eb681-116">Testar a funcionalidade do tipo "arrastar e soltar" no seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="eb681-116">To test the drag-and-drop functionality in your application</span></span>  
  
1. <span data-ttu-id="eb681-117">Salve e compile o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb681-117">Save and build your application.</span></span> <span data-ttu-id="eb681-118">Enquanto estiver em execução, execute o WordPad.</span><span class="sxs-lookup"><span data-stu-id="eb681-118">While it is running, run WordPad.</span></span>  
  
     <span data-ttu-id="eb681-119">O WordPad é um editor de texto instalado pelo Windows que permite realizar operações do tipo "arrastar e soltar".</span><span class="sxs-lookup"><span data-stu-id="eb681-119">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="eb681-120">Ele pode ser acessado clicando no botão **Iniciar**, selecionando **Executar**, digitando `WordPad` na caixa de texto da caixa de diálogo **Executar** e clicando em **OK**.</span><span class="sxs-lookup"><span data-stu-id="eb681-120">It is accessible by clicking the **Start** button, selecting **Run**, typing `WordPad` in the text box of the **Run** dialog box, and then clicking **OK**.</span></span>  
  
2. <span data-ttu-id="eb681-121">Após abrir o WordPad, digite uma cadeia de texto nele.</span><span class="sxs-lookup"><span data-stu-id="eb681-121">Once WordPad is open, type a string of text in it.</span></span> <span data-ttu-id="eb681-122">Usando o mouse, selecione o texto e arraste o texto selecionado para o <xref:System.Windows.Forms.RichTextBox> controle do aplicativo windows.</span><span class="sxs-lookup"><span data-stu-id="eb681-122">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.RichTextBox> control in your Windows application.</span></span>  
  
     <span data-ttu-id="eb681-123">Observe que quando você aponta <xref:System.Windows.Forms.RichTextBox> o mouse para o <xref:System.Windows.Forms.RichTextBox.DragEnter> controle (e, consequentemente, aumentar o evento), o ponteiro do mouse muda e você pode soltar o texto selecionado no <xref:System.Windows.Forms.RichTextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="eb681-123">Notice that when you point the mouse at the <xref:System.Windows.Forms.RichTextBox> control (and, consequently, raise the <xref:System.Windows.Forms.RichTextBox.DragEnter> event), the mouse pointer changes and you can drop the selected text into the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
     <span data-ttu-id="eb681-124">Quando você solta o botão do mouse, o texto <xref:System.Windows.Forms.RichTextBox.DragDrop> selecionado é descartado (ou seja, o evento é levantado) e é inserido dentro do <xref:System.Windows.Forms.RichTextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="eb681-124">When you release the mouse button, the selected text is dropped (that is, the <xref:System.Windows.Forms.RichTextBox.DragDrop> event is raised) and is inserted within the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb681-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="eb681-125">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="eb681-126">Como Executar Operações de do Tipo "Arrastar e Soltar" entre Aplicativos</span><span class="sxs-lookup"><span data-stu-id="eb681-126">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [<span data-ttu-id="eb681-127">Controle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="eb681-127">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="eb681-128">Controles para usar em formulários windows</span><span class="sxs-lookup"><span data-stu-id="eb681-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
