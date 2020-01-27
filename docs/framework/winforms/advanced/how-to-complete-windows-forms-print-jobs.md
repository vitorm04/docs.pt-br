---
title: Concluir trabalhos de impressão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: b8ef4fa05b2107247181e82b72389f9503507135
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746497"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a><span data-ttu-id="1cf51-102">Como concluir trabalhos de impressão do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1cf51-102">How to: Complete Windows Forms Print Jobs</span></span>
<span data-ttu-id="1cf51-103">Frequentemente, processadores de texto e outros aplicativos que envolvem impressão fornecerão a opção para exibir uma mensagem aos usuários de que um trabalho de impressão foi concluído.</span><span class="sxs-lookup"><span data-stu-id="1cf51-103">Frequently, word processors and other applications that involve printing will provide the option to display a message to users that a print job is complete.</span></span> <span data-ttu-id="1cf51-104">Você pode fornecer essa funcionalidade no Windows Forms manipulando o evento <xref:System.Drawing.Printing.PrintDocument.EndPrint> do componente <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="1cf51-104">You can provide this functionality in your Windows Forms by handling the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 <span data-ttu-id="1cf51-105">O procedimento a seguir requer que você tenha criado um aplicativo baseado no Windows com um componente <xref:System.Drawing.Printing.PrintDocument> nele, que é a maneira padrão de habilitar a impressão de um aplicativo baseado no Windows.</span><span class="sxs-lookup"><span data-stu-id="1cf51-105">The following procedure requires that you have created a Windows-based application with a <xref:System.Drawing.Printing.PrintDocument> component on it, which is the standard way of enabling printing from a Windows-based application.</span></span> <span data-ttu-id="1cf51-106">Para obter mais informações sobre a impressão de Windows Forms usando o componente <xref:System.Drawing.Printing.PrintDocument>, consulte [como: criar trabalhos de impressão padrão do Windows Forms](how-to-create-standard-windows-forms-print-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="1cf51-106">For more information about printing from Windows Forms using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Create Standard Windows Forms Print Jobs](how-to-create-standard-windows-forms-print-jobs.md).</span></span>  
  
### <a name="to-complete-a-print-job"></a><span data-ttu-id="1cf51-107">Para concluir um trabalho de impressão</span><span class="sxs-lookup"><span data-stu-id="1cf51-107">To complete a print job</span></span>  
  
1. <span data-ttu-id="1cf51-108">Defina a propriedade <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> do componente <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="1cf51-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. <span data-ttu-id="1cf51-109">Escreva o código para manipular o evento <xref:System.Drawing.Printing.PrintDocument.EndPrint>.</span><span class="sxs-lookup"><span data-stu-id="1cf51-109">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event.</span></span>  
  
     <span data-ttu-id="1cf51-110">No exemplo de código a seguir, uma caixa de mensagem é exibida, indicando que o documento terminou a impressão.</span><span class="sxs-lookup"><span data-stu-id="1cf51-110">In the following code example, a message box is displayed, indicating that the document has finished printing.</span></span>  
  
    ```vb  
    Private Sub PrintDocument1_EndPrint(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintEventArgs) Handles PrintDocument1.EndPrint  
       MessageBox.Show(PrintDocument1.DocumentName + " has finished printing.")  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_EndPrint(object sender,   
    System.Drawing.Printing.PrintEventArgs e)  
    {  
       MessageBox.Show(printDocument1.DocumentName +   
          " has finished printing.");  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_EndPrint(System::Object ^ sender,  
          System::Drawing::Printing::PrintEventArgs ^ e)  
       {  
          MessageBox::Show(String::Concat(printDocument1->DocumentName,  
             " has finished printing."));  
       }  
    ```  
  
     <span data-ttu-id="1cf51-111">(Visual C# e Visual C++) Coloque o código a seguir no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="1cf51-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.EndPrint += new  
       System.Drawing.Printing.PrintEventHandler  
       (this.printDocument1_EndPrint);  
    ```  
  
    ```cpp  
    this->printDocument1->EndPrint += gcnew  
       System::Drawing::Printing::PrintEventHandler  
       (this, &Form1::printDocument1_EndPrint);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1cf51-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="1cf51-112">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="1cf51-113">Suporte à impressão nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1cf51-113">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
