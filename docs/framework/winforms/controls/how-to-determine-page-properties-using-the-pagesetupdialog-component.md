---
title: Como determinar propriedades de página usando o componente PageSetupDialog
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
ms.openlocfilehash: 8a015c199193dfd9c43bec53cc93cbf9dc201413
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142037"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="0f1d4-102">Como determinar propriedades de página usando o componente PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="0f1d4-102">How to: Determine Page Properties Using the PageSetupDialog Component</span></span>
<span data-ttu-id="0f1d4-103">O componente [PageSetupDialog](pagesetupdialog-component-windows-forms.md) apresenta o layout, tamanho do papel e outras opções de layout da página ao usuário para um documento.</span><span class="sxs-lookup"><span data-stu-id="0f1d4-103">The [PageSetupDialog](pagesetupdialog-component-windows-forms.md) component presents layout, paper size, and other page layout choices to the user for a document.</span></span>  
  
 <span data-ttu-id="0f1d4-104">Você precisa especificar uma <xref:System.Drawing.Printing.PrintDocument> instância da classe — este é o documento a ser impresso.</span><span class="sxs-lookup"><span data-stu-id="0f1d4-104">You need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class—this is the document to be printed.</span></span> <span data-ttu-id="0f1d4-105">Além disso, os usuários devem ter uma impressora instalada em seu computador, localmente <xref:System.Windows.Forms.PageSetupDialog> ou através de uma rede, pois é em parte assim que o componente determina as escolhas de formatação de página apresentadas ao usuário.</span><span class="sxs-lookup"><span data-stu-id="0f1d4-105">Additionally, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PageSetupDialog> component determines the page formatting choices presented to the user.</span></span>  
  
 <span data-ttu-id="0f1d4-106">Um aspecto importante do <xref:System.Windows.Forms.PageSetupDialog> trabalho com o componente <xref:System.Drawing.Printing.PageSettings> é como ele interage com a classe.</span><span class="sxs-lookup"><span data-stu-id="0f1d4-106">An important aspect of working with the <xref:System.Windows.Forms.PageSetupDialog> component is how it interacts with the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="0f1d4-107">A <xref:System.Drawing.Printing.PageSettings> classe é usada para especificar configurações que modificam a forma como uma página será impressa, como orientação de papel, o tamanho da página e as margens.</span><span class="sxs-lookup"><span data-stu-id="0f1d4-107">The <xref:System.Drawing.Printing.PageSettings> class is used to specify settings that modify the way a page will be printed, such as paper orientation, the size of the page, and the margins.</span></span> <span data-ttu-id="0f1d4-108">Cada uma dessas configurações é representada <xref:System.Drawing.Printing.PageSettings> como uma propriedade da classe.</span><span class="sxs-lookup"><span data-stu-id="0f1d4-108">Each of these settings is represented as a property of the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="0f1d4-109">A <xref:System.Windows.Forms.PageSetupDialog> classe modifica esses valores de <xref:System.Drawing.Printing.PageSettings> propriedade para uma determinada instância da classe <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> que está associada ao documento (e é representada como uma propriedade).</span><span class="sxs-lookup"><span data-stu-id="0f1d4-109">The <xref:System.Windows.Forms.PageSetupDialog> class modifies these property values for a given instance of the <xref:System.Drawing.Printing.PageSettings> class that is associated with the document (and is represented as a <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> property).</span></span>  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="0f1d4-110">Para determinar propriedades de página usando o componente PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="0f1d4-110">To set page properties using the PageSetupDialog component</span></span>  
  
1. <span data-ttu-id="0f1d4-111">Use <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> o método para exibir a <xref:System.Drawing.Printing.PrintDocument> caixa de diálogo, especificando o uso.</span><span class="sxs-lookup"><span data-stu-id="0f1d4-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="0f1d4-112">No exemplo abaixo, <xref:System.Windows.Forms.Button> o <xref:System.Windows.Forms.Control.Click> manipulador de eventos do <xref:System.Windows.Forms.PageSetupDialog> controle abre uma instância do componente.</span><span class="sxs-lookup"><span data-stu-id="0f1d4-112">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span> <span data-ttu-id="0f1d4-113">Um documento existente é especificado na <xref:System.Windows.Forms.PageSetupDialog.Document%2A> <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> propriedade, e `false`sua propriedade é definida como .</span><span class="sxs-lookup"><span data-stu-id="0f1d4-113">An existing document is specified in the <xref:System.Windows.Forms.PageSetupDialog.Document%2A> property, and its <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> property is set to `false`.</span></span>  
  
     <span data-ttu-id="0f1d4-114">O exemplo pressupõe <xref:System.Windows.Forms.Button> que seu <xref:System.Drawing.Printing.PrintDocument> formulário `myDocument`tenha <xref:System.Windows.Forms.PageSetupDialog> um controle, um componente chamado e um componente.</span><span class="sxs-lookup"><span data-stu-id="0f1d4-114">The example assumes your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="0f1d4-115">(Visual C# e Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="0f1d4-115">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0f1d4-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="0f1d4-116">See also</span></span>

- <xref:System.Windows.Forms.PageSetupDialog>
- [<span data-ttu-id="0f1d4-117">Como Criar Trabalhos de Impressão Padrão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f1d4-117">How to: Create Standard Windows Forms Print Jobs</span></span>](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [<span data-ttu-id="0f1d4-118">Componente PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="0f1d4-118">PageSetupDialog Component</span></span>](pagesetupdialog-component-windows-forms.md)
