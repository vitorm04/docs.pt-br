---
title: "Como usar argumentos nomeados e opcionais na programação do Office (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
caps.latest.revision: 34
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c773e7a6d902b9e61e724a69c9fdf5d61606de50
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="488f4-102">Como usar argumentos nomeados e opcionais na programação do Office (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="488f4-102">How to: Use Named and Optional Arguments in Office Programming (C# Programming Guide)</span></span>
<span data-ttu-id="488f4-103">Os argumentos nomeados e opcionais, introduzidos em [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], aprimoram a conveniência, a flexibilidade e a legibilidade na programação em C#.</span><span class="sxs-lookup"><span data-stu-id="488f4-103">Named arguments and optional arguments, introduced in [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="488f4-104">Além disso, esses recursos facilitam bastante o acesso a interfaces COM, como as APIs de Automação do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="488f4-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>  
  
 <span data-ttu-id="488f4-105">No exemplo a seguir, o método [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) tem 16 parâmetros que representam as características de uma tabela, como o número de colunas e linhas, formatação, bordas, fontes e cores.</span><span class="sxs-lookup"><span data-stu-id="488f4-105">In the following example, method [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="488f4-106">Todos os 16 parâmetros são opcionais, pois na maioria das vezes você não quiser especificar valores específicos para todos eles.</span><span class="sxs-lookup"><span data-stu-id="488f4-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="488f4-107">No entanto, sem argumentos nomeados e opcionais, um valor ou um valor de espaço reservado precisa ser fornecido para cada parâmetro.</span><span class="sxs-lookup"><span data-stu-id="488f4-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="488f4-108">Com argumentos nomeados e opcionais, você especifica valores apenas para os parâmetros que são necessários para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="488f4-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>  
  
 <span data-ttu-id="488f4-109">Você deve ter o Microsoft Office Word instalado em seu computador para concluir esses procedimentos.</span><span class="sxs-lookup"><span data-stu-id="488f4-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a><span data-ttu-id="488f4-110">Para criar um novo aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="488f4-110">To create a new console application</span></span>  
  
1.  <span data-ttu-id="488f4-111">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="488f4-111">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="488f4-112">No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="488f4-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="488f4-113">No painel **Templates Categories (Categorias de Modelos)**, expanda **Visual C#** e clique em **Windows**.</span><span class="sxs-lookup"><span data-stu-id="488f4-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>  
  
4.  <span data-ttu-id="488f4-114">Observe a parte superior do painel **Modelos** para se certificar de que **.NET Framework 4** é exibido na caixa **Estrutura de Destino**.</span><span class="sxs-lookup"><span data-stu-id="488f4-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>  
  
5.  <span data-ttu-id="488f4-115">No painel **Modelos**, clique em **Aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="488f4-115">In the **Templates** pane, click **Console Application**.</span></span>  
  
6.  <span data-ttu-id="488f4-116">Digite um nome para o projeto no campo **Nome**.</span><span class="sxs-lookup"><span data-stu-id="488f4-116">Type a name for your project in the **Name** field.</span></span>  
  
7.  <span data-ttu-id="488f4-117">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="488f4-117">Click **OK**.</span></span>  
  
     <span data-ttu-id="488f4-118">O novo projeto aparece no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="488f4-118">The new project appears in **Solution Explorer**.</span></span>  
  
### <a name="to-add-a-reference"></a><span data-ttu-id="488f4-119">Para adicionar uma referência</span><span class="sxs-lookup"><span data-stu-id="488f4-119">To add a reference</span></span>  
  
1.  <span data-ttu-id="488f4-120">No **Gerenciador de Soluções**, clique com o botão direito do mouse no nome do projeto e, em seguida, clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="488f4-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="488f4-121">A caixa de diálogo **Adicionar Referência** é exibida.</span><span class="sxs-lookup"><span data-stu-id="488f4-121">The **Add Reference** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="488f4-122">Na página **.NET**, selecione **Microsoft.Office.Interop.Word** na lista **Nome do Componente**.</span><span class="sxs-lookup"><span data-stu-id="488f4-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>  
  
3.  <span data-ttu-id="488f4-123">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="488f4-123">Click **OK**.</span></span>  
  
### <a name="to-add-necessary-using-directives"></a><span data-ttu-id="488f4-124">Para adicionar as diretivas using necessárias</span><span class="sxs-lookup"><span data-stu-id="488f4-124">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="488f4-125">No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo **Program.cs** e, em seguida, clique em **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="488f4-125">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="488f4-126">Adicione as seguintes diretivas `using` na parte superior do arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="488f4-126">Add the following `using` directives to the top of the code file.</span></span>  
  
     <span data-ttu-id="488f4-127">[!code-cs[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="488f4-127">[!code-cs[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]</span></span>  
  
### <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="488f4-128">Para exibir texto em um documento do Word</span><span class="sxs-lookup"><span data-stu-id="488f4-128">To display text in a Word document</span></span>  
  
1.  <span data-ttu-id="488f4-129">Na classe `Program` em Program.cs, adicione o seguinte método para criar um aplicativo do Word e um documento do Word.</span><span class="sxs-lookup"><span data-stu-id="488f4-129">In the `Program` class in Program.cs, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="488f4-130">O método [Add](http://go.microsoft.com/fwlink/?LinkId=145381) tem quatro parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="488f4-130">The [Add](http://go.microsoft.com/fwlink/?LinkId=145381) method has four optional parameters.</span></span> <span data-ttu-id="488f4-131">Este exemplo usa os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="488f4-131">This example uses their default values.</span></span> <span data-ttu-id="488f4-132">Portanto, nenhum argumento é necessário na instrução de chamada.</span><span class="sxs-lookup"><span data-stu-id="488f4-132">Therefore, no arguments are necessary in the calling statement.</span></span>  
  
     <span data-ttu-id="488f4-133">[!code-cs[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="488f4-133">[!code-cs[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]</span></span>  
  
2.  <span data-ttu-id="488f4-134">Adicione o código a seguir ao final do método para definir onde exibir o texto no documento e o texto a ser exibido.</span><span class="sxs-lookup"><span data-stu-id="488f4-134">Add the following code at the end of the method to define where to display text in the document, and what text to display.</span></span>  
  
     <span data-ttu-id="488f4-135">[!code-cs[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="488f4-135">[!code-cs[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]</span></span>  
  
### <a name="to-run-the-application"></a><span data-ttu-id="488f4-136">Para executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="488f4-136">To run the application</span></span>  
  
1.  <span data-ttu-id="488f4-137">Adicione a seguinte instrução a Main.</span><span class="sxs-lookup"><span data-stu-id="488f4-137">Add the following statement to Main.</span></span>  
  
     <span data-ttu-id="488f4-138">[!code-cs[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="488f4-138">[!code-cs[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]</span></span>  
  
2.  <span data-ttu-id="488f4-139">Pressione CTRL+F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="488f4-139">Press CTRL+F5 to run the project.</span></span> <span data-ttu-id="488f4-140">É exibido um documento do Word contendo o texto especificado.</span><span class="sxs-lookup"><span data-stu-id="488f4-140">A Word document appears that contains the specified text.</span></span>  
  
### <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="488f4-141">Para alterar o texto para uma tabela</span><span class="sxs-lookup"><span data-stu-id="488f4-141">To change the text to a table</span></span>  
  
1.  <span data-ttu-id="488f4-142">Use o método `ConvertToTable` para colocar o texto em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="488f4-142">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="488f4-143">O método tem 16 parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="488f4-143">The method has sixteen optional parameters.</span></span> <span data-ttu-id="488f4-144">O IntelliSense coloca os parâmetros opcionais entre colchetes, como mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="488f4-144">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="488f4-145">![Lista de parâmetros do método ConvertToTable.](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span><span class="sxs-lookup"><span data-stu-id="488f4-145">![List of parameters for ConvertToTable method.](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span></span>  
<span data-ttu-id="488f4-146">Parâmetros de ConvertToTable</span><span class="sxs-lookup"><span data-stu-id="488f4-146">ConvertToTable parameters</span></span>  
  
     <span data-ttu-id="488f4-147">Os argumentos nomeados e opcionais permitem que você especifique valores apenas para os parâmetros que deseja alterar.</span><span class="sxs-lookup"><span data-stu-id="488f4-147">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="488f4-148">Adicione o seguinte código ao final do método `DisplayInWord` para criar uma tabela simples.</span><span class="sxs-lookup"><span data-stu-id="488f4-148">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="488f4-149">O argumento especifica que as vírgulas na cadeia de caracteres de texto em `range` separam as células da tabela.</span><span class="sxs-lookup"><span data-stu-id="488f4-149">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>  
  
     <span data-ttu-id="488f4-150">[!code-cs[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="488f4-150">[!code-cs[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]</span></span>  
  
     <span data-ttu-id="488f4-151">Em versões anteriores do C#, a chamada para `ConvertToTable` requer um argumento de referência para cada parâmetro, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="488f4-151">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code.</span></span>  
  
     <span data-ttu-id="488f4-152">[!code-cs[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="488f4-152">[!code-cs[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]</span></span>  
  
2.  <span data-ttu-id="488f4-153">Pressione CTRL+F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="488f4-153">Press CTRL+F5 to run the project.</span></span>  
  
### <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="488f4-154">Para fazer experiências com outros parâmetros</span><span class="sxs-lookup"><span data-stu-id="488f4-154">To experiment with other parameters</span></span>  
  
1.  <span data-ttu-id="488f4-155">Para alterar a tabela para que ela tenha uma coluna e três linhas, substitua a última linha em `DisplayInWord` pela instrução a seguir e digite CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="488f4-155">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span>  
  
     <span data-ttu-id="488f4-156">[!code-cs[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="488f4-156">[!code-cs[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]</span></span>  
  
2.  <span data-ttu-id="488f4-157">Para especificar um formato predefinido para a tabela, substitua a última linha em `DisplayInWord` pela a instrução a seguir e digite CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="488f4-157">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span> <span data-ttu-id="488f4-158">O formato pode ser qualquer uma das constantes [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382).</span><span class="sxs-lookup"><span data-stu-id="488f4-158">The format can be any of the [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) constants.</span></span>  
  
     <span data-ttu-id="488f4-159">[!code-cs[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="488f4-159">[!code-cs[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="488f4-160">Exemplo</span><span class="sxs-lookup"><span data-stu-id="488f4-160">Example</span></span>  
 <span data-ttu-id="488f4-161">O código a seguir inclui o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="488f4-161">The following code includes the full example.</span></span>  
  
 <span data-ttu-id="488f4-162">[!code-cs[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="488f4-162">[!code-cs[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="488f4-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="488f4-163">See Also</span></span>  
 [<span data-ttu-id="488f4-164">Argumentos nomeados e opcionais</span><span class="sxs-lookup"><span data-stu-id="488f4-164">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)

