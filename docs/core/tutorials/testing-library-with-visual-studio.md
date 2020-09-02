---
title: Testar um .NET Standard biblioteca de classes com o .NET Core usando o Visual Studio
description: Crie um projeto de teste de unidade para uma biblioteca de classes do .NET Core. Verifique se uma biblioteca de classes do .NET Core funciona corretamente com testes de unidade.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 049f0636b1c2c2df33461714aea5a11810ef00ad
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359188"
---
# <a name="tutorial-test-a-net-standard-class-library-with-net-core-using-visual-studio"></a><span data-ttu-id="31403-104">Tutorial: testar uma biblioteca de classes de .NET Standard com o .NET Core usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="31403-104">Tutorial: Test a .NET Standard class library with .NET Core using Visual Studio</span></span>

<span data-ttu-id="31403-105">Este tutorial mostra como automatizar o teste de unidade adicionando um projeto de teste a uma solução.</span><span class="sxs-lookup"><span data-stu-id="31403-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="31403-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="31403-106">Prerequisites</span></span>

- <span data-ttu-id="31403-107">Este tutorial funciona com a solução que você cria em [criar uma .net Standard biblioteca usando o Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="31403-107">This tutorial works with the solution that you create in [Create a .NET Standard library using Visual Studio](library-with-visual-studio.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="31403-108">Crie um projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="31403-108">Create a unit test project</span></span>

<span data-ttu-id="31403-109">As unidade de teste fornecem testes de software automatizados durante o desenvolvimento e a publicação.</span><span class="sxs-lookup"><span data-stu-id="31403-109">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="31403-110">[MSTest](https://github.com/Microsoft/testfx-docs) é uma das três estruturas de teste que você pode escolher.</span><span class="sxs-lookup"><span data-stu-id="31403-110">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="31403-111">Os outros são [xUnit](https://xunit.net/) e [NUnit](https://nunit.org/).</span><span class="sxs-lookup"><span data-stu-id="31403-111">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="31403-112">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="31403-112">Start Visual Studio.</span></span>

1. <span data-ttu-id="31403-113">Abra a `ClassLibraryProjects` solução que você criou em [criar uma .net Standard biblioteca usando o Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="31403-113">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library using Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="31403-114">Adicione um novo projeto de teste de unidade chamado "StringLibraryTest" à solução.</span><span class="sxs-lookup"><span data-stu-id="31403-114">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="31403-115">Clique com o botão direito do mouse na solução em **Gerenciador de soluções** e selecione **Adicionar**  >  **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="31403-115">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="31403-116">Na página **Adicionar um novo projeto** , digite **MSTest** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="31403-116">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="31403-117">Escolha **C#** ou **Visual Basic** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma.</span><span class="sxs-lookup"><span data-stu-id="31403-117">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="31403-118">Escolha o modelo de **projeto de teste MSTest (.NET Core)** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="31403-118">Choose the **MSTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="31403-119">Na página **configurar seu novo projeto** , digite **StringLibraryTest** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="31403-119">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="31403-120">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="31403-120">Then choose **Create**.</span></span>

1. <span data-ttu-id="31403-121">O Visual Studio cria o projeto e abre o arquivo de classe na janela de código com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="31403-121">Visual Studio creates the project and opens the class file in the code window with the following code.</span></span> <span data-ttu-id="31403-122">Se o idioma que você deseja usar não for mostrado, altere o seletor de idioma na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="31403-122">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

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

   ```vb
   Imports Microsoft.VisualStudio.TestTools.UnitTesting

   Namespace StringLibraryTest
       <TestClass>
       Public Class UnitTest1
           <TestMethod>
           Sub TestSub()

           End Sub
       End Class
   End Namespace
   ```

   <span data-ttu-id="31403-123">O código-fonte criado pelo modelo de teste de unidade faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="31403-123">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="31403-124">Ele importa o namespace <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, que contém os tipos usados para o teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="31403-124">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="31403-125">Ele aplica o atributo<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> à classe `UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="31403-125">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="31403-126">Ele aplica o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributo para definir `TestMethod1` em C# ou `TestSub` em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="31403-126">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic.</span></span>

   <span data-ttu-id="31403-127">Cada método marcado com [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) em uma classe de teste marcada com [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) é executado automaticamente quando o teste de unidade é executado.</span><span class="sxs-lookup"><span data-stu-id="31403-127">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="31403-128">Adicionar uma referência ao projeto</span><span class="sxs-lookup"><span data-stu-id="31403-128">Add a project reference</span></span>

<span data-ttu-id="31403-129">Para que o projeto de teste funcione com a `StringLibrary` classe, adicione uma referência no projeto **StringLibraryTest** ao `StringLibrary` projeto.</span><span class="sxs-lookup"><span data-stu-id="31403-129">For the test project to work with the `StringLibrary` class, add a reference in the **StringLibraryTest** project to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="31403-130">Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó **dependências** do projeto **StringLibraryTest** e selecione **Adicionar referência de projeto** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="31403-130">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Project Reference** from the context menu.</span></span>

1. <span data-ttu-id="31403-131">No diálogo **Gerenciador de referências** , expanda o nó **projetos** e selecione a caixa ao lado de **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="31403-131">In the **Reference Manager** dialog, expand the **Projects** node, and select the box next to **StringLibrary**.</span></span> <span data-ttu-id="31403-132">Adicionar uma referência ao `StringLibrary` assembly permite que o compilador encontre métodos **StringLibrary** ao compilar o projeto **StringLibraryTest** .</span><span class="sxs-lookup"><span data-stu-id="31403-132">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods while compiling the **StringLibraryTest** project.</span></span>

1. <span data-ttu-id="31403-133">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="31403-133">Select **OK**.</span></span>

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="31403-134">Adicionar e executar métodos de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="31403-134">Add and run unit test methods</span></span>

<span data-ttu-id="31403-135">Quando o Visual Studio executa um teste de unidade, ele executa cada método marcado com o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributo em uma classe marcada com o  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="31403-135">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="31403-136">Um método de teste termina quando a primeira falha é encontrada ou quando todos os testes contidos no método foram bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="31403-136">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="31403-137">Os testes mais comuns chamam membros da classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>.</span><span class="sxs-lookup"><span data-stu-id="31403-137">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="31403-138">Muitos métodos assert incluem pelo menos dois parâmetros, um deles é o resultado esperado do teste, e o outro é o resultado real do teste.</span><span class="sxs-lookup"><span data-stu-id="31403-138">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="31403-139">Alguns dos `Assert` métodos chamados mais frequentemente da classe são mostrados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="31403-139">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="31403-140">Métodos assert</span><span class="sxs-lookup"><span data-stu-id="31403-140">Assert methods</span></span>     | <span data-ttu-id="31403-141">Função</span><span class="sxs-lookup"><span data-stu-id="31403-141">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="31403-142">Verifica se os dois valores ou objetos são iguais.</span><span class="sxs-lookup"><span data-stu-id="31403-142">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="31403-143">A declaração falhará se os valores ou objetos não forem iguais.</span><span class="sxs-lookup"><span data-stu-id="31403-143">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="31403-144">Verifica se duas variáveis de objeto se referem ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="31403-144">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="31403-145">A assert falhará se as variáveis se referirem a objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="31403-145">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="31403-146">Verifica se uma condição é `false`.</span><span class="sxs-lookup"><span data-stu-id="31403-146">Verifies that a condition is `false`.</span></span> <span data-ttu-id="31403-147">O assert falhará se a condição for `true`.</span><span class="sxs-lookup"><span data-stu-id="31403-147">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="31403-148">Verifica se um objeto não está `null` .</span><span class="sxs-lookup"><span data-stu-id="31403-148">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="31403-149">A assert falhará se o objeto for `null`.</span><span class="sxs-lookup"><span data-stu-id="31403-149">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="31403-150">Você também pode usar o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> método em um método de teste para indicar o tipo de exceção que ele deve lançar.</span><span class="sxs-lookup"><span data-stu-id="31403-150">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="31403-151">O teste falhará se a exceção especificada não for lançada.</span><span class="sxs-lookup"><span data-stu-id="31403-151">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="31403-152">Ao testar o método `StringLibrary.StartsWithUpper`, você quer fornecer um número de cadeias de caracteres que comecem com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="31403-152">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="31403-153">Você espera que o método retorne `true` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="31403-153">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="31403-154">Da mesma forma, você deseja fornecer um número de cadeias de caracteres que comecem com algo diferente de um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="31403-154">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="31403-155">Você espera que o método retorne `false` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="31403-155">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="31403-156">Como o método de biblioteca lida com cadeias de caracteres, você também deseja certificar-se de que ele manipula com êxito uma [cadeia de caracteres vazia ( `String.Empty` )](xref:System.String.Empty), uma cadeia de caracteres válida que não tem caracteres e cujo número <xref:System.String.Length> é 0 e uma `null` cadeia de caracteres que não foi inicializada.</span><span class="sxs-lookup"><span data-stu-id="31403-156">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="31403-157">Você pode chamar `StartsWithUpper` diretamente como um método estático e passar um único <xref:System.String> argumento.</span><span class="sxs-lookup"><span data-stu-id="31403-157">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="31403-158">Ou você pode chamar `StartsWithUpper` como um método de extensão em uma `string` variável atribuída a `null` .</span><span class="sxs-lookup"><span data-stu-id="31403-158">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="31403-159">Você definirá três métodos, cada um deles chamará um <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> método para cada elemento em uma matriz de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="31403-159">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="31403-160">Você chamará uma sobrecarga de método que permite especificar uma mensagem de erro a ser exibida em caso de falha de teste.</span><span class="sxs-lookup"><span data-stu-id="31403-160">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="31403-161">A mensagem identifica a cadeia de caracteres que causou a falha.</span><span class="sxs-lookup"><span data-stu-id="31403-161">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="31403-162">Para criar os métodos de teste:</span><span class="sxs-lookup"><span data-stu-id="31403-162">To create the test methods:</span></span>

1. <span data-ttu-id="31403-163">Na janela de código *UnitTest1.cs* ou *UnitTest1. vb* , substitua o código pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="31403-163">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibraryTest/UnitTest1.vb":::

   <span data-ttu-id="31403-164">O teste de caracteres maiúsculos no `TestStartsWithUpper` método inclui a letra maiúscula grega alfa (u + 0391) e a letra maiúscula cirílica em (u + 041C).</span><span class="sxs-lookup"><span data-stu-id="31403-164">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="31403-165">O teste de caracteres minúsculos no `TestDoesNotStartWithUpper` método inclui a letra grega pequena alfa (u + 03B1) e a letra cirílica minúscula Ghe (u + 0433).</span><span class="sxs-lookup"><span data-stu-id="31403-165">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="31403-166">Na barra de menus, selecione **arquivo**  >  **salvar UnitTest1.cs como** ou **arquivo**  >  **salvar UnitTest1. vb como**.</span><span class="sxs-lookup"><span data-stu-id="31403-166">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="31403-167">Na caixa de diálogo **Salvar Arquivo Como**, selecione a seta ao lado do botão **Salvar** e selecione **Salvar com Codificação**.</span><span class="sxs-lookup"><span data-stu-id="31403-167">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="31403-168">![Caixa de diálogo Salvar arquivo como do Visual Studio](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="31403-168">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="31403-169">Na caixa de diálogo **Confirmar Salvar Como**, selecione o botão **Sim** para salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="31403-169">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="31403-170">Na caixa de diálogo **Opções Avançadas de Salvamento**, selecione **Unicode (UTF-8 com assinatura) – página de código 65001** na lista suspensa **Codificação** e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="31403-170">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="31403-171">![Caixa de diálogo Opções Avançadas de Salvamento do Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="31403-171">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="31403-172">Se você não salvar seu código-fonte como um arquivo codificado em UTF8, o Visual Studio poderá salvá-lo como um arquivo ASCII.</span><span class="sxs-lookup"><span data-stu-id="31403-172">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="31403-173">Quando isso acontece, o tempo de execução não decodifica com precisão os caracteres UTF8 fora do intervalo ASCII, e os resultados de teste não estarão corretos.</span><span class="sxs-lookup"><span data-stu-id="31403-173">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="31403-174">Na barra de menus, selecione **testar**  >  **executar todos os testes**.</span><span class="sxs-lookup"><span data-stu-id="31403-174">On the menu bar, select **Test** > **Run All Tests**.</span></span> <span data-ttu-id="31403-175">Se a janela **Gerenciador de testes** não abrir, abra-a escolhendo **Test**  >  **Test Explorer**.</span><span class="sxs-lookup"><span data-stu-id="31403-175">If the **Test Explorer** window doesn't open, open it by choosing **Test** > **Test Explorer**.</span></span> <span data-ttu-id="31403-176">Os três testes estão listados na seção **Testes Aprovados**, e a seção **Resumo** relata o resultado da execução de teste.</span><span class="sxs-lookup"><span data-stu-id="31403-176">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="31403-177">![Janela Gerenciador de Testes com testes aprovados](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="31403-177">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="31403-178">Lidar com falhas de teste</span><span class="sxs-lookup"><span data-stu-id="31403-178">Handle test failures</span></span>

<span data-ttu-id="31403-179">Se você estiver fazendo o TDD (desenvolvimento controlado por teste), você escreverá testes primeiro e eles falharão na primeira vez em que forem executados.</span><span class="sxs-lookup"><span data-stu-id="31403-179">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="31403-180">Em seguida, você adiciona código ao aplicativo que torna o teste com sucesso.</span><span class="sxs-lookup"><span data-stu-id="31403-180">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="31403-181">Para este tutorial, você criou o teste depois de gravar o código do aplicativo que ele valida, para que você não tenha visto o teste falhar.</span><span class="sxs-lookup"><span data-stu-id="31403-181">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="31403-182">Para validar que um teste falha quando você espera que ele falhe, adicione um valor inválido para a entrada de teste.</span><span class="sxs-lookup"><span data-stu-id="31403-182">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="31403-183">Modifique a matriz `words` no método `TestDoesNotStartWithUpper` para incluir a cadeia de caracteres “Error”.</span><span class="sxs-lookup"><span data-stu-id="31403-183">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="31403-184">Não é necessário salvar o arquivo porque o Visual Studio salva automaticamente os arquivos abertos quando uma solução é criada para executar testes.</span><span class="sxs-lookup"><span data-stu-id="31403-184">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="31403-185">Execute o teste selecionando **testar**  >  **executar todos os testes** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="31403-185">Run the test by selecting **Test** > **Run All Tests** from the menu bar.</span></span> <span data-ttu-id="31403-186">A Janela **Gerenciador de Testes** indica que dois testes tiveram êxito e um falhou.</span><span class="sxs-lookup"><span data-stu-id="31403-186">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="31403-187">![Janela Gerenciador de Testes com testes com falha](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="31403-187">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="31403-188">Selecione o teste com falha, `TestDoesNotStartWith` .</span><span class="sxs-lookup"><span data-stu-id="31403-188">Select the failed test, `TestDoesNotStartWith`.</span></span>

   <span data-ttu-id="31403-189">A janela **Gerenciador de Testes** mostra a mensagem produzida pelo assert: "Assert.IsFalse falhou.</span><span class="sxs-lookup"><span data-stu-id="31403-189">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="31403-190">Esperado para 'Error': false, real: True".</span><span class="sxs-lookup"><span data-stu-id="31403-190">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="31403-191">Devido à falha, nenhuma cadeia de caracteres na matriz após o "erro" foi testada.</span><span class="sxs-lookup"><span data-stu-id="31403-191">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="31403-192">![Janela do Gerenciador de testes mostrando a falha de asserção IsFalse](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="31403-192">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="31403-193">Remova a cadeia de caracteres "Error" que você adicionou na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="31403-193">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="31403-194">Execute novamente o teste e os testes são aprovados.</span><span class="sxs-lookup"><span data-stu-id="31403-194">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="31403-195">Testar a versão de lançamento da biblioteca</span><span class="sxs-lookup"><span data-stu-id="31403-195">Test the Release version of the library</span></span>

<span data-ttu-id="31403-196">Agora que todos os testes passaram durante a execução da compilação de depuração da biblioteca, execute o testa um tempo adicional em relação à compilação da versão da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="31403-196">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="31403-197">Vários fatores, incluindo as otimizações do compilador, podem produzir um comportamento diferente entre as compilações de Depuração e Lançamento.</span><span class="sxs-lookup"><span data-stu-id="31403-197">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="31403-198">Para testar a compilação de Lançamento:</span><span class="sxs-lookup"><span data-stu-id="31403-198">To test the Release build:</span></span>

1. <span data-ttu-id="31403-199">Na barra de ferramentas do Visual Studio, altere a configuração de compilação de **Depurar** para **Lançamento**.</span><span class="sxs-lookup"><span data-stu-id="31403-199">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="31403-200">![Barra de ferramentas do Visual Studio com build de versão realçado](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="31403-200">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="31403-201">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **StringLibrary** e selecione **Compilar** no menu de contexto para recompilar a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="31403-201">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="31403-202">![Menu de contexto de StringLibrary com comando de build](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="31403-202">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="31403-203">Execute os testes de unidade escolhendo **testar executar**  >  **todos os testes** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="31403-203">Run the unit tests by choosing **Test Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="31403-204">Os testes são aprovados.</span><span class="sxs-lookup"><span data-stu-id="31403-204">The tests pass.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="31403-205">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="31403-205">Additional resources</span></span>

* [<span data-ttu-id="31403-206">Noções básicas do teste de unidade – Visual Studio</span><span class="sxs-lookup"><span data-stu-id="31403-206">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)
* [<span data-ttu-id="31403-207">Teste de unidade no .NET Core e no .NET Standard</span><span class="sxs-lookup"><span data-stu-id="31403-207">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="31403-208">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="31403-208">Next steps</span></span>

<span data-ttu-id="31403-209">Neste tutorial, você testou uma unidade de biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="31403-209">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="31403-210">Você pode tornar a biblioteca disponível para outras pessoas publicando-a no [NuGet](https://nuget.org) como um pacote.</span><span class="sxs-lookup"><span data-stu-id="31403-210">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="31403-211">Para saber como, siga um tutorial do NuGet:</span><span class="sxs-lookup"><span data-stu-id="31403-211">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="31403-212">Criar e publicar um pacote NuGet usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="31403-212">Create and publish a NuGet package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

<span data-ttu-id="31403-213">Se você publicar uma biblioteca como um pacote NuGet, outras pessoas poderão instalá-la e usá-la.</span><span class="sxs-lookup"><span data-stu-id="31403-213">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="31403-214">Para saber como, siga um tutorial do NuGet:</span><span class="sxs-lookup"><span data-stu-id="31403-214">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="31403-215">Instalar e usar um pacote no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="31403-215">Install and use a package in Visual Studio</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

<span data-ttu-id="31403-216">Uma biblioteca não precisa ser distribuída como um pacote.</span><span class="sxs-lookup"><span data-stu-id="31403-216">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="31403-217">Ele pode ser agrupado com um aplicativo de console que o utiliza.</span><span class="sxs-lookup"><span data-stu-id="31403-217">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="31403-218">Para saber como publicar um aplicativo de console, consulte o tutorial anterior nesta série:</span><span class="sxs-lookup"><span data-stu-id="31403-218">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="31403-219">Publicar um aplicativo de console do .NET Core usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="31403-219">Publish a .NET Core console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
