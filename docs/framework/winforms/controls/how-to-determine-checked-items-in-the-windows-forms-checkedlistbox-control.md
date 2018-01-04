---
title: Como determinar itens verificados no controle CheckedListBox dos Windows Forms
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
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63960740b2fc0cb2c96f9a853480f37857c7901b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a><span data-ttu-id="1b280-102">Como determinar itens verificados no controle CheckedListBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1b280-102">How to: Determine Checked Items in the Windows Forms CheckedListBox Control</span></span>
<span data-ttu-id="1b280-103">Ao apresentar dados em um Windows Forms <xref:System.Windows.Forms.CheckedListBox> controle, ou pode iterar por meio da coleção armazenada no <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> propriedade ou percorra a lista usando o <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> método para determinar quais itens são verificados.</span><span class="sxs-lookup"><span data-stu-id="1b280-103">When presenting data in a Windows Forms <xref:System.Windows.Forms.CheckedListBox> control, you can either iterate through the collection stored in the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> property, or step through the list using the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method to determine which items are checked.</span></span> <span data-ttu-id="1b280-104">O <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> método recebe um número de índice do item como seu argumento e retorna `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="1b280-104">The <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method takes an item index number as its argument and returns `true` or `false`.</span></span> <span data-ttu-id="1b280-105">Ao contrário do que você esperava, o <xref:System.Windows.Forms.ListBox.SelectedItems%2A> e <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> propriedades não determinar quais itens são verificados; elas determinam quais itens são realçados.</span><span class="sxs-lookup"><span data-stu-id="1b280-105">Contrary to what you might expect, the <xref:System.Windows.Forms.ListBox.SelectedItems%2A> and <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> properties do not determine which items are checked; they determine which items are highlighted.</span></span>  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a><span data-ttu-id="1b280-106">Como determinar itens marcados em um controle CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="1b280-106">To determine checked items in a CheckedListBox control</span></span>  
  
1.  <span data-ttu-id="1b280-107">Percorrer o <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> coleção, começando em 0 porque a coleção é baseada em zero.</span><span class="sxs-lookup"><span data-stu-id="1b280-107">Iterate through the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> collection, starting at 0 since the collection is zero-based.</span></span> <span data-ttu-id="1b280-108">Observe que esse método lhe fornecerá o número de item na lista de itens marcados, não na lista global.</span><span class="sxs-lookup"><span data-stu-id="1b280-108">Note that this method will give you the item number in the list of checked items, not the overall list.</span></span> <span data-ttu-id="1b280-109">Portanto, se o primeiro item na lista não estiver marcado e o segundo item estiver marcado, o código a seguir exibirá o texto como "Item marcado 1 = MyListItem2".</span><span class="sxs-lookup"><span data-stu-id="1b280-109">So if the first item in the list is not checked and the second item is checked, the code below will display text like "Checked Item 1 = MyListItem2".</span></span>  
  
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
  
     - <span data-ttu-id="1b280-110">ou –</span><span class="sxs-lookup"><span data-stu-id="1b280-110">or -</span></span>  
  
2.  <span data-ttu-id="1b280-111">Percorrer o <xref:System.Windows.Forms.CheckedListBox.Items%2A> coleção, começando em 0 porque a coleção é baseado em zero e chamar o <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> método para cada item.</span><span class="sxs-lookup"><span data-stu-id="1b280-111">Step through the <xref:System.Windows.Forms.CheckedListBox.Items%2A> collection, starting at 0 since the collection is zero-based, and call the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method for each item.</span></span> <span data-ttu-id="1b280-112">Observe que esse método lhe fornecerá o número de item na lista geral, portanto, se o primeiro item na lista não estiver marcado e o segundo item estiver marcado, ele exibirá algo como "Item 2 = MyListItem2".</span><span class="sxs-lookup"><span data-stu-id="1b280-112">Note that this method will give you the item number in the overall list, so if the first item in the list is not checked and the second item is checked, it will display something like "Item 2 = MyListItem2".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1b280-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b280-113">See Also</span></span>  
 [<span data-ttu-id="1b280-114">Controles dos Windows Forms usados para listar opções</span><span class="sxs-lookup"><span data-stu-id="1b280-114">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
