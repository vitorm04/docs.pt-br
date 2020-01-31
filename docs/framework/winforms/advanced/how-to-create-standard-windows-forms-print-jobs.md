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
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Como criar trabalhos de impressão padrão do Windows Forms
A base da impressão no Windows Forms é o componente <xref:System.Drawing.Printing.PrintDocument> – mais especificamente, o evento <xref:System.Drawing.Printing.PrintDocument.PrintPage>. Ao escrever código para manipular o evento de <xref:System.Drawing.Printing.PrintDocument.PrintPage>, você pode especificar o que imprimir e como imprimi-lo.  
  
### <a name="to-create-a-print-job"></a>Para criar um trabalho de impressão  
  
1. Adicione um componente <xref:System.Drawing.Printing.PrintDocument> ao formulário.  
  
2. Escreva o código para manipular o evento <xref:System.Drawing.Printing.PrintDocument.PrintPage>.  
  
     Você terá de codificar sua própria lógica de impressão. Além disso, precisará especificar o material a ser impresso.  
  
     No exemplo de código a seguir, um gráfico de exemplo na forma de um retângulo vermelho é criado no manipulador de eventos <xref:System.Drawing.Printing.PrintDocument.PrintPage> para atuar como material a ser impresso.  
  
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
  
     (Visual C# e Visual C++) Coloque o código a seguir no construtor do formulário para registrar o manipulador de eventos.  
  
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
  
     Talvez você também queira escrever código para os eventos <xref:System.Drawing.Printing.PrintDocument.BeginPrint> e <xref:System.Drawing.Printing.PrintDocument.EndPrint>, talvez incluindo um inteiro que representa o número total de páginas a serem impressas, uma vez que cada página é impressa.  
  
    > [!NOTE]
    > Você pode adicionar um componente <xref:System.Windows.Forms.PrintDialog> ao formulário para fornecer uma interface do usuário (IU) limpa e eficiente aos seus usuários. Definir a propriedade <xref:System.Windows.Forms.PrintDialog.Document%2A> do componente <xref:System.Windows.Forms.PrintDialog> permite que você defina as propriedades relacionadas ao documento de impressão com o qual você está trabalhando no formulário. Para obter mais informações sobre o componente <xref:System.Windows.Forms.PrintDialog>, consulte [componente PrintDialog](../controls/printdialog-component-windows-forms.md).  
  
     Para obter mais informações sobre as especificidades de Windows Forms trabalhos de impressão, incluindo como criar um trabalho de impressão programaticamente, consulte <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Drawing.Printing.PrintDocument>
- [Suporte à impressão nos Windows Forms](windows-forms-print-support.md)
