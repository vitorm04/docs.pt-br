---
title: Como determinar itens verificados no controle CheckedListBox dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 98b4ef7c4ac73e1560bd5c68f22898e46585d082
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Como determinar itens verificados no controle CheckedListBox dos Windows Forms
Ao apresentar dados em um Windows Forms <xref:System.Windows.Forms.CheckedListBox> controle, ou pode iterar por meio da coleção armazenada no <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> propriedade ou percorra a lista usando o <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> método para determinar quais itens são verificados. O <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> método recebe um número de índice do item como seu argumento e retorna `true` ou `false`. Ao contrário do que você esperava, o <xref:System.Windows.Forms.ListBox.SelectedItems%2A> e <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> propriedades não determinar quais itens são verificados; elas determinam quais itens são realçados.  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>Como determinar itens marcados em um controle CheckedListBox  
  
1.  Percorrer o <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> coleção, começando em 0 porque a coleção é baseada em zero. Observe que esse método lhe fornecerá o número de item na lista de itens marcados, não na lista global. Portanto, se o primeiro item na lista não estiver marcado e o segundo item estiver marcado, o código a seguir exibirá o texto como "Item marcado 1 = MyListItem2".  
  
    ```vb  
    ' Determine if there are any items checked.  
    If CheckedListBox1.CheckedItems.Count <> 0 Then  
       ' If so, loop through all checked items and print results.  
       Dim x As Integer  
       Dim s As String = ""  
       For x = 0 To CheckedListBox1.CheckedItems.Count - 1  
          s = s & "Checked Item " & (x + 1).ToString & " = " & CheckedListBox1.CheckedItems(x).ToString & ControlChars.CrLf  
       Next x  
       MessageBox.Show(s)  
    End If  
    ```  
  
    ```csharp  
    // Determine if there are any items checked.  
    if(checkedListBox1.CheckedItems.Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       string s = "";  
       for(int x = 0; x <= checkedListBox1.CheckedItems.Count - 1 ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
    MessageBox.Show (s);  
    }  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x <= checkedListBox1->CheckedItems->Count - 1; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     - ou –  
  
2.  Percorrer o <xref:System.Windows.Forms.CheckedListBox.Items%2A> coleção, começando em 0 porque a coleção é baseado em zero e chamar o <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> método para cada item. Observe que esse método lhe fornecerá o número de item na lista geral, portanto, se o primeiro item na lista não estiver marcado e o segundo item estiver marcado, ele exibirá algo como "Item 2 = MyListItem2".  
  
    ```vb  
    Dim i As Integer  
    Dim s As String  
    s = "Checked Items:" & ControlChars.CrLf  
    For i = 0 To (CheckedListBox1.Items.Count - 1)  
       If CheckedListBox1.GetItemChecked(i) = True Then  
          s = s & "Item " & (i + 1).ToString & " = " & CheckedListBox1.Items(i).ToString & ControlChars.CrLf  
       End If  
    Next  
    MessageBox.Show(s)  
    ```  
  
    ```csharp  
    int i;  
    string s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1.Items.Count-1); i++)  
    {  
       if (checkedListBox1.GetItemChecked(i))  
       {  
          s = s + "Item " + (i+1).ToString() + " = " + checkedListBox1.Items[i].ToString() + "\n";  
       }  
    }  
    MessageBox.Show (s);  
    ```  
  
    ```cpp  
    int i;  
    String ^ s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1->Items->Count-1); i++)  
    {  
       if (checkedListBox1->GetItemChecked(i))  
       {  
          s = String::Concat(s, "Item ", (i+1).ToString(), " = ",  
             checkedListBox1->Item[i]->ToString(), "\n");  
       }  
    }  
    MessageBox::Show(s);  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Controles dos Windows Forms usados para listar opções](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
