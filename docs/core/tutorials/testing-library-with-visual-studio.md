---
title: Testar um .NET Standard biblioteca de classes com o .NET Core no Visual Studio
description: Crie um projeto de teste de unidade para sua biblioteca de classes do .NET Core. Verifique se sua biblioteca de classes do .NET Core funciona corretamente com testes de unidade.
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 48ada77b8422030fd93aa29df1df50a3ae5104fe
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283501"
---
# <a name="tutorial-test-a-net-standard-library-with-net-core-in-visual-studio"></a><span data-ttu-id="7845c-104">Tutorial: testar uma biblioteca de .NET Standard com o .NET Core no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7845c-104">Tutorial: Test a .NET Standard library with .NET Core in Visual Studio</span></span>

<span data-ttu-id="7845c-105">Este tutorial mostra como automatizar o teste de unidade adicionando um projeto de teste a uma solução.</span><span class="sxs-lookup"><span data-stu-id="7845c-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7845c-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7845c-106">Prerequisites</span></span>

- <span data-ttu-id="7845c-107">Este tutorial funciona com a solução que você cria em [criar uma .net Standard biblioteca no Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="7845c-107">This tutorial works with the solution that you create in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="7845c-108">Crie um projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="7845c-108">Create a unit test project</span></span>

1. <span data-ttu-id="7845c-109">Abra a `ClassLibraryProjects` solução que você criou em [criar uma .net Standard biblioteca no Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="7845c-109">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="7845c-110">Adicione um novo projeto de teste de unidade chamado "StringLibraryTest" à solução.</span><span class="sxs-lookup"><span data-stu-id="7845c-110">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="7845c-111">Clique com o botão direito do mouse na solução em **Gerenciador de soluções** e selecione **Adicionar**  >  **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="7845c-111">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="7845c-112">Na página **Adicionar um novo projeto** , digite **MSTest** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="7845c-112">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="7845c-113">Escolha **C#** ou **Visual Basic** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma.</span><span class="sxs-lookup"><span data-stu-id="7845c-113">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="7845c-114">Escolha o modelo de **projeto de teste MSTest (.NET Core)** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="7845c-114">Choose the **MSTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="7845c-115">Na página **configurar seu novo projeto** , digite **StringLibraryTest** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="7845c-115">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="7845c-116">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="7845c-116">Then choose **Create**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="7845c-117">MSTest é uma das três estruturas de teste que você pode escolher.</span><span class="sxs-lookup"><span data-stu-id="7845c-117">MSTest is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="7845c-118">Os outros são xUnit e nUnit.</span><span class="sxs-lookup"><span data-stu-id="7845c-118">The others are xUnit and nUnit.</span></span>

1. <span data-ttu-id="7845c-119">O Visual Studio cria o projeto e abre o arquivo de classe na janela de código com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7845c-119">Visual Studio creates the project and opens the class file in the code window with the following code.</span></span> <span data-ttu-id="7845c-120">Se o idioma que você deseja usar não for mostrado, altere o seletor de idioma na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="7845c-120">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

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

   <span data-ttu-id="7845c-121">O código-fonte criado pelo modelo de teste de unidade faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7845c-121">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="7845c-122">Ele importa o namespace <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, que contém os tipos usados para o teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="7845c-122">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="7845c-123">Ele aplica o atributo<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> à classe `UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="7845c-123">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="7845c-124">Ele aplica o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributo para definir `TestMethod1` em C# ou `TestSub` em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7845c-124">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic.</span></span>

   <span data-ttu-id="7845c-125">Cada método marcado com [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) em uma classe de teste marcada com [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) é executado automaticamente quando o teste de unidade é executado.</span><span class="sxs-lookup"><span data-stu-id="7845c-125">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

1. <span data-ttu-id="7845c-126">Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó **dependências** do projeto **StringLibraryTest** e selecione **Adicionar referência de projeto** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="7845c-126">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Project Reference** from the context menu.</span></span>

1. <span data-ttu-id="7845c-127">No diálogo **Gerenciador de referências** , expanda o nó **projetos** e selecione a caixa ao lado de **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="7845c-127">In the **Reference Manager** dialog, expand the **Projects** node, and select the box next to **StringLibrary**.</span></span> <span data-ttu-id="7845c-128">Adicionar uma referência ao `StringLibrary` assembly permite que o compilador encontre métodos **StringLibrary** ao compilar o projeto **StringLibraryTest** .</span><span class="sxs-lookup"><span data-stu-id="7845c-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods while compiling the **StringLibraryTest** project.</span></span>

1. <span data-ttu-id="7845c-129">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="7845c-129">Select **OK**.</span></span>

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="7845c-130">Adicionar e executar métodos de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="7845c-130">Add and run unit test methods</span></span>

<span data-ttu-id="7845c-131">Quando o Visual Studio executa um teste de unidade, ele executa cada método marcado com o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributo em uma classe marcada com o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="7845c-131">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="7845c-132">Um método de teste termina quando a primeira falha é encontrada ou quando todos os testes contidos no método foram bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="7845c-132">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="7845c-133">Os testes mais comuns chamam membros da classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>.</span><span class="sxs-lookup"><span data-stu-id="7845c-133">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="7845c-134">Muitos métodos assert incluem pelo menos dois parâmetros, um deles é o resultado esperado do teste, e o outro é o resultado real do teste.</span><span class="sxs-lookup"><span data-stu-id="7845c-134">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="7845c-135">Alguns dos `Assert` métodos chamados mais frequentemente da classe são mostrados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="7845c-135">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="7845c-136">Métodos assert</span><span class="sxs-lookup"><span data-stu-id="7845c-136">Assert methods</span></span>     | <span data-ttu-id="7845c-137">Função</span><span class="sxs-lookup"><span data-stu-id="7845c-137">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="7845c-138">Verifica se os dois valores ou objetos são iguais.</span><span class="sxs-lookup"><span data-stu-id="7845c-138">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="7845c-139">A declaração falhará se os valores ou objetos não forem iguais.</span><span class="sxs-lookup"><span data-stu-id="7845c-139">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="7845c-140">Verifica se duas variáveis de objeto se referem ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="7845c-140">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="7845c-141">A assert falhará se as variáveis se referirem a objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="7845c-141">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="7845c-142">Verifica se uma condição é `false`.</span><span class="sxs-lookup"><span data-stu-id="7845c-142">Verifies that a condition is `false`.</span></span> <span data-ttu-id="7845c-143">O assert falhará se a condição for `true`.</span><span class="sxs-lookup"><span data-stu-id="7845c-143">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="7845c-144">Verifica se um objeto não está `null` .</span><span class="sxs-lookup"><span data-stu-id="7845c-144">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="7845c-145">A assert falhará se o objeto for `null`.</span><span class="sxs-lookup"><span data-stu-id="7845c-145">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="7845c-146">Você também pode usar o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> método em um método de teste para indicar o tipo de exceção que ele deve lançar.</span><span class="sxs-lookup"><span data-stu-id="7845c-146">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="7845c-147">O teste falhará se a exceção especificada não for lançada.</span><span class="sxs-lookup"><span data-stu-id="7845c-147">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="7845c-148">Ao testar o método `StringLibrary.StartsWithUpper`, você quer fornecer um número de cadeias de caracteres que comecem com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="7845c-148">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="7845c-149">Você espera que o método retorne `true` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7845c-149">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7845c-150">Da mesma forma, você deseja fornecer um número de cadeias de caracteres que comecem com algo diferente de um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="7845c-150">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="7845c-151">Você espera que o método retorne `false` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7845c-151">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="7845c-152">Como o método de biblioteca lida com cadeias de caracteres, você também deseja certificar-se de que ele manipula com êxito uma [cadeia de caracteres vazia ( `String.Empty` )](xref:System.String.Empty), uma cadeia de caracteres válida que não tem caracteres e cujo número <xref:System.String.Length> é 0 e uma `null` cadeia de caracteres que não foi inicializada.</span><span class="sxs-lookup"><span data-stu-id="7845c-152">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="7845c-153">Se `StartsWithUpper` é chamado como um método de extensão em uma <xref:System.String> instância, não é possível passar uma `null` cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7845c-153">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it can't be passed a `null` string.</span></span> <span data-ttu-id="7845c-154">No entanto, você também pode chamá-lo diretamente como um método estático e passa um único argumento <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="7845c-154">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="7845c-155">Você definirá três métodos, cada um deles chamará um <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> método repetidamente para cada elemento em uma matriz de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7845c-155">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="7845c-156">Como o método de teste falha assim que encontra a primeira falha, você chamará uma sobrecarga de método que permite passar uma cadeia de caracteres que indica o valor da cadeia de caracteres usado na chamada do método.</span><span class="sxs-lookup"><span data-stu-id="7845c-156">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="7845c-157">Para criar os métodos de teste:</span><span class="sxs-lookup"><span data-stu-id="7845c-157">To create the test methods:</span></span>

1. <span data-ttu-id="7845c-158">Na janela de código *UnitTest1.cs* ou *UnitTest1. vb* , substitua o código pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="7845c-158">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibraryTest/UnitTest1.vb":::

   <span data-ttu-id="7845c-159">O teste de caracteres maiúsculos no `TestStartsWithUpper` método inclui a letra maiúscula grega alfa (u + 0391) e a letra maiúscula cirílica em (u + 041C).</span><span class="sxs-lookup"><span data-stu-id="7845c-159">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="7845c-160">O teste de caracteres minúsculos no `TestDoesNotStartWithUpper` método inclui a letra grega pequena alfa (u + 03B1) e a letra cirílica minúscula Ghe (u + 0433).</span><span class="sxs-lookup"><span data-stu-id="7845c-160">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="7845c-161">Na barra de menus, selecione **arquivo**  >  **salvar UnitTest1.cs como** ou **arquivo**  >  **salvar UnitTest1. vb como**.</span><span class="sxs-lookup"><span data-stu-id="7845c-161">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="7845c-162">Na caixa de diálogo **Salvar Arquivo Como**, selecione a seta ao lado do botão **Salvar** e selecione **Salvar com Codificação**.</span><span class="sxs-lookup"><span data-stu-id="7845c-162">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="7845c-163">![Caixa de diálogo Salvar arquivo como do Visual Studio](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="7845c-163">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="7845c-164">Na caixa de diálogo **Confirmar Salvar Como**, selecione o botão **Sim** para salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="7845c-164">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="7845c-165">Na caixa de diálogo **Opções Avançadas de Salvamento**, selecione **Unicode (UTF-8 com assinatura) – página de código 65001** na lista suspensa **Codificação** e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="7845c-165">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="7845c-166">![Caixa de diálogo Opções Avançadas de Salvamento do Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="7845c-166">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="7845c-167">Se você não salvar seu código-fonte como um arquivo codificado em UTF8, o Visual Studio poderá salvá-lo como um arquivo ASCII.</span><span class="sxs-lookup"><span data-stu-id="7845c-167">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="7845c-168">Quando isso acontece, o tempo de execução não decodifica com precisão os caracteres UTF8 fora do intervalo ASCII, e os resultados de teste não estarão corretos.</span><span class="sxs-lookup"><span data-stu-id="7845c-168">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="7845c-169">Na barra de menus, selecione **testar**  >  **executar todos os testes**.</span><span class="sxs-lookup"><span data-stu-id="7845c-169">On the menu bar, select **Test** > **Run All Tests**.</span></span> <span data-ttu-id="7845c-170">Se a janela **Gerenciador de testes** não abrir, abra-a escolhendo **Test**  >  **Test Explorer**.</span><span class="sxs-lookup"><span data-stu-id="7845c-170">If the **Test Explorer** window doesn't open, open it by choosing **Test** > **Test Explorer**.</span></span> <span data-ttu-id="7845c-171">Os três testes estão listados na seção **Testes Aprovados**, e a seção **Resumo** relata o resultado da execução de teste.</span><span class="sxs-lookup"><span data-stu-id="7845c-171">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="7845c-172">![Janela Gerenciador de Testes com testes aprovados](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="7845c-172">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="7845c-173">Lidar com falhas de teste</span><span class="sxs-lookup"><span data-stu-id="7845c-173">Handle test failures</span></span>

<span data-ttu-id="7845c-174">Se você estiver fazendo o TDD (desenvolvimento controlado por teste), você escreverá testes primeiro e eles falharão na primeira vez em que forem executados.</span><span class="sxs-lookup"><span data-stu-id="7845c-174">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="7845c-175">Em seguida, você adiciona código ao aplicativo que torna o teste com sucesso.</span><span class="sxs-lookup"><span data-stu-id="7845c-175">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="7845c-176">Nesse caso, você criou o teste depois de gravar o código do aplicativo que ele valida, para que você não tenha visto o teste falhar.</span><span class="sxs-lookup"><span data-stu-id="7845c-176">In this case, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="7845c-177">Para validar que um teste falha quando você espera que ele falhe, adicione um valor inválido para a entrada de teste.</span><span class="sxs-lookup"><span data-stu-id="7845c-177">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="7845c-178">Modifique a matriz `words` no método `TestDoesNotStartWithUpper` para incluir a cadeia de caracteres “Error”.</span><span class="sxs-lookup"><span data-stu-id="7845c-178">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="7845c-179">Não é necessário salvar o arquivo porque o Visual Studio salva automaticamente os arquivos abertos quando uma solução é criada para executar testes.</span><span class="sxs-lookup"><span data-stu-id="7845c-179">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="7845c-180">Execute o teste selecionando **testar**  >  **executar todos os testes** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="7845c-180">Run the test by selecting **Test** > **Run All Tests** from the menu bar.</span></span> <span data-ttu-id="7845c-181">A Janela **Gerenciador de Testes** indica que dois testes tiveram êxito e um falhou.</span><span class="sxs-lookup"><span data-stu-id="7845c-181">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="7845c-182">![Janela Gerenciador de Testes com testes com falha](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="7845c-182">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="7845c-183">Selecione o teste com falha, `TestDoesNotStartWith` .</span><span class="sxs-lookup"><span data-stu-id="7845c-183">Select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="7845c-184">A janela **Gerenciador de Testes** mostra a mensagem produzida pelo assert: "Assert.IsFalse falhou.</span><span class="sxs-lookup"><span data-stu-id="7845c-184">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="7845c-185">Esperado para 'Error': false, real: True".</span><span class="sxs-lookup"><span data-stu-id="7845c-185">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="7845c-186">Devido à falha, todas as cadeias de caracteres na matriz após "erro" não foram testadas.</span><span class="sxs-lookup"><span data-stu-id="7845c-186">Because of the failure, all strings in the array after "Error" weren't tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="7845c-187">![Janela do Gerenciador de testes mostrando a falha de asserção IsFalse](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="7845c-187">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="7845c-188">Desfaça as modificações feitas na etapa 1 e remova a cadeia de caracteres "Error".</span><span class="sxs-lookup"><span data-stu-id="7845c-188">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="7845c-189">Execute novamente o teste e os testes são aprovados.</span><span class="sxs-lookup"><span data-stu-id="7845c-189">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="7845c-190">Testar a versão de lançamento da biblioteca</span><span class="sxs-lookup"><span data-stu-id="7845c-190">Test the Release version of the library</span></span>

<span data-ttu-id="7845c-191">Agora que todos os testes passaram ao executar a versão de depuração da biblioteca, execute o testa um tempo adicional em relação à compilação da versão da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="7845c-191">Now that the tests have all passed when running the Debug version of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="7845c-192">Vários fatores, incluindo as otimizações do compilador, podem produzir um comportamento diferente entre as compilações de Depuração e Lançamento.</span><span class="sxs-lookup"><span data-stu-id="7845c-192">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="7845c-193">Para testar a compilação de Lançamento:</span><span class="sxs-lookup"><span data-stu-id="7845c-193">To test the Release build:</span></span>

1. <span data-ttu-id="7845c-194">Na barra de ferramentas do Visual Studio, altere a configuração de compilação de **Depurar** para **Lançamento**.</span><span class="sxs-lookup"><span data-stu-id="7845c-194">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="7845c-195">![Barra de ferramentas do Visual Studio com build de versão realçado](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="7845c-195">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="7845c-196">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **StringLibrary** e selecione **Compilar** no menu de contexto para recompilar a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="7845c-196">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="7845c-197">![Menu de contexto de StringLibrary com comando de build](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="7845c-197">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="7845c-198">Execute os testes de unidade escolhendo **testar executar**  >  **todos os testes** na barra de menus.</span><span class="sxs-lookup"><span data-stu-id="7845c-198">Run the unit tests by choosing **Test Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="7845c-199">Os testes são aprovados.</span><span class="sxs-lookup"><span data-stu-id="7845c-199">The tests pass.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7845c-200">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="7845c-200">Additional resources</span></span>

- [<span data-ttu-id="7845c-201">Noções básicas do teste de unidade – Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7845c-201">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)

## <a name="next-steps"></a><span data-ttu-id="7845c-202">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="7845c-202">Next steps</span></span>

<span data-ttu-id="7845c-203">Neste tutorial, você testou uma unidade de biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="7845c-203">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="7845c-204">Você pode tornar a biblioteca disponível para outras pessoas publicando-a no [NuGet](https://nuget.org) como um pacote.</span><span class="sxs-lookup"><span data-stu-id="7845c-204">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="7845c-205">Para saber como, siga um tutorial do NuGet:</span><span class="sxs-lookup"><span data-stu-id="7845c-205">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7845c-206">Criar e publicar um pacote NuGet usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7845c-206">Create and publish a NuGet package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

<span data-ttu-id="7845c-207">Se você publicar uma biblioteca como um pacote NuGet, outras pessoas poderão instalá-la e usá-la.</span><span class="sxs-lookup"><span data-stu-id="7845c-207">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="7845c-208">Para saber como, siga um tutorial do NuGet:</span><span class="sxs-lookup"><span data-stu-id="7845c-208">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7845c-209">Instalar e usar um pacote no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7845c-209">Install and use a package in Visual Studio</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

<span data-ttu-id="7845c-210">Uma biblioteca não precisa ser distribuída como um pacote.</span><span class="sxs-lookup"><span data-stu-id="7845c-210">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="7845c-211">Ele pode ser agrupado com um aplicativo de console que o utiliza.</span><span class="sxs-lookup"><span data-stu-id="7845c-211">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="7845c-212">Para saber como publicar um aplicativo de console, consulte o tutorial anterior nesta série:</span><span class="sxs-lookup"><span data-stu-id="7845c-212">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7845c-213">Publicar um aplicativo de console do .NET Core com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7845c-213">Publish a .NET Core console application with Visual Studio</span></span>](publishing-with-visual-studio.md)
