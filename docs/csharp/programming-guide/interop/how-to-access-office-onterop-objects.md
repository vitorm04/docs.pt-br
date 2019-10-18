---
title: Como acessar objetos de interoperabilidade do Office usando C# os recursos C# visuais – guia de programação
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: f0b763ad6b65c74b8c406fe006ef4036e70a99d4
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523555"
---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a><span data-ttu-id="0d204-102">Como acessar objetos de interoperabilidade do Office usando funcionalidades do Visual C# (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="0d204-102">How to: Access Office Interop Objects by Using Visual C# Features (C# Programming Guide)</span></span>

<span data-ttu-id="0d204-103">O Visual C# tem funcionalidades que simplificam o acesso a objetos de API do Office.</span><span class="sxs-lookup"><span data-stu-id="0d204-103">Visual C# has features that simplify access to Office API objects.</span></span> <span data-ttu-id="0d204-104">Os novos recursos incluem argumentos nomeados e opcionais, um novo tipo chamado `dynamic` e a capacidade de passar argumentos para parâmetros de referência em métodos COM como se fossem parâmetros de valor.</span><span class="sxs-lookup"><span data-stu-id="0d204-104">The new features include named and optional arguments, a new type called `dynamic`, and the ability to pass arguments to reference parameters in COM methods as if they were value parameters.</span></span>

<span data-ttu-id="0d204-105">Neste tópico, você usará os novos recursos para escrever código que cria e exibe uma planilha do Microsoft Office Excel.</span><span class="sxs-lookup"><span data-stu-id="0d204-105">In this topic you will use the new features to write code that creates and displays a Microsoft Office Excel worksheet.</span></span> <span data-ttu-id="0d204-106">Em seguida, você irá escrever código para adicionar um documento do Office Word que contenha um ícone que esteja vinculado à planilha do Excel.</span><span class="sxs-lookup"><span data-stu-id="0d204-106">You will then write code to add an Office Word document that contains an icon that is linked to the Excel worksheet.</span></span>

<span data-ttu-id="0d204-107">Para concluir este passo a passo, você deve ter o Microsoft Office Excel 2007 e o Microsoft Office Word 2007 ou versões posteriores, instaladas no computador.</span><span class="sxs-lookup"><span data-stu-id="0d204-107">To complete this walkthrough, you must have Microsoft Office Excel 2007 and Microsoft Office Word 2007, or later versions, installed on your computer.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="0d204-108">Para criar um novo aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="0d204-108">To create a new console application</span></span>

1. <span data-ttu-id="0d204-109">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0d204-109">Start Visual Studio.</span></span>

2. <span data-ttu-id="0d204-110">No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="0d204-110">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="0d204-111">A caixa de diálogo **Novo Projeto** é exibida.</span><span class="sxs-lookup"><span data-stu-id="0d204-111">The **New Project** dialog box appears.</span></span>

3. <span data-ttu-id="0d204-112">No painel **Modelos Instalados**, expanda **Visual C#** e, em seguida, selecione **Windows**.</span><span class="sxs-lookup"><span data-stu-id="0d204-112">In the **Installed Templates** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="0d204-113">Observe a parte superior da caixa de diálogo **Novo Projeto** para verificar se **.NET Framework 4** (ou versão posterior) está selecionado como uma estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="0d204-113">Look at the top of the **New Project** dialog box to make sure that **.NET Framework 4** (or later version) is selected as a target framework.</span></span>

5. <span data-ttu-id="0d204-114">No painel **Modelos**, clique em **Aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="0d204-114">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="0d204-115">Digite um nome para o projeto no campo **Nome**.</span><span class="sxs-lookup"><span data-stu-id="0d204-115">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="0d204-116">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="0d204-116">Click **OK**.</span></span>

     <span data-ttu-id="0d204-117">O novo projeto aparece no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="0d204-117">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-references"></a><span data-ttu-id="0d204-118">Para adicionar referências</span><span class="sxs-lookup"><span data-stu-id="0d204-118">To add references</span></span>

