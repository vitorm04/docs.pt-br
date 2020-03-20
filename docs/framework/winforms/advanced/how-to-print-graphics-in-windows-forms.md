---
title: 'Como: Imprimir gráficos'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 15f3a507839430ce058302e7f5abd317ef84626f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182530"
---
# <a name="how-to-print-graphics-in-windows-forms"></a>Como imprimir elementos gráficos no Windows Forms
Frequentemente, você vai querer imprimir gráficos em seu aplicativo baseado no Windows. A <xref:System.Drawing.Graphics> classe fornece métodos para desenhar objetos para um dispositivo, como uma tela ou impressora.  
  
### <a name="to-print-graphics"></a>Para imprimir gráficos  
  
1. Adicione <xref:System.Drawing.Printing.PrintDocument> um componente ao seu formulário.  
  
2. No <xref:System.Drawing.Printing.PrintDocument.PrintPage> manipulador de eventos, use a <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> propriedade da <xref:System.Drawing.Printing.PrintPageEventArgs> classe para instruir a impressora sobre que tipo de gráficos imprimir.  
  
     O exemplo de código a seguir mostra um manipulador de eventos usado para criar uma elipse azul dentro de um retângulo delimitador. O retângulo tem a seguinte localização e dimensões: começando em 100, 150 com uma largura de 250 e uma altura de 250.  
  
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
  
     (Visual C# e Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Suporte à impressão no Windows Forms](windows-forms-print-support.md)
