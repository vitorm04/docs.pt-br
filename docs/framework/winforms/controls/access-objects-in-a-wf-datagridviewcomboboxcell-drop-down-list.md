---
title: 'Como: Acessar objetos de acesso em uma lista suspensa DataGridViewComboBoxCell do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 17b7c93effe9338a9e2d6cb207a948a956d9b666
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640417"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a><span data-ttu-id="cf8d8-102">Como: Acessar objetos de acesso em uma lista suspensa DataGridViewComboBoxCell do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf8d8-102">How to: Access Objects in a Windows Forms DataGridViewComboBoxCell Drop-Down List</span></span>
<span data-ttu-id="cf8d8-103">Como o <xref:System.Windows.Forms.ComboBox> controle, o <xref:System.Windows.Forms.DataGridViewComboBoxColumn> e <xref:System.Windows.Forms.DataGridViewComboBoxCell> tipos que você possa adicionar objetos arbitrários às suas listas suspensas.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-103">Like the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and <xref:System.Windows.Forms.DataGridViewComboBoxCell> types enable you to add arbitrary objects to their drop-down lists.</span></span> <span data-ttu-id="cf8d8-104">Com esse recurso, você pode representar estados complexos em uma lista suspensa sem a necessidade de armazenar objetos correspondentes em uma coleção separada.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-104">With this feature, you can represent complex states in a drop-down list without having to store corresponding objects in a separate collection.</span></span>  
  
 <span data-ttu-id="cf8d8-105">Ao contrário de <xref:System.Windows.Forms.ComboBox> controle, o <xref:System.Windows.Forms.DataGridView> tipos não têm um <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> propriedade para recuperar o objeto atualmente selecionado.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-105">Unlike the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridView> types do not have a <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> property for retrieving the currently selected object.</span></span> <span data-ttu-id="cf8d8-106">Em vez disso, você deve definir a <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> propriedade para o nome de uma propriedade em seu objeto de negócios.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-106">Instead, you must set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> property to the name of a property on your business object.</span></span> <span data-ttu-id="cf8d8-107">Quando o usuário faz uma seleção, a propriedade indicada do objeto comercial define a célula <xref:System.Windows.Forms.DataGridViewCell.Value%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-107">When the user makes a selection, the indicated property of the business object sets the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
 <span data-ttu-id="cf8d8-108">Para recuperar o objeto comercial por meio do valor de célula, a propriedade `ValueMember` deve indicar uma propriedade que retorne uma referência ao objeto comercial em si.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-108">To retrieve the business object through the cell value, the `ValueMember` property must indicate a property that returns a reference to the business object itself.</span></span> <span data-ttu-id="cf8d8-109">Portanto, se o tipo de objeto comercial não estiver sob seu controle, você deverá adicionar essa propriedade estendendo o tipo por meio de herança.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-109">Therefore, if the type of the business object is not under your control, you must add such a property by extending the type through inheritance.</span></span>  
  
 <span data-ttu-id="cf8d8-110">Os procedimentos a seguir demonstram como preencher uma lista suspensa com objetos comerciais e recuperar os objetos por meio da célula <xref:System.Windows.Forms.DataGridViewCell.Value%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-110">The following procedures demonstrate how to populate a drop-down list with business objects and retrieve the objects through the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a><span data-ttu-id="cf8d8-111">Para adicionar objetos comerciais à lista suspensa</span><span class="sxs-lookup"><span data-stu-id="cf8d8-111">To add business objects to the drop-down list</span></span>  
  
