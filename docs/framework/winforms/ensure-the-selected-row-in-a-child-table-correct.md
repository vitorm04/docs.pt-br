---
title: 'Como: assegurar que a linha selecionada em uma tabela filho permaneça na posição correta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- master-details view
- row position [Windows Forms]
- parent/child view [Windows Forms]
- resetting child position
- data binding [.NET Framework], row selection
- caching [.NET Framework], child position
- child position
- master/details view [Windows Forms]
- child tables row selection
- current child position
ms.assetid: c5fa2562-43a4-46fa-a604-52d8526a87bd
ms.openlocfilehash: bbebd9f040c60016305a861abee3723450a7456b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651976"
---
# <a name="how-to-ensure-the-selected-row-in-a-child-table-remains-at-the-correct-position"></a><span data-ttu-id="6eb9a-102">Como: assegurar que a linha selecionada em uma tabela filho permaneça na posição correta</span><span class="sxs-lookup"><span data-stu-id="6eb9a-102">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>
<span data-ttu-id="6eb9a-103">Muitas vezes, ao trabalhar com a vinculação de dados nos Windows Forms, você exibirá dados no que é chamado de modo de exibição pai/filho ou detalhes/mestre.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-103">Oftentimes when you work with data binding in Windows Forms, you will display data in what is called a parent/child or master/details view.</span></span> <span data-ttu-id="6eb9a-104">Isso se refere a um cenário de associação de dados em que os dados da mesma fonte são exibidos em dois controles.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-104">This refers to a data-binding scenario where data from the same source is displayed in two controls.</span></span> <span data-ttu-id="6eb9a-105">Alterar a seleção em um controle faz com que os dados exibidos no segundo controle mudem.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-105">Changing the selection in one control causes the data displayed in the second control to change.</span></span> <span data-ttu-id="6eb9a-106">Por exemplo, o primeiro controle pode conter uma lista de clientes e o segundo, uma lista de pedidos relacionada ao cliente selecionado no primeiro controle.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-106">For example, the first control might contain a list of customers and the second a list of orders related to the selected customer in the first control.</span></span>  
  
 <span data-ttu-id="6eb9a-107">Iniciando com o .NET Framework versão 2.0, quando você exibe dados no modo de exibição pai/filho, pode ser necessário executar etapas adicionais para que a linha selecionada atualmente na tabela filho não seja redefinida para a primeira linha da tabela.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-107">Starting with the .NET Framework version 2.0, when you display data in a parent/child view you might have to take extra steps to make sure that the currently selected row in the child table is not reset to the first row of the table.</span></span> <span data-ttu-id="6eb9a-108">Para fazer isso, será preciso armazenar em cache a posição da tabela filho e redefini-la após a alteração da tabela pai.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-108">In order to do this, you will have to cache the child table position and reset it after the parent table changes.</span></span> <span data-ttu-id="6eb9a-109">Normalmente, a redefinição do filho ocorre na primeira vez que um campo em uma linha da tabela pai muda.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-109">Typically the child reset occurs the first time a field in a row of the parent table changes.</span></span>  
  
### <a name="to-cache-the-current-child-position"></a><span data-ttu-id="6eb9a-110">Para armazenar em cache a posição filho atual</span><span class="sxs-lookup"><span data-stu-id="6eb9a-110">To Cache the Current Child Position</span></span>  
  
1. <span data-ttu-id="6eb9a-111">Declare uma variável de inteiro para armazenar a posição de lista filho e uma variável booliana para indicar se a posição filho deve ser armazenada em cache.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-111">Declare an integer variable to store the child list position and a Boolean variable to store whether to cache the child position.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2. <span data-ttu-id="6eb9a-112">Lidar com o <xref:System.Windows.Forms.CurrencyManager.ListChanged> evento para a associação <xref:System.Windows.Forms.CurrencyManager> e verifique se há um <xref:System.ComponentModel.ListChangedType> de <xref:System.ComponentModel.ListChangedType.Reset>.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-112">Handle the <xref:System.Windows.Forms.CurrencyManager.ListChanged> event for the binding's <xref:System.Windows.Forms.CurrencyManager> and check for a <xref:System.ComponentModel.ListChangedType> of <xref:System.ComponentModel.ListChangedType.Reset>.</span></span>  
  
3. <span data-ttu-id="6eb9a-113">Verifique a posição atual do <xref:System.Windows.Forms.CurrencyManager>.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-113">Check the current position of the <xref:System.Windows.Forms.CurrencyManager>.</span></span> <span data-ttu-id="6eb9a-114">Se for maior que a primeira entrada na lista (normalmente 0), salve-a em uma variável.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-114">If it is greater than first entry in the list (typically 0), save it to a variable.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="6eb9a-115">Lidar com a lista de pai <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> evento para o Gerenciador de moeda pai.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-115">Handle the parent list's <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> event for the parent currency manager.</span></span> <span data-ttu-id="6eb9a-116">No manipulador, defina o valor booliano para indicar que este não é um cenário de cache.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-116">In the handler, set the Boolean value to indicate it is not a caching scenario.</span></span> <span data-ttu-id="6eb9a-117">Se o <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> ocorre, a alteração para o pai é uma alteração de posição de lista e não uma alteração de valor do item.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-117">If the <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> occurs, the change to the parent is a list position change and not an item value change.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### <a name="to-reset-the-child-position"></a><span data-ttu-id="6eb9a-118">Para redefinir a posição filho</span><span class="sxs-lookup"><span data-stu-id="6eb9a-118">To Reset the Child Position</span></span>  
  