1. <span data-ttu-id="0d204-119">No **Gerenciador de Soluções**, clique com o botão direito do mouse no nome do projeto e, em seguida, clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="0d204-119">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="0d204-120">A caixa de diálogo **Adicionar Referência** é exibida.</span><span class="sxs-lookup"><span data-stu-id="0d204-120">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="0d204-121">Na página **Assemblies**, selecione **Microsoft.Office.Interop.Word** na lista **Nome do Componente** e, mantendo a tecla CTRL pressionada, selecione **Microsoft.Office.Interop.Excel**.</span><span class="sxs-lookup"><span data-stu-id="0d204-121">On the **Assemblies**  page, select **Microsoft.Office.Interop.Word** in the **Component Name** list, and then hold down the CTRL key and select **Microsoft.Office.Interop.Excel**.</span></span>  <span data-ttu-id="0d204-122">Se você não vir os assemblies, talvez seja necessário garantir que eles sejam instalados e exibidos.</span><span class="sxs-lookup"><span data-stu-id="0d204-122">If you do not see the assemblies, you may need to ensure they are installed and displayed.</span></span> <span data-ttu-id="0d204-123">Consulte [como instalar assemblies de interoperabilidade primária do Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).</span><span class="sxs-lookup"><span data-stu-id="0d204-123">See [How to: Install Office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).</span></span>

3. <span data-ttu-id="0d204-124">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="0d204-124">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="0d204-125">Para adicionar as diretivas using necessárias</span><span class="sxs-lookup"><span data-stu-id="0d204-125">To add necessary using directives</span></span>

1. <span data-ttu-id="0d204-126">No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo *Program.cs* e, em seguida, clique em **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="0d204-126">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="0d204-127">Adicione as seguintes diretivas de `using` à parte superior do arquivo de código:</span><span class="sxs-lookup"><span data-stu-id="0d204-127">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a><span data-ttu-id="0d204-128">Para criar uma lista de contas bancárias</span><span class="sxs-lookup"><span data-stu-id="0d204-128">To create a list of bank accounts</span></span>

1. <span data-ttu-id="0d204-129">Cole a seguinte definição de classe em **Program.cs**, na classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="0d204-129">Paste the following class definition into **Program.cs**, under the `Program` class.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. <span data-ttu-id="0d204-130">Adicione o seguinte código ao método `Main` para criar uma lista `bankAccounts` que contenha duas contas.</span><span class="sxs-lookup"><span data-stu-id="0d204-130">Add the following code to the `Main` method to create a `bankAccounts` list that contains two accounts.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a><span data-ttu-id="0d204-131">Para declarar um método que exporta as informações de conta para o Excel</span><span class="sxs-lookup"><span data-stu-id="0d204-131">To declare a method that exports account information to Excel</span></span>