1. <span data-ttu-id="cf8d8-112">Criar um novo <xref:System.Windows.Forms.DataGridViewComboBoxColumn> e preencher seu <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-112">Create a new <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and populate its <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span></span> <span data-ttu-id="cf8d8-113">Como alternativa, você pode definir a coluna <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> propriedade à coleção de objetos de negócios.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-113">Alternatively, you can set the column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property to the collection of business objects.</span></span> <span data-ttu-id="cf8d8-114">Nesse caso, no entanto, você não pode adicionar "não atribuído" à lista suspensa sem criar um objeto comercial correspondente em sua coleção.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-114">In that case, however, you cannot add "unassigned" to the drop-down list without creating a corresponding business object in your collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2. <span data-ttu-id="cf8d8-115">Defina as <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> e <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-115">Set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> and <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> properties.</span></span> <span data-ttu-id="cf8d8-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indica a propriedade do objeto comercial a exibir na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indicates the property of the business object to display in the drop-down list.</span></span> <span data-ttu-id="cf8d8-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indica a propriedade que retorna uma referência ao objeto comercial.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indicates the property that returns a reference to the business object.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3. <span data-ttu-id="cf8d8-118">Certifique-se de que o tipo de objeto de negócios contenha uma propriedade que retorne uma referência à instância atual.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-118">Make sure that your business object type contains a property that returns a reference to the current instance.</span></span> <span data-ttu-id="cf8d8-119">Essa propriedade deve ser nomeada com o valor atribuído a <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-119">This property must be named with the value assigned to <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> in the previous step.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a><span data-ttu-id="cf8d8-120">Para recuperar o objeto comercial selecionado no momento</span><span class="sxs-lookup"><span data-stu-id="cf8d8-120">To retrieve the currently selected business object</span></span>  
  
- <span data-ttu-id="cf8d8-121">Obter a célula <xref:System.Windows.Forms.DataGridViewCell.Value%2A> propriedade e convertê-lo para o tipo de objeto comercial.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-121">Get the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property and cast it to the business object type.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a><span data-ttu-id="cf8d8-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf8d8-122">Example</span></span>  
 <span data-ttu-id="cf8d8-123">O exemplo completo demonstra o uso de objetos de negócios em uma lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-123">The complete example demonstrates the use of business objects in a drop-down list.</span></span> <span data-ttu-id="cf8d8-124">No exemplo, uma <xref:System.Windows.Forms.DataGridView> controle é associado a uma coleção de `Task` objetos.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-124">In the example, a <xref:System.Windows.Forms.DataGridView> control is bound to a collection of `Task` objects.</span></span> <span data-ttu-id="cf8d8-125">Cada objeto `Task` tem uma propriedade `AssignedTo` que indica o objeto `Employee` atualmente atribuído à tarefa.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-125">Each `Task` object has an `AssignedTo` property that indicates the `Employee` object currently assigned to that task.</span></span> <span data-ttu-id="cf8d8-126">A coluna `Assigned To` exibe o de valor da propriedade `Name` para cada funcionário atribuído ou "não atribuído", se o valor da propriedade `Task.AssignedTo` for `null`.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-126">The `Assigned To` column displays the `Name` property value for each assigned employee, or "unassigned" if the `Task.AssignedTo` property value is `null`.</span></span>  
  
 <span data-ttu-id="cf8d8-127">Para exibir o comportamento deste exemplo, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="cf8d8-127">To view the behavior of this example, perform the following steps:</span></span>  
  
1. <span data-ttu-id="cf8d8-128">Altere as atribuições na coluna `Assigned To` selecionando valores diferentes nas listas suspensas ou pressionando CTRL+0 em uma célula de caixa de combinação.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-128">Change assignments in the `Assigned To` column by selecting different values from the drop-down lists or pressing CTRL+0 in a combo-box cell.</span></span>  
  
2. <span data-ttu-id="cf8d8-129">Clique em `Generate Report` para exibir as atribuições atuais.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-129">Click `Generate Report` to display the current assignments.</span></span> <span data-ttu-id="cf8d8-130">Isso demonstra que uma alteração à coluna `Assigned To` atualiza automaticamente a coleção `tasks`.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-130">This demonstrates that a change in the `Assigned To` column automatically updates the `tasks` collection.</span></span>  
  
3. <span data-ttu-id="cf8d8-131">Clique em um botão `Request Status` para chamar o método `RequestStatus` do objeto `Employee` atual para aquela linha.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-131">Click a `Request Status` button to call the `RequestStatus` method of the current `Employee` object for that row.</span></span> <span data-ttu-id="cf8d8-132">Isso demonstra que o objeto selecionado foi recuperado com êxito.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-132">This demonstrates that the selected object has been successfully retrieved.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cf8d8-133">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="cf8d8-133">Compiling the Code</span></span>  
 <span data-ttu-id="cf8d8-134">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="cf8d8-134">This example requires:</span></span>  
  
- <span data-ttu-id="cf8d8-135">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-135">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf8d8-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf8d8-136">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ComboBox>
- [<span data-ttu-id="cf8d8-137">Exibindo dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf8d8-137">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
