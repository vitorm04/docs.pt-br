---
title: Trabalhos completos de impressão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: 62f67002bfbaf46e73bae06fdaff26efde865c06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182591"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a><span data-ttu-id="5b81c-102">Como concluir trabalhos de impressão do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5b81c-102">How to: Complete Windows Forms Print Jobs</span></span>
<span data-ttu-id="5b81c-103">Frequentemente, processadores de texto e outros aplicativos que envolvem impressão fornecerão a opção para exibir uma mensagem aos usuários de que um trabalho de impressão foi concluído.</span><span class="sxs-lookup"><span data-stu-id="5b81c-103">Frequently, word processors and other applications that involve printing will provide the option to display a message to users that a print job is complete.</span></span> <span data-ttu-id="5b81c-104">Você pode fornecer essa funcionalidade em seus <xref:System.Drawing.Printing.PrintDocument.EndPrint> Formulários <xref:System.Drawing.Printing.PrintDocument> do Windows manipulando o evento do componente.</span><span class="sxs-lookup"><span data-stu-id="5b81c-104">You can provide this functionality in your Windows Forms by handling the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 <span data-ttu-id="5b81c-105">O procedimento a seguir exige que você tenha <xref:System.Drawing.Printing.PrintDocument> criado um aplicativo baseado no Windows com um componente nele, que é a maneira padrão de habilitar a impressão a partir de um aplicativo baseado no Windows.</span><span class="sxs-lookup"><span data-stu-id="5b81c-105">The following procedure requires that you have created a Windows-based application with a <xref:System.Drawing.Printing.PrintDocument> component on it, which is the standard way of enabling printing from a Windows-based application.</span></span> <span data-ttu-id="5b81c-106">Para obter mais informações sobre <xref:System.Drawing.Printing.PrintDocument> a impressão de Formulários do Windows usando o componente, consulte [Como: Criar trabalhos padrão](how-to-create-standard-windows-forms-print-jobs.md)de impressão de formulários do Windows .</span><span class="sxs-lookup"><span data-stu-id="5b81c-106">For more information about printing from Windows Forms using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Create Standard Windows Forms Print Jobs](how-to-create-standard-windows-forms-print-jobs.md).</span></span>  
  
### <a name="to-complete-a-print-job"></a><span data-ttu-id="5b81c-107">Para concluir um trabalho de impressão</span><span class="sxs-lookup"><span data-stu-id="5b81c-107">To complete a print job</span></span>  
  
1. <span data-ttu-id="5b81c-108">Defina <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> a <xref:System.Drawing.Printing.PrintDocument> propriedade do componente.</span><span class="sxs-lookup"><span data-stu-id="5b81c-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. <span data-ttu-id="5b81c-109">Escreva código para <xref:System.Drawing.Printing.PrintDocument.EndPrint> lidar com o evento.</span><span class="sxs-lookup"><span data-stu-id="5b81c-109">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event.</span></span>  
  
     <span data-ttu-id="5b81c-110">No exemplo de código a seguir, uma caixa de mensagem é exibida, indicando que o documento terminou a impressão.</span><span class="sxs-lookup"><span data-stu-id="5b81c-110">In the following code example, a message box is displayed, indicating that the document has finished printing.</span></span>  
  
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
  
     <span data-ttu-id="5b81c-111">(Visual C# e Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="5b81c-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b81c-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="5b81c-112">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="5b81c-113">Suporte à impressão no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5b81c-113">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
