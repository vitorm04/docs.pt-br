---
title: 'Passo a passo: Identificando Erros que Ocorrem Durante a Entrada de Dados no Controle DataGridView do Windows Forms'
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
ms.openlocfilehash: cee6fe3b049378fa7bbe2585a3607049eaf231bc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046085"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="104d3-102">Passo a passo: Identificando Erros que Ocorrem Durante a Entrada de Dados no Controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="104d3-102">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>

<span data-ttu-id="104d3-103">O tratamento de erros do armazenamento de dados subjacente é um recurso necessário para um aplicativo de entrada de dados.</span><span class="sxs-lookup"><span data-stu-id="104d3-103">Handling errors from the underlying data store is a required feature for a data-entry application.</span></span> <span data-ttu-id="104d3-104">O controle <xref:System.Windows.Forms.DataGridView> de Windows Forms facilita esse processo expondo o <xref:System.Windows.Forms.DataGridView.DataError> evento, que é gerado quando o armazenamento de dados detecta uma violação de restrição ou uma regra de negócio quebrada.</span><span class="sxs-lookup"><span data-stu-id="104d3-104">The Windows Forms <xref:System.Windows.Forms.DataGridView> control makes this easy by exposing the <xref:System.Windows.Forms.DataGridView.DataError> event, which is raised when the data store detects a constraint violation or a broken business rule.</span></span>

<span data-ttu-id="104d3-105">Neste tutorial, você irá recuperar linhas da `Customers` tabela no banco de dados de exemplo Northwind e exibi-las em um <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="104d3-105">In this walkthrough, you will retrieve rows from the `Customers` table in the Northwind sample database and display them in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="104d3-106">Quando um valor `CustomerID` duplicado for detectado em uma nova linha ou em uma linha existente editada, o <xref:System.Windows.Forms.DataGridView.DataError> evento ocorrerá, que será manipulado <xref:System.Windows.Forms.MessageBox> exibindo um que descreve a exceção.</span><span class="sxs-lookup"><span data-stu-id="104d3-106">When a duplicate `CustomerID` value is detected in a new row or an edited existing row, the <xref:System.Windows.Forms.DataGridView.DataError> event will occur, which will be handled by displaying a <xref:System.Windows.Forms.MessageBox> that describes the exception.</span></span>

