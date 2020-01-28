---
title: 'Como: escolher as impressoras anexadas ao computador de um usuário'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: 7fc2427468540ac0a1480f6140cbb34c3a0f1ab3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746504"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a><span data-ttu-id="8a1f9-102">Como escolher as impressoras conectadas ao computador de um usuário no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8a1f9-102">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>
<span data-ttu-id="8a1f9-103">Geralmente, os usuários escolhem uma impressora diferente da impressora padrão para imprimir.</span><span class="sxs-lookup"><span data-stu-id="8a1f9-103">Often, users want to choose a printer other than the default printer to print to.</span></span> <span data-ttu-id="8a1f9-104">Você pode permitir que os usuários escolham uma impressora dentre as que estão instaladas no momento usando o componente <xref:System.Windows.Forms.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="8a1f9-104">You can enable users to choose a printer from among those currently installed by using the <xref:System.Windows.Forms.PrintDialog> component.</span></span> <span data-ttu-id="8a1f9-105">Por meio do componente <xref:System.Windows.Forms.PrintDialog>, a <xref:System.Windows.Forms.DialogResult> do componente <xref:System.Windows.Forms.PrintDialog> é capturada e usada para selecionar a impressora.</span><span class="sxs-lookup"><span data-stu-id="8a1f9-105">Through the <xref:System.Windows.Forms.PrintDialog> component, the <xref:System.Windows.Forms.DialogResult> of the <xref:System.Windows.Forms.PrintDialog> component is captured and used to select the printer.</span></span>  
  
 <span data-ttu-id="8a1f9-106">No procedimento a seguir, um arquivo de texto é selecionado para ser impresso na impressora padrão.</span><span class="sxs-lookup"><span data-stu-id="8a1f9-106">In the following procedure, a text file is selected to be printed to the default printer.</span></span> <span data-ttu-id="8a1f9-107">Em seguida, a classe <xref:System.Windows.Forms.PrintDialog> é instanciada.</span><span class="sxs-lookup"><span data-stu-id="8a1f9-107">The <xref:System.Windows.Forms.PrintDialog> class is then instantiated.</span></span>  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a><span data-ttu-id="8a1f9-108">Para escolher uma impressora e imprimir um arquivo</span><span class="sxs-lookup"><span data-stu-id="8a1f9-108">To choose a printer and then print a file</span></span>  
  
1. <span data-ttu-id="8a1f9-109">Selecione a impressora a ser usada usando o componente <xref:System.Windows.Forms.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="8a1f9-109">Select the printer to be used using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
     <span data-ttu-id="8a1f9-110">No exemplo de código a seguir, há dois eventos que estão sendo manipulados.</span><span class="sxs-lookup"><span data-stu-id="8a1f9-110">In the following code example, there are two events being handled.</span></span> <span data-ttu-id="8a1f9-111">Na primeira, um evento de <xref:System.Windows.Forms.Control.Click> do controle de <xref:System.Windows.Forms.Button>, a classe <xref:System.Windows.Forms.PrintDialog> é instanciada e a impressora selecionada pelo usuário é capturada na propriedade <xref:System.Windows.Forms.DialogResult>.</span><span class="sxs-lookup"><span data-stu-id="8a1f9-111">In the first, a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event, the <xref:System.Windows.Forms.PrintDialog> class is instantiated and the printer selected by the user is captured in the <xref:System.Windows.Forms.DialogResult> property.</span></span>  
  
     <span data-ttu-id="8a1f9-112">No segundo evento, o evento <xref:System.Drawing.Printing.PrintDocument.PrintPage> do componente <xref:System.Drawing.Printing.PrintDocument>, um documento de exemplo é impresso na impressora especificada.</span><span class="sxs-lookup"><span data-stu-id="8a1f9-112">In the second event, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event of the <xref:System.Drawing.Printing.PrintDocument> component, a sample document is printed to the printer specified.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim PrintDialog1 As New PrintDialog()  
       PrintDialog1.Document = PrintDocument1  
       Dim result As DialogResult = PrintDialog1.ShowDialog()  
  
       If (result = DialogResult.OK) Then  
         PrintDocument1.Print()  
       End If   
  
    End Sub  
  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))          
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       PrintDialog printDialog1 = new PrintDialog();  
       printDialog1.Document = printDocument1;  
       DialogResult result = printDialog1.ShowDialog();  
       if (result == DialogResult.OK)  
       {  
          printDocument1.Print();  
       }  
    }  
  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          PrintDialog ^ printDialog1 = gcnew PrintDialog();  
          printDialog1->Document = printDocument1;  
          System::Windows::Forms::DialogResult result =   
             printDialog1->ShowDialog();  
          if (result == DialogResult::OK)  
          {  
             printDocument1->Print();  
          }  
       }  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     <span data-ttu-id="8a1f9-113">(Visual C# e Visual C++) Coloque o código a seguir no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="8a1f9-113">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8a1f9-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="8a1f9-114">See also</span></span>

- [<span data-ttu-id="8a1f9-115">Suporte à impressão nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8a1f9-115">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
