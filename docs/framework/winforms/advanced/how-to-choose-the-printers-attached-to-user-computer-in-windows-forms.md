---
title: 'Como: escolher as impressoras conectadas ao computador de um usuário no Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: bebb879020e6e45e77f109bf9c377b7322d5e8f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184022"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a><span data-ttu-id="a4c16-102">Como: escolher as impressoras conectadas ao computador de um usuário no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a4c16-102">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>
<span data-ttu-id="a4c16-103">Geralmente, os usuários escolhem uma impressora diferente da impressora padrão para imprimir.</span><span class="sxs-lookup"><span data-stu-id="a4c16-103">Often, users want to choose a printer other than the default printer to print to.</span></span> <span data-ttu-id="a4c16-104">Você pode habilitar os usuários escolham uma impressora dentre as instaladas no momento usando o <xref:System.Windows.Forms.PrintDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="a4c16-104">You can enable users to choose a printer from among those currently installed by using the <xref:System.Windows.Forms.PrintDialog> component.</span></span> <span data-ttu-id="a4c16-105">Por meio de <xref:System.Windows.Forms.PrintDialog> componente, o <xref:System.Windows.Forms.DialogResult> da <xref:System.Windows.Forms.PrintDialog> componente é capturado e usado para selecionar a impressora.</span><span class="sxs-lookup"><span data-stu-id="a4c16-105">Through the <xref:System.Windows.Forms.PrintDialog> component, the <xref:System.Windows.Forms.DialogResult> of the <xref:System.Windows.Forms.PrintDialog> component is captured and used to select the printer.</span></span>  
  
 <span data-ttu-id="a4c16-106">No procedimento a seguir, um arquivo de texto é selecionado para ser impresso na impressora padrão.</span><span class="sxs-lookup"><span data-stu-id="a4c16-106">In the following procedure, a text file is selected to be printed to the default printer.</span></span> <span data-ttu-id="a4c16-107">O <xref:System.Windows.Forms.PrintDialog> classe é então instanciada.</span><span class="sxs-lookup"><span data-stu-id="a4c16-107">The <xref:System.Windows.Forms.PrintDialog> class is then instantiated.</span></span>  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a><span data-ttu-id="a4c16-108">Para escolher uma impressora e imprimir um arquivo</span><span class="sxs-lookup"><span data-stu-id="a4c16-108">To choose a printer and then print a file</span></span>  
  
1.  <span data-ttu-id="a4c16-109">Selecione a impressora a ser usada com o <xref:System.Windows.Forms.PrintDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="a4c16-109">Select the printer to be used using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
     <span data-ttu-id="a4c16-110">No exemplo de código a seguir, há dois eventos que estão sendo manipulados.</span><span class="sxs-lookup"><span data-stu-id="a4c16-110">In the following code example, there are two events being handled.</span></span> <span data-ttu-id="a4c16-111">No primeiro, um <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Click> evento, o <xref:System.Windows.Forms.PrintDialog> classe é instanciada e a impressora selecionada pelo usuário é capturada no <xref:System.Windows.Forms.DialogResult> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a4c16-111">In the first, a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event, the <xref:System.Windows.Forms.PrintDialog> class is instantiated and the printer selected by the user is captured in the <xref:System.Windows.Forms.DialogResult> property.</span></span>  
  
     <span data-ttu-id="a4c16-112">No segundo evento, o <xref:System.Drawing.Printing.PrintDocument.PrintPage> eventos do <xref:System.Drawing.Printing.PrintDocument> componente, um documento de exemplo é impresso na impressora especificada.</span><span class="sxs-lookup"><span data-stu-id="a4c16-112">In the second event, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event of the <xref:System.Drawing.Printing.PrintDocument> component, a sample document is printed to the printer specified.</span></span>  
  
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
  
     <span data-ttu-id="a4c16-113">(Visual c# e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="a4c16-113">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a4c16-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4c16-114">See also</span></span>

- [<span data-ttu-id="a4c16-115">Suporte à impressão no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a4c16-115">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
