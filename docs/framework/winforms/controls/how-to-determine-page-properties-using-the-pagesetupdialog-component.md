---
title: 'Como: Determinar propriedades de página usando o componente PageSetupDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- page properties
- page setup
- PageSetupDialog component
ms.assetid: 6dae05bc-c0fd-4357-bb93-841a1631d98f
ms.openlocfilehash: 7c65eb54bb95b9a20cd1e43f0d491af47985f2e0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329200"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a>Como: Determinar propriedades de página usando o componente PageSetupDialog
O componente [PageSetupDialog](pagesetupdialog-component-windows-forms.md) apresenta o layout, tamanho do papel e outras opções de layout da página ao usuário para um documento.  
  
 Você precisa especificar uma instância da <xref:System.Drawing.Printing.PrintDocument> classe — este é o documento a ser impresso. Além disso, os usuários devem ter uma impressora instalada em seu computador, localmente ou através de uma rede, pois isso é parcialmente como o <xref:System.Windows.Forms.PageSetupDialog> componente determina a formatação opções apresentadas ao usuário da página.  
  
 Um aspecto importante de trabalhar com o <xref:System.Windows.Forms.PageSetupDialog> componente é como ele interage com o <xref:System.Drawing.Printing.PageSettings> classe. O <xref:System.Drawing.Printing.PageSettings> classe é usada para especificar configurações que modificam a maneira que uma página será impressa, como a orientação do papel, o tamanho da página e as margens. Cada uma dessas configurações é representada como uma propriedade do <xref:System.Drawing.Printing.PageSettings> classe. O <xref:System.Windows.Forms.PageSetupDialog> classe modifica esses valores de propriedade para uma determinada instância das <xref:System.Drawing.Printing.PageSettings> classe, que está associada ao documento (e é representado como um <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> propriedade).  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a>Para determinar propriedades de página usando o componente PageSetupDialog  
  
1. Use o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo, especificando o <xref:System.Drawing.Printing.PrintDocument> usar.  
  
     No exemplo a seguir, o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Click> manipulador de eventos abre uma instância da <xref:System.Windows.Forms.PageSetupDialog> componente. Um documento existente é especificado na <xref:System.Windows.Forms.PageSetupDialog.Document%2A> propriedade e sua <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> estiver definida como `false`.  
  
     O exemplo supõe que seu formulário tem um <xref:System.Windows.Forms.Button> controle, um <xref:System.Drawing.Printing.PrintDocument> componente denominado `myDocument`e um <xref:System.Windows.Forms.PageSetupDialog> componente.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       'You will have to specify your own print document.  
       PageSetupDialog1.Document = myDocument  
       ' Sets the print document's color setting to false,  
       ' so that the page will not be printed in color.  
       PageSetupDialog1.Document.DefaultPageSettings.Color = False  
       PageSetupDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       pageSetupDialog1.Document = myDocument;  
       // Sets the print document's color setting to false,  
       // so that the page will not be printed in color.  
       pageSetupDialog1.Document.DefaultPageSettings.Color = false;  
       pageSetupDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button1_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          pageSetupDialog1->Document = myDocument;  
          // Sets the print document's color setting to false,  
          // so that the page will not be printed in color.  
          pageSetupDialog1->Document->DefaultPageSettings->Color = false;  
          pageSetupDialog1->ShowDialog();  
       }  
    ```  
  
     (Visual c# e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.PageSetupDialog>
- [Como: criar trabalhos de impressão padrão do Windows Forms](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [Componente PageSetupDialog](pagesetupdialog-component-windows-forms.md)
