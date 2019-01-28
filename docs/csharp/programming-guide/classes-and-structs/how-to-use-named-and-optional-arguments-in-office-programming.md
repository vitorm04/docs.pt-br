---
title: 'Como: usar argumentos nomeados e opcionais na programação do Office – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 96ffaff9b6d29a8630c161e2e560e7e60ad90ef0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498746"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="e842e-102">Como: usar argumentos nomeados e opcionais na programação do Office (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e842e-102">How to: Use Named and Optional Arguments in Office Programming (C# Programming Guide)</span></span>
<span data-ttu-id="e842e-103">Os argumentos nomeados e opcionais, introduzidos em [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], aprimoram a conveniência, a flexibilidade e a legibilidade na programação em C#.</span><span class="sxs-lookup"><span data-stu-id="e842e-103">Named arguments and optional arguments, introduced in [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="e842e-104">Além disso, esses recursos facilitam bastante o acesso a interfaces COM, como as APIs de Automação do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="e842e-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>  
  
 <span data-ttu-id="e842e-105">No exemplo a seguir, o método [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) tem 16 parâmetros que representam as características de uma tabela, como o número de colunas e linhas, formatação, bordas, fontes e cores.</span><span class="sxs-lookup"><span data-stu-id="e842e-105">In the following example, method [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="e842e-106">Todos os 16 parâmetros são opcionais, pois na maioria das vezes você não quiser especificar valores específicos para todos eles.</span><span class="sxs-lookup"><span data-stu-id="e842e-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="e842e-107">No entanto, sem argumentos nomeados e opcionais, um valor ou um valor de espaço reservado precisa ser fornecido para cada parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e842e-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="e842e-108">Com argumentos nomeados e opcionais, você especifica valores apenas para os parâmetros que são necessários para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="e842e-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>  
  
 <span data-ttu-id="e842e-109">Você deve ter o Microsoft Office Word instalado em seu computador para concluir esses procedimentos.</span><span class="sxs-lookup"><span data-stu-id="e842e-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a><span data-ttu-id="e842e-110">Para criar um novo aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="e842e-110">To create a new console application</span></span>  
  
1.  <span data-ttu-id="e842e-111">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e842e-111">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="e842e-112">No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="e842e-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="e842e-113">No painel **Templates Categories (Categorias de Modelos)**, expanda **Visual C#** e clique em **Windows**.</span><span class="sxs-lookup"><span data-stu-id="e842e-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>  
  
4.  <span data-ttu-id="e842e-114">Observe a parte superior do painel **Modelos** para se certificar de que **.NET Framework 4** é exibido na caixa **Estrutura de Destino**.</span><span class="sxs-lookup"><span data-stu-id="e842e-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>  
  
5.  <span data-ttu-id="e842e-115">No painel **Modelos**, clique em **Aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="e842e-115">In the **Templates** pane, click **Console Application**.</span></span>  
  
6.  <span data-ttu-id="e842e-116">Digite um nome para o projeto no campo **Nome**.</span><span class="sxs-lookup"><span data-stu-id="e842e-116">Type a name for your project in the **Name** field.</span></span>  
  
7.  <span data-ttu-id="e842e-117">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="e842e-117">Click **OK**.</span></span>  
  
     <span data-ttu-id="e842e-118">O novo projeto aparece no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="e842e-118">The new project appears in **Solution Explorer**.</span></span>  
  
### <a name="to-add-a-reference"></a><span data-ttu-id="e842e-119">Para adicionar uma referência</span><span class="sxs-lookup"><span data-stu-id="e842e-119">To add a reference</span></span>  
  
1.  <span data-ttu-id="e842e-120">No **Gerenciador de Soluções**, clique com o botão direito do mouse no nome do projeto e, em seguida, clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="e842e-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="e842e-121">A caixa de diálogo **Adicionar Referência** é exibida.</span><span class="sxs-lookup"><span data-stu-id="e842e-121">The **Add Reference** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="e842e-122">Na página **.NET**, selecione **Microsoft.Office.Interop.Word** na lista **Nome do Componente**.</span><span class="sxs-lookup"><span data-stu-id="e842e-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>  
  
3.  <span data-ttu-id="e842e-123">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="e842e-123">Click **OK**.</span></span>  
  
### <a name="to-add-necessary-using-directives"></a><span data-ttu-id="e842e-124">Para adicionar as diretivas using necessárias</span><span class="sxs-lookup"><span data-stu-id="e842e-124">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="e842e-125">No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo **Program.cs** e, em seguida, clique em **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="e842e-125">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="e842e-126">Adicione as seguintes diretivas `using` na parte superior do arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="e842e-126">Add the following `using` directives to the top of the code file.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]  
  
### <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="e842e-127">Para exibir texto em um documento do Word</span><span class="sxs-lookup"><span data-stu-id="e842e-127">To display text in a Word document</span></span>  
  
1.  <span data-ttu-id="e842e-128">Na classe `Program` em Program.cs, adicione o seguinte método para criar um aplicativo do Word e um documento do Word.</span><span class="sxs-lookup"><span data-stu-id="e842e-128">In the `Program` class in Program.cs, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="e842e-129">O método [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) tem quatro parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="e842e-129">The [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) method has four optional parameters.</span></span> <span data-ttu-id="e842e-130">Este exemplo usa os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="e842e-130">This example uses their default values.</span></span> <span data-ttu-id="e842e-131">Portanto, nenhum argumento é necessário na instrução de chamada.</span><span class="sxs-lookup"><span data-stu-id="e842e-131">Therefore, no arguments are necessary in the calling statement.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]  
  
