---
title: Como inserir aspas em uma cadeia de caracteres
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: c14747291d6c41144eef97b258f852bbe14ef07d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735904"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a>Como inserir aspas em uma cadeia de caracteres (Windows Forms)
Às vezes, você pode querer colocar aspas (" ") em uma cadeia de caracteres de texto. Por exemplo:  
  
 Ela disse: "Você merece um agrado!"  
  
 Como alternativa, você também pode usar o campo <xref:Microsoft.VisualBasic.ControlChars.Quote> como uma constante.  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a>Para colocar as aspas em uma cadeia de caracteres no código  
  
1. Em Visual Basic, insira duas aspas em uma linha como uma aspa incorporada. No Visual C# e Visual C++, insira a sequência de escape \\"como uma aspa incorporada. Por exemplo, para criar a cadeia de caracteres anterior, use o código a seguir.  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     - ou -  
  
2. Insira o caractere ASCII ou Unicode para aspas. Em Visual Basic, use o caractere ASCII (34). No Visual C#, use o caractere Unicode (\u0022).  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    > Neste exemplo, não é possível usar \u0022 porque você não pode usar um nome de caractere universal que designa um caractere no conjunto de caracteres básicos. Caso contrário, você produz C3851. Para obter mais informações, consulte [Erro do compilador C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).  
  
     - ou -  
  
3. Você também pode definir uma constante para o caractere e usá-la quando necessário.  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [Visão geral do controle TextBox](textbox-control-overview-windows-forms.md)
- [Como controlar o ponto de inserção em um controle TextBox dos Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Como criar uma caixa de texto de senha com o controle TextBox dos Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Como criar uma caixa de texto somente leitura](how-to-create-a-read-only-text-box-windows-forms.md)
- [Como selecionar texto no controle TextBox dos Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Como exibir várias linhas no controle TextBox dos Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Controle TextBox](textbox-control-windows-forms.md)
