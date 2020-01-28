---
title: Exibir visualização de impressão em aplicativos Windows Forms
titleSuffix: ''
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
ms.openlocfilehash: ac02339ad86e491cd047dcd4b0c8841374b3bb2e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745576"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Como exibir visualização de impressão em aplicativos dos Windows Forms
Você pode usar o controle de <xref:System.Windows.Forms.PrintPreviewDialog> para permitir que os usuários exibam um documento, geralmente antes de serem impressos.  
  
 Para fazer isso, você precisa especificar uma instância da classe <xref:System.Drawing.Printing.PrintDocument>; Este é o documento a ser impresso. Para obter mais informações sobre como usar a visualização de impressão com o componente <xref:System.Drawing.Printing.PrintDocument>, consulte [como imprimir em Windows Forms usando a visualização de impressão](../advanced/how-to-print-in-windows-forms-using-print-preview.md).  
  
> [!NOTE]
> Para usar o controle de <xref:System.Windows.Forms.PrintPreviewDialog> em tempo de execução, os usuários devem ter uma impressora instalada em seu computador, seja localmente ou por meio de uma rede, pois isso faz parte de como o componente de <xref:System.Windows.Forms.PrintPreviewDialog> determina como será a aparência de um documento quando impresso.  
  
 O controle <xref:System.Windows.Forms.PrintPreviewDialog> usa a classe <xref:System.Drawing.Printing.PrinterSettings>. Além disso, o controle de <xref:System.Windows.Forms.PrintPreviewDialog> usa a classe <xref:System.Drawing.Printing.PageSettings>, assim como o componente de <xref:System.Windows.Forms.PrintPreviewDialog>. O documento de impressão especificado na propriedade <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> do controle de <xref:System.Windows.Forms.PrintPreviewDialog> se refere a instâncias das classes <xref:System.Drawing.Printing.PrinterSettings> e <xref:System.Drawing.Printing.PageSettings>, e elas são usadas para renderizar o documento na janela de visualização.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Para exibir páginas usando o controle PrintPreviewDialog  
  
- Use o método <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> para exibir a caixa de diálogo, especificando o <xref:System.Drawing.Printing.PrintDocument> a ser usado.  
  
     No exemplo de código a seguir, o manipulador de eventos <xref:System.Windows.Forms.Control.Click> do controle de <xref:System.Windows.Forms.Button> abre uma instância do controle de <xref:System.Windows.Forms.PrintPreviewDialog>. O documento de impressão é especificado na propriedade <xref:System.Windows.Forms.PrintDialog.Document%2A>. No exemplo a seguir, nenhum documento de impressão é especificado.  
  
     O exemplo requer que o formulário tenha um controle de <xref:System.Windows.Forms.Button>, um componente de <xref:System.Drawing.Printing.PrintDocument> chamado `myDocument`e um controle de <xref:System.Windows.Forms.PrintPreviewDialog>.  
  
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
  
     (Visual C#, Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Veja também

- [Componente PrintDocument](printdocument-component-windows-forms.md)
- [Controle PrintPreviewDialog](printpreviewdialog-control-windows-forms.md)
- [Suporte à impressão nos Windows Forms](../advanced/windows-forms-print-support.md)
- [Windows Forms](../index.md)
