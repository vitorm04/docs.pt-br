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
ms.openlocfilehash: cfdc8d21b3ddad19fd38eef9cb1c506920da9de6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609893"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Como: Exibir visualização de impressão em aplicativos do Windows Forms
Você pode usar o <xref:System.Windows.Forms.PrintPreviewDialog> controle para permitir que os usuários exibam um documento, muitas vezes antes que seja a ser impresso.  
  
 Para fazer isso, você precisa especificar uma instância da <xref:System.Drawing.Printing.PrintDocument> classe; este é o documento a ser impresso. Para obter mais informações sobre como usar a visualização de impressão com o <xref:System.Drawing.Printing.PrintDocument> componente, consulte [como: Impressão no Windows Forms usando Visualizar impressão](../advanced/how-to-print-in-windows-forms-using-print-preview.md).  
  
> [!NOTE]
>  Para usar o <xref:System.Windows.Forms.PrintPreviewDialog> controle em tempo de execução, os usuários devem ter uma impressora instalada em seu computador, localmente ou através de uma rede, pois isso é parcialmente como o <xref:System.Windows.Forms.PrintPreviewDialog> componente determina qual será a aparência de um documento quando impresso.  
  
 O <xref:System.Windows.Forms.PrintPreviewDialog> controle usa o <xref:System.Drawing.Printing.PrinterSettings> classe. Além disso, o <xref:System.Windows.Forms.PrintPreviewDialog> controle usa o <xref:System.Drawing.Printing.PageSettings> classe, assim como o <xref:System.Windows.Forms.PrintPreviewDialog> componente faz. O documento de impressão especificado na <xref:System.Windows.Forms.PrintPreviewDialog> do controle <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> propriedade refere-se a instâncias de ambas as <xref:System.Drawing.Printing.PrinterSettings> e <xref:System.Drawing.Printing.PageSettings> classes e eles são usados para renderizar o documento na janela de visualização.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Para exibir páginas usando o controle PrintPreviewDialog  
  
- Use o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo, especificando o <xref:System.Drawing.Printing.PrintDocument> usar.  
  
     No exemplo de código a seguir, o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Click> manipulador de eventos abre uma instância da <xref:System.Windows.Forms.PrintPreviewDialog> controle. O documento de impressão é especificado no <xref:System.Windows.Forms.PrintDialog.Document%2A> propriedade. No exemplo a seguir, nenhum documento de impressão é especificado.  
  
     O exemplo requer que o formulário tem um <xref:System.Windows.Forms.Button> controle, um <xref:System.Drawing.Printing.PrintDocument> componente denominado `myDocument`e um <xref:System.Windows.Forms.PrintPreviewDialog> controle.  
  
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
  
     (Visual c#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
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
