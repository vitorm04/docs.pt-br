---
title: Testar um .NET Standard biblioteca de classes com o .NET Core no Visual Studio
description: Crie um projeto de teste de unidade para sua biblioteca de classes do .NET Core. Verifique se sua biblioteca de classes do .NET Core funciona corretamente com testes de unidade.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 3a4f25b0d250469102fdac6ee960e42b2d969aed
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559572"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a><span data-ttu-id="be2b4-104">Testar uma biblioteca de .NET Standard com o .NET Core no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="be2b4-104">Test a .NET Standard library with .NET Core in Visual Studio</span></span>

<span data-ttu-id="be2b4-105">Em [criar uma biblioteca de .net Standard no Visual Studio](library-with-visual-studio.md), você criou uma biblioteca de classes simples que adiciona um método de extensão à classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="be2b4-105">In [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md), you created a simple class library that adds an extension method to the <xref:System.String> class.</span></span> <span data-ttu-id="be2b4-106">Agora, você criará um teste de unidade para ter certeza de que ela funciona conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="be2b4-106">Now, you'll create a unit test to make sure that it works as expected.</span></span> <span data-ttu-id="be2b4-107">Você adicionará seu projeto de teste de unidade à solução criada no artigo anterior.</span><span class="sxs-lookup"><span data-stu-id="be2b4-107">You'll add your unit test project to the solution you created in the previous article.</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="be2b4-108">Crie um projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="be2b4-108">Create a unit test project</span></span>

<span data-ttu-id="be2b4-109">Para criar o projeto de teste de unidade, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="be2b4-109">To create the unit test project, do the following:</span></span>

1. <span data-ttu-id="be2b4-110">Abra a solução `ClassLibraryProjects` que você criou no artigo [criar uma biblioteca de .net Standard no Visual Studio](library-with-visual-studio.md) .</span><span class="sxs-lookup"><span data-stu-id="be2b4-110">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="be2b4-111">Adicione um novo projeto de teste de unidade chamado "StringLibraryTest" à solução.</span><span class="sxs-lookup"><span data-stu-id="be2b4-111">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="be2b4-112">Clique com o botão direito do mouse na solução em **Gerenciador de soluções** e selecione **Adicionar** > **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="be2b4-112">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="be2b4-113">Na página **Adicionar um novo projeto** , digite **MSTest** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="be2b4-113">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="be2b4-114">Escolha **C#** ou **Visual Basic** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma.</span><span class="sxs-lookup"><span data-stu-id="be2b4-114">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="be2b4-115">Escolha o modelo de **projeto de teste MSTest (.NET Core)** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="be2b4-115">Choose the **MsTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="be2b4-116">Na página **configurar seu novo projeto** , digite **StringLibraryTest** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="be2b4-116">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="be2b4-117">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="be2b4-117">Then choose **Create**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="be2b4-118">Além de um MSTest, você também pode criar projetos de teste xUnit e nUnit para .NET Core no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="be2b4-118">In addition to an MSTest, you can also create xUnit and nUnit test projects for .NET Core in Visual Studio.</span></span>