<span data-ttu-id="104d3-107">Para copiar o código deste tópico como uma única listagem, confira [Como: Manipule erros que ocorrem durante a entrada de dados no controle](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)DataGridView Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="104d3-107">To copy the code in this topic as a single listing, see [How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="104d3-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="104d3-108">Prerequisites</span></span>

<span data-ttu-id="104d3-109">Para concluir este passo a passo, você precisará de:</span><span class="sxs-lookup"><span data-stu-id="104d3-109">In order to complete this walkthrough, you will need:</span></span>

- <span data-ttu-id="104d3-110">Acesso a um servidor com o banco de dados de exemplo Northwind do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="104d3-110">Access to a server that has the Northwind SQL Server sample database.</span></span>

## <a name="creating-the-form"></a><span data-ttu-id="104d3-111">Criando o formulário</span><span class="sxs-lookup"><span data-stu-id="104d3-111">Creating the Form</span></span>

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a><span data-ttu-id="104d3-112">Tratar erros de entrada de dados no controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="104d3-112">To handle data-entry errors in the DataGridView control</span></span>

1. <span data-ttu-id="104d3-113">Crie uma classe que deriva de <xref:System.Windows.Forms.Form> e contém um <xref:System.Windows.Forms.DataGridView> controle e um <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="104d3-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control and a <xref:System.Windows.Forms.BindingSource> component.</span></span>

    <span data-ttu-id="104d3-114">O exemplo de código a seguir fornece inicialização básica e inclui um método `Main`.</span><span class="sxs-lookup"><span data-stu-id="104d3-114">The following code example provides basic initialization and includes a `Main` method.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. <span data-ttu-id="104d3-115">Implemente um método na definição de classe do formulário para manipular os detalhes de conexão ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="104d3-115">Implement a method in your form's class definition for handling the details of connecting to the database.</span></span>

    <span data-ttu-id="104d3-116">Este exemplo de código usa `GetData` um método que retorna um <xref:System.Data.DataTable> objeto populado.</span><span class="sxs-lookup"><span data-stu-id="104d3-116">This code example uses a `GetData` method that returns a populated <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="104d3-117">Verifique se a variável `connectionString` é definida como um valor apropriado para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="104d3-117">Be sure that you set the `connectionString` variable to a value that is appropriate for your database.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="104d3-118">O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="104d3-118">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="104d3-119">O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="104d3-119">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="104d3-120">Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="104d3-120">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. <span data-ttu-id="104d3-121">Implemente um manipulador para o evento <xref:System.Windows.Forms.Form.Load> do formulário que inicializa <xref:System.Windows.Forms.DataGridView> o <xref:System.Windows.Forms.BindingSource> e e define a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="104d3-121">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> and <xref:System.Windows.Forms.BindingSource> and sets up the data binding.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. <span data-ttu-id="104d3-122">Manipule o <xref:System.Windows.Forms.DataGridView.DataError> evento <xref:System.Windows.Forms.DataGridView>no.</span><span class="sxs-lookup"><span data-stu-id="104d3-122">Handle the <xref:System.Windows.Forms.DataGridView.DataError> event on the <xref:System.Windows.Forms.DataGridView>.</span></span>

    <span data-ttu-id="104d3-123">Se o contexto do erro for uma operação de confirmação, exiba o erro em um <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="104d3-123">If the context for the error is a commit operation, display the error in a <xref:System.Windows.Forms.MessageBox>.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a><span data-ttu-id="104d3-124">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="104d3-124">Testing the Application</span></span>

<span data-ttu-id="104d3-125">Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.</span><span class="sxs-lookup"><span data-stu-id="104d3-125">You can now test the form to make sure it behaves as expected.</span></span>

#### <a name="to-test-the-form"></a><span data-ttu-id="104d3-126">Para testar o formulário</span><span class="sxs-lookup"><span data-stu-id="104d3-126">To test the form</span></span>

- <span data-ttu-id="104d3-127">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="104d3-127">Press F5 to run the application.</span></span>

  <span data-ttu-id="104d3-128">Você verá um <xref:System.Windows.Forms.DataGridView> controle preenchido com dados da tabela Customers.</span><span class="sxs-lookup"><span data-stu-id="104d3-128">You will see a <xref:System.Windows.Forms.DataGridView> control filled with data from the Customers table.</span></span> <span data-ttu-id="104d3-129">Se você inserir um valor duplicado `CustomerID` para e confirmar a edição, o valor da célula será revertido automaticamente e você <xref:System.Windows.Forms.MessageBox> verá um que exibe o erro de entrada de dados.</span><span class="sxs-lookup"><span data-stu-id="104d3-129">If you enter a duplicate value for `CustomerID` and commit the edit, the cell value will revert automatically and you will see a <xref:System.Windows.Forms.MessageBox> that displays the data entry error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="104d3-130">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="104d3-130">Next Steps</span></span>

<span data-ttu-id="104d3-131">Esse aplicativo oferece uma compreensão básica dos <xref:System.Windows.Forms.DataGridView> recursos do controle.</span><span class="sxs-lookup"><span data-stu-id="104d3-131">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="104d3-132">Você pode personalizar a aparência e o comportamento do <xref:System.Windows.Forms.DataGridView> controle de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="104d3-132">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>

- <span data-ttu-id="104d3-133">Alterar estilos de borda e cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="104d3-133">Change border and header styles.</span></span> <span data-ttu-id="104d3-134">Para obter mais informações, confira [Como: Altere os estilos da borda e da linha de grade no](change-the-border-and-gridline-styles-in-the-datagrid.md)controle Windows Forms DataGridView.</span><span class="sxs-lookup"><span data-stu-id="104d3-134">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>

- <span data-ttu-id="104d3-135">Habilitar ou restringir a entrada do usuário <xref:System.Windows.Forms.DataGridView> para o controle.</span><span class="sxs-lookup"><span data-stu-id="104d3-135">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="104d3-136">Para obter mais informações, confira [Como: Impeça a adição e exclusão de linhas no controle](prevent-row-addition-and-deletion-datagridview.md)Windows Forms DataGridView e [como: Tornar as colunas somente leitura no controle](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)Windows Forms DataGridView.</span><span class="sxs-lookup"><span data-stu-id="104d3-136">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>

- <span data-ttu-id="104d3-137">Valide a entrada do usuário <xref:System.Windows.Forms.DataGridView> para o controle.</span><span class="sxs-lookup"><span data-stu-id="104d3-137">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="104d3-138">Para obter mais informações, confira [Passo a passo: Validação de dados no controle](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)Windows Forms DataGridView.</span><span class="sxs-lookup"><span data-stu-id="104d3-138">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>

- <span data-ttu-id="104d3-139">Manipule grandes conjuntos de dados usando o modo virtual.</span><span class="sxs-lookup"><span data-stu-id="104d3-139">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="104d3-140">Para obter mais informações, confira [Passo a passo: Implementando o modo virtual no controle](implementing-virtual-mode-wf-datagridview-control.md)Windows Forms DataGridView.</span><span class="sxs-lookup"><span data-stu-id="104d3-140">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>

- <span data-ttu-id="104d3-141">Personalize a aparência das células.</span><span class="sxs-lookup"><span data-stu-id="104d3-141">Customize the appearance of cells.</span></span> <span data-ttu-id="104d3-142">Para obter mais informações, confira [Como: Personalize a aparência das células no controle](customize-the-appearance-of-cells-in-the-datagrid.md) Windows Forms DataGridView e [como: Defina os estilos de célula padrão para o controle](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)Windows Forms DataGridView.</span><span class="sxs-lookup"><span data-stu-id="104d3-142">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="104d3-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="104d3-143">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="104d3-144">Entrada de Dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="104d3-144">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="104d3-145">Como: Manipular erros que ocorrem durante a entrada de dados no controle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="104d3-145">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="104d3-146">Passo a passo: Validando dados no controle Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="104d3-146">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="104d3-147">Protegendo informações de conexão</span><span class="sxs-lookup"><span data-stu-id="104d3-147">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
