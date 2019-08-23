---
title: 'Como: Exibir visualização de impressão em aplicativos do Windows Forms'
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
ms.openlocfilehash: 8252906de9a574f49617609a4cb08a1e8aa6a992
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929001"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Como: Exibir visualização de impressão em aplicativos do Windows Forms
Você pode usar o <xref:System.Windows.Forms.PrintPreviewDialog> controle para permitir que os usuários exibam um documento, geralmente antes de serem impressos.  
  
 Para fazer isso, você precisa especificar uma instância da <xref:System.Drawing.Printing.PrintDocument> classe; este é o documento a ser impresso. Para obter mais informações sobre como usar a visualização <xref:System.Drawing.Printing.PrintDocument> de impressão com [o componente, consulte Como: Imprima no Windows Forms usando a visualização](../advanced/how-to-print-in-windows-forms-using-print-preview.md)de impressão.  
  
> [!NOTE]
> Para usar o <xref:System.Windows.Forms.PrintPreviewDialog> controle em tempo de execução, os usuários devem ter uma impressora instalada em seu computador, seja localmente ou por meio de uma rede, pois isso faz <xref:System.Windows.Forms.PrintPreviewDialog> parte de como o componente determina como será a aparência de um documento quando impresso.  
  
 O <xref:System.Windows.Forms.PrintPreviewDialog> controle usa a <xref:System.Drawing.Printing.PrinterSettings> classe. Além disso, <xref:System.Windows.Forms.PrintPreviewDialog> o controle usa <xref:System.Drawing.Printing.PageSettings> a classe, assim como <xref:System.Windows.Forms.PrintPreviewDialog> faz o componente. O documento de impressão especificado na <xref:System.Windows.Forms.PrintPreviewDialog> Propriedade do <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> controle refere-se <xref:System.Drawing.Printing.PrinterSettings> às instâncias das classes <xref:System.Drawing.Printing.PageSettings> e, que são usadas para renderizar o documento na janela de visualização.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Para exibir páginas usando o controle PrintPreviewDialog  
  
- Use o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo, especificando <xref:System.Drawing.Printing.PrintDocument> o a ser usado.  
  
     No exemplo de código a seguir, <xref:System.Windows.Forms.Button> o manipulador <xref:System.Windows.Forms.Control.Click> de eventos do controle <xref:System.Windows.Forms.PrintPreviewDialog> abre uma instância do controle. O documento de impressão é especificado na <xref:System.Windows.Forms.PrintDialog.Document%2A> propriedade. No exemplo a seguir, nenhum documento de impressão é especificado.  
  
     O exemplo requer que o formulário tenha um <xref:System.Windows.Forms.Button> controle, um <xref:System.Drawing.Printing.PrintDocument> componente chamado `myDocument`e um <xref:System.Windows.Forms.PrintPreviewDialog> controle.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Componente PrintDocument](printdocument-component-windows-forms.md)
- [Controle PrintPreviewDialog](printpreviewdialog-control-windows-forms.md)
- [Suporte à impressão nos Windows Forms](../advanced/windows-forms-print-support.md)
- [Windows Forms](../index.md)
