---
title: Adicionar e remover itens do controle ComboBox, ListBox ou CheckedListBox
ms.date: 03/30/2017
description: Saiba como adicionar e remover um Windows Forms controles ComboBox, ListBox e CheckedListBox simplesmente e sem Associação de dados.
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
ms.openlocfilehash: f3701257bbe410bf03c4c21700705e87b581bf2e
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904436"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="25d23-103">Como adicionar e remover itens de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25d23-103">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="25d23-104">Itens podem ser adicionados a uma caixa de combinação dos Windows Forms, caixa de listagem ou caixa de listagem marcada de várias maneiras, porque esses controles podem ser vinculados a uma variedade de fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="25d23-104">Items can be added to a Windows Forms combo box, list box, or checked list box in a variety of ways, because these controls can be bound to a variety of data sources.</span></span> <span data-ttu-id="25d23-105">No entanto, este tópico demonstra o método mais simples e não requer nenhuma vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="25d23-105">However, this topic demonstrates the simplest method and requires no data binding.</span></span> <span data-ttu-id="25d23-106">Normalmente, os itens exibidos são cadeias de caracteres; No entanto, qualquer objeto pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="25d23-106">The items displayed are usually strings; however, any object can be used.</span></span> <span data-ttu-id="25d23-107">O texto que é exibido no controle é o valor retornado pelo método do objeto `ToString` .</span><span class="sxs-lookup"><span data-stu-id="25d23-107">The text that is displayed in the control is the value returned by the object's `ToString` method.</span></span>  
  
### <a name="to-add-items"></a><span data-ttu-id="25d23-108">Para adicionar Itens</span><span class="sxs-lookup"><span data-stu-id="25d23-108">To add items</span></span>  
  
1. <span data-ttu-id="25d23-109">Adicione a cadeia de caracteres ou objeto à lista usando o método `Add` da classe `ObjectCollection`.</span><span class="sxs-lookup"><span data-stu-id="25d23-109">Add the string or object to the list by using the `Add` method of the `ObjectCollection` class.</span></span> <span data-ttu-id="25d23-110">A coleção é referenciada usando a `Items` Propriedade:</span><span class="sxs-lookup"><span data-stu-id="25d23-110">The collection is referenced using the `Items` property:</span></span>  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - <span data-ttu-id="25d23-111">ou –</span><span class="sxs-lookup"><span data-stu-id="25d23-111">or -</span></span>  
  
2. <span data-ttu-id="25d23-112">Insira a cadeia de caracteres ou o objeto no ponto desejado na lista com o `Insert` método:</span><span class="sxs-lookup"><span data-stu-id="25d23-112">Insert the string or object at the desired point in the list with the `Insert` method:</span></span>  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - <span data-ttu-id="25d23-113">ou –</span><span class="sxs-lookup"><span data-stu-id="25d23-113">or -</span></span>  
  
3. <span data-ttu-id="25d23-114">Atribua uma matriz inteira à `Items` coleção:</span><span class="sxs-lookup"><span data-stu-id="25d23-114">Assign an entire array to the `Items` collection:</span></span>  
  
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
  
### <a name="to-remove-an-item"></a><span data-ttu-id="25d23-115">Para remover um item</span><span class="sxs-lookup"><span data-stu-id="25d23-115">To remove an item</span></span>  
  
1. <span data-ttu-id="25d23-116">Chame o `Remove` `RemoveAt` método ou para excluir itens.</span><span class="sxs-lookup"><span data-stu-id="25d23-116">Call the `Remove` or `RemoveAt` method to delete items.</span></span>  
  
     <span data-ttu-id="25d23-117">O `Remove` tem um argumento que especifica o item a ser removido.`RemoveAt`</span><span class="sxs-lookup"><span data-stu-id="25d23-117">`Remove` has one argument that specifies the item to remove.`RemoveAt`</span></span> <span data-ttu-id="25d23-118">remove o item com o número de índice especificado.</span><span class="sxs-lookup"><span data-stu-id="25d23-118">removes the item with the specified index number.</span></span>  
  
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
  
### <a name="to-remove-all-items"></a><span data-ttu-id="25d23-119">Para remover todos os itens</span><span class="sxs-lookup"><span data-stu-id="25d23-119">To remove all items</span></span>  
  
1. <span data-ttu-id="25d23-120">Chame o método `Clear` para remover todos os itens da coleção:</span><span class="sxs-lookup"><span data-stu-id="25d23-120">Call the `Clear` method to remove all items from the collection:</span></span>  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="25d23-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="25d23-121">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="25d23-122">Como classificar o conteúdo de um controle ComboBox, ListBox ou CheckedListBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25d23-122">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="25d23-123">Quando usar um ComboBox dos Windows Forms em vez de um ListBox</span><span class="sxs-lookup"><span data-stu-id="25d23-123">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="25d23-124">Controles dos Windows Forms usados para listar opções</span><span class="sxs-lookup"><span data-stu-id="25d23-124">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