1. <span data-ttu-id="0d204-132">Adicione o método a seguir à classe `Program` para configurar uma planilha do Excel.</span><span class="sxs-lookup"><span data-stu-id="0d204-132">Add the following method to the `Program` class to set up an Excel worksheet.</span></span>

     <span data-ttu-id="0d204-133">O método <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> tem um parâmetro opcional para especificar um modelo específico.</span><span class="sxs-lookup"><span data-stu-id="0d204-133">Method <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> has an optional parameter for specifying a particular template.</span></span> <span data-ttu-id="0d204-134">Os parâmetros opcionais, novos no C# 4, permitem omitir o argumento para esse parâmetro se você quiser usar o valor padrão do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0d204-134">Optional parameters, new in C# 4, enable you to omit the argument for that parameter if you want to use the parameter's default value.</span></span> <span data-ttu-id="0d204-135">Como nenhum argumento é enviado no código a seguir, `Add` usa o modelo padrão e cria uma nova pasta de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0d204-135">Because no argument is sent in the following code, `Add` uses the default template and creates a new workbook.</span></span> <span data-ttu-id="0d204-136">A instrução equivalente em versões anteriores do C# requer um argumento de espaço reservado: `ExcelApp.Workbooks.Add(Type.Missing)`.</span><span class="sxs-lookup"><span data-stu-id="0d204-136">The equivalent statement in earlier versions of C# requires a placeholder argument: `ExcelApp.Workbooks.Add(Type.Missing)`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. <span data-ttu-id="0d204-137">Adicione o código a seguir no final de `DisplayInExcel`.</span><span class="sxs-lookup"><span data-stu-id="0d204-137">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="0d204-138">O código insere valores nas duas primeiras colunas da primeira linha da planilha.</span><span class="sxs-lookup"><span data-stu-id="0d204-138">The code inserts values into the first two columns of the first row of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. <span data-ttu-id="0d204-139">Adicione o código a seguir no final de `DisplayInExcel`.</span><span class="sxs-lookup"><span data-stu-id="0d204-139">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="0d204-140">O loop `foreach` coloca as informações da lista de contas nas duas primeiras colunas de sucessivas linhas da planilha.</span><span class="sxs-lookup"><span data-stu-id="0d204-140">The `foreach` loop puts the information from the list of accounts into the first two columns of successive rows of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. <span data-ttu-id="0d204-141">Adicione o seguinte código no final de `DisplayInExcel` para ajustar as larguras das colunas para adequar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="0d204-141">Add the following code at the end of `DisplayInExcel` to adjust the column widths to fit the content.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     <span data-ttu-id="0d204-142">As versões anteriores do C# exigem a conversão explícita para essas operações, porque `ExcelApp.Columns[1]` retorna um `Object`, e `AutoFit` é um método <xref:Microsoft.Office.Interop.Excel.Range> do Excel.</span><span class="sxs-lookup"><span data-stu-id="0d204-142">Earlier versions of C# require explicit casting for these operations because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel <xref:Microsoft.Office.Interop.Excel.Range> method.</span></span> <span data-ttu-id="0d204-143">As linhas a seguir mostram a conversão.</span><span class="sxs-lookup"><span data-stu-id="0d204-143">The following lines show the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     <span data-ttu-id="0d204-144">C#4, e versões posteriores, converte o `Object` retornado para `dynamic` automaticamente se o assembly for referenciado pela opção do compilador [-link](../../language-reference/compiler-options/link-compiler-option.md) ou, de maneira equivalente, se a propriedade **inserir tipos de interoperabilidade** do Excel estiver definida como true.</span><span class="sxs-lookup"><span data-stu-id="0d204-144">C# 4, and later versions, converts the returned `Object` to `dynamic` automatically if the assembly is referenced by the [-link](../../language-reference/compiler-options/link-compiler-option.md) compiler option or, equivalently, if the Excel **Embed Interop Types** property is set to true.</span></span> <span data-ttu-id="0d204-145">True é o valor padrão para essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="0d204-145">True is the default value for this property.</span></span>

## <a name="to-run-the-project"></a><span data-ttu-id="0d204-146">Para executar o projeto</span><span class="sxs-lookup"><span data-stu-id="0d204-146">To run the project</span></span>

1. <span data-ttu-id="0d204-147">Adicione a seguinte linha no final de `Main`.</span><span class="sxs-lookup"><span data-stu-id="0d204-147">Add the following line at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. <span data-ttu-id="0d204-148">Pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="0d204-148">Press CTRL+F5.</span></span>

     <span data-ttu-id="0d204-149">Uma planilha do Excel é exibida contendo os dados das duas contas.</span><span class="sxs-lookup"><span data-stu-id="0d204-149">An Excel worksheet appears that contains the data from the two accounts.</span></span>

## <a name="to-add-a-word-document"></a><span data-ttu-id="0d204-150">Para adicionar um documento do Word</span><span class="sxs-lookup"><span data-stu-id="0d204-150">To add a Word document</span></span>