1. <span data-ttu-id="6eb9a-119">Lidar com o <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> eventos para o filho da associação <xref:System.Windows.Forms.CurrencyManager>.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-119">Handle the <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> event for the child binding's <xref:System.Windows.Forms.CurrencyManager>.</span></span>  
  
2. <span data-ttu-id="6eb9a-120">Redefina a posição da tabela filho para a posição em cache salva no procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-120">Reset the child table position to the cached position saved in the previous procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="6eb9a-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6eb9a-121">Example</span></span>  
 <span data-ttu-id="6eb9a-122">O exemplo a seguir demonstra como salvar a posição atual no <xref:System.Windows.Forms.CurrencyManager>para uma tabela filho e redefinir a posição após a conclusão de uma edição na tabela pai.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-122">The following example demonstrates how to save the current position on the <xref:System.Windows.Forms.CurrencyManager>.for a child table and reset the position after an edit is completed on the parent table.</span></span> <span data-ttu-id="6eb9a-123">Este exemplo contém dois <xref:System.Windows.Forms.DataGridView> controles associados a duas tabelas em um <xref:System.Data.DataSet> usando um <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-123">This example contains two <xref:System.Windows.Forms.DataGridView> controls bound to two tables in a <xref:System.Data.DataSet> using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="6eb9a-124">É estabelecido um relacionamento entre as duas tabelas e o relacionamento é adicionado para o <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-124">A relation is established between the two tables and the relation is added to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="6eb9a-125">A posição na tabela filho inicialmente é definida como a terceira linha para fins de demonstração.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-125">The position in the child table is initially set to the third row for demonstration purposes.</span></span>  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 <span data-ttu-id="6eb9a-126">Para testar o exemplo de código, execute as etapas a seguir:</span><span class="sxs-lookup"><span data-stu-id="6eb9a-126">To test the code example, perform the following steps:</span></span>  
  
1. <span data-ttu-id="6eb9a-127">Execute o exemplo.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-127">Run the example.</span></span>  
  
2. <span data-ttu-id="6eb9a-128">Marque a caixa de seleção **Armazenar em cache e redefinir posição**.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-128">Make sure the **Cache and reset position** check box is selected.</span></span>  
  
3. <span data-ttu-id="6eb9a-129">Clique no botão **Limpar campo pai** para provocar uma alteração em um campo da tabela pai.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-129">Click the **Clear parent field** button to cause a change in a field of the parent table.</span></span> <span data-ttu-id="6eb9a-130">Observe que a linha selecionada na tabela filho não muda.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-130">Notice that the selected row in the child table does not change.</span></span>  
  
4. <span data-ttu-id="6eb9a-131">Feche e execute o exemplo novamente.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-131">Close and run the example again.</span></span> <span data-ttu-id="6eb9a-132">Você precisa fazer isso porque o comportamento de reinicialização ocorre apenas na primeira alteração da linha pai.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-132">You need to do this because the reset behavior occurs only on the first change in the parent row.</span></span>  
  
5. <span data-ttu-id="6eb9a-133">Desmarque a caixa de seleção **Armazenar em cache e redefinir posição**.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-133">Clear the **Cache and reset position** check box.</span></span>  
  
6. <span data-ttu-id="6eb9a-134">Clique no botão **Limpar campo pai**.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-134">Click the **Clear parent field** button.</span></span> <span data-ttu-id="6eb9a-135">Observe que a linha selecionada na tabela filho muda para a primeira linha.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-135">Notice that the selected row in the child table changes to the first row.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6eb9a-136">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="6eb9a-136">Compiling the Code</span></span>  
 <span data-ttu-id="6eb9a-137">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="6eb9a-137">This example requires:</span></span>  
  
- <span data-ttu-id="6eb9a-138">Referência aos assemblies System, System.Data, System.Drawing, System.Windows.Forms e System.XML.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-138">References to the System, System.Data, System.Drawing, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="6eb9a-139">Para obter informações sobre como criar este exemplo da linha de comando do Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [construção de linha de comando com csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6eb9a-139">For information about how to build this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6eb9a-140">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="6eb9a-140">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb9a-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6eb9a-141">See also</span></span>

- [<span data-ttu-id="6eb9a-142">Como: Certifique-se de vários controles associados à mesma fonte de dados permaneçam sincronizados</span><span class="sxs-lookup"><span data-stu-id="6eb9a-142">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](multiple-controls-bound-to-data-source-synchronized.md)
- [<span data-ttu-id="6eb9a-143">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="6eb9a-143">BindingSource Component</span></span>](./controls/bindingsource-component.md)
- [<span data-ttu-id="6eb9a-144">Vinculação de dados e os Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6eb9a-144">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
