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
ms.openlocfilehash: d9607de7c74132e0d7dce605b16d62c79b7dbccb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182577"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Como criar trabalhos de impressão padrão do Windows Forms
A base da impressão no <xref:System.Drawing.Printing.PrintDocument> Windows Forms é <xref:System.Drawing.Printing.PrintDocument.PrintPage> o componente — mais especificamente, o evento. Ao escrever código <xref:System.Drawing.Printing.PrintDocument.PrintPage> para lidar com o evento, você pode especificar o que imprimir e como imprimi-lo.  
  
### <a name="to-create-a-print-job"></a>Para criar um trabalho de impressão  
  
1. Adicione <xref:System.Drawing.Printing.PrintDocument> um componente ao seu formulário.  
  
2. Escreva código para <xref:System.Drawing.Printing.PrintDocument.PrintPage> lidar com o evento.  
  
     Você terá de codificar sua própria lógica de impressão. Além disso, precisará especificar o material a ser impresso.  
  
     No exemplo de código a seguir, um gráfico de amostra na <xref:System.Drawing.Printing.PrintDocument.PrintPage> forma de um retângulo vermelho é criado no manipulador de eventos para agir como material a ser impresso.  
  
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
  
     (Visual C# e Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
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
  
     Você também pode querer escrever <xref:System.Drawing.Printing.PrintDocument.BeginPrint> <xref:System.Drawing.Printing.PrintDocument.EndPrint> código para os eventos e eventos, talvez incluindo um inteiro representando o número total de páginas para imprimir que é decretada à medida que cada página imprime.  
  
    > [!NOTE]
    > Você pode <xref:System.Windows.Forms.PrintDialog> adicionar um componente ao seu formulário para fornecer uma interface de usuário (UI) limpa e eficiente aos seus usuários. A <xref:System.Windows.Forms.PrintDialog.Document%2A> configuração <xref:System.Windows.Forms.PrintDialog> da propriedade do componente permite definir propriedades relacionadas ao documento de impressão com o que você está trabalhando em seu formulário. Para obter mais <xref:System.Windows.Forms.PrintDialog> informações sobre o componente, consulte [PrintDialog Component](../controls/printdialog-component-windows-forms.md).  
  
     Para obter mais informações sobre as especificidades dos trabalhos de impressão do <xref:System.Drawing.Printing.PrintPageEventArgs>Windows Forms, incluindo como criar um trabalho de impressão programáticamente, consulte .  
  
## <a name="see-also"></a>Confira também

- <xref:System.Drawing.Printing.PrintDocument>
- [Suporte à impressão no Windows Forms](windows-forms-print-support.md)
