---
title: Determinar itens marcados no controle CheckedListBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 5854f7e6be759daeb604458ea8554d3c98ed39c2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743246"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Como determinar itens verificados no controle CheckedListBox dos Windows Forms
Ao apresentar dados em um Windows Forms <xref:System.Windows.Forms.CheckedListBox> controle, você pode iterar pela coleção armazenada na propriedade <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> ou percorrer a lista usando o método <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> para determinar quais itens estão marcados. O método <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> usa um número de índice de item como seu argumento e retorna `true` ou `false`. Ao contrário do que você pode esperar, as propriedades <xref:System.Windows.Forms.ListBox.SelectedItems%2A> e <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> não determinam quais itens são verificados; Eles determinam quais itens são realçados.  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>Como determinar itens marcados em um controle CheckedListBox  
  
1. Itere pela coleção de <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>, começando em 0, pois a coleção é baseada em zero. Observe que esse método lhe fornecerá o número de item na lista de itens marcados, não na lista global. Portanto, se o primeiro item na lista não estiver marcado e o segundo item estiver marcado, o código a seguir exibirá o texto como "Item marcado 1 = MyListItem2".  
  
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
       for(int x = 0; x < checkedListBox1.CheckedItems.Count ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
       MessageBox.Show(s);  
    }  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x < checkedListBox1->CheckedItems->Count; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     - ou –  
  
2. Percorra a coleção de <xref:System.Windows.Forms.CheckedListBox.Items%2A>, começando em 0, uma vez que a coleção é baseada em zero e chame o método <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> para cada item. Observe que esse método lhe fornecerá o número de item na lista geral, portanto, se o primeiro item na lista não estiver marcado e o segundo item estiver marcado, ele exibirá algo como "Item 2 = MyListItem2".  
  
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

- [Controles dos Windows Forms usados para listar opções](windows-forms-controls-used-to-list-options.md)