1. <span data-ttu-id="be2b4-119">O Visual Studio cria o projeto e abre o arquivo de classe na janela de código com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="be2b4-119">Visual Studio creates the project and opens the class file in the code window with the following code:</span></span>

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

   <span data-ttu-id="be2b4-120">O código-fonte criado pelo modelo de teste de unidade faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="be2b4-120">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="be2b4-121">Ele importa o namespace <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, que contém os tipos usados para o teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="be2b4-121">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>

   - <span data-ttu-id="be2b4-122">Ele aplica o atributo [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) à classe `UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="be2b4-122">It applies the [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="be2b4-123">Cada método de teste em uma classe de teste marcada com o atributo [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) é executado automaticamente quando o teste de unidade é executado.</span><span class="sxs-lookup"><span data-stu-id="be2b4-123">Each test method in a test class tagged with the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute is executed automatically when the unit test is run.</span></span>

   - <span data-ttu-id="be2b4-124">Ele aplica o atributo [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) para definir `TestMethod1` no C# ou `TestSub` no Visual Basic como um método de teste para a execução automática quando o teste de unidade é executado.</span><span class="sxs-lookup"><span data-stu-id="be2b4-124">It applies the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="be2b4-125">No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Dependências** do projeto **StringLibraryTest** e selecione **Adicionar Referência** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="be2b4-125">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="be2b4-126">![menu de contexto de dependências StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="be2b4-126">![Context menu of StringLibraryTest dependencies](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span></span>

1. <span data-ttu-id="be2b4-127">Na caixa de diálogo **Gerenciador de Referências**, expanda o nó **Projetos** e marque a caixa ao lado de **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="be2b4-127">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="be2b4-128">A adição de uma referência ao assembly `StringLibrary` permite que o compilador localize os métodos **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="be2b4-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="be2b4-129">Selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="be2b4-129">Select the **OK** button.</span></span> <span data-ttu-id="be2b4-130">Uma referência é adicionada ao seu projeto de biblioteca de classes, `StringLibrary`.</span><span class="sxs-lookup"><span data-stu-id="be2b4-130">A reference is added to your class library project, `StringLibrary`.</span></span>

   ![Caixa de diálogo Gerenciador de referências no Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="be2b4-132">Adicionar e executar métodos de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="be2b4-132">Add and run unit test methods</span></span>

<span data-ttu-id="be2b4-133">Quando o Visual Studio executa um teste de unidade, ele executa cada método marcado com o atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> em uma classe de teste de unidade, a classe à qual o atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> é aplicado.</span><span class="sxs-lookup"><span data-stu-id="be2b4-133">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a unit test class, the class to which the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute is applied.</span></span> <span data-ttu-id="be2b4-134">Um método de teste termina quando a primeira falha é encontrada ou quando todos os testes contidos no método foram bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="be2b4-134">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="be2b4-135">Os testes mais comuns chamam membros da classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>.</span><span class="sxs-lookup"><span data-stu-id="be2b4-135">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="be2b4-136">Muitos métodos assert incluem pelo menos dois parâmetros, um deles é o resultado esperado do teste, e o outro é o resultado real do teste.</span><span class="sxs-lookup"><span data-stu-id="be2b4-136">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="be2b4-137">Alguns dos métodos chamados mais frequentemente da classe `Assert` são mostrados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="be2b4-137">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="be2b4-138">Métodos assert</span><span class="sxs-lookup"><span data-stu-id="be2b4-138">Assert methods</span></span>     | <span data-ttu-id="be2b4-139">Função</span><span class="sxs-lookup"><span data-stu-id="be2b4-139">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="be2b4-140">Verifica se os dois valores ou objetos são iguais.</span><span class="sxs-lookup"><span data-stu-id="be2b4-140">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="be2b4-141">A declaração falhará se os valores ou objetos não forem iguais.</span><span class="sxs-lookup"><span data-stu-id="be2b4-141">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="be2b4-142">Verifica se duas variáveis de objeto se referem ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="be2b4-142">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="be2b4-143">A assert falhará se as variáveis se referirem a objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="be2b4-143">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="be2b4-144">Verifica se uma condição é `false`.</span><span class="sxs-lookup"><span data-stu-id="be2b4-144">Verifies that a condition is `false`.</span></span> <span data-ttu-id="be2b4-145">O assert falhará se a condição for `true`.</span><span class="sxs-lookup"><span data-stu-id="be2b4-145">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="be2b4-146">Verifica se um objeto não está `null`.</span><span class="sxs-lookup"><span data-stu-id="be2b4-146">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="be2b4-147">A assert falhará se o objeto for `null`.</span><span class="sxs-lookup"><span data-stu-id="be2b4-147">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="be2b4-148">Você também pode usar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> em um método de teste para indicar o tipo de exceção que ele deve lançar.</span><span class="sxs-lookup"><span data-stu-id="be2b4-148">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="be2b4-149">O teste falhará se a exceção especificada não for lançada.</span><span class="sxs-lookup"><span data-stu-id="be2b4-149">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="be2b4-150">Ao testar o método `StringLibrary.StartsWithUpper`, você quer fornecer um número de cadeias de caracteres que comecem com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="be2b4-150">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="be2b4-151">Você espera que o método retorne `true` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A>.</span><span class="sxs-lookup"><span data-stu-id="be2b4-151">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> method.</span></span> <span data-ttu-id="be2b4-152">Da mesma forma, você deseja fornecer um número de cadeias de caracteres que comecem com algo diferente de um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="be2b4-152">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="be2b4-153">Você espera que o método retorne `false` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A>.</span><span class="sxs-lookup"><span data-stu-id="be2b4-153">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> method.</span></span>

<span data-ttu-id="be2b4-154">Como o método de biblioteca lida com cadeias de caracteres, você também deseja certificar-se de que ele manipula com êxito uma [cadeia de caracteres vazia (`String.Empty`)](xref:System.String.Empty), uma cadeia de caracteres válida que não tem caracteres e cujo <xref:System.String.Length> é 0 e uma cadeia de caracteres `null` que não foi inicializada.</span><span class="sxs-lookup"><span data-stu-id="be2b4-154">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="be2b4-155">Se `StartsWithUpper` for chamado como um método de extensão em uma instância de <xref:System.String>, ele não poderá passar uma cadeia de caracteres de `null`.</span><span class="sxs-lookup"><span data-stu-id="be2b4-155">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it can't be passed a `null` string.</span></span> <span data-ttu-id="be2b4-156">No entanto, você também pode chamá-lo diretamente como um método estático e passa um único argumento <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="be2b4-156">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="be2b4-157">Você definirá três métodos, cada um dos quais chama um método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> repetidamente para cada elemento em uma matriz de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="be2b4-157">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="be2b4-158">Como o método de teste falha assim que encontra a primeira falha, você chamará uma sobrecarga de método que permite passar uma cadeia de caracteres que indica o valor da cadeia de caracteres usado na chamada do método.</span><span class="sxs-lookup"><span data-stu-id="be2b4-158">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="be2b4-159">Para criar os métodos de teste:</span><span class="sxs-lookup"><span data-stu-id="be2b4-159">To create the test methods:</span></span>

1. <span data-ttu-id="be2b4-160">Na janela de código *UnitTest1.cs* ou *UnitTest1. vb* , substitua o código pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="be2b4-160">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   <span data-ttu-id="be2b4-161">O teste de caracteres maiúsculos no método `TestStartsWithUpper` inclui a letra maiúscula grega alfa (U + 0391) e a letra maiúscula cirílica em (U + 041C).</span><span class="sxs-lookup"><span data-stu-id="be2b4-161">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="be2b4-162">O teste de caracteres minúsculos no método `TestDoesNotStartWithUpper` inclui a letra grega pequena alfa (U + 03B1) e a letra cirílica minúscula Ghe (U + 0433).</span><span class="sxs-lookup"><span data-stu-id="be2b4-162">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="be2b4-163">Na barra de menus, selecione **arquivo** > **salvar UnitTest1.cs como** ou **arquivo** > **salvar UnitTest1. vb como**.</span><span class="sxs-lookup"><span data-stu-id="be2b4-163">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="be2b4-164">Na caixa de diálogo **Salvar Arquivo Como**, selecione a seta ao lado do botão **Salvar** e selecione **Salvar com Codificação**.</span><span class="sxs-lookup"><span data-stu-id="be2b4-164">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="be2b4-165">![de diálogo Salvar arquivo como do Visual Studio](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="be2b4-165">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="be2b4-166">Na caixa de diálogo **Confirmar Salvar Como**, selecione o botão **Sim** para salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="be2b4-166">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="be2b4-167">Na caixa de diálogo **Opções Avançadas de Salvamento**, selecione **Unicode (UTF-8 com assinatura) – página de código 65001** na lista suspensa **Codificação** e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="be2b4-167">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="be2b4-168">caixa de diálogo opções de salvamento avançadas do ![Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="be2b4-168">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="be2b4-169">Se você não salvar seu código-fonte como um arquivo codificado em UTF8, o Visual Studio poderá salvá-lo como um arquivo ASCII.</span><span class="sxs-lookup"><span data-stu-id="be2b4-169">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="be2b4-170">Quando isso acontece, o tempo de execução não decodifica com precisão os caracteres UTF8 fora do intervalo ASCII, e os resultados de teste não estarão corretos.</span><span class="sxs-lookup"><span data-stu-id="be2b4-170">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="be2b4-171">Na barra de menus, selecione **Testar** > **Executar** > **Todos os Testes**.</span><span class="sxs-lookup"><span data-stu-id="be2b4-171">On the menu bar, select **Test** > **Run** > **All Tests**.</span></span> <span data-ttu-id="be2b4-172">A janela **Gerenciador de Testes** é aberta e mostra que os testes foram executados com êxito.</span><span class="sxs-lookup"><span data-stu-id="be2b4-172">The **Test Explorer** window opens and shows that the tests ran successfully.</span></span> <span data-ttu-id="be2b4-173">Os três testes estão listados na seção **Testes Aprovados**, e a seção **Resumo** relata o resultado da execução de teste.</span><span class="sxs-lookup"><span data-stu-id="be2b4-173">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="be2b4-174">![janela do Gerenciador de testes com testes aprovados](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="be2b4-174">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="be2b4-175">Lidar com falhas de teste</span><span class="sxs-lookup"><span data-stu-id="be2b4-175">Handle test failures</span></span>

<span data-ttu-id="be2b4-176">Sua execução de teste não apresentou falhas, mas altere-a um pouco para que um dos métodos do teste falhe:</span><span class="sxs-lookup"><span data-stu-id="be2b4-176">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="be2b4-177">Modifique a matriz `words` no método `TestDoesNotStartWithUpper` para incluir a cadeia de caracteres “Error”.</span><span class="sxs-lookup"><span data-stu-id="be2b4-177">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="be2b4-178">Não é necessário salvar o arquivo porque o Visual Studio salva automaticamente os arquivos abertos quando uma solução é criada para executar testes.</span><span class="sxs-lookup"><span data-stu-id="be2b4-178">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="be2b4-179">Execute o teste selecionando **Testar** > **Executar** > **Todos os Testes** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="be2b4-179">Run the test by selecting **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="be2b4-180">A Janela **Gerenciador de Testes** indica que dois testes tiveram êxito e um falhou.</span><span class="sxs-lookup"><span data-stu-id="be2b4-180">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="be2b4-181">![janela do Gerenciador de testes com testes com falha](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="be2b4-181">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="be2b4-182">Selecione o teste com falha, `TestDoesNotStartWith`.</span><span class="sxs-lookup"><span data-stu-id="be2b4-182">Select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="be2b4-183">A janela **Gerenciador de Testes** mostra a mensagem produzida pelo assert: "Assert.IsFalse falhou.</span><span class="sxs-lookup"><span data-stu-id="be2b4-183">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="be2b4-184">Esperado para 'Error': false, real: True".</span><span class="sxs-lookup"><span data-stu-id="be2b4-184">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="be2b4-185">Devido à falha, todas as cadeias de caracteres na matriz após "erro" não foram testadas.</span><span class="sxs-lookup"><span data-stu-id="be2b4-185">Because of the failure, all strings in the array after "Error" weren't tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="be2b4-186">![janela do Gerenciador de testes mostrando a falha de asserção IsFalse](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="be2b4-186">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="be2b4-187">Desfaça as modificações feitas na etapa 1 e remova a cadeia de caracteres "Error".</span><span class="sxs-lookup"><span data-stu-id="be2b4-187">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="be2b4-188">Execute novamente o teste, e eles serão aprovados.</span><span class="sxs-lookup"><span data-stu-id="be2b4-188">Rerun the test and the tests will pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="be2b4-189">Testar a versão de lançamento da biblioteca</span><span class="sxs-lookup"><span data-stu-id="be2b4-189">Test the Release version of the library</span></span>

<span data-ttu-id="be2b4-190">Você estava executando nossos testes na versão de Depuração da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="be2b4-190">You've been running your tests against the Debug version of the library.</span></span> <span data-ttu-id="be2b4-191">Agora que todos os testes foram aprovados, e nós testamos adequadamente nossa biblioteca, você deve executar os testes mais uma vez no build de Lançamento da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="be2b4-191">Now that your tests have all passed and you've adequately tested your library, you should run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="be2b4-192">Vários fatores, incluindo as otimizações do compilador, podem produzir um comportamento diferente entre as compilações de Depuração e Lançamento.</span><span class="sxs-lookup"><span data-stu-id="be2b4-192">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="be2b4-193">Para testar a compilação de Lançamento:</span><span class="sxs-lookup"><span data-stu-id="be2b4-193">To test the Release build:</span></span>

1. <span data-ttu-id="be2b4-194">Na barra de ferramentas do Visual Studio, altere a configuração de compilação de **Depurar** para **Lançamento**.</span><span class="sxs-lookup"><span data-stu-id="be2b4-194">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="be2b4-195">![barra de ferramentas do Visual Studio com o Build de versão realçado](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="be2b4-195">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="be2b4-196">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **StringLibrary** e selecione **Compilar** no menu de contexto para recompilar a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="be2b4-196">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="be2b4-197">![menu de contexto StringLibrary com o comando Build](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="be2b4-197">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="be2b4-198">Execute os testes de unidade escolhendo **Testar** > **Executar** > **Todos os Testes** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="be2b4-198">Run the unit tests by choosing **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="be2b4-199">Os testes são aprovados.</span><span class="sxs-lookup"><span data-stu-id="be2b4-199">The tests pass.</span></span>

<span data-ttu-id="be2b4-200">Agora que você concluiu o teste de sua biblioteca, a próxima etapa é disponibilizá-la aos chamadores.</span><span class="sxs-lookup"><span data-stu-id="be2b4-200">Now that you've finished testing your library, the next step is to make it available to callers.</span></span> <span data-ttu-id="be2b4-201">Você pode agrupá-la com um ou mais aplicativos, ou pode distribuí-la como um pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="be2b4-201">You can bundle it with one or more applications, or you can distribute it as a NuGet package.</span></span> <span data-ttu-id="be2b4-202">Para obter mais informações, consulte [Consumindo uma biblioteca de classes .NET Standard](consuming-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="be2b4-202">For more information, see [Consuming a .NET Standard Class Library](consuming-library-with-visual-studio.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="be2b4-203">Veja também</span><span class="sxs-lookup"><span data-stu-id="be2b4-203">See also</span></span>

- [<span data-ttu-id="be2b4-204">Noções básicas do teste de unidade – Visual Studio</span><span class="sxs-lookup"><span data-stu-id="be2b4-204">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)
