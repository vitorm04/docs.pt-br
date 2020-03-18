---
title: Teste uma biblioteca de classe .NET Standard com .NET Core no Visual Studio
description: Crie um projeto de teste de unidade para sua biblioteca de classes do .NET Core. Verifique se sua biblioteca de classes do .NET Core funciona corretamente com testes de unidade.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156615"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a><span data-ttu-id="0dbea-104">Teste uma biblioteca .NET Standard com .NET Core no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0dbea-104">Test a .NET Standard library with .NET Core in Visual Studio</span></span>

<span data-ttu-id="0dbea-105">Em [Build a .NET Standard library in Visual Studio,](library-with-visual-studio.md)você criou uma <xref:System.String> biblioteca de classe simples que adiciona um método de extensão à classe.</span><span class="sxs-lookup"><span data-stu-id="0dbea-105">In [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md), you created a simple class library that adds an extension method to the <xref:System.String> class.</span></span> <span data-ttu-id="0dbea-106">Agora, você criará um teste de unidade para ter certeza de que ela funciona conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="0dbea-106">Now, you'll create a unit test to make sure that it works as expected.</span></span> <span data-ttu-id="0dbea-107">Você adicionará seu projeto de teste de unidade à solução criada no artigo anterior.</span><span class="sxs-lookup"><span data-stu-id="0dbea-107">You'll add your unit test project to the solution you created in the previous article.</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="0dbea-108">Crie um projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="0dbea-108">Create a unit test project</span></span>

<span data-ttu-id="0dbea-109">Para criar o projeto de teste de unidade, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0dbea-109">To create the unit test project, do the following:</span></span>

1. <span data-ttu-id="0dbea-110">Abra `ClassLibraryProjects` a solução criada na [biblioteca Build a .NET Standard no](library-with-visual-studio.md) artigo do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0dbea-110">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="0dbea-111">Adicione um novo projeto de teste de unidade chamado "StringLibraryTest" à solução.</span><span class="sxs-lookup"><span data-stu-id="0dbea-111">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="0dbea-112">Clique com o botão direito do mouse na solução no **Solution Explorer** e selecione **Adicionar** > **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="0dbea-112">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="0dbea-113">Na **página Adicionar uma nova** página de projeto, digite **mstest** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="0dbea-113">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="0dbea-114">Escolha **C#** ou **Visual Basic** na lista de idiomas e escolha Todas as **plataformas** da lista Plataforma.</span><span class="sxs-lookup"><span data-stu-id="0dbea-114">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="0dbea-115">Escolha o modelo **MsTest Test Project (.NET Core)** e escolha **Next**.</span><span class="sxs-lookup"><span data-stu-id="0dbea-115">Choose the **MsTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="0dbea-116">Na **página Configurar sua nova** página de projeto, digite **StringLibraryTest** na caixa **nome do Projeto.**</span><span class="sxs-lookup"><span data-stu-id="0dbea-116">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="0dbea-117">Depois, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="0dbea-117">Then choose **Create**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="0dbea-118">Além de um MSTest, você também pode criar projetos de teste xUnit e nUnit para .NET Core no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0dbea-118">In addition to an MSTest, you can also create xUnit and nUnit test projects for .NET Core in Visual Studio.</span></span>