2.  <span data-ttu-id="e842e-132">Adicione o código a seguir ao final do método para definir onde exibir o texto no documento e o texto a ser exibido.</span><span class="sxs-lookup"><span data-stu-id="e842e-132">Add the following code at the end of the method to define where to display text in the document, and what text to display.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]  
  
### <a name="to-run-the-application"></a><span data-ttu-id="e842e-133">Para executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="e842e-133">To run the application</span></span>  
  
1.  <span data-ttu-id="e842e-134">Adicione a seguinte instrução a Main.</span><span class="sxs-lookup"><span data-stu-id="e842e-134">Add the following statement to Main.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]  
  
2.  <span data-ttu-id="e842e-135">Pressione CTRL+F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="e842e-135">Press CTRL+F5 to run the project.</span></span> <span data-ttu-id="e842e-136">É exibido um documento do Word contendo o texto especificado.</span><span class="sxs-lookup"><span data-stu-id="e842e-136">A Word document appears that contains the specified text.</span></span>  
  
### <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="e842e-137">Para alterar o texto para uma tabela</span><span class="sxs-lookup"><span data-stu-id="e842e-137">To change the text to a table</span></span>  
  
1.  <span data-ttu-id="e842e-138">Use o método `ConvertToTable` para colocar o texto em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="e842e-138">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="e842e-139">O método tem 16 parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="e842e-139">The method has sixteen optional parameters.</span></span> <span data-ttu-id="e842e-140">O IntelliSense coloca os parâmetros opcionais entre colchetes, como mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="e842e-140">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="e842e-141">![Lista de parâmetros do método ConvertToTable.](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span><span class="sxs-lookup"><span data-stu-id="e842e-141">![List of parameters for ConvertToTable method.](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span></span>  
<span data-ttu-id="e842e-142">Parâmetros de ConvertToTable</span><span class="sxs-lookup"><span data-stu-id="e842e-142">ConvertToTable parameters</span></span>  
  
     <span data-ttu-id="e842e-143">Os argumentos nomeados e opcionais permitem que você especifique valores apenas para os parâmetros que deseja alterar.</span><span class="sxs-lookup"><span data-stu-id="e842e-143">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="e842e-144">Adicione o seguinte código ao final do método `DisplayInWord` para criar uma tabela simples.</span><span class="sxs-lookup"><span data-stu-id="e842e-144">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="e842e-145">O argumento especifica que as vírgulas na cadeia de caracteres de texto em `range` separam as células da tabela.</span><span class="sxs-lookup"><span data-stu-id="e842e-145">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]  
  
     <span data-ttu-id="e842e-146">Em versões anteriores do C#, a chamada para `ConvertToTable` requer um argumento de referência para cada parâmetro, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e842e-146">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]  
  
2.  <span data-ttu-id="e842e-147">Pressione CTRL+F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="e842e-147">Press CTRL+F5 to run the project.</span></span>  
  
### <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="e842e-148">Para fazer experiências com outros parâmetros</span><span class="sxs-lookup"><span data-stu-id="e842e-148">To experiment with other parameters</span></span>  
  
1.  <span data-ttu-id="e842e-149">Para alterar a tabela para que ela tenha uma coluna e três linhas, substitua a última linha em `DisplayInWord` pela instrução a seguir e digite CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="e842e-149">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]  
  
2.  <span data-ttu-id="e842e-150">Para especificar um formato predefinido para a tabela, substitua a última linha em `DisplayInWord` pela a instrução a seguir e digite CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="e842e-150">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span> <span data-ttu-id="e842e-151">O formato pode ser qualquer uma das constantes [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>).</span><span class="sxs-lookup"><span data-stu-id="e842e-151">The format can be any of the [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) constants.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]  
  
## <a name="example"></a><span data-ttu-id="e842e-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e842e-152">Example</span></span>  
 <span data-ttu-id="e842e-153">O código a seguir inclui o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="e842e-153">The following code includes the full example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e842e-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e842e-154">See also</span></span>

- [<span data-ttu-id="e842e-155">Argumentos nomeados e opcionais</span><span class="sxs-lookup"><span data-stu-id="e842e-155">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
