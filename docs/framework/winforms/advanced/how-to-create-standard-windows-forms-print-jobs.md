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
ms.openlocfilehash: d9607de7c74132e0d7dce605b16d62c79b7dbccb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182577"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="980a9-102">Como criar trabalhos de impressão padrão do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="980a9-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="980a9-103">A base da impressão no <xref:System.Drawing.Printing.PrintDocument> Windows Forms é <xref:System.Drawing.Printing.PrintDocument.PrintPage> o componente — mais especificamente, o evento.</span><span class="sxs-lookup"><span data-stu-id="980a9-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="980a9-104">Ao escrever código <xref:System.Drawing.Printing.PrintDocument.PrintPage> para lidar com o evento, você pode especificar o que imprimir e como imprimi-lo.</span><span class="sxs-lookup"><span data-stu-id="980a9-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="980a9-105">Para criar um trabalho de impressão</span><span class="sxs-lookup"><span data-stu-id="980a9-105">To create a print job</span></span>  
  
1. <span data-ttu-id="980a9-106">Adicione <xref:System.Drawing.Printing.PrintDocument> um componente ao seu formulário.</span><span class="sxs-lookup"><span data-stu-id="980a9-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="980a9-107">Escreva código para <xref:System.Drawing.Printing.PrintDocument.PrintPage> lidar com o evento.</span><span class="sxs-lookup"><span data-stu-id="980a9-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="980a9-108">Você terá de codificar sua própria lógica de impressão.</span><span class="sxs-lookup"><span data-stu-id="980a9-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="980a9-109">Além disso, precisará especificar o material a ser impresso.</span><span class="sxs-lookup"><span data-stu-id="980a9-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="980a9-110">No exemplo de código a seguir, um gráfico de amostra na <xref:System.Drawing.Printing.PrintDocument.PrintPage> forma de um retângulo vermelho é criado no manipulador de eventos para agir como material a ser impresso.</span><span class="sxs-lookup"><span data-stu-id="980a9-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
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
  
     <span data-ttu-id="980a9-111">(Visual C# e Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="980a9-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="980a9-112">Você também pode querer escrever <xref:System.Drawing.Printing.PrintDocument.BeginPrint> <xref:System.Drawing.Printing.PrintDocument.EndPrint> código para os eventos e eventos, talvez incluindo um inteiro representando o número total de páginas para imprimir que é decretada à medida que cada página imprime.</span><span class="sxs-lookup"><span data-stu-id="980a9-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="980a9-113">Você pode <xref:System.Windows.Forms.PrintDialog> adicionar um componente ao seu formulário para fornecer uma interface de usuário (UI) limpa e eficiente aos seus usuários.</span><span class="sxs-lookup"><span data-stu-id="980a9-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="980a9-114">A <xref:System.Windows.Forms.PrintDialog.Document%2A> configuração <xref:System.Windows.Forms.PrintDialog> da propriedade do componente permite definir propriedades relacionadas ao documento de impressão com o que você está trabalhando em seu formulário.</span><span class="sxs-lookup"><span data-stu-id="980a9-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="980a9-115">Para obter mais <xref:System.Windows.Forms.PrintDialog> informações sobre o componente, consulte [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="980a9-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="980a9-116">Para obter mais informações sobre as especificidades dos trabalhos de impressão do <xref:System.Drawing.Printing.PrintPageEventArgs>Windows Forms, incluindo como criar um trabalho de impressão programáticamente, consulte .</span><span class="sxs-lookup"><span data-stu-id="980a9-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="980a9-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="980a9-117">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="980a9-118">Suporte à impressão no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="980a9-118">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