1. <span data-ttu-id="0d204-151">Para ilustrar maneiras adicionais pelas quais o C# 4 e versões posteriores aprimoram a programação do Office, o código a seguir abre um aplicativo Word e cria um ícone vinculado à planilha do Excel.</span><span class="sxs-lookup"><span data-stu-id="0d204-151">To illustrate additional ways in which C# 4, and later versions, enhances Office programming, the following code opens a Word application and creates an icon that links to the Excel worksheet.</span></span>

     <span data-ttu-id="0d204-152">Cole o método `CreateIconInWordDoc`, fornecido posteriormente nesta etapa, na classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="0d204-152">Paste method `CreateIconInWordDoc`, provided later in this step, into the `Program` class.</span></span> <span data-ttu-id="0d204-153">O `CreateIconInWordDoc` usa argumentos nomeados e opcionais para reduzir a complexidade das chamadas de método a <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> e <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d204-153">`CreateIconInWordDoc` uses named and optional arguments to reduce the complexity of the method calls to <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> and <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span></span> <span data-ttu-id="0d204-154">Essas chamadas incorporam dois novos recursos apresentados no C# 4 que simplificam as chamadas aos métodos COM que possuem parâmetros de referência.</span><span class="sxs-lookup"><span data-stu-id="0d204-154">These calls incorporate two other new features introduced in C# 4 that simplify calls to COM methods that have reference parameters.</span></span> <span data-ttu-id="0d204-155">Primeiro, você pode enviar argumentos para os parâmetros de referência como se fossem parâmetros de valor.</span><span class="sxs-lookup"><span data-stu-id="0d204-155">First, you can send arguments to the reference parameters as if they were value parameters.</span></span> <span data-ttu-id="0d204-156">Ou seja, você pode enviar valores diretamente, sem criar uma variável para cada parâmetro de referência.</span><span class="sxs-lookup"><span data-stu-id="0d204-156">That is, you can send values directly, without creating a variable for each reference parameter.</span></span> <span data-ttu-id="0d204-157">O compilador gera variáveis temporárias para conter os valores de argumento e descarta as variáveis quando você retornar da chamada.</span><span class="sxs-lookup"><span data-stu-id="0d204-157">The compiler generates temporary variables to hold the argument values, and discards the variables when you return from the call.</span></span> <span data-ttu-id="0d204-158">Em segundo lugar, você pode omitir a palavra-chave `ref` na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="0d204-158">Second, you can omit the `ref` keyword in the argument list.</span></span>

     <span data-ttu-id="0d204-159">O método `Add` tem quatro parâmetros de referência que são opcionais.</span><span class="sxs-lookup"><span data-stu-id="0d204-159">The `Add` method has four reference parameters, all of which are optional.</span></span> <span data-ttu-id="0d204-160">No C# 4.0 e versões posteriores, você poderá omitir argumentos para alguns ou todos os parâmetros se desejar usar os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="0d204-160">In C# 4.0 and later versions, you can omit arguments for any or all of the parameters if you want to use their default values.</span></span> <span data-ttu-id="0d204-161">No C# 3.0 e versões anteriores, um argumento deve ser fornecido para cada parâmetro e o argumento deve ser uma variável, pois os parâmetros são parâmetros de referência.</span><span class="sxs-lookup"><span data-stu-id="0d204-161">In C# 3.0 and earlier versions, an argument must be provided for each parameter, and the argument must be a variable because the parameters are reference parameters.</span></span>

     <span data-ttu-id="0d204-162">O método `PasteSpecial` insere o conteúdo da área de transferência.</span><span class="sxs-lookup"><span data-stu-id="0d204-162">The `PasteSpecial` method inserts the contents of the Clipboard.</span></span> <span data-ttu-id="0d204-163">O método tem sete parâmetros de referência que são opcionais.</span><span class="sxs-lookup"><span data-stu-id="0d204-163">The method has seven reference parameters, all of which are optional.</span></span> <span data-ttu-id="0d204-164">O código a seguir especifica argumentos para dois deles: `Link`, para criar um link para a origem do conteúdo da área de transferência, e `DisplayAsIcon`, para exibir o link como um ícone.</span><span class="sxs-lookup"><span data-stu-id="0d204-164">The following code specifies arguments for two of them: `Link`, to create a link to the source of the Clipboard contents, and `DisplayAsIcon`, to display the link as an icon.</span></span> <span data-ttu-id="0d204-165">No C# 4.0 e versões posteriores, você pode usar argumentos nomeados para esses dois e omitir os outros.</span><span class="sxs-lookup"><span data-stu-id="0d204-165">In C# 4.0 and later versions, you can use named arguments for those two and omit the others.</span></span> <span data-ttu-id="0d204-166">Embora esses sejam parâmetros de referência, você não precisa usar a palavra-chave `ref` ou criar variáveis para os enviar como argumentos.</span><span class="sxs-lookup"><span data-stu-id="0d204-166">Although these are reference parameters, you do not have to use the `ref` keyword, or to create variables to send in as arguments.</span></span> <span data-ttu-id="0d204-167">Você pode enviar os valores diretamente.</span><span class="sxs-lookup"><span data-stu-id="0d204-167">You can send the values directly.</span></span> <span data-ttu-id="0d204-168">No C# 3.0 e versões anteriores, você deve fornecer um argumento variável para cada parâmetro de referência.</span><span class="sxs-lookup"><span data-stu-id="0d204-168">In C# 3.0 and earlier versions, you must supply a variable argument for each reference parameter.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     <span data-ttu-id="0d204-169">No C# 3.0 e versões anteriores da linguagem, o código a seguir mais complexo é necessário.</span><span class="sxs-lookup"><span data-stu-id="0d204-169">In C# 3.0 and earlier versions of the language, the following more complex code is required.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. <span data-ttu-id="0d204-170">Adicione a instrução a seguir no final de `Main`.</span><span class="sxs-lookup"><span data-stu-id="0d204-170">Add the following statement at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. <span data-ttu-id="0d204-171">Adicione a instrução a seguir no final de `DisplayInExcel`.</span><span class="sxs-lookup"><span data-stu-id="0d204-171">Add the following statement at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="0d204-172">O método `Copy` adiciona a planilha na área de transferência.</span><span class="sxs-lookup"><span data-stu-id="0d204-172">The `Copy` method adds the worksheet to the Clipboard.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. <span data-ttu-id="0d204-173">Pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="0d204-173">Press CTRL+F5.</span></span>

     <span data-ttu-id="0d204-174">Um documento do Word é exibido contendo um ícone.</span><span class="sxs-lookup"><span data-stu-id="0d204-174">A Word document appears that contains an icon.</span></span> <span data-ttu-id="0d204-175">Clique duas vezes no ícone para colocar a planilha no primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="0d204-175">Double-click the icon to bring the worksheet to the foreground.</span></span>

