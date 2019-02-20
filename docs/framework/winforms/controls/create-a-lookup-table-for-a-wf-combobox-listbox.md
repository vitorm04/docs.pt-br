---
title: 'Como: Criar uma tabela de pesquisa para um Windows Forms ComboBox, ListBox ou CheckedListBox controle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
ms.openlocfilehash: 5f1a2b220c3fb5d348f8aa45fbf07140844c9adf
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441613"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="1f626-102">Como: Criar uma tabela de pesquisa para um Windows Forms ComboBox, ListBox ou CheckedListBox controle</span><span class="sxs-lookup"><span data-stu-id="1f626-102">How to: Create a Lookup Table for a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="1f626-103">Às vezes, é útil exibir dados em um formato amigável em um formulário do Windows Forms, porém, armazene os dados em um formato que seja mais significativo para o programa.</span><span class="sxs-lookup"><span data-stu-id="1f626-103">Sometimes it is useful to display data in a user-friendly format on a Windows Form, but store the data in a format that is more meaningful to your program.</span></span> <span data-ttu-id="1f626-104">Por exemplo, um formulário de pedido de alimentos pode exibir os itens de menu por nome em uma caixa de listagem.</span><span class="sxs-lookup"><span data-stu-id="1f626-104">For example, an order form for food might display the menu items by name in a list box.</span></span> <span data-ttu-id="1f626-105">No entanto, a tabela de dados que registra a ordem conteria os números de identificação exclusivos que representam os alimentos.</span><span class="sxs-lookup"><span data-stu-id="1f626-105">However, the data table recording the order would contain the unique ID numbers representing the food.</span></span> <span data-ttu-id="1f626-106">As tabelas a seguir mostram um exemplo de como armazenar e exibir dados de formulários de pedidos de alimentos.</span><span class="sxs-lookup"><span data-stu-id="1f626-106">The following tables show an example of how to store and display order-form data for food.</span></span>  
  
### <a name="orderdetailstable"></a><span data-ttu-id="1f626-107">OrderDetailsTable</span><span class="sxs-lookup"><span data-stu-id="1f626-107">OrderDetailsTable</span></span>  
  
|<span data-ttu-id="1f626-108">OrderID</span><span class="sxs-lookup"><span data-stu-id="1f626-108">OrderID</span></span>|<span data-ttu-id="1f626-109">ItemID</span><span class="sxs-lookup"><span data-stu-id="1f626-109">ItemID</span></span>|<span data-ttu-id="1f626-110">Quantidade</span><span class="sxs-lookup"><span data-stu-id="1f626-110">Quantity</span></span>|  
|-------------|------------|--------------|  
|<span data-ttu-id="1f626-111">4085</span><span class="sxs-lookup"><span data-stu-id="1f626-111">4085</span></span>|<span data-ttu-id="1f626-112">12</span><span class="sxs-lookup"><span data-stu-id="1f626-112">12</span></span>|<span data-ttu-id="1f626-113">1</span><span class="sxs-lookup"><span data-stu-id="1f626-113">1</span></span>|  
|<span data-ttu-id="1f626-114">4086</span><span class="sxs-lookup"><span data-stu-id="1f626-114">4086</span></span>|<span data-ttu-id="1f626-115">13</span><span class="sxs-lookup"><span data-stu-id="1f626-115">13</span></span>|<span data-ttu-id="1f626-116">3</span><span class="sxs-lookup"><span data-stu-id="1f626-116">3</span></span>|  
  
### <a name="itemtable"></a><span data-ttu-id="1f626-117">ItemTable</span><span class="sxs-lookup"><span data-stu-id="1f626-117">ItemTable</span></span>  
  
