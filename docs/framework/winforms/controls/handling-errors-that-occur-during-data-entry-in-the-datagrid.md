---
title: 'Walkthrough: Manipulando erros que ocorrem durante a entrada de dados no controle DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
ms.openlocfilehash: 77a4dcd9cf069ed8bbee6c49aa41db619c8e12ff
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738729"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="fb0aa-102">Instruções passo a passo: identificando erros que ocorram durante a entrada de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fb0aa-102">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>

<span data-ttu-id="fb0aa-103">O tratamento de erros do armazenamento de dados subjacente é um recurso necessário para um aplicativo de entrada de dados.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-103">Handling errors from the underlying data store is a required feature for a data-entry application.</span></span> <span data-ttu-id="fb0aa-104">O controle de <xref:System.Windows.Forms.DataGridView> de Windows Forms facilita isso expondo o evento de <xref:System.Windows.Forms.DataGridView.DataError>, que é gerado quando o repositório de dados detecta uma violação de restrição ou uma regra de negócio quebrada.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-104">The Windows Forms <xref:System.Windows.Forms.DataGridView> control makes this easy by exposing the <xref:System.Windows.Forms.DataGridView.DataError> event, which is raised when the data store detects a constraint violation or a broken business rule.</span></span>

<span data-ttu-id="fb0aa-105">Neste tutorial, você irá recuperar linhas da tabela `Customers` no banco de dados de exemplo Northwind e exibi-las em um controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-105">In this walkthrough, you will retrieve rows from the `Customers` table in the Northwind sample database and display them in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="fb0aa-106">Quando um valor de `CustomerID` duplicado for detectado em uma nova linha ou em uma linha existente editada, o evento de <xref:System.Windows.Forms.DataGridView.DataError> ocorrerá, o qual será tratado exibindo uma <xref:System.Windows.Forms.MessageBox> que descreve a exceção.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-106">When a duplicate `CustomerID` value is detected in a new row or an edited existing row, the <xref:System.Windows.Forms.DataGridView.DataError> event will occur, which will be handled by displaying a <xref:System.Windows.Forms.MessageBox> that describes the exception.</span></span>

