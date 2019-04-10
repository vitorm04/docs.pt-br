---
title: 'Como: concluir trabalhos de impressão do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: 256b9a3d8842aaa4b032e67ebac9ca6a9e1ef34a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293749"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a><span data-ttu-id="f96c3-102">Como: concluir trabalhos de impressão do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f96c3-102">How to: Complete Windows Forms Print Jobs</span></span>
<span data-ttu-id="f96c3-103">Frequentemente, processadores de texto e outros aplicativos que envolvem impressão fornecerão a opção para exibir uma mensagem aos usuários de que um trabalho de impressão foi concluído.</span><span class="sxs-lookup"><span data-stu-id="f96c3-103">Frequently, word processors and other applications that involve printing will provide the option to display a message to users that a print job is complete.</span></span> <span data-ttu-id="f96c3-104">Você pode fornecer essa funcionalidade em seus formulários do Windows manipulando o <xref:System.Drawing.Printing.PrintDocument.EndPrint> eventos do <xref:System.Drawing.Printing.PrintDocument> componente.</span><span class="sxs-lookup"><span data-stu-id="f96c3-104">You can provide this functionality in your Windows Forms by handling the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 <span data-ttu-id="f96c3-105">O procedimento a seguir requer que você tenha criado um aplicativo baseado em Windows com um <xref:System.Drawing.Printing.PrintDocument> componente nele, que é a maneira padrão de habilitar a impressão de um aplicativo baseado em Windows.</span><span class="sxs-lookup"><span data-stu-id="f96c3-105">The following procedure requires that you have created a Windows-based application with a <xref:System.Drawing.Printing.PrintDocument> component on it, which is the standard way of enabling printing from a Windows-based application.</span></span> <span data-ttu-id="f96c3-106">Para obter mais informações sobre impressão nos Windows Forms usando o <xref:System.Drawing.Printing.PrintDocument> componente, consulte [como: Criar trabalhos de impressão padrão do Windows Forms](how-to-create-standard-windows-forms-print-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="f96c3-106">For more information about printing from Windows Forms using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Create Standard Windows Forms Print Jobs](how-to-create-standard-windows-forms-print-jobs.md).</span></span>  
  
### <a name="to-complete-a-print-job"></a><span data-ttu-id="f96c3-107">Para concluir um trabalho de impressão</span><span class="sxs-lookup"><span data-stu-id="f96c3-107">To complete a print job</span></span>  
  
1. <span data-ttu-id="f96c3-108">Defina as <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> propriedade do <xref:System.Drawing.Printing.PrintDocument> componente.</span><span class="sxs-lookup"><span data-stu-id="f96c3-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. <span data-ttu-id="f96c3-109">Escrever código para manipular o <xref:System.Drawing.Printing.PrintDocument.EndPrint> eventos.</span><span class="sxs-lookup"><span data-stu-id="f96c3-109">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event.</span></span>  
  
     <span data-ttu-id="f96c3-110">No exemplo de código a seguir, uma caixa de mensagem é exibida, indicando que o documento terminou a impressão.</span><span class="sxs-lookup"><span data-stu-id="f96c3-110">In the following code example, a message box is displayed, indicating that the document has finished printing.</span></span>  
  
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
  
     <span data-ttu-id="f96c3-111">(Visual c# e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="f96c3-111">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f96c3-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f96c3-112">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="f96c3-113">Suporte à impressão no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f96c3-113">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
