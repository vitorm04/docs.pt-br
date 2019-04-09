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
ms.openlocfilehash: 22247c941eff575f0f3e5683e46376054ba13bb5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154356"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a><span data-ttu-id="b9b5d-102">Como: Exibir visualização de impressão em aplicativos do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b9b5d-102">How to: Display Print Preview in Windows Forms Applications</span></span>
<span data-ttu-id="b9b5d-103">Você pode usar o <xref:System.Windows.Forms.PrintPreviewDialog> controle para permitir que os usuários exibam um documento, muitas vezes antes que seja a ser impresso.</span><span class="sxs-lookup"><span data-stu-id="b9b5d-103">You can use the <xref:System.Windows.Forms.PrintPreviewDialog> control to enable users to display a document, often before it is to be printed.</span></span>  
  
 <span data-ttu-id="b9b5d-104">Para fazer isso, você precisa especificar uma instância da <xref:System.Drawing.Printing.PrintDocument> classe; este é o documento a ser impresso.</span><span class="sxs-lookup"><span data-stu-id="b9b5d-104">To do this, you need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class; this is the document to be printed.</span></span> <span data-ttu-id="b9b5d-105">Para obter mais informações sobre como usar a visualização de impressão com o <xref:System.Drawing.Printing.PrintDocument> componente, consulte [como: Impressão no Windows Forms usando Visualizar impressão](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span><span class="sxs-lookup"><span data-stu-id="b9b5d-105">For more information about using print preview with the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print in Windows Forms Using Print Preview](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9b5d-106">Para usar o <xref:System.Windows.Forms.PrintPreviewDialog> controle em tempo de execução, os usuários devem ter uma impressora instalada em seu computador, localmente ou através de uma rede, pois isso é parcialmente como o <xref:System.Windows.Forms.PrintPreviewDialog> componente determina qual será a aparência de um documento quando impresso.</span><span class="sxs-lookup"><span data-stu-id="b9b5d-106">To use the <xref:System.Windows.Forms.PrintPreviewDialog> control at run time, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PrintPreviewDialog> component determines how a document will look when printed.</span></span>  
  
 <span data-ttu-id="b9b5d-107">O <xref:System.Windows.Forms.PrintPreviewDialog> controle usa o <xref:System.Drawing.Printing.PrinterSettings> classe.</span><span class="sxs-lookup"><span data-stu-id="b9b5d-107">The <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span> <span data-ttu-id="b9b5d-108">Além disso, o <xref:System.Windows.Forms.PrintPreviewDialog> controle usa o <xref:System.Drawing.Printing.PageSettings> classe, assim como o <xref:System.Windows.Forms.PrintPreviewDialog> componente faz.</span><span class="sxs-lookup"><span data-stu-id="b9b5d-108">Additionally, the <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PageSettings> class, just as the <xref:System.Windows.Forms.PrintPreviewDialog> component does.</span></span> <span data-ttu-id="b9b5d-109">O documento de impressão especificado na <xref:System.Windows.Forms.PrintPreviewDialog> do controle <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> propriedade refere-se a instâncias de ambas as <xref:System.Drawing.Printing.PrinterSettings> e <xref:System.Drawing.Printing.PageSettings> classes e eles são usados para renderizar o documento na janela de visualização.</span><span class="sxs-lookup"><span data-stu-id="b9b5d-109">The print document specified in the <xref:System.Windows.Forms.PrintPreviewDialog> control's <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> property refers to instances of both the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and these are used to render the document in the preview window.</span></span>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a><span data-ttu-id="b9b5d-110">Para exibir páginas usando o controle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="b9b5d-110">To view pages using the PrintPreviewDialog control</span></span>  
  
-   <span data-ttu-id="b9b5d-111">Use o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo, especificando o <xref:System.Drawing.Printing.PrintDocument> usar.</span><span class="sxs-lookup"><span data-stu-id="b9b5d-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="b9b5d-112">No exemplo de código a seguir, o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Click> manipulador de eventos abre uma instância da <xref:System.Windows.Forms.PrintPreviewDialog> controle.</span><span class="sxs-lookup"><span data-stu-id="b9b5d-112">In the following code example, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="b9b5d-113">O documento de impressão é especificado no <xref:System.Windows.Forms.PrintDialog.Document%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b9b5d-113">The print document is specified in the <xref:System.Windows.Forms.PrintDialog.Document%2A> property.</span></span> <span data-ttu-id="b9b5d-114">No exemplo a seguir, nenhum documento de impressão é especificado.</span><span class="sxs-lookup"><span data-stu-id="b9b5d-114">In the example below, no print document is specified.</span></span>  
  
     <span data-ttu-id="b9b5d-115">O exemplo requer que o formulário tem um <xref:System.Windows.Forms.Button> controle, um <xref:System.Drawing.Printing.PrintDocument> componente denominado `myDocument`e um <xref:System.Windows.Forms.PrintPreviewDialog> controle.</span><span class="sxs-lookup"><span data-stu-id="b9b5d-115">The example requires that your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
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
  
     <span data-ttu-id="b9b5d-116">(Visual c#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="b9b5d-116">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b9b5d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9b5d-117">See also</span></span>

- [<span data-ttu-id="b9b5d-118">Componente PrintDocument</span><span class="sxs-lookup"><span data-stu-id="b9b5d-118">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
- [<span data-ttu-id="b9b5d-119">Controle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="b9b5d-119">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="b9b5d-120">Suporte à impressão no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b9b5d-120">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="b9b5d-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b9b5d-121">Windows Forms</span></span>](../index.md)
