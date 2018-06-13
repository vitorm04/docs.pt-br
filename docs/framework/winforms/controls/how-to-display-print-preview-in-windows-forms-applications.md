---
title: Como exibir visualização de impressão em aplicativos dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
ms.openlocfilehash: 1c1291ea675d823fab3052b0fa365cb2d4c31088
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532802"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Como exibir visualização de impressão em aplicativos dos Windows Forms
Você pode usar o <xref:System.Windows.Forms.PrintPreviewDialog> controle para permitir que os usuários exibam um documento, geralmente antes de que é impressa.  
  
 Para fazer isso, você precisa especificar uma instância do <xref:System.Drawing.Printing.PrintDocument> classe; este é o documento a ser impresso. Para obter mais informações sobre como usar a visualização de impressão com o <xref:System.Drawing.Printing.PrintDocument> componente, consulte [como: imprimir no Windows Forms usando impressão Preview](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md).  
  
> [!NOTE]
>  Para usar o <xref:System.Windows.Forms.PrintPreviewDialog> controle em tempo de execução, os usuários devem ter uma impressora instalada no computador, localmente ou por meio de uma rede, pois é parcialmente como o <xref:System.Windows.Forms.PrintPreviewDialog> componente determina a aparência de um documento quando impresso.  
  
 O <xref:System.Windows.Forms.PrintPreviewDialog> controlar usa o <xref:System.Drawing.Printing.PrinterSettings> classe. Além disso, o <xref:System.Windows.Forms.PrintPreviewDialog> controlar usa o <xref:System.Drawing.Printing.PageSettings> classe, assim como o <xref:System.Windows.Forms.PrintPreviewDialog> componente. O documento de impressão especificado no <xref:System.Windows.Forms.PrintPreviewDialog> do controle <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> propriedade refere-se a instâncias de ambos os <xref:System.Drawing.Printing.PrinterSettings> e <xref:System.Drawing.Printing.PageSettings> classes e elas são usadas para renderizar o documento na janela de visualização.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Para exibir páginas usando o controle PrintPreviewDialog  
  
-   Use o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo, especificando o <xref:System.Drawing.Printing.PrintDocument> para usar.  
  
     No exemplo de código a seguir, o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Click> manipulador de eventos abre uma instância do <xref:System.Windows.Forms.PrintPreviewDialog> controle. O documento de impressão é especificado no <xref:System.Windows.Forms.PrintDialog.Document%2A> propriedade. No exemplo a seguir, nenhum documento de impressão é especificado.  
  
     O exemplo requer que o formulário tem uma <xref:System.Windows.Forms.Button> controle, uma <xref:System.Drawing.Printing.PrintDocument> componente denominado `myDocument`e um <xref:System.Windows.Forms.PrintPreviewDialog> controle.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       ' You will have to specify your own print document.  
       PrintPreviewDialog1.Document = myDocument  
       PrintPreviewDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       printPreviewDialog1.Document = myDocument;  
       printPreviewDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          printPreviewDialog1->Document = myDocument;  
          printPreviewDialog1->ShowDialog();  
       }  
    ```  
  
     (Visual c# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Componente PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 [Controle PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [Suporte à impressão nos Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
