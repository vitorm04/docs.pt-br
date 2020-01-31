---
title: Criar trabalhos de impressão padrão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
ms.openlocfilehash: 4850dc901630179cc44fefda7e25bbabcfb4725f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741511"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="6d3d2-102">Como criar trabalhos de impressão padrão do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6d3d2-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="6d3d2-103">A base da impressão no Windows Forms é o componente <xref:System.Drawing.Printing.PrintDocument> – mais especificamente, o evento <xref:System.Drawing.Printing.PrintDocument.PrintPage>.</span><span class="sxs-lookup"><span data-stu-id="6d3d2-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="6d3d2-104">Ao escrever código para manipular o evento de <xref:System.Drawing.Printing.PrintDocument.PrintPage>, você pode especificar o que imprimir e como imprimi-lo.</span><span class="sxs-lookup"><span data-stu-id="6d3d2-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="6d3d2-105">Para criar um trabalho de impressão</span><span class="sxs-lookup"><span data-stu-id="6d3d2-105">To create a print job</span></span>  
  
1. <span data-ttu-id="6d3d2-106">Adicione um componente <xref:System.Drawing.Printing.PrintDocument> ao formulário.</span><span class="sxs-lookup"><span data-stu-id="6d3d2-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="6d3d2-107">Escreva o código para manipular o evento <xref:System.Drawing.Printing.PrintDocument.PrintPage>.</span><span class="sxs-lookup"><span data-stu-id="6d3d2-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="6d3d2-108">Você terá de codificar sua própria lógica de impressão.</span><span class="sxs-lookup"><span data-stu-id="6d3d2-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="6d3d2-109">Além disso, precisará especificar o material a ser impresso.</span><span class="sxs-lookup"><span data-stu-id="6d3d2-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="6d3d2-110">No exemplo de código a seguir, um gráfico de exemplo na forma de um retângulo vermelho é criado no manipulador de eventos <xref:System.Drawing.Printing.PrintDocument.PrintPage> para atuar como material a ser impresso.</span><span class="sxs-lookup"><span data-stu-id="6d3d2-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     <span data-ttu-id="6d3d2-111">(Visual C# e Visual C++) Coloque o código a seguir no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="6d3d2-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
     <span data-ttu-id="6d3d2-112">Talvez você também queira escrever código para os eventos <xref:System.Drawing.Printing.PrintDocument.BeginPrint> e <xref:System.Drawing.Printing.PrintDocument.EndPrint>, talvez incluindo um inteiro que representa o número total de páginas a serem impressas, uma vez que cada página é impressa.</span><span class="sxs-lookup"><span data-stu-id="6d3d2-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6d3d2-113">Você pode adicionar um componente <xref:System.Windows.Forms.PrintDialog> ao formulário para fornecer uma interface do usuário (IU) limpa e eficiente aos seus usuários.</span><span class="sxs-lookup"><span data-stu-id="6d3d2-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="6d3d2-114">Definir a propriedade <xref:System.Windows.Forms.PrintDialog.Document%2A> do componente <xref:System.Windows.Forms.PrintDialog> permite que você defina as propriedades relacionadas ao documento de impressão com o qual você está trabalhando no formulário.</span><span class="sxs-lookup"><span data-stu-id="6d3d2-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="6d3d2-115">Para obter mais informações sobre o componente <xref:System.Windows.Forms.PrintDialog>, consulte [componente PrintDialog](../controls/printdialog-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6d3d2-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="6d3d2-116">Para obter mais informações sobre as especificidades de Windows Forms trabalhos de impressão, incluindo como criar um trabalho de impressão programaticamente, consulte <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="6d3d2-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d3d2-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="6d3d2-117">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="6d3d2-118">Suporte à impressão nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6d3d2-118">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
