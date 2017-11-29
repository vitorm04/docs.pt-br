---
title: "Como determinar propriedades de página usando o componente PageSetupDialog"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- page properties
- page setup
- PageSetupDialog component
ms.assetid: 6dae05bc-c0fd-4357-bb93-841a1631d98f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e7dc3603d37106c122f3e92503b37dcfc02d7fef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a>Como determinar propriedades de página usando o componente PageSetupDialog
O componente [PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) apresenta o layout, tamanho do papel e outras opções de layout da página ao usuário para um documento.  
  
 Você precisa especificar uma instância do <xref:System.Drawing.Printing.PrintDocument> classe — este é o documento a ser impresso. Além disso, os usuários devem ter uma impressora instalada no computador, localmente ou por meio de uma rede, pois é parcialmente como o <xref:System.Windows.Forms.PageSetupDialog> componente determina a página formatação apresentadas ao usuário.  
  
 Um aspecto importante de trabalhar com o <xref:System.Windows.Forms.PageSetupDialog> componente é como ele interage com o <xref:System.Drawing.Printing.PageSettings> classe. O <xref:System.Drawing.Printing.PageSettings> classe é usada para especificar as configurações que modificam a maneira como uma página será impressa, como a orientação do papel, o tamanho da página e as margens. Cada uma dessas configurações é representada como uma propriedade de <xref:System.Drawing.Printing.PageSettings> classe. O <xref:System.Windows.Forms.PageSetupDialog> classe modifica esses valores de propriedade para uma determinada instância do <xref:System.Drawing.Printing.PageSettings> classe que está associado com o documento (e é representado como um <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> propriedade).  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a>Para determinar propriedades de página usando o componente PageSetupDialog  
  
1.  Use o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo, especificando o <xref:System.Drawing.Printing.PrintDocument> para usar.  
  
     No exemplo a seguir, o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Click> manipulador de eventos abre uma instância do <xref:System.Windows.Forms.PageSetupDialog> componente. Um documento existente é especificado no <xref:System.Windows.Forms.PageSetupDialog.Document%2A> propriedade e seu <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> está definida como `false`.  
  
     O exemplo supõe que o formulário tem uma <xref:System.Windows.Forms.Button> controle, uma <xref:System.Drawing.Printing.PrintDocument> componente denominado `myDocument`e um <xref:System.Windows.Forms.PageSetupDialog> componente.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [Como Criar Trabalhos de Impressão Padrão dos Windows Forms](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [Componente PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
