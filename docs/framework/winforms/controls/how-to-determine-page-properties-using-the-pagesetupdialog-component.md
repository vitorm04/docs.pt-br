---
title: 'Como: Determinar propriedades de página usando o componente PageSetupDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- page properties
- page setup
- PageSetupDialog component
ms.assetid: 6dae05bc-c0fd-4357-bb93-841a1631d98f
ms.openlocfilehash: 7c65eb54bb95b9a20cd1e43f0d491af47985f2e0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329200"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="9c57b-102">Como: Determinar propriedades de página usando o componente PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="9c57b-102">How to: Determine Page Properties Using the PageSetupDialog Component</span></span>
<span data-ttu-id="9c57b-103">O componente [PageSetupDialog](pagesetupdialog-component-windows-forms.md) apresenta o layout, tamanho do papel e outras opções de layout da página ao usuário para um documento.</span><span class="sxs-lookup"><span data-stu-id="9c57b-103">The [PageSetupDialog](pagesetupdialog-component-windows-forms.md) component presents layout, paper size, and other page layout choices to the user for a document.</span></span>  
  
 <span data-ttu-id="9c57b-104">Você precisa especificar uma instância da <xref:System.Drawing.Printing.PrintDocument> classe — este é o documento a ser impresso.</span><span class="sxs-lookup"><span data-stu-id="9c57b-104">You need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class—this is the document to be printed.</span></span> <span data-ttu-id="9c57b-105">Além disso, os usuários devem ter uma impressora instalada em seu computador, localmente ou através de uma rede, pois isso é parcialmente como o <xref:System.Windows.Forms.PageSetupDialog> componente determina a formatação opções apresentadas ao usuário da página.</span><span class="sxs-lookup"><span data-stu-id="9c57b-105">Additionally, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PageSetupDialog> component determines the page formatting choices presented to the user.</span></span>  
  
 <span data-ttu-id="9c57b-106">Um aspecto importante de trabalhar com o <xref:System.Windows.Forms.PageSetupDialog> componente é como ele interage com o <xref:System.Drawing.Printing.PageSettings> classe.</span><span class="sxs-lookup"><span data-stu-id="9c57b-106">An important aspect of working with the <xref:System.Windows.Forms.PageSetupDialog> component is how it interacts with the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="9c57b-107">O <xref:System.Drawing.Printing.PageSettings> classe é usada para especificar configurações que modificam a maneira que uma página será impressa, como a orientação do papel, o tamanho da página e as margens.</span><span class="sxs-lookup"><span data-stu-id="9c57b-107">The <xref:System.Drawing.Printing.PageSettings> class is used to specify settings that modify the way a page will be printed, such as paper orientation, the size of the page, and the margins.</span></span> <span data-ttu-id="9c57b-108">Cada uma dessas configurações é representada como uma propriedade do <xref:System.Drawing.Printing.PageSettings> classe.</span><span class="sxs-lookup"><span data-stu-id="9c57b-108">Each of these settings is represented as a property of the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="9c57b-109">O <xref:System.Windows.Forms.PageSetupDialog> classe modifica esses valores de propriedade para uma determinada instância das <xref:System.Drawing.Printing.PageSettings> classe, que está associada ao documento (e é representado como um <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> propriedade).</span><span class="sxs-lookup"><span data-stu-id="9c57b-109">The <xref:System.Windows.Forms.PageSetupDialog> class modifies these property values for a given instance of the <xref:System.Drawing.Printing.PageSettings> class that is associated with the document (and is represented as a <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> property).</span></span>  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="9c57b-110">Para determinar propriedades de página usando o componente PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="9c57b-110">To set page properties using the PageSetupDialog component</span></span>  
  
1. <span data-ttu-id="9c57b-111">Use o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo, especificando o <xref:System.Drawing.Printing.PrintDocument> usar.</span><span class="sxs-lookup"><span data-stu-id="9c57b-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="9c57b-112">No exemplo a seguir, o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Click> manipulador de eventos abre uma instância da <xref:System.Windows.Forms.PageSetupDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="9c57b-112">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span> <span data-ttu-id="9c57b-113">Um documento existente é especificado na <xref:System.Windows.Forms.PageSetupDialog.Document%2A> propriedade e sua <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> estiver definida como `false`.</span><span class="sxs-lookup"><span data-stu-id="9c57b-113">An existing document is specified in the <xref:System.Windows.Forms.PageSetupDialog.Document%2A> property, and its <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> property is set to `false`.</span></span>  
  
     <span data-ttu-id="9c57b-114">O exemplo supõe que seu formulário tem um <xref:System.Windows.Forms.Button> controle, um <xref:System.Drawing.Printing.PrintDocument> componente denominado `myDocument`e um <xref:System.Windows.Forms.PageSetupDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="9c57b-114">The example assumes your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       'You will have to specify your own print document.  
       PageSetupDialog1.Document = myDocument  
       ' Sets the print document's color setting to false,  
       ' so that the page will not be printed in color.  
       PageSetupDialog1.Document.DefaultPageSettings.Color = False  
       PageSetupDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       pageSetupDialog1.Document = myDocument;  
       // Sets the print document's color setting to false,  
       // so that the page will not be printed in color.  
       pageSetupDialog1.Document.DefaultPageSettings.Color = false;  
       pageSetupDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button1_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          pageSetupDialog1->Document = myDocument;  
          // Sets the print document's color setting to false,  
          // so that the page will not be printed in color.  
          pageSetupDialog1->Document->DefaultPageSettings->Color = false;  
          pageSetupDialog1->ShowDialog();  
       }  
    ```  
  
     <span data-ttu-id="9c57b-115">(Visual c# e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="9c57b-115">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9c57b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c57b-116">See also</span></span>

- <xref:System.Windows.Forms.PageSetupDialog>
- [<span data-ttu-id="9c57b-117">Como: Criar trabalhos de impressão padrão do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9c57b-117">How to: Create Standard Windows Forms Print Jobs</span></span>](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [<span data-ttu-id="9c57b-118">Componente PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="9c57b-118">PageSetupDialog Component</span></span>](pagesetupdialog-component-windows-forms.md)
