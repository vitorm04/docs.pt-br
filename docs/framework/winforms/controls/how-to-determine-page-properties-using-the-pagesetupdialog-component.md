---
title: Como determinar propriedades de página usando o componente PageSetupDialog
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
ms.openlocfilehash: 8a015c199193dfd9c43bec53cc93cbf9dc201413
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142037"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a>Como determinar propriedades de página usando o componente PageSetupDialog
O componente [PageSetupDialog](pagesetupdialog-component-windows-forms.md) apresenta o layout, tamanho do papel e outras opções de layout da página ao usuário para um documento.  
  
 Você precisa especificar uma <xref:System.Drawing.Printing.PrintDocument> instância da classe — este é o documento a ser impresso. Além disso, os usuários devem ter uma impressora instalada em seu computador, localmente <xref:System.Windows.Forms.PageSetupDialog> ou através de uma rede, pois é em parte assim que o componente determina as escolhas de formatação de página apresentadas ao usuário.  
  
 Um aspecto importante do <xref:System.Windows.Forms.PageSetupDialog> trabalho com o componente <xref:System.Drawing.Printing.PageSettings> é como ele interage com a classe. A <xref:System.Drawing.Printing.PageSettings> classe é usada para especificar configurações que modificam a forma como uma página será impressa, como orientação de papel, o tamanho da página e as margens. Cada uma dessas configurações é representada <xref:System.Drawing.Printing.PageSettings> como uma propriedade da classe. A <xref:System.Windows.Forms.PageSetupDialog> classe modifica esses valores de <xref:System.Drawing.Printing.PageSettings> propriedade para uma determinada instância da classe <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> que está associada ao documento (e é representada como uma propriedade).  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a>Para determinar propriedades de página usando o componente PageSetupDialog  
  
1. Use <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> o método para exibir a <xref:System.Drawing.Printing.PrintDocument> caixa de diálogo, especificando o uso.  
  
     No exemplo abaixo, <xref:System.Windows.Forms.Button> o <xref:System.Windows.Forms.Control.Click> manipulador de eventos do <xref:System.Windows.Forms.PageSetupDialog> controle abre uma instância do componente. Um documento existente é especificado na <xref:System.Windows.Forms.PageSetupDialog.Document%2A> <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> propriedade, e `false`sua propriedade é definida como .  
  
     O exemplo pressupõe <xref:System.Windows.Forms.Button> que seu <xref:System.Drawing.Printing.PrintDocument> formulário `myDocument`tenha <xref:System.Windows.Forms.PageSetupDialog> um controle, um componente chamado e um componente.  
  
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
  
     (Visual C# e Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.PageSetupDialog>
- [Como Criar Trabalhos de Impressão Padrão dos Windows Forms](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [Componente PageSetupDialog](pagesetupdialog-component-windows-forms.md)
