---
title: 'Como: Exibir visualização de impressão em aplicativos do Windows Forms'
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
ms.openlocfilehash: 8252906de9a574f49617609a4cb08a1e8aa6a992
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929001"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a><span data-ttu-id="741c7-102">Como: Exibir visualização de impressão em aplicativos do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="741c7-102">How to: Display Print Preview in Windows Forms Applications</span></span>
<span data-ttu-id="741c7-103">Você pode usar o <xref:System.Windows.Forms.PrintPreviewDialog> controle para permitir que os usuários exibam um documento, geralmente antes de serem impressos.</span><span class="sxs-lookup"><span data-stu-id="741c7-103">You can use the <xref:System.Windows.Forms.PrintPreviewDialog> control to enable users to display a document, often before it is to be printed.</span></span>  
  
 <span data-ttu-id="741c7-104">Para fazer isso, você precisa especificar uma instância da <xref:System.Drawing.Printing.PrintDocument> classe; este é o documento a ser impresso.</span><span class="sxs-lookup"><span data-stu-id="741c7-104">To do this, you need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class; this is the document to be printed.</span></span> <span data-ttu-id="741c7-105">Para obter mais informações sobre como usar a visualização <xref:System.Drawing.Printing.PrintDocument> de impressão com [o componente, consulte Como: Imprima no Windows Forms usando a visualização](../advanced/how-to-print-in-windows-forms-using-print-preview.md)de impressão.</span><span class="sxs-lookup"><span data-stu-id="741c7-105">For more information about using print preview with the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print in Windows Forms Using Print Preview](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="741c7-106">Para usar o <xref:System.Windows.Forms.PrintPreviewDialog> controle em tempo de execução, os usuários devem ter uma impressora instalada em seu computador, seja localmente ou por meio de uma rede, pois isso faz <xref:System.Windows.Forms.PrintPreviewDialog> parte de como o componente determina como será a aparência de um documento quando impresso.</span><span class="sxs-lookup"><span data-stu-id="741c7-106">To use the <xref:System.Windows.Forms.PrintPreviewDialog> control at run time, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PrintPreviewDialog> component determines how a document will look when printed.</span></span>  
  
 <span data-ttu-id="741c7-107">O <xref:System.Windows.Forms.PrintPreviewDialog> controle usa a <xref:System.Drawing.Printing.PrinterSettings> classe.</span><span class="sxs-lookup"><span data-stu-id="741c7-107">The <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span> <span data-ttu-id="741c7-108">Além disso, <xref:System.Windows.Forms.PrintPreviewDialog> o controle usa <xref:System.Drawing.Printing.PageSettings> a classe, assim como <xref:System.Windows.Forms.PrintPreviewDialog> faz o componente.</span><span class="sxs-lookup"><span data-stu-id="741c7-108">Additionally, the <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PageSettings> class, just as the <xref:System.Windows.Forms.PrintPreviewDialog> component does.</span></span> <span data-ttu-id="741c7-109">O documento de impressão especificado na <xref:System.Windows.Forms.PrintPreviewDialog> Propriedade do <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> controle refere-se <xref:System.Drawing.Printing.PrinterSettings> às instâncias das classes <xref:System.Drawing.Printing.PageSettings> e, que são usadas para renderizar o documento na janela de visualização.</span><span class="sxs-lookup"><span data-stu-id="741c7-109">The print document specified in the <xref:System.Windows.Forms.PrintPreviewDialog> control's <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> property refers to instances of both the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and these are used to render the document in the preview window.</span></span>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a><span data-ttu-id="741c7-110">Para exibir páginas usando o controle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="741c7-110">To view pages using the PrintPreviewDialog control</span></span>  
  
- <span data-ttu-id="741c7-111">Use o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo, especificando <xref:System.Drawing.Printing.PrintDocument> o a ser usado.</span><span class="sxs-lookup"><span data-stu-id="741c7-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="741c7-112">No exemplo de código a seguir, <xref:System.Windows.Forms.Button> o manipulador <xref:System.Windows.Forms.Control.Click> de eventos do controle <xref:System.Windows.Forms.PrintPreviewDialog> abre uma instância do controle.</span><span class="sxs-lookup"><span data-stu-id="741c7-112">In the following code example, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="741c7-113">O documento de impressão é especificado na <xref:System.Windows.Forms.PrintDialog.Document%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="741c7-113">The print document is specified in the <xref:System.Windows.Forms.PrintDialog.Document%2A> property.</span></span> <span data-ttu-id="741c7-114">No exemplo a seguir, nenhum documento de impressão é especificado.</span><span class="sxs-lookup"><span data-stu-id="741c7-114">In the example below, no print document is specified.</span></span>  
  
     <span data-ttu-id="741c7-115">O exemplo requer que o formulário tenha um <xref:System.Windows.Forms.Button> controle, um <xref:System.Drawing.Printing.PrintDocument> componente chamado `myDocument`e um <xref:System.Windows.Forms.PrintPreviewDialog> controle.</span><span class="sxs-lookup"><span data-stu-id="741c7-115">The example requires that your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
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
  
     <span data-ttu-id="741c7-116">(Visual C#, Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="741c7-116">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="741c7-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="741c7-117">See also</span></span>

- [<span data-ttu-id="741c7-118">Componente PrintDocument</span><span class="sxs-lookup"><span data-stu-id="741c7-118">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
- [<span data-ttu-id="741c7-119">Controle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="741c7-119">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="741c7-120">Suporte à impressão nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="741c7-120">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="741c7-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="741c7-121">Windows Forms</span></span>](../index.md)