1. <span data-ttu-id="0dbea-119">O Visual Studio cria o projeto e abre o arquivo de classe na janela de código com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0dbea-119">Visual Studio creates the project and opens the class file in the code window with the following code:</span></span>

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

   <span data-ttu-id="0dbea-120">O código-fonte criado pelo modelo de teste de unidade faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0dbea-120">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="0dbea-121">Ele importa o namespace <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, que contém os tipos usados para o teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="0dbea-121">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>

   - <span data-ttu-id="0dbea-122">Ele aplica o atributo [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) à classe `UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="0dbea-122">It applies the [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="0dbea-123">Cada método de teste em uma classe de teste marcada com o atributo [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) é executado automaticamente quando o teste de unidade é executado.</span><span class="sxs-lookup"><span data-stu-id="0dbea-123">Each test method in a test class tagged with the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute is executed automatically when the unit test is run.</span></span>

   - <span data-ttu-id="0dbea-124">Ele aplica o atributo `TestMethod1` [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) para `TestSub` definir em C# ou no Visual Basic como um método de teste para execução automática quando o teste da unidade é executado.</span><span class="sxs-lookup"><span data-stu-id="0dbea-124">It applies the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="0dbea-125">No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Dependências** do projeto **StringLibraryTest** e selecione **Adicionar Referência** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="0dbea-125">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0dbea-126">![Menu de contexto das dependências StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="0dbea-126">![Context menu of StringLibraryTest dependencies](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span></span>

1. <span data-ttu-id="0dbea-127">Na caixa de diálogo **Gerenciador de Referências**, expanda o nó **Projetos** e marque a caixa ao lado de **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="0dbea-127">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="0dbea-128">A adição de uma referência ao assembly `StringLibrary` permite que o compilador localize os métodos **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="0dbea-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="0dbea-129">Selecione o botão **OK.**</span><span class="sxs-lookup"><span data-stu-id="0dbea-129">Select the **OK** button.</span></span> <span data-ttu-id="0dbea-130">Uma referência é adicionada ao `StringLibrary`seu projeto de biblioteca de classes, .</span><span class="sxs-lookup"><span data-stu-id="0dbea-130">A reference is added to your class library project, `StringLibrary`.</span></span>

   ![Diálogo de gerente de referência no Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="0dbea-132">Adicionar e executar métodos de teste unitários</span><span class="sxs-lookup"><span data-stu-id="0dbea-132">Add and run unit test methods</span></span>

<span data-ttu-id="0dbea-133">Quando o Visual Studio executa um teste de unidade, ele executa cada método marcado com o atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> em uma classe de teste de unidade, a classe à qual o atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> é aplicado.</span><span class="sxs-lookup"><span data-stu-id="0dbea-133">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a unit test class, the class to which the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute is applied.</span></span> <span data-ttu-id="0dbea-134">Um método de teste termina quando a primeira falha é encontrada ou quando todos os testes contidos no método foram bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="0dbea-134">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="0dbea-135">Os testes mais comuns chamam membros da classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>.</span><span class="sxs-lookup"><span data-stu-id="0dbea-135">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="0dbea-136">Muitos métodos assert incluem pelo menos dois parâmetros, um deles é o resultado esperado do teste, e o outro é o resultado real do teste.</span><span class="sxs-lookup"><span data-stu-id="0dbea-136">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="0dbea-137">Alguns `Assert` dos métodos mais freqüentes da classe são mostrados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="0dbea-137">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="0dbea-138">Métodos assert</span><span class="sxs-lookup"><span data-stu-id="0dbea-138">Assert methods</span></span>     | <span data-ttu-id="0dbea-139">Função</span><span class="sxs-lookup"><span data-stu-id="0dbea-139">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="0dbea-140">Verifica se os dois valores ou objetos são iguais.</span><span class="sxs-lookup"><span data-stu-id="0dbea-140">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="0dbea-141">A afirmação falha se os valores ou objetos não forem iguais.</span><span class="sxs-lookup"><span data-stu-id="0dbea-141">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="0dbea-142">Verifica se duas variáveis de objeto se referem ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="0dbea-142">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="0dbea-143">A assert falhará se as variáveis se referirem a objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="0dbea-143">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="0dbea-144">Verifica se uma condição é `false`.</span><span class="sxs-lookup"><span data-stu-id="0dbea-144">Verifies that a condition is `false`.</span></span> <span data-ttu-id="0dbea-145">O assert falhará se a condição for `true`.</span><span class="sxs-lookup"><span data-stu-id="0dbea-145">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="0dbea-146">Verifica se um objeto `null`não é .</span><span class="sxs-lookup"><span data-stu-id="0dbea-146">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="0dbea-147">A assert falhará se o objeto for `null`.</span><span class="sxs-lookup"><span data-stu-id="0dbea-147">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="0dbea-148">Você também pode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> usar o método em um método de teste para indicar o tipo de exceção que se espera lançar.</span><span class="sxs-lookup"><span data-stu-id="0dbea-148">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="0dbea-149">O teste falha se a exceção especificada não for lançada.</span><span class="sxs-lookup"><span data-stu-id="0dbea-149">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="0dbea-150">Ao testar o método `StringLibrary.StartsWithUpper`, você quer fornecer um número de cadeias de caracteres que comecem com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="0dbea-150">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="0dbea-151">Você espera que o método retorne `true` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A>.</span><span class="sxs-lookup"><span data-stu-id="0dbea-151">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> method.</span></span> <span data-ttu-id="0dbea-152">Da mesma forma, você deseja fornecer um número de cadeias de caracteres que comecem com algo diferente de um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="0dbea-152">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="0dbea-153">Você espera que o método retorne `false` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A>.</span><span class="sxs-lookup"><span data-stu-id="0dbea-153">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> method.</span></span>

<span data-ttu-id="0dbea-154">Uma vez que o seu método de biblioteca lida com strings, você também quer ter certeza de <xref:System.String.Length> que ele `null` lida com sucesso com uma [seqüência de caracteres (`String.Empty`)](xref:System.String.Empty), uma seqüência válida que não tem caracteres e cujo é 0, e uma string que não foi inicializada.</span><span class="sxs-lookup"><span data-stu-id="0dbea-154">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="0dbea-155">Se `StartsWithUpper` é chamado como um <xref:System.String> método de extensão em `null` uma instância, ele não pode ser aprovado uma string.</span><span class="sxs-lookup"><span data-stu-id="0dbea-155">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it can't be passed a `null` string.</span></span> <span data-ttu-id="0dbea-156">No entanto, você também pode chamá-lo diretamente como um método estático e passa um único argumento <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="0dbea-156">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="0dbea-157">Você definirá três métodos, cada <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> um dos quais chama um método repetidamente para cada elemento em uma matriz de strings.</span><span class="sxs-lookup"><span data-stu-id="0dbea-157">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="0dbea-158">Como o método de teste falha assim que encontrar a primeira falha, você chamará uma sobrecarga de método que permite que você passe uma string que indica o valor da seqüência usado na chamada do método.</span><span class="sxs-lookup"><span data-stu-id="0dbea-158">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="0dbea-159">Para criar os métodos de teste:</span><span class="sxs-lookup"><span data-stu-id="0dbea-159">To create the test methods:</span></span>

1. <span data-ttu-id="0dbea-160">Na janela de código *UnitTest1.cs* ou *UnitTest1.vb,* substitua o código pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0dbea-160">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   <span data-ttu-id="0dbea-161">O teste de caracteres `TestStartsWithUpper` maiúsculos no método inclui a letra maiúscula grega alfa (U+0391) e a letra maiúscula cirílico EM (U+041C).</span><span class="sxs-lookup"><span data-stu-id="0dbea-161">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="0dbea-162">O teste de caracteres `TestDoesNotStartWithUpper` minúsculos no método inclui a pequena letra alfa grega (U+03B1) e a letra pequena cirílico Ghe (U+0433).</span><span class="sxs-lookup"><span data-stu-id="0dbea-162">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="0dbea-163">Na barra de menu, selecione **Salvar arquivos** > **UnitTest1.cs Como** ou Salvar **arquivos** > **UnitTest1.vb As**.</span><span class="sxs-lookup"><span data-stu-id="0dbea-163">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="0dbea-164">Na caixa de diálogo **Salvar Arquivo Como**, selecione a seta ao lado do botão **Salvar** e selecione **Salvar com Codificação**.</span><span class="sxs-lookup"><span data-stu-id="0dbea-164">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0dbea-165">![Visual Studio Salvar Arquivo Como diálogo](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="0dbea-165">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="0dbea-166">Na caixa de diálogo **Confirmar Salvar Como**, selecione o botão **Sim** para salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="0dbea-166">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="0dbea-167">Na caixa de diálogo **Opções Avançadas de Salvamento**, selecione **Unicode (UTF-8 com assinatura) – página de código 65001** na lista suspensa **Codificação** e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="0dbea-167">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0dbea-168">![Caixa de diálogo Opções Avançadas de Salvamento do Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="0dbea-168">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="0dbea-169">Se você não salvar seu código-fonte como um arquivo codificado em UTF8, o Visual Studio poderá salvá-lo como um arquivo ASCII.</span><span class="sxs-lookup"><span data-stu-id="0dbea-169">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="0dbea-170">Quando isso acontece, o tempo de execução não decodifica com precisão os caracteres UTF8 fora da faixa ASCII, e os resultados do teste não serão corretos.</span><span class="sxs-lookup"><span data-stu-id="0dbea-170">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="0dbea-171">Na barra de menu, selecione **Executar** > **todos** > **os testes**.</span><span class="sxs-lookup"><span data-stu-id="0dbea-171">On the menu bar, select **Test** > **Run** > **All Tests**.</span></span> <span data-ttu-id="0dbea-172">A janela **Gerenciador de Testes** é aberta e mostra que os testes foram executados com êxito.</span><span class="sxs-lookup"><span data-stu-id="0dbea-172">The **Test Explorer** window opens and shows that the tests ran successfully.</span></span> <span data-ttu-id="0dbea-173">Os três testes estão listados na seção **Testes Aprovados**, e a seção **Resumo** relata o resultado da execução de teste.</span><span class="sxs-lookup"><span data-stu-id="0dbea-173">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0dbea-174">![Janela Gerenciador de Testes com testes aprovados](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="0dbea-174">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="0dbea-175">Lidar com falhas de teste</span><span class="sxs-lookup"><span data-stu-id="0dbea-175">Handle test failures</span></span>

<span data-ttu-id="0dbea-176">Sua execução de teste não apresentou falhas, mas altere-a um pouco para que um dos métodos do teste falhe:</span><span class="sxs-lookup"><span data-stu-id="0dbea-176">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="0dbea-177">Modifique a matriz `words` no método `TestDoesNotStartWithUpper` para incluir a cadeia de caracteres “Error”.</span><span class="sxs-lookup"><span data-stu-id="0dbea-177">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="0dbea-178">Não é necessário salvar o arquivo porque o Visual Studio salva automaticamente os arquivos abertos quando uma solução é criada para executar testes.</span><span class="sxs-lookup"><span data-stu-id="0dbea-178">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="0dbea-179">Execute o teste selecionando **Test** > **Run** > **All Tests** na barra de menu.</span><span class="sxs-lookup"><span data-stu-id="0dbea-179">Run the test by selecting **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="0dbea-180">A Janela **Gerenciador de Testes** indica que dois testes tiveram êxito e um falhou.</span><span class="sxs-lookup"><span data-stu-id="0dbea-180">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0dbea-181">![Janela Gerenciador de Testes com testes com falha](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="0dbea-181">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="0dbea-182">Selecione o `TestDoesNotStartWith`teste de falha, .</span><span class="sxs-lookup"><span data-stu-id="0dbea-182">Select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="0dbea-183">A janela **Gerenciador de Testes** mostra a mensagem produzida pelo assert: "Assert.IsFalse falhou.</span><span class="sxs-lookup"><span data-stu-id="0dbea-183">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="0dbea-184">Esperado para 'Error': false, real: True".</span><span class="sxs-lookup"><span data-stu-id="0dbea-184">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="0dbea-185">Por causa da falha, todas as strings na matriz após "Erro" não foram testadas.</span><span class="sxs-lookup"><span data-stu-id="0dbea-185">Because of the failure, all strings in the array after "Error" weren't tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0dbea-186">![Janela do Explorador de Teste mostrando a falha de afirmação isfalse](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="0dbea-186">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="0dbea-187">Desfaça as modificações feitas na etapa 1 e remova a cadeia de caracteres "Error".</span><span class="sxs-lookup"><span data-stu-id="0dbea-187">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="0dbea-188">Execute novamente o teste, e eles serão aprovados.</span><span class="sxs-lookup"><span data-stu-id="0dbea-188">Rerun the test and the tests will pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="0dbea-189">Teste a versão de versão da biblioteca</span><span class="sxs-lookup"><span data-stu-id="0dbea-189">Test the Release version of the library</span></span>

<span data-ttu-id="0dbea-190">Você estava executando nossos testes na versão de Depuração da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="0dbea-190">You've been running your tests against the Debug version of the library.</span></span> <span data-ttu-id="0dbea-191">Agora que todos os testes foram aprovados, e nós testamos adequadamente nossa biblioteca, você deve executar os testes mais uma vez no build de Lançamento da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="0dbea-191">Now that your tests have all passed and you've adequately tested your library, you should run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="0dbea-192">Vários fatores, incluindo as otimizações do compilador, podem produzir um comportamento diferente entre as compilações de Depuração e Lançamento.</span><span class="sxs-lookup"><span data-stu-id="0dbea-192">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="0dbea-193">Para testar a compilação de Lançamento:</span><span class="sxs-lookup"><span data-stu-id="0dbea-193">To test the Release build:</span></span>

1. <span data-ttu-id="0dbea-194">Na barra de ferramentas do Visual Studio, altere a configuração de compilação de **Depurar** para **Lançamento**.</span><span class="sxs-lookup"><span data-stu-id="0dbea-194">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0dbea-195">![Barra de ferramentas do Visual Studio com build de versão realçado](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="0dbea-195">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="0dbea-196">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **StringLibrary** e selecione **Compilar** no menu de contexto para recompilar a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="0dbea-196">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0dbea-197">![Menu de contexto de StringLibrary com comando de build](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="0dbea-197">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="0dbea-198">Execute os testes da unidade escolhendo **Test** > **Run** > **All Tests** na barra de menu.</span><span class="sxs-lookup"><span data-stu-id="0dbea-198">Run the unit tests by choosing **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="0dbea-199">Os testes são aprovados.</span><span class="sxs-lookup"><span data-stu-id="0dbea-199">The tests pass.</span></span>

<span data-ttu-id="0dbea-200">Agora que você concluiu o teste de sua biblioteca, a próxima etapa é disponibilizá-la aos chamadores.</span><span class="sxs-lookup"><span data-stu-id="0dbea-200">Now that you've finished testing your library, the next step is to make it available to callers.</span></span> <span data-ttu-id="0dbea-201">Você pode agrupá-la com um ou mais aplicativos, ou pode distribuí-la como um pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="0dbea-201">You can bundle it with one or more applications, or you can distribute it as a NuGet package.</span></span> <span data-ttu-id="0dbea-202">Para obter mais informações, consulte [Consumindo uma biblioteca de classes .NET Standard](consuming-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="0dbea-202">For more information, see [Consuming a .NET Standard Class Library](consuming-library-with-visual-studio.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0dbea-203">Confira também</span><span class="sxs-lookup"><span data-stu-id="0dbea-203">See also</span></span>

- [<span data-ttu-id="0dbea-204">Noções básicas de teste unitário - Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0dbea-204">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)
