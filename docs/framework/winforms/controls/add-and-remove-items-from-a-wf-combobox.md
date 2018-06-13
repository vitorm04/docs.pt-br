---
title: Como adicionar e remover itens de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- combo boxes [Windows Forms], adding items
- list boxes [Windows Forms], removing items
- ComboBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], adding and removing items
- list boxes [Windows Forms], adding items
- combo boxes [Windows Forms], removing items
- CheckedListBox control [Windows Forms], adding and removing items
ms.assetid: 7224c8d2-4118-443e-ae1e-d7c17d1e69ee
ms.openlocfilehash: f9319ffe5e9c4f06565648565ce21dec6fc672f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527181"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="57b02-102">Como adicionar e remover itens de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="57b02-102">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="57b02-103">Itens podem ser adicionados a uma caixa de combinação dos Windows Forms, caixa de listagem ou caixa de listagem marcada de várias maneiras, porque esses controles podem ser vinculados a uma variedade de fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="57b02-103">Items can be added to a Windows Forms combo box, list box, or checked list box in a variety of ways, because these controls can be bound to a variety of data sources.</span></span> <span data-ttu-id="57b02-104">No entanto, este tópico demonstra o método mais simples e não requer nenhuma vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="57b02-104">However, this topic demonstrates the simplest method and requires no data binding.</span></span> <span data-ttu-id="57b02-105">Normalmente, os itens exibidos são cadeias de caracteres; No entanto, qualquer objeto pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="57b02-105">The items displayed are usually strings; however, any object can be used.</span></span> <span data-ttu-id="57b02-106">O texto que é exibido no controle é o valor retornado pelo objeto de `ToString` método.</span><span class="sxs-lookup"><span data-stu-id="57b02-106">The text that is displayed in the control is the value returned by the object's `ToString` method.</span></span>  
  
### <a name="to-add-items"></a><span data-ttu-id="57b02-107">Para adicionar Itens</span><span class="sxs-lookup"><span data-stu-id="57b02-107">To add items</span></span>  
  
1.  <span data-ttu-id="57b02-108">Adicione a cadeia de caracteres ou objeto à lista usando o método `Add` da classe `ObjectCollection`.</span><span class="sxs-lookup"><span data-stu-id="57b02-108">Add the string or object to the list by using the `Add` method of the `ObjectCollection` class.</span></span> <span data-ttu-id="57b02-109">A coleção é referenciada usando o `Items` propriedade:</span><span class="sxs-lookup"><span data-stu-id="57b02-109">The collection is referenced using the `Items` property:</span></span>  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - <span data-ttu-id="57b02-110">ou –</span><span class="sxs-lookup"><span data-stu-id="57b02-110">or -</span></span>  
  
2.  <span data-ttu-id="57b02-111">Insira a cadeia de caracteres ou o objeto no ponto desejado na lista com o `Insert` método:</span><span class="sxs-lookup"><span data-stu-id="57b02-111">Insert the string or object at the desired point in the list with the `Insert` method:</span></span>  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - <span data-ttu-id="57b02-112">ou –</span><span class="sxs-lookup"><span data-stu-id="57b02-112">or -</span></span>  
  
3.  <span data-ttu-id="57b02-113">Atribuir uma matriz de inteira para o `Items` coleção:</span><span class="sxs-lookup"><span data-stu-id="57b02-113">Assign an entire array to the `Items` collection:</span></span>  
  
    ```vb  
    Dim ItemObject(9) As System.Object  
    Dim i As Integer  
       For i = 0 To 9  
       ItemObject(i) = "Item" & i  
    Next i  
    ListBox1.Items.AddRange(ItemObject)  
    ```  
  
    ```csharp  
    System.Object[] ItemObject = new System.Object[10];  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = "Item" + i;  
    }  
    listBox1.Items.AddRange(ItemObject);  
    ```  
  
    ```cpp  
    Array<System::Object^>^ ItemObject = gcnew Array<System::Object^>(10);  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = String::Concat("Item", i.ToString());  
    }  
    listBox1->Items->AddRange(ItemObject);  
    ```  
  
### <a name="to-remove-an-item"></a><span data-ttu-id="57b02-114">Para remover um item</span><span class="sxs-lookup"><span data-stu-id="57b02-114">To remove an item</span></span>  
  
1.  <span data-ttu-id="57b02-115">Chamar o `Remove` ou `RemoveAt` método para excluir itens.</span><span class="sxs-lookup"><span data-stu-id="57b02-115">Call the `Remove` or `RemoveAt` method to delete items.</span></span>  
  
     <span data-ttu-id="57b02-116">O `Remove` tem um argumento que especifica o item a ser removido.`RemoveAt`</span><span class="sxs-lookup"><span data-stu-id="57b02-116">`Remove` has one argument that specifies the item to remove.`RemoveAt`</span></span> <span data-ttu-id="57b02-117">remove o item com o número de índice especificado.</span><span class="sxs-lookup"><span data-stu-id="57b02-117">removes the item with the specified index number.</span></span>  
  
    ```vb  
    ' To remove item with index 0:  
    ComboBox1.Items.RemoveAt(0)  
    ' To remove currently selected item:  
    ComboBox1.Items.Remove(ComboBox1.SelectedItem)  
    ' To remove "Tokyo" item:  
    ComboBox1.Items.Remove("Tokyo")  
    ```  
  
    ```csharp  
    // To remove item with index 0:  
    comboBox1.Items.RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1.Items.Remove(comboBox1.SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1.Items.Remove("Tokyo");  
    ```  
  
    ```cpp  
    // To remove item with index 0:  
    comboBox1->Items->RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1->Items->Remove(comboBox1->SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1->Items->Remove("Tokyo");  
    ```  
  
### <a name="to-remove-all-items"></a><span data-ttu-id="57b02-118">Para remover todos os itens</span><span class="sxs-lookup"><span data-stu-id="57b02-118">To remove all items</span></span>  
  
1.  <span data-ttu-id="57b02-119">Chame o método `Clear` para remover todos os itens da coleção:</span><span class="sxs-lookup"><span data-stu-id="57b02-119">Call the `Clear` method to remove all items from the collection:</span></span>  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="57b02-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57b02-120">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [<span data-ttu-id="57b02-121">Como classificar o conteúdo de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="57b02-121">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [<span data-ttu-id="57b02-122">Quando usar um ComboBox dos Windows Forms em vez de um ListBox</span><span class="sxs-lookup"><span data-stu-id="57b02-122">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [<span data-ttu-id="57b02-123">Controles dos Windows Forms usados para listar opções</span><span class="sxs-lookup"><span data-stu-id="57b02-123">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
