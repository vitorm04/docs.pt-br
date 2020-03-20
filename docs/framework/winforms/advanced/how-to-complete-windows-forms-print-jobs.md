---
title: Trabalhos completos de impressão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: 62f67002bfbaf46e73bae06fdaff26efde865c06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182591"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>Como concluir trabalhos de impressão do Windows Forms
Frequentemente, processadores de texto e outros aplicativos que envolvem impressão fornecerão a opção para exibir uma mensagem aos usuários de que um trabalho de impressão foi concluído. Você pode fornecer essa funcionalidade em seus <xref:System.Drawing.Printing.PrintDocument.EndPrint> Formulários <xref:System.Drawing.Printing.PrintDocument> do Windows manipulando o evento do componente.  
  
 O procedimento a seguir exige que você tenha <xref:System.Drawing.Printing.PrintDocument> criado um aplicativo baseado no Windows com um componente nele, que é a maneira padrão de habilitar a impressão a partir de um aplicativo baseado no Windows. Para obter mais informações sobre <xref:System.Drawing.Printing.PrintDocument> a impressão de Formulários do Windows usando o componente, consulte [Como: Criar trabalhos padrão](how-to-create-standard-windows-forms-print-jobs.md)de impressão de formulários do Windows .  
  
### <a name="to-complete-a-print-job"></a>Para concluir um trabalho de impressão  
  
1. Defina <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> a <xref:System.Drawing.Printing.PrintDocument> propriedade do componente.  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. Escreva código para <xref:System.Drawing.Printing.PrintDocument.EndPrint> lidar com o evento.  
  
     No exemplo de código a seguir, uma caixa de mensagem é exibida, indicando que o documento terminou a impressão.  
  
    ```vb  
    Private Sub PrintDocument1_EndPrint(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintEventArgs) Handles PrintDocument1.EndPrint  
       MessageBox.Show(PrintDocument1.DocumentName + " has finished printing.")  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_EndPrint(object sender,
    System.Drawing.Printing.PrintEventArgs e)  
    {  
       MessageBox.Show(printDocument1.DocumentName +
          " has finished printing.");  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_EndPrint(System::Object ^ sender,  
          System::Drawing::Printing::PrintEventArgs ^ e)  
       {  
          MessageBox::Show(String::Concat(printDocument1->DocumentName,  
             " has finished printing."));  
       }  
    ```  
  
     (Visual C# e Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.printDocument1.EndPrint += new  
       System.Drawing.Printing.PrintEventHandler  
       (this.printDocument1_EndPrint);  
    ```  
  
    ```cpp  
    this->printDocument1->EndPrint += gcnew  
       System::Drawing::Printing::PrintEventHandler  
       (this, &Form1::printDocument1_EndPrint);  
    ```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Drawing.Printing.PrintDocument>
- [Suporte à impressão no Windows Forms](windows-forms-print-support.md)
