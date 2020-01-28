---
title: Exibir visualização de impressão em aplicativos Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
ms.openlocfilehash: ac02339ad86e491cd047dcd4b0c8841374b3bb2e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745576"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a><span data-ttu-id="6371a-102">Como exibir visualização de impressão em aplicativos dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6371a-102">How to: Display Print Preview in Windows Forms Applications</span></span>
<span data-ttu-id="6371a-103">Você pode usar o controle de <xref:System.Windows.Forms.PrintPreviewDialog> para permitir que os usuários exibam um documento, geralmente antes de serem impressos.</span><span class="sxs-lookup"><span data-stu-id="6371a-103">You can use the <xref:System.Windows.Forms.PrintPreviewDialog> control to enable users to display a document, often before it is to be printed.</span></span>  
  
 <span data-ttu-id="6371a-104">Para fazer isso, você precisa especificar uma instância da classe <xref:System.Drawing.Printing.PrintDocument>; Este é o documento a ser impresso.</span><span class="sxs-lookup"><span data-stu-id="6371a-104">To do this, you need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class; this is the document to be printed.</span></span> <span data-ttu-id="6371a-105">Para obter mais informações sobre como usar a visualização de impressão com o componente <xref:System.Drawing.Printing.PrintDocument>, consulte [como imprimir em Windows Forms usando a visualização de impressão](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span><span class="sxs-lookup"><span data-stu-id="6371a-105">For more information about using print preview with the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print in Windows Forms Using Print Preview](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6371a-106">Para usar o controle de <xref:System.Windows.Forms.PrintPreviewDialog> em tempo de execução, os usuários devem ter uma impressora instalada em seu computador, seja localmente ou por meio de uma rede, pois isso faz parte de como o componente de <xref:System.Windows.Forms.PrintPreviewDialog> determina como será a aparência de um documento quando impresso.</span><span class="sxs-lookup"><span data-stu-id="6371a-106">To use the <xref:System.Windows.Forms.PrintPreviewDialog> control at run time, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PrintPreviewDialog> component determines how a document will look when printed.</span></span>  
  
 <span data-ttu-id="6371a-107">O controle <xref:System.Windows.Forms.PrintPreviewDialog> usa a classe <xref:System.Drawing.Printing.PrinterSettings>.</span><span class="sxs-lookup"><span data-stu-id="6371a-107">The <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span> <span data-ttu-id="6371a-108">Além disso, o controle de <xref:System.Windows.Forms.PrintPreviewDialog> usa a classe <xref:System.Drawing.Printing.PageSettings>, assim como o componente de <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="6371a-108">Additionally, the <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PageSettings> class, just as the <xref:System.Windows.Forms.PrintPreviewDialog> component does.</span></span> <span data-ttu-id="6371a-109">O documento de impressão especificado na propriedade <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> do controle de <xref:System.Windows.Forms.PrintPreviewDialog> se refere a instâncias das classes <xref:System.Drawing.Printing.PrinterSettings> e <xref:System.Drawing.Printing.PageSettings>, e elas são usadas para renderizar o documento na janela de visualização.</span><span class="sxs-lookup"><span data-stu-id="6371a-109">The print document specified in the <xref:System.Windows.Forms.PrintPreviewDialog> control's <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> property refers to instances of both the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and these are used to render the document in the preview window.</span></span>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a><span data-ttu-id="6371a-110">Para exibir páginas usando o controle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="6371a-110">To view pages using the PrintPreviewDialog control</span></span>  
  
- <span data-ttu-id="6371a-111">Use o método <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> para exibir a caixa de diálogo, especificando o <xref:System.Drawing.Printing.PrintDocument> a ser usado.</span><span class="sxs-lookup"><span data-stu-id="6371a-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="6371a-112">No exemplo de código a seguir, o manipulador de eventos <xref:System.Windows.Forms.Control.Click> do controle de <xref:System.Windows.Forms.Button> abre uma instância do controle de <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="6371a-112">In the following code example, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="6371a-113">O documento de impressão é especificado na propriedade <xref:System.Windows.Forms.PrintDialog.Document%2A>.</span><span class="sxs-lookup"><span data-stu-id="6371a-113">The print document is specified in the <xref:System.Windows.Forms.PrintDialog.Document%2A> property.</span></span> <span data-ttu-id="6371a-114">No exemplo a seguir, nenhum documento de impressão é especificado.</span><span class="sxs-lookup"><span data-stu-id="6371a-114">In the example below, no print document is specified.</span></span>  
  
     <span data-ttu-id="6371a-115">O exemplo requer que o formulário tenha um controle de <xref:System.Windows.Forms.Button>, um componente de <xref:System.Drawing.Printing.PrintDocument> chamado `myDocument`e um controle de <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="6371a-115">The example requires that your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       ' You will have to specify your own print document.  
       PrintPreviewDialog1.Document = myDocument  
       PrintPreviewDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       printPreviewDialog1.Document = myDocument;  
       printPreviewDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          printPreviewDialog1->Document = myDocument;  
          printPreviewDialog1->ShowDialog();  
       }  
    ```  
  
     <span data-ttu-id="6371a-116">(Visual C#, Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="6371a-116">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6371a-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="6371a-117">See also</span></span>

- [<span data-ttu-id="6371a-118">Componente PrintDocument</span><span class="sxs-lookup"><span data-stu-id="6371a-118">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
- [<span data-ttu-id="6371a-119">Controle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="6371a-119">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="6371a-120">Suporte à impressão nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6371a-120">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="6371a-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6371a-121">Windows Forms</span></span>](../index.md)