|<span data-ttu-id="1f626-118">ID</span><span class="sxs-lookup"><span data-stu-id="1f626-118">ID</span></span>|<span data-ttu-id="1f626-119">Nome</span><span class="sxs-lookup"><span data-stu-id="1f626-119">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="1f626-120">12</span><span class="sxs-lookup"><span data-stu-id="1f626-120">12</span></span>|<span data-ttu-id="1f626-121">Batata</span><span class="sxs-lookup"><span data-stu-id="1f626-121">Potato</span></span>|  
|<span data-ttu-id="1f626-122">13</span><span class="sxs-lookup"><span data-stu-id="1f626-122">13</span></span>|<span data-ttu-id="1f626-123">Frango</span><span class="sxs-lookup"><span data-stu-id="1f626-123">Chicken</span></span>|  
  
 <span data-ttu-id="1f626-124">Nesse cenário, uma tabela, **OrderDetailsTable**, armazena as informações reais que serão exibidas e salvas.</span><span class="sxs-lookup"><span data-stu-id="1f626-124">In this scenario, one table, **OrderDetailsTable**, stores the actual information you are concerned with displaying and saving.</span></span> <span data-ttu-id="1f626-125">Porém, para economizar espaço, isso é feito de maneira bastante enigmática.</span><span class="sxs-lookup"><span data-stu-id="1f626-125">But to save space, it does so in a fairly cryptic fashion.</span></span> <span data-ttu-id="1f626-126">A outra tabela, **ItemTable**, contém apenas informações relacionadas à aparência sobre qual número de ID é equivalente a qual nome de alimento, e nada sobre os pedidos de alimentos.</span><span class="sxs-lookup"><span data-stu-id="1f626-126">The other table, **ItemTable**, contains only appearance-related information about which ID number is equivalent to which food name, and nothing about the actual food orders.</span></span>  
  
 <span data-ttu-id="1f626-127">O **ItemTable** está conectado às <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, ou <xref:System.Windows.Forms.CheckedListBox> controle por meio de três propriedades.</span><span class="sxs-lookup"><span data-stu-id="1f626-127">The **ItemTable** is connected to the <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control through three properties.</span></span> <span data-ttu-id="1f626-128">A propriedade `DataSource` contém o nome dessa tabela.</span><span class="sxs-lookup"><span data-stu-id="1f626-128">The `DataSource` property contains the name of this table.</span></span> <span data-ttu-id="1f626-129">A propriedade `DisplayMember` contém a coluna de dados da tabela que você deseja exibir no controle (o nome do alimento).</span><span class="sxs-lookup"><span data-stu-id="1f626-129">The `DisplayMember` property contains the data column of that table that you want to display in the control (the food name).</span></span> <span data-ttu-id="1f626-130">A propriedade `ValueMember` contém a coluna de dados dessa tabela com as informações armazenadas (o número de ID).</span><span class="sxs-lookup"><span data-stu-id="1f626-130">The `ValueMember` property contains the data column of that table with the stored information (the ID number).</span></span>  
  
 <span data-ttu-id="1f626-131">O **OrderDetailsTable** está conectado ao controle por sua coleção de associações, acessada por meio de <xref:System.Windows.Forms.Control.DataBindings%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="1f626-131">The **OrderDetailsTable** is connected to the control by its bindings collection, accessed through the <xref:System.Windows.Forms.Control.DataBindings%2A> property.</span></span> <span data-ttu-id="1f626-132">Ao adicionar um objeto de associação à coleção, uma propriedade de controle será conectada a um membro de dados específico (a coluna de números de ID) em uma fonte de dados (**OrderDetailsTable**).</span><span class="sxs-lookup"><span data-stu-id="1f626-132">When you add a binding object to the collection, you connect a control property to a specific data member (the column of ID numbers) in a data source (the **OrderDetailsTable**).</span></span> <span data-ttu-id="1f626-133">Quando uma seleção é feita no controle, a entrada de formulário será salva nessa tabela.</span><span class="sxs-lookup"><span data-stu-id="1f626-133">When a selection is made in the control, this table is where the form input is saved.</span></span>  
  
### <a name="to-create-a-lookup-table"></a><span data-ttu-id="1f626-134">Criar uma tabela de pesquisa</span><span class="sxs-lookup"><span data-stu-id="1f626-134">To create a lookup table</span></span>  
  
1.  <span data-ttu-id="1f626-135">Adicionar um <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, ou <xref:System.Windows.Forms.CheckedListBox> controle ao formulário.</span><span class="sxs-lookup"><span data-stu-id="1f626-135">Add a <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control to the form.</span></span>  
  
2.  <span data-ttu-id="1f626-136">Conecte-se à fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="1f626-136">Connect to your data source.</span></span>  
  
