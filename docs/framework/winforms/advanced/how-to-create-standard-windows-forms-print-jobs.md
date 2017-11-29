---
title: "Como criar trabalhos de impressão padrão do Windows Forms"
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
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c2b0ce30f76fe7f8cbdc156c4a8ff5abffafae10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Como criar trabalhos de impressão padrão do Windows Forms
É a base de impressão no Windows Forms a <xref:System.Drawing.Printing.PrintDocument> componente — mais especificamente, o <xref:System.Drawing.Printing.PrintDocument.PrintPage> evento. Escrevendo código para manipular o <xref:System.Drawing.Printing.PrintDocument.PrintPage> eventos, você pode especificar o que imprimir e como imprimi-lo.  
  
### <a name="to-create-a-print-job"></a>Para criar um trabalho de impressão  
  
1.  Adicionar um <xref:System.Drawing.Printing.PrintDocument> componente para seu formulário.  
  
2.  Escreva código para manipular o <xref:System.Drawing.Printing.PrintDocument.PrintPage> evento.  
  
     Você terá de codificar sua própria lógica de impressão. Além disso, precisará especificar o material a ser impresso.  
  
     No exemplo de código a seguir, uma amostra de gráfico na forma de um retângulo vermelho criado no <xref:System.Drawing.Printing.PrintDocument.PrintPage> manipulador de eventos para atuar como material a ser impresso.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
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
  
     Você também deseja escrever código para o <xref:System.Drawing.Printing.PrintDocument.BeginPrint> e <xref:System.Drawing.Printing.PrintDocument.EndPrint> eventos, talvez incluindo um inteiro que representa o número total de páginas para imprimir que é reduzido à medida que cada página impressa.  
  
    > [!NOTE]
    >  Você pode adicionar um <xref:System.Windows.Forms.PrintDialog> componente ao formulário para fornecer uma interface de usuário normal e eficiente (UI) para seus usuários. Definindo o <xref:System.Windows.Forms.PrintDialog.Document%2A> propriedade o <xref:System.Windows.Forms.PrintDialog> permite que o componente para definir as propriedades relacionadas ao imprimir documentos que você está trabalhando com do formulário. Para obter mais informações sobre o <xref:System.Windows.Forms.PrintDialog> componente, consulte [componente PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md).  
  
     Para obter mais informações sobre as especificações de Windows Forms trabalhos de impressão, incluindo como criar um trabalho de impressão programaticamente, consulte <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Suporte à impressão nos Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
