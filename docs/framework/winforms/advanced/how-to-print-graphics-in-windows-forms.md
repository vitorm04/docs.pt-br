---
title: Como imprimir elementos gráficos no Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 8281e1e0a3d350c3b81e26bbe59c098536ef064e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-print-graphics-in-windows-forms"></a>Como imprimir elementos gráficos no Windows Forms
Frequentemente, você desejará imprimir elementos gráficos no seu aplicativo do Windows. O <xref:System.Drawing.Graphics> classe fornece métodos para desenhar objetos em um dispositivo, como uma tela ou impressora.  
  
### <a name="to-print-graphics"></a>Imprimir elementos gráficos  
  
1.  Adicionar um <xref:System.Drawing.Printing.PrintDocument> componente para seu formulário.  
  
2.  No <xref:System.Drawing.Printing.PrintDocument.PrintPage> manipulador de eventos, use o <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> propriedade o <xref:System.Drawing.Printing.PrintPageEventArgs> classe para instruir a impressora sobre o tipo de gráfico para imprimir.  
  
     O exemplo de código a seguir mostra um manipulador de eventos usado para criar uma elipse azul dentro de um retângulo delimitador. O retângulo tem as seguintes posição e dimensões: começando em 100, 150 com uma largura de 250 e altura de 250.  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillEllipse(Brushes.Blue, New Rectangle(100, 150, 250, 250))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Blue,   
         new Rectangle(100, 150, 250, 250));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Blue,  
             Rectangle(100, 150, 250, 250));  
       }  
    ```  
  
     (Visual c# e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Brush>  
 [Suporte à impressão nos Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