3.  <span data-ttu-id="1f626-137">Estabeleça uma relação de dados entre as duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="1f626-137">Establish a data relation between the two tables.</span></span> <span data-ttu-id="1f626-138">Consulte [Introdução a Objetos DataRelation](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="1f626-138">See [Introduction to DataRelation Objects](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).</span></span>  
  
4.  <span data-ttu-id="1f626-139">Defina as propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="1f626-139">Set the following properties.</span></span> <span data-ttu-id="1f626-140">Elas podem ser definidos no código ou no designer.</span><span class="sxs-lookup"><span data-stu-id="1f626-140">They can be set in code or in the designer.</span></span>  
  
    |<span data-ttu-id="1f626-141">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1f626-141">Property</span></span>|<span data-ttu-id="1f626-142">Configuração</span><span class="sxs-lookup"><span data-stu-id="1f626-142">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|<span data-ttu-id="1f626-143">A tabela que contém informações sobre qual número de ID é equivalente a qual item.</span><span class="sxs-lookup"><span data-stu-id="1f626-143">The table that contains information about which ID number is equivalent to which item.</span></span> <span data-ttu-id="1f626-144">No cenário anterior, isso é `ItemTable`.</span><span class="sxs-lookup"><span data-stu-id="1f626-144">In the previous scenario, this is `ItemTable`.</span></span>|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|<span data-ttu-id="1f626-145">A coluna da tabela de fonte de dados a ser exibida no controle.</span><span class="sxs-lookup"><span data-stu-id="1f626-145">The column of the data source table that you want to display in the control.</span></span> <span data-ttu-id="1f626-146">No cenário anterior, isso é `"Name"` (para definir no código, use aspas).</span><span class="sxs-lookup"><span data-stu-id="1f626-146">In the previous scenario, this is `"Name"` (to set in code, use quotation marks).</span></span>|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|<span data-ttu-id="1f626-147">A coluna da tabela de fonte de dados que contém as informações armazenadas.</span><span class="sxs-lookup"><span data-stu-id="1f626-147">The column of the data source table that contains the stored information.</span></span> <span data-ttu-id="1f626-148">No cenário anterior, isso é `"ID"` (para definir no código, use aspas).</span><span class="sxs-lookup"><span data-stu-id="1f626-148">In the previous scenario, this is `"ID"` (to set in code, use quotation marks).</span></span>|  
  
5.  <span data-ttu-id="1f626-149">Em um procedimento, chame o <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> método da <xref:System.Windows.Forms.ControlBindingsCollection> classe para associar o controle <xref:System.Windows.Forms.ListControl.SelectedValue%2A> propriedade para a tabela que registra a entrada de formulário.</span><span class="sxs-lookup"><span data-stu-id="1f626-149">In a procedure, call the <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> method of the <xref:System.Windows.Forms.ControlBindingsCollection> class to bind the control's <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property to the table recording the form input.</span></span> <span data-ttu-id="1f626-150">Você também pode fazer isso no Designer, em vez de no código, acessando o controle <xref:System.Windows.Forms.Control.DataBindings%2A> propriedade em de **propriedades** janela.</span><span class="sxs-lookup"><span data-stu-id="1f626-150">You can also do this in the Designer instead of in code, by accessing the control's <xref:System.Windows.Forms.Control.DataBindings%2A> property in the **Properties** window.</span></span> <span data-ttu-id="1f626-151">No cenário anterior, isso é `OrderDetailsTable` e a coluna é `"ItemID"`.</span><span class="sxs-lookup"><span data-stu-id="1f626-151">In the previous scenario, this is `OrderDetailsTable`, and the column is `"ItemID"`.</span></span>  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1f626-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f626-152">See also</span></span>
- [<span data-ttu-id="1f626-153">Vinculação de dados e os Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f626-153">Data Binding and Windows Forms</span></span>](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)
- [<span data-ttu-id="1f626-154">Visão geral do controle ListBox</span><span class="sxs-lookup"><span data-stu-id="1f626-154">ListBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)
- [<span data-ttu-id="1f626-155">Visão geral do controle ComboBox</span><span class="sxs-lookup"><span data-stu-id="1f626-155">ComboBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)
- [<span data-ttu-id="1f626-156">Visão geral do controle CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="1f626-156">CheckedListBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)
- [<span data-ttu-id="1f626-157">Controles dos Windows Forms usados para listar opções</span><span class="sxs-lookup"><span data-stu-id="1f626-157">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
