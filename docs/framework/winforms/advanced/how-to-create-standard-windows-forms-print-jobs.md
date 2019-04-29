---
title: 'Como: criar trabalhos de impressão padrão do Windows Forms'
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
ms.openlocfilehash: 816da93218e20f73f16c14769ed1a549dd3d8eb3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937651"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Como: criar trabalhos de impressão padrão do Windows Forms
O fundamento da impressão nos Windows Forms é a <xref:System.Drawing.Printing.PrintDocument> componente — mais especificamente, o <xref:System.Drawing.Printing.PrintDocument.PrintPage> eventos. Escrevendo código para manipular o <xref:System.Drawing.Printing.PrintDocument.PrintPage> evento, você pode especificar o que imprimir e como imprimi-lo.  
  
### <a name="to-create-a-print-job"></a>Para criar um trabalho de impressão  
  
1. Adicionar um <xref:System.Drawing.Printing.PrintDocument> ao seu formulário.  
  
2. Escrever código para manipular o <xref:System.Drawing.Printing.PrintDocument.PrintPage> eventos.  
  
     Você terá de codificar sua própria lógica de impressão. Além disso, precisará especificar o material a ser impresso.  
  
     Exemplo de código a seguir, uma amostra de gráfico na forma de um retângulo vermelho é criada no <xref:System.Drawing.Printing.PrintDocument.PrintPage> manipulador de eventos para atuar como material a ser impresso.  
  
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
  
     (Visual c# e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
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
  
     Talvez você queira escrever código para o <xref:System.Drawing.Printing.PrintDocument.BeginPrint> e <xref:System.Drawing.Printing.PrintDocument.EndPrint> eventos, talvez incluindo um inteiro que representa o número total de páginas para impressão que é reduzido à medida que cada página é impressa.  
  
    > [!NOTE]
    >  Você pode adicionar um <xref:System.Windows.Forms.PrintDialog> ao seu formulário para fornecer uma interface clara e eficiente de usuário (UI) para seus usuários. Definindo o <xref:System.Windows.Forms.PrintDialog.Document%2A> propriedade do <xref:System.Windows.Forms.PrintDialog> habilita componente que você defina propriedades relacionadas ao imprimir documento você está trabalhando com em seu formulário. Para obter mais informações sobre o <xref:System.Windows.Forms.PrintDialog> componente, consulte [componente PrintDialog](../controls/printdialog-component-windows-forms.md).  
  
     Para obter mais informações sobre as especificidades dos Windows Forms trabalhos de impressão, incluindo como criar um trabalho de impressão de forma programática, consulte <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Printing.PrintDocument>
- [Suporte à impressão nos Windows Forms](windows-forms-print-support.md)