## <a name="to-set-the-embed-interop-types-property"></a><span data-ttu-id="0d204-176">Para definir a propriedade Inserir Tipos Interop</span><span class="sxs-lookup"><span data-stu-id="0d204-176">To set the Embed Interop Types property</span></span>

1. <span data-ttu-id="0d204-177">Melhorias adicionais são possíveis quando você chama um tipo COM que não requer um assembly de interoperabilidade primário (PIA) no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0d204-177">Additional enhancements are possible when you call a COM type that does not require a primary interop assembly (PIA) at run time.</span></span> <span data-ttu-id="0d204-178">A remoção da dependência nos PIAs resulta na independência de versão e em uma implantação mais fácil.</span><span class="sxs-lookup"><span data-stu-id="0d204-178">Removing the dependency on PIAs results in version independence and easier deployment.</span></span> <span data-ttu-id="0d204-179">Para obter mais informações sobre as vantagens da programação sem PIAs, consulte [Passo a passo: inserindo tipos de assemblies gerenciados](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="0d204-179">For more information about the advantages of programming without PIAs, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>

     <span data-ttu-id="0d204-180">Além disso, a programação é mais fácil porque os tipos necessários e retornados por métodos COM podem ser representados usando o tipo `dynamic`, em vez de `Object`.</span><span class="sxs-lookup"><span data-stu-id="0d204-180">In addition, programming is easier because the types that are required and returned by COM methods can be represented by using the type `dynamic` instead of `Object`.</span></span> <span data-ttu-id="0d204-181">Variáveis com o tipo `dynamic` não são avaliadas até o tempo de execução, o que elimina a necessidade de conversão explícita.</span><span class="sxs-lookup"><span data-stu-id="0d204-181">Variables that have type `dynamic` are not evaluated until run time, which eliminates the need for explicit casting.</span></span> <span data-ttu-id="0d204-182">Para obter mais informações, veja [Usando o tipo dynamic](../types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="0d204-182">For more information, see [Using Type dynamic](../types/using-type-dynamic.md).</span></span>

     <span data-ttu-id="0d204-183">No C# 4, a inserção de informações de tipo, em vez do uso de PIAs, é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="0d204-183">In C# 4, embedding type information instead of using PIAs is default behavior.</span></span> <span data-ttu-id="0d204-184">Devido a esse padrão, vários dos exemplos anteriores são simplificados pois a conversão explícita não é necessária.</span><span class="sxs-lookup"><span data-stu-id="0d204-184">Because of that default, several of the previous examples are simplified because explicit casting is not required.</span></span> <span data-ttu-id="0d204-185">Por exemplo, a declaração de `worksheet` em `DisplayInExcel` é escrita como `Excel._Worksheet workSheet = excelApp.ActiveSheet`, em vez de `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span><span class="sxs-lookup"><span data-stu-id="0d204-185">For example, the declaration of `worksheet` in `DisplayInExcel` is written as `Excel._Worksheet workSheet = excelApp.ActiveSheet` rather than `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span></span> <span data-ttu-id="0d204-186">As chamadas para `AutoFit` no mesmo método também exigem conversão explícita sem o padrão, pois `ExcelApp.Columns[1]` retorna um `Object`, e `AutoFit` é um método do Excel.</span><span class="sxs-lookup"><span data-stu-id="0d204-186">The calls to `AutoFit` in the same method also would require explicit casting without the default, because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel  method.</span></span> <span data-ttu-id="0d204-187">O código a seguir mostra a conversão.</span><span class="sxs-lookup"><span data-stu-id="0d204-187">The following code shows the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. <span data-ttu-id="0d204-188">Para alterar o padrão e usar PIAs em vez de inserir informações de tipo, expanda o nó **Referências** no **Gerenciador de Soluções** e, em seguida, selecione **Microsoft.Office.Interop.Excel** ou **Microsoft.Office.Interop.Word**.</span><span class="sxs-lookup"><span data-stu-id="0d204-188">To change the default and use PIAs instead of embedding type information, expand the **References** node in **Solution Explorer** and then select **Microsoft.Office.Interop.Excel** or **Microsoft.Office.Interop.Word**.</span></span>

3. <span data-ttu-id="0d204-189">Se você não conseguir ver a janela **Propriedades**, pressione **F4**.</span><span class="sxs-lookup"><span data-stu-id="0d204-189">If you cannot see the **Properties** window, press **F4**.</span></span>

4. <span data-ttu-id="0d204-190">Localize **Inserir Tipos Interop** na lista de propriedades e altere seu valor para **False**.</span><span class="sxs-lookup"><span data-stu-id="0d204-190">Find **Embed Interop Types** in the list of properties, and change its value to **False**.</span></span> <span data-ttu-id="0d204-191">De maneira equivalente, você pode compilar usando a opção [-Reference](../../language-reference/compiler-options/reference-compiler-option.md) do compilador em vez de [-link](../../language-reference/compiler-options/link-compiler-option.md) em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="0d204-191">Equivalently, you can compile by using the [-reference](../../language-reference/compiler-options/reference-compiler-option.md) compiler option instead of [-link](../../language-reference/compiler-options/link-compiler-option.md) at a command prompt.</span></span>

## <a name="to-add-additional-formatting-to-the-table"></a><span data-ttu-id="0d204-192">Para adicionar formatação adicional à tabela</span><span class="sxs-lookup"><span data-stu-id="0d204-192">To add additional formatting to the table</span></span>

1. <span data-ttu-id="0d204-193">Substitua as duas chamadas para `AutoFit` em `DisplayInExcel` pela instrução a seguir.</span><span class="sxs-lookup"><span data-stu-id="0d204-193">Replace the two calls to `AutoFit` in `DisplayInExcel` with the following statement.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     <span data-ttu-id="0d204-194">O método <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> tem sete parâmetros de valor, que são opcionais.</span><span class="sxs-lookup"><span data-stu-id="0d204-194">The <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method has seven value parameters, all of which are optional.</span></span> <span data-ttu-id="0d204-195">Argumentos nomeados e opcionais permitem que você forneça argumentos para nenhum, alguns ou todos eles.</span><span class="sxs-lookup"><span data-stu-id="0d204-195">Named and optional arguments enable you to provide arguments for none, some, or all of them.</span></span> <span data-ttu-id="0d204-196">Na instrução anterior, um argumento é fornecido para apenas um dos parâmetros, `Format`.</span><span class="sxs-lookup"><span data-stu-id="0d204-196">In the previous statement, an argument is supplied for only one of the parameters, `Format`.</span></span> <span data-ttu-id="0d204-197">Como `Format` é o primeiro parâmetro na lista de parâmetros, você não precisará fornecer o nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0d204-197">Because `Format` is the first parameter in the parameter list, you do not have to provide the parameter name.</span></span> <span data-ttu-id="0d204-198">No entanto, poderá ser mais fácil entender a instrução se o nome do parâmetro estiver incluído, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="0d204-198">However, the statement might be easier to understand if the parameter name is included, as is shown in the following code.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. <span data-ttu-id="0d204-199">Pressione CTRL + F5 para ver o resultado.</span><span class="sxs-lookup"><span data-stu-id="0d204-199">Press CTRL+F5 to see the result.</span></span> <span data-ttu-id="0d204-200">Outros formatos estão listados na enumeração <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat>.</span><span class="sxs-lookup"><span data-stu-id="0d204-200">Other formats are listed in the <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> enumeration.</span></span>

3. <span data-ttu-id="0d204-201">Compare a instrução na etapa 1 com o código a seguir, que mostra os argumentos que são necessários no C# 3.0 ou versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="0d204-201">Compare the statement in step 1 with the following code, which shows the arguments that are required in C# 3.0 and earlier versions.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a><span data-ttu-id="0d204-202">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d204-202">Example</span></span>

<span data-ttu-id="0d204-203">O código a seguir mostra um exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="0d204-203">The following code shows the complete example.</span></span>

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a><span data-ttu-id="0d204-204">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d204-204">See also</span></span>

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [<span data-ttu-id="0d204-205">dynamic</span><span class="sxs-lookup"><span data-stu-id="0d204-205">dynamic</span></span>](../../language-reference/keywords/dynamic.md)
- [<span data-ttu-id="0d204-206">Usando o tipo dynamic</span><span class="sxs-lookup"><span data-stu-id="0d204-206">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="0d204-207">Argumentos nomeados e opcionais</span><span class="sxs-lookup"><span data-stu-id="0d204-207">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="0d204-208">Como usar argumentos nomeados e opcionais na programação do Office</span><span class="sxs-lookup"><span data-stu-id="0d204-208">How to: Use Named and Optional Arguments in Office Programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