<span data-ttu-id="fb0aa-107">Para copiar o código deste tópico como uma única lista, consulte [Como tratar erros que ocorrem durante a entrada de dados no controle DataGridView do Windows Forms](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="fb0aa-107">To copy the code in this topic as a single listing, see [How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fb0aa-108">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fb0aa-108">Prerequisites</span></span>

<span data-ttu-id="fb0aa-109">Para concluir este passo a passo, você precisará de:</span><span class="sxs-lookup"><span data-stu-id="fb0aa-109">In order to complete this walkthrough, you will need:</span></span>

- <span data-ttu-id="fb0aa-110">Acesso a um servidor que tem o banco de dados de exemplo SQL Server Northwind.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-110">Access to a server that has the Northwind SQL Server sample database.</span></span>

## <a name="creating-the-form"></a><span data-ttu-id="fb0aa-111">Criando o formulário</span><span class="sxs-lookup"><span data-stu-id="fb0aa-111">Creating the Form</span></span>

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a><span data-ttu-id="fb0aa-112">Tratar erros de entrada de dados no controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="fb0aa-112">To handle data-entry errors in the DataGridView control</span></span>

1. <span data-ttu-id="fb0aa-113">Crie uma classe que derive de <xref:System.Windows.Forms.Form> e contenha um controle de <xref:System.Windows.Forms.DataGridView> e um componente de <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control and a <xref:System.Windows.Forms.BindingSource> component.</span></span>

    <span data-ttu-id="fb0aa-114">O exemplo de código a seguir fornece inicialização básica e inclui um método `Main`.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-114">The following code example provides basic initialization and includes a `Main` method.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. <span data-ttu-id="fb0aa-115">Implemente um método na definição de classe do formulário para manipular os detalhes de conexão ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-115">Implement a method in your form's class definition for handling the details of connecting to the database.</span></span>

    <span data-ttu-id="fb0aa-116">Este exemplo de código usa um método `GetData` que retorna um objeto <xref:System.Data.DataTable> populado.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-116">This code example uses a `GetData` method that returns a populated <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="fb0aa-117">Verifique se a variável `connectionString` é definida como um valor apropriado para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-117">Be sure that you set the `connectionString` variable to a value that is appropriate for your database.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="fb0aa-118">O armazenamento das informações confidenciais, como uma senha, dentro da cadeia de conexão pode afetar a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-118">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="fb0aa-119">O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-119">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="fb0aa-120">Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="fb0aa-120">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. <span data-ttu-id="fb0aa-121">Implemente um manipulador para o evento <xref:System.Windows.Forms.Form.Load> do seu formulário que inicializa o <xref:System.Windows.Forms.DataGridView> e <xref:System.Windows.Forms.BindingSource> e configura a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-121">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> and <xref:System.Windows.Forms.BindingSource> and sets up the data binding.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. <span data-ttu-id="fb0aa-122">Manipule o evento de <xref:System.Windows.Forms.DataGridView.DataError> no <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-122">Handle the <xref:System.Windows.Forms.DataGridView.DataError> event on the <xref:System.Windows.Forms.DataGridView>.</span></span>

    <span data-ttu-id="fb0aa-123">Se o contexto do erro for uma operação de confirmação, exiba o erro em um <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-123">If the context for the error is a commit operation, display the error in a <xref:System.Windows.Forms.MessageBox>.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a><span data-ttu-id="fb0aa-124">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="fb0aa-124">Testing the Application</span></span>

<span data-ttu-id="fb0aa-125">Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-125">You can now test the form to make sure it behaves as expected.</span></span>

#### <a name="to-test-the-form"></a><span data-ttu-id="fb0aa-126">Para testar o formulário</span><span class="sxs-lookup"><span data-stu-id="fb0aa-126">To test the form</span></span>

- <span data-ttu-id="fb0aa-127">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-127">Press F5 to run the application.</span></span>

  <span data-ttu-id="fb0aa-128">Você verá um controle <xref:System.Windows.Forms.DataGridView> preenchido com dados da tabela Customers.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-128">You will see a <xref:System.Windows.Forms.DataGridView> control filled with data from the Customers table.</span></span> <span data-ttu-id="fb0aa-129">Se você inserir um valor duplicado para `CustomerID` e confirmar a edição, o valor da célula será revertido automaticamente e você verá um <xref:System.Windows.Forms.MessageBox> que exibe o erro de entrada de dados.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-129">If you enter a duplicate value for `CustomerID` and commit the edit, the cell value will revert automatically and you will see a <xref:System.Windows.Forms.MessageBox> that displays the data entry error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fb0aa-130">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="fb0aa-130">Next Steps</span></span>

<span data-ttu-id="fb0aa-131">Esse aplicativo oferece uma compreensão básica dos recursos do controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-131">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="fb0aa-132">Você pode personalizar a aparência e o comportamento do controle de <xref:System.Windows.Forms.DataGridView> de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="fb0aa-132">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>

- <span data-ttu-id="fb0aa-133">Alterar estilos de borda e cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-133">Change border and header styles.</span></span> <span data-ttu-id="fb0aa-134">Para obter mais informações, consulte [Como alterar os estilos de borda e linha de grade no controle DataGridView dos Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="fb0aa-134">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>

- <span data-ttu-id="fb0aa-135">Habilitar ou restringir a entrada do usuário para o controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-135">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="fb0aa-136">Para obter mais informações, consulte [Como evitar a adição e a exclusão de linhas no controle DataGridView do Windows Forms](prevent-row-addition-and-deletion-datagridview.md) e [Como tornar colunas somente leitura no controle DataGridView do Windows Forms](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="fb0aa-136">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>

- <span data-ttu-id="fb0aa-137">Valide a entrada do usuário para o controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-137">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="fb0aa-138">Para obter mais informações, consulte [Passo a passo: validando dados no controle DataGridView dos Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="fb0aa-138">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>

- <span data-ttu-id="fb0aa-139">Manipule grandes conjuntos de dados usando o modo virtual.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-139">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="fb0aa-140">Para obter mais informações, consulte [Passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="fb0aa-140">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>

- <span data-ttu-id="fb0aa-141">Personalize a aparência das células.</span><span class="sxs-lookup"><span data-stu-id="fb0aa-141">Customize the appearance of cells.</span></span> <span data-ttu-id="fb0aa-142">Para obter mais informações, consulte [Como personalizar a aparência de células no controle DataGridView dos Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md) e [Como definir estilos de célula padrão no controle DataGridView dos Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="fb0aa-142">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb0aa-143">Veja também</span><span class="sxs-lookup"><span data-stu-id="fb0aa-143">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="fb0aa-144">Entrada de Dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fb0aa-144">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="fb0aa-145">Como manipular erros ocorridos durante a entrada de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fb0aa-145">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="fb0aa-146">Passo a passo: validando dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fb0aa-146">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="fb0aa-147">Protegendo informações de conexão</span><span class="sxs-lookup"><span data-stu-id="fb0aa-147">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
