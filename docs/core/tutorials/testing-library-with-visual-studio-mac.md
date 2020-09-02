---
title: Testar um .NET Standard biblioteca de classes com o .NET Core usando Visual Studio para Mac
description: Crie um projeto de teste de unidade para uma biblioteca de classes do .NET Core. Verifique se uma biblioteca de classes do .NET Core funciona corretamente com testes de unidade.
ms.date: 06/08/2020
ms.openlocfilehash: d3c8a5e01d16047949e977f3af6a429970d996d0
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359214"
---
# <a name="test-a-net-standard-class-library-with-net-core-using-visual-studio"></a><span data-ttu-id="e616e-104">Testar um .NET Standard biblioteca de classes com o .NET Core usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e616e-104">Test a .NET Standard class library with .NET Core using Visual Studio</span></span>

<span data-ttu-id="e616e-105">Este tutorial mostra como automatizar o teste de unidade adicionando um projeto de teste a uma solução.</span><span class="sxs-lookup"><span data-stu-id="e616e-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e616e-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e616e-106">Prerequisites</span></span>

- <span data-ttu-id="e616e-107">Este tutorial funciona com a solução que você cria em [criar uma .net Standard biblioteca usando Visual Studio para Mac](library-with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="e616e-107">This tutorial works with the solution that you create in [Create a .NET Standard library using Visual Studio for Mac](library-with-visual-studio-mac.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="e616e-108">Crie um projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="e616e-108">Create a unit test project</span></span>

<span data-ttu-id="e616e-109">As unidade de teste fornecem testes de software automatizados durante o desenvolvimento e a publicação.</span><span class="sxs-lookup"><span data-stu-id="e616e-109">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="e616e-110">[MSTest](https://github.com/Microsoft/testfx-docs) é uma das três estruturas de teste que você pode escolher.</span><span class="sxs-lookup"><span data-stu-id="e616e-110">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="e616e-111">Os outros são [xUnit](https://xunit.net/) e [NUnit](https://nunit.org/).</span><span class="sxs-lookup"><span data-stu-id="e616e-111">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="e616e-112">Iniciar Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="e616e-112">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="e616e-113">Abra a `ClassLibraryProjects` solução que você criou em [criar uma .net Standard biblioteca usando Visual Studio para Mac](library-with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="e616e-113">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library using Visual Studio for Mac](library-with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="e616e-114">No painel de **solução** , <kbd>pressione CTRL +</kbd>clique na `ClassLibraryProjects` solução e selecione **Adicionar**  >  **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="e616e-114">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="e616e-115">Na caixa de diálogo **novo projeto** , selecione **testes** no nó **da Web e do console** .</span><span class="sxs-lookup"><span data-stu-id="e616e-115">In the **New Project** dialog, select **Tests** from the **Web and Console** node.</span></span> <span data-ttu-id="e616e-116">Selecione o **projeto MSTest** seguido por **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e616e-116">Select the **MSTest Project** followed by **Next**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-project.png" alt-text="Caixa de diálogo novo projeto do Visual Studio Mac criando projeto de teste":::

1. <span data-ttu-id="e616e-118">Selecione **.NET Core 3,1**.</span><span class="sxs-lookup"><span data-stu-id="e616e-118">Select **.NET Core 3.1**.</span></span> <span data-ttu-id="e616e-119">Nomeie o novo projeto como "StringLibraryTest" e selecione **criar**.</span><span class="sxs-lookup"><span data-stu-id="e616e-119">Name the new project "StringLibraryTest" and select **Create**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-new-project-name.png" alt-text="Caixa de diálogo Novo Projeto do Visual Studio para Mac fornecendo um nome de projeto":::

   <span data-ttu-id="e616e-121">O Visual Studio cria um arquivo de classe com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="e616e-121">Visual Studio creates a class file with the following code:</span></span>

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   <span data-ttu-id="e616e-122">O código-fonte criado pelo modelo de teste de unidade faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e616e-122">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="e616e-123">Ele importa o namespace <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, que contém os tipos usados para o teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="e616e-123">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="e616e-124">Ele aplica o atributo<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> à classe `UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="e616e-124">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="e616e-125">Ele aplica o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributo a `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="e616e-125">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to `TestMethod1`.</span></span>

   <span data-ttu-id="e616e-126">Cada método marcado com [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) em uma classe de teste marcada com [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) é executado automaticamente quando o teste de unidade é executado.</span><span class="sxs-lookup"><span data-stu-id="e616e-126">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="e616e-127">Adicionar uma referência ao projeto</span><span class="sxs-lookup"><span data-stu-id="e616e-127">Add a project reference</span></span>

<span data-ttu-id="e616e-128">Para que o projeto de teste funcione com a `StringLibrary` classe, adicione uma referência ao `StringLibrary` projeto.</span><span class="sxs-lookup"><span data-stu-id="e616e-128">For the test project to work with the `StringLibrary` class, add a reference to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="e616e-129">No painel de **solução** , <kbd>pressione CTRL</kbd>e clique em **dependências** em **StringLibraryTest**.</span><span class="sxs-lookup"><span data-stu-id="e616e-129">In the **Solution** pad, <kbd>ctrl</kbd>-click **Dependencies** under **StringLibraryTest**.</span></span> <span data-ttu-id="e616e-130">Selecione **Adicionar referência** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="e616e-130">Select **Add Reference** from the context menu.</span></span>

1. <span data-ttu-id="e616e-131">Na caixa de diálogo **referências** , selecione o projeto **StringLibrary** .</span><span class="sxs-lookup"><span data-stu-id="e616e-131">In the **References** dialog, select the **StringLibrary** project.</span></span> <span data-ttu-id="e616e-132">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="e616e-132">Select **OK**.</span></span>

      :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-edit-references.png" alt-text="Caixa de diálogo Editar Referências do Visual Studio para Mac":::

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="e616e-134">Adicionar e executar métodos de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="e616e-134">Add and run unit test methods</span></span>

<span data-ttu-id="e616e-135">Quando o Visual Studio executa um teste de unidade, ele executa cada método marcado com o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributo em uma classe marcada com o  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="e616e-135">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="e616e-136">Um método de teste termina quando a primeira falha é encontrada ou quando todos os testes contidos no método foram bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="e616e-136">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="e616e-137">Os testes mais comuns chamam membros da classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>.</span><span class="sxs-lookup"><span data-stu-id="e616e-137">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="e616e-138">Muitos métodos assert incluem pelo menos dois parâmetros, um deles é o resultado esperado do teste, e o outro é o resultado real do teste.</span><span class="sxs-lookup"><span data-stu-id="e616e-138">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="e616e-139">Alguns dos `Assert` métodos chamados mais frequentemente da classe são mostrados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="e616e-139">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="e616e-140">Métodos assert</span><span class="sxs-lookup"><span data-stu-id="e616e-140">Assert methods</span></span>     | <span data-ttu-id="e616e-141">Função</span><span class="sxs-lookup"><span data-stu-id="e616e-141">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="e616e-142">Verifica se os dois valores ou objetos são iguais.</span><span class="sxs-lookup"><span data-stu-id="e616e-142">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="e616e-143">A declaração falhará se os valores ou objetos não forem iguais.</span><span class="sxs-lookup"><span data-stu-id="e616e-143">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="e616e-144">Verifica se duas variáveis de objeto se referem ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="e616e-144">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="e616e-145">A assert falhará se as variáveis se referirem a objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="e616e-145">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="e616e-146">Verifica se uma condição é `false`.</span><span class="sxs-lookup"><span data-stu-id="e616e-146">Verifies that a condition is `false`.</span></span> <span data-ttu-id="e616e-147">O assert falhará se a condição for `true`.</span><span class="sxs-lookup"><span data-stu-id="e616e-147">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="e616e-148">Verifica se um objeto não está `null` .</span><span class="sxs-lookup"><span data-stu-id="e616e-148">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="e616e-149">A assert falhará se o objeto for `null`.</span><span class="sxs-lookup"><span data-stu-id="e616e-149">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="e616e-150">Você também pode usar o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> método em um método de teste para indicar o tipo de exceção que ele deve lançar.</span><span class="sxs-lookup"><span data-stu-id="e616e-150">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="e616e-151">O teste falhará se a exceção especificada não for lançada.</span><span class="sxs-lookup"><span data-stu-id="e616e-151">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="e616e-152">Ao testar o método `StringLibrary.StartsWithUpper`, você quer fornecer um número de cadeias de caracteres que comecem com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="e616e-152">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="e616e-153">Você espera que o método retorne `true` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e616e-153">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e616e-154">Da mesma forma, você deseja fornecer um número de cadeias de caracteres que comecem com algo diferente de um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="e616e-154">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="e616e-155">Você espera que o método retorne `false` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e616e-155">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="e616e-156">Como o método de biblioteca lida com cadeias de caracteres, você também deseja certificar-se de que ele manipula com êxito uma [cadeia de caracteres vazia ( `String.Empty` )](xref:System.String.Empty), uma cadeia de caracteres válida que não tem caracteres e cujo número <xref:System.String.Length> é 0 e uma `null` cadeia de caracteres que não foi inicializada.</span><span class="sxs-lookup"><span data-stu-id="e616e-156">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="e616e-157">Você pode chamar `StartsWithUpper` diretamente como um método estático e passar um único <xref:System.String> argumento.</span><span class="sxs-lookup"><span data-stu-id="e616e-157">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="e616e-158">Ou você pode chamar `StartsWithUpper` como um método de extensão em uma `string` variável atribuída a `null` .</span><span class="sxs-lookup"><span data-stu-id="e616e-158">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="e616e-159">Você definirá três métodos, cada um deles chamará um <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> método para cada elemento em uma matriz de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e616e-159">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="e616e-160">Você chamará uma sobrecarga de método que permite especificar uma mensagem de erro a ser exibida em caso de falha de teste.</span><span class="sxs-lookup"><span data-stu-id="e616e-160">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="e616e-161">A mensagem identifica a cadeia de caracteres que causou a falha.</span><span class="sxs-lookup"><span data-stu-id="e616e-161">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="e616e-162">Para criar os métodos de teste:</span><span class="sxs-lookup"><span data-stu-id="e616e-162">To create the test methods:</span></span>

1. <span data-ttu-id="e616e-163">Abra o arquivo *UnitTest1.cs* e substitua o código pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="e616e-163">Open the *UnitTest1.cs* file and replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="e616e-164">O teste de caracteres maiúsculos no `TestStartsWithUpper` método inclui a letra maiúscula grega alfa (u + 0391) e a letra maiúscula cirílica em (u + 041C).</span><span class="sxs-lookup"><span data-stu-id="e616e-164">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="e616e-165">O teste de caracteres minúsculos no `TestDoesNotStartWithUpper` método inclui a letra grega pequena alfa (u + 03B1) e a letra cirílica minúscula Ghe (u + 0433).</span><span class="sxs-lookup"><span data-stu-id="e616e-165">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="e616e-166">Na barra de menus, selecione **arquivo**  >  **salvar como**.</span><span class="sxs-lookup"><span data-stu-id="e616e-166">On the menu bar, select **File** > **Save As**.</span></span> <span data-ttu-id="e616e-167">Na caixa de diálogo, verifique se a **codificação** está definida como **Unicode (UTF-8)**.</span><span class="sxs-lookup"><span data-stu-id="e616e-167">In the dialog, make sure that **Encoding** is set to **Unicode (UTF-8)**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/save-file-as-dialog.png" alt-text="Caixa de diálogo Salvar arquivo como do Visual Studio":::

1. <span data-ttu-id="e616e-169">Quando for perguntado se deseja substituir o arquivo existente, selecione **substituir**.</span><span class="sxs-lookup"><span data-stu-id="e616e-169">When you're asked if you want to replace the existing file, select **Replace**.</span></span>

   <span data-ttu-id="e616e-170">Se você não salvar seu código-fonte como um arquivo codificado em UTF8, o Visual Studio poderá salvá-lo como um arquivo ASCII.</span><span class="sxs-lookup"><span data-stu-id="e616e-170">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="e616e-171">Quando isso acontece, o tempo de execução não decodifica com precisão os caracteres UTF8 fora do intervalo ASCII, e os resultados de teste não estarão corretos.</span><span class="sxs-lookup"><span data-stu-id="e616e-171">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="e616e-172">Abra o painel **Testes de Unidade** no lado direito da tela.</span><span class="sxs-lookup"><span data-stu-id="e616e-172">Open the **Unit Tests** panel on the right side of the screen.</span></span> <span data-ttu-id="e616e-173">Selecione **Exibir**  >  **testes** no menu.</span><span class="sxs-lookup"><span data-stu-id="e616e-173">Select **View** > **Tests** from the menu.</span></span>

1. <span data-ttu-id="e616e-174">Clique no ícone **Dock** para manter o painel aberto.</span><span class="sxs-lookup"><span data-stu-id="e616e-174">Click the **Dock** icon to keep the panel open.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-dock-icon.png" alt-text="Ícone de encaixe do painel Testes de Unidade do Visual Studio para Mac":::

1. <span data-ttu-id="e616e-176">Clique no botão **Executar Tudo**.</span><span class="sxs-lookup"><span data-stu-id="e616e-176">Click the **Run All** button.</span></span>

   <span data-ttu-id="e616e-177">Todos os testes serão aprovados.</span><span class="sxs-lookup"><span data-stu-id="e616e-177">All tests pass.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-pass.png" alt-text="Visual Studio para Mac aprovações de teste esperadas":::

## <a name="handle-test-failures"></a><span data-ttu-id="e616e-179">Lidar com falhas de teste</span><span class="sxs-lookup"><span data-stu-id="e616e-179">Handle test failures</span></span>

<span data-ttu-id="e616e-180">Se você estiver fazendo o TDD (desenvolvimento controlado por teste), você escreverá testes primeiro e eles falharão na primeira vez em que forem executados.</span><span class="sxs-lookup"><span data-stu-id="e616e-180">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="e616e-181">Em seguida, você adiciona código ao aplicativo que torna o teste com sucesso.</span><span class="sxs-lookup"><span data-stu-id="e616e-181">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="e616e-182">Para este tutorial, você criou o teste depois de gravar o código do aplicativo que ele valida, para que você não tenha visto o teste falhar.</span><span class="sxs-lookup"><span data-stu-id="e616e-182">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="e616e-183">Para validar que um teste falha quando você espera que ele falhe, adicione um valor inválido para a entrada de teste.</span><span class="sxs-lookup"><span data-stu-id="e616e-183">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="e616e-184">Modifique a matriz `words` no método `TestDoesNotStartWithUpper` para incluir a cadeia de caracteres “Error”.</span><span class="sxs-lookup"><span data-stu-id="e616e-184">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="e616e-185">Não é necessário salvar o arquivo porque o Visual Studio salva automaticamente os arquivos abertos quando uma solução é criada para executar testes.</span><span class="sxs-lookup"><span data-stu-id="e616e-185">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="e616e-186">Execute os testes novamente.</span><span class="sxs-lookup"><span data-stu-id="e616e-186">Run the tests again.</span></span>

   <span data-ttu-id="e616e-187">Desta vez, a janela **Test Explorer** indica que dois testes foram bem-sucedidos e um deles falhou.</span><span class="sxs-lookup"><span data-stu-id="e616e-187">This time, the **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/failed-test-window.png" alt-text="Janela Gerenciador de Testes com testes com falha":::

1. <span data-ttu-id="e616e-189"><kbd>Ctrl</kbd>-clique no teste com falha, `TestDoesNotStartWithUpper` e selecione **Mostrar painel de resultados** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="e616e-189"><kbd>ctrl</kbd>-click the failed test, `TestDoesNotStartWithUpper`, and select **Show Results Pad** from the context menu.</span></span>

   <span data-ttu-id="e616e-190">O painel de **resultados** exibe a mensagem produzida pelo Assert: "Assert. IsFalse falhou.</span><span class="sxs-lookup"><span data-stu-id="e616e-190">The **Results** pad displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="e616e-191">Esperado para 'Error': false, real: True".</span><span class="sxs-lookup"><span data-stu-id="e616e-191">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="e616e-192">Devido à falha, nenhuma cadeia de caracteres na matriz após o "erro" foi testada.</span><span class="sxs-lookup"><span data-stu-id="e616e-192">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-failure.png" alt-text="Janela do Gerenciador de testes mostrando a falha de asserção IsFalse":::

1. <span data-ttu-id="e616e-194">Remova a cadeia de caracteres "Error" que você adicionou na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="e616e-194">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="e616e-195">Execute novamente o teste e os testes são aprovados.</span><span class="sxs-lookup"><span data-stu-id="e616e-195">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="e616e-196">Testar a versão de lançamento da biblioteca</span><span class="sxs-lookup"><span data-stu-id="e616e-196">Test the Release version of the library</span></span>

<span data-ttu-id="e616e-197">Agora que todos os testes passaram durante a execução da compilação de depuração da biblioteca, execute o testa um tempo adicional em relação à compilação da versão da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="e616e-197">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="e616e-198">Vários fatores, incluindo as otimizações do compilador, podem produzir um comportamento diferente entre as compilações de Depuração e Lançamento.</span><span class="sxs-lookup"><span data-stu-id="e616e-198">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="e616e-199">Para testar a compilação de Lançamento:</span><span class="sxs-lookup"><span data-stu-id="e616e-199">To test the Release build:</span></span>

1. <span data-ttu-id="e616e-200">Na barra de ferramentas do Visual Studio, altere a configuração de compilação de **Depurar** para **Lançamento**.</span><span class="sxs-lookup"><span data-stu-id="e616e-200">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="Barra de ferramentas do Visual Studio com build de versão realçado":::

1. <span data-ttu-id="e616e-202">No painel de **solução** , <kbd>pressione CTRL +</kbd>clique no projeto **StringLibrary** e selecione **Compilar** no menu de contexto para recompilar a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="e616e-202">In the **Solution** pad, <kbd>ctrl</kbd>-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/build-library-context-menu.png" alt-text="Menu de contexto de StringLibrary com comando de build":::

1. <span data-ttu-id="e616e-204">Execute os testes de unidade novamente.</span><span class="sxs-lookup"><span data-stu-id="e616e-204">Run the unit tests again.</span></span>

   <span data-ttu-id="e616e-205">Os testes são aprovados.</span><span class="sxs-lookup"><span data-stu-id="e616e-205">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="e616e-206">Depurar testes</span><span class="sxs-lookup"><span data-stu-id="e616e-206">Debug tests</span></span>

<span data-ttu-id="e616e-207">Você pode usar o mesmo processo mostrado no [tutorial: Depurar um aplicativo de console do .NET Core usando Visual Studio para Mac](debugging-with-visual-studio-mac.md) para depurar código usando seu projeto de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="e616e-207">You can use the same process shown in [Tutorial: Debug a .NET Core console application using Visual Studio for Mac](debugging-with-visual-studio-mac.md) to debug code using your unit test project.</span></span> <span data-ttu-id="e616e-208">Em vez de iniciar o projeto de aplicativo de demonstração, <kbd>pressione CTRL</kbd>e clique no projeto **StringLibraryTests** e selecione **Iniciar Depuração de projeto** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="e616e-208">Instead of starting the ShowCase app project, <kbd>ctrl</kbd>-click the **StringLibraryTests** project, and select **Start Debugging Project** from the context menu.</span></span> <span data-ttu-id="e616e-209">O Visual Studio inicia o projeto de teste com o depurador anexado.</span><span class="sxs-lookup"><span data-stu-id="e616e-209">Visual Studio starts the test project with the debugger attached.</span></span> <span data-ttu-id="e616e-210">A execução será interrompida em qualquer ponto de interrupção que você adicionou ao projeto de teste ou ao código de biblioteca subjacente.</span><span class="sxs-lookup"><span data-stu-id="e616e-210">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e616e-211">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="e616e-211">Additional resources</span></span>

* [<span data-ttu-id="e616e-212">Teste de unidade no .NET Core e no .NET Standard</span><span class="sxs-lookup"><span data-stu-id="e616e-212">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="e616e-213">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e616e-213">Next steps</span></span>

<span data-ttu-id="e616e-214">Neste tutorial, você testou uma unidade de biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="e616e-214">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="e616e-215">Você pode tornar a biblioteca disponível para outras pessoas publicando-a no [NuGet](https://nuget.org) como um pacote.</span><span class="sxs-lookup"><span data-stu-id="e616e-215">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="e616e-216">Para saber como, siga um tutorial do NuGet:</span><span class="sxs-lookup"><span data-stu-id="e616e-216">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e616e-217">Criar e publicar um pacote (CLI do dotnet)</span><span class="sxs-lookup"><span data-stu-id="e616e-217">Create and publish a package (dotnet CLI)</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="e616e-218">Se você publicar uma biblioteca como um pacote NuGet, outras pessoas poderão instalá-la e usá-la.</span><span class="sxs-lookup"><span data-stu-id="e616e-218">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="e616e-219">Para saber como, siga um tutorial do NuGet:</span><span class="sxs-lookup"><span data-stu-id="e616e-219">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e616e-220">Instalar e usar um pacote no Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="e616e-220">Install and use a package in Visual Studio for Mac</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

<span data-ttu-id="e616e-221">Uma biblioteca não precisa ser distribuída como um pacote.</span><span class="sxs-lookup"><span data-stu-id="e616e-221">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="e616e-222">Ele pode ser agrupado com um aplicativo de console que o utiliza.</span><span class="sxs-lookup"><span data-stu-id="e616e-222">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="e616e-223">Para saber como publicar um aplicativo de console, consulte o tutorial anterior nesta série:</span><span class="sxs-lookup"><span data-stu-id="e616e-223">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e616e-224">Publicar um aplicativo de console do .NET Core usando Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="e616e-224">Publish a .NET Core console application using Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)
