---
title: Testar um .NET Standard biblioteca de classes com o .NET Core usando Visual Studio Code
description: Crie um projeto de teste de unidade para uma biblioteca de classes do .NET Core. Verifique se uma biblioteca de classes do .NET Core funciona corretamente com testes de unidade.
ms.date: 06/08/2020
ms.openlocfilehash: b5f394b5dea2bf0b4af6e8b119df3fa0ec113dd3
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811711"
---
# <a name="tutorial-test-a-net-standard-class-library-with-net-core-using-visual-studio-code"></a><span data-ttu-id="deba6-104">Tutorial: testar uma biblioteca de classes .NET Standard com o .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="deba6-104">Tutorial: Test a .NET Standard class library with .NET Core using Visual Studio Code</span></span>

<span data-ttu-id="deba6-105">Este tutorial mostra como automatizar o teste de unidade adicionando um projeto de teste a uma solução.</span><span class="sxs-lookup"><span data-stu-id="deba6-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="deba6-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="deba6-106">Prerequisites</span></span>

- <span data-ttu-id="deba6-107">Este tutorial funciona com a solução que você cria em [criar uma .net Standard biblioteca no Visual Studio Code](library-with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="deba6-107">This tutorial works with the solution that you create in [Create a .NET Standard library in Visual Studio Code](library-with-visual-studio-code.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="deba6-108">Crie um projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="deba6-108">Create a unit test project</span></span>

<span data-ttu-id="deba6-109">As unidade de teste fornecem testes de software automatizados durante o desenvolvimento e a publicação.</span><span class="sxs-lookup"><span data-stu-id="deba6-109">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="deba6-110">A estrutura de teste que você usa neste tutorial é MSTest.</span><span class="sxs-lookup"><span data-stu-id="deba6-110">The testing framework that you use in this tutorial is MSTest.</span></span> <span data-ttu-id="deba6-111">[MSTest](https://github.com/Microsoft/testfx-docs) é uma das três estruturas de teste que você pode escolher.</span><span class="sxs-lookup"><span data-stu-id="deba6-111">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="deba6-112">Os outros são [xUnit](https://xunit.net/) e [NUnit](https://nunit.org/).</span><span class="sxs-lookup"><span data-stu-id="deba6-112">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="deba6-113">Iniciar o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="deba6-113">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="deba6-114">Abra a `ClassLibraryProjects` solução que você criou em [criar uma .net Standard biblioteca no Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="deba6-114">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="deba6-115">Crie um projeto de teste de unidade chamado "StringLibraryTest".</span><span class="sxs-lookup"><span data-stu-id="deba6-115">Create a unit test project named "StringLibraryTest".</span></span>

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   <span data-ttu-id="deba6-116">O modelo de projeto cria um arquivo UnitTest1.cs com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="deba6-116">The project template creates a UnitTest1.cs file with the following code:</span></span>

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

   <span data-ttu-id="deba6-117">O código-fonte criado pelo modelo de teste de unidade faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="deba6-117">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="deba6-118">Ele importa o namespace <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, que contém os tipos usados para o teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="deba6-118">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="deba6-119">Ele aplica o atributo<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> à classe `UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="deba6-119">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="deba6-120">Ele aplica o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributo a ser definido `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="deba6-120">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1`.</span></span>

   <span data-ttu-id="deba6-121">Cada método marcado com [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) em uma classe de teste marcada com [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) é executado automaticamente quando o teste de unidade é executado.</span><span class="sxs-lookup"><span data-stu-id="deba6-121">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

1. <span data-ttu-id="deba6-122">Adicione o projeto de teste à solução.</span><span class="sxs-lookup"><span data-stu-id="deba6-122">Add the test project to the solution.</span></span>

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

## <a name="add-a-project-reference"></a><span data-ttu-id="deba6-123">Adicionar uma referência ao projeto</span><span class="sxs-lookup"><span data-stu-id="deba6-123">Add a project reference</span></span>

<span data-ttu-id="deba6-124">Para que o projeto de teste funcione com a `StringLibrary` classe, adicione uma referência no `StringLibraryTest` projeto ao `StringLibrary` projeto.</span><span class="sxs-lookup"><span data-stu-id="deba6-124">For the test project to work with the `StringLibrary` class, add a reference in the `StringLibraryTest` project to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="deba6-125">Execute o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="deba6-125">Run the following command:</span></span>

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="deba6-126">Adicionar e executar métodos de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="deba6-126">Add and run unit test methods</span></span>

<span data-ttu-id="deba6-127">Quando o Visual Studio executa um teste de unidade, ele executa cada método marcado com o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributo em uma classe marcada com o  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="deba6-127">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="deba6-128">Um método de teste termina quando a primeira falha é encontrada ou quando todos os testes contidos no método foram bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="deba6-128">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="deba6-129">Os testes mais comuns chamam membros da classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>.</span><span class="sxs-lookup"><span data-stu-id="deba6-129">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="deba6-130">Muitos métodos assert incluem pelo menos dois parâmetros, um deles é o resultado esperado do teste, e o outro é o resultado real do teste.</span><span class="sxs-lookup"><span data-stu-id="deba6-130">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="deba6-131">Alguns dos `Assert` métodos chamados mais frequentemente da classe são mostrados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="deba6-131">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="deba6-132">Métodos assert</span><span class="sxs-lookup"><span data-stu-id="deba6-132">Assert methods</span></span>     | <span data-ttu-id="deba6-133">Função</span><span class="sxs-lookup"><span data-stu-id="deba6-133">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="deba6-134">Verifica se os dois valores ou objetos são iguais.</span><span class="sxs-lookup"><span data-stu-id="deba6-134">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="deba6-135">A declaração falhará se os valores ou objetos não forem iguais.</span><span class="sxs-lookup"><span data-stu-id="deba6-135">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="deba6-136">Verifica se duas variáveis de objeto se referem ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="deba6-136">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="deba6-137">A assert falhará se as variáveis se referirem a objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="deba6-137">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="deba6-138">Verifica se uma condição é `false`.</span><span class="sxs-lookup"><span data-stu-id="deba6-138">Verifies that a condition is `false`.</span></span> <span data-ttu-id="deba6-139">O assert falhará se a condição for `true`.</span><span class="sxs-lookup"><span data-stu-id="deba6-139">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="deba6-140">Verifica se um objeto não está `null` .</span><span class="sxs-lookup"><span data-stu-id="deba6-140">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="deba6-141">A assert falhará se o objeto for `null`.</span><span class="sxs-lookup"><span data-stu-id="deba6-141">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="deba6-142">Você também pode usar o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> método em um método de teste para indicar o tipo de exceção que ele deve lançar.</span><span class="sxs-lookup"><span data-stu-id="deba6-142">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="deba6-143">O teste falhará se a exceção especificada não for lançada.</span><span class="sxs-lookup"><span data-stu-id="deba6-143">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="deba6-144">Ao testar o método `StringLibrary.StartsWithUpper`, você quer fornecer um número de cadeias de caracteres que comecem com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="deba6-144">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="deba6-145">Você espera que o método retorne `true` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="deba6-145">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="deba6-146">Da mesma forma, você deseja fornecer um número de cadeias de caracteres que comecem com algo diferente de um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="deba6-146">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="deba6-147">Você espera que o método retorne `false` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="deba6-147">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="deba6-148">Como o método de biblioteca lida com cadeias de caracteres, você também deseja certificar-se de que ele manipula com êxito uma [cadeia de caracteres vazia ( `String.Empty` )](xref:System.String.Empty) e uma `null` cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="deba6-148">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty) and a and a `null` string.</span></span> <span data-ttu-id="deba6-149">Uma cadeia de caracteres vazia é aquela que não tem caracteres e cujo número <xref:System.String.Length> é 0.</span><span class="sxs-lookup"><span data-stu-id="deba6-149">An empty string is one that has no characters and whose <xref:System.String.Length> is 0.</span></span> <span data-ttu-id="deba6-150">Uma `null` cadeia de caracteres é aquela que não foi inicializada.</span><span class="sxs-lookup"><span data-stu-id="deba6-150">A `null` string is one that hasn't been initialized.</span></span> <span data-ttu-id="deba6-151">Você pode chamar `StartsWithUpper` diretamente como um método estático e passar um único <xref:System.String> argumento.</span><span class="sxs-lookup"><span data-stu-id="deba6-151">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="deba6-152">Ou você pode chamar `StartsWithUpper` como um método de extensão em uma `string` variável atribuída a `null` .</span><span class="sxs-lookup"><span data-stu-id="deba6-152">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="deba6-153">Você definirá três métodos, cada um deles chamará um <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> método para cada elemento em uma matriz de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="deba6-153">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="deba6-154">Você chamará uma sobrecarga de método que permite especificar uma mensagem de erro a ser exibida em caso de falha de teste.</span><span class="sxs-lookup"><span data-stu-id="deba6-154">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="deba6-155">A mensagem identifica a cadeia de caracteres que causou a falha.</span><span class="sxs-lookup"><span data-stu-id="deba6-155">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="deba6-156">Para criar os métodos de teste:</span><span class="sxs-lookup"><span data-stu-id="deba6-156">To create the test methods:</span></span>

1. <span data-ttu-id="deba6-157">Abra *StringLibraryTest/UnitTest1. cs* e substitua todo o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="deba6-157">Open *StringLibraryTest/UnitTest1.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="deba6-158">O teste de caracteres maiúsculos no `TestStartsWithUpper` método inclui a letra maiúscula grega alfa (u + 0391) e a letra maiúscula cirílica em (u + 041C).</span><span class="sxs-lookup"><span data-stu-id="deba6-158">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="deba6-159">O teste de caracteres minúsculos no `TestDoesNotStartWithUpper` método inclui a letra grega pequena alfa (u + 03B1) e a letra cirílica minúscula Ghe (u + 0433).</span><span class="sxs-lookup"><span data-stu-id="deba6-159">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="deba6-160">Salve suas alterações.</span><span class="sxs-lookup"><span data-stu-id="deba6-160">Save your changes.</span></span>

1. <span data-ttu-id="deba6-161">Execute os testes:</span><span class="sxs-lookup"><span data-stu-id="deba6-161">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="deba6-162">A saída do terminal mostra que todos os testes passaram.</span><span class="sxs-lookup"><span data-stu-id="deba6-162">The terminal output shows that all tests passed.</span></span>

   ```output
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.

   Test Run Successful.
   Total tests: 3
        Passed: 3
   Total time: 5.1116 Seconds
   ```

## <a name="handle-test-failures"></a><span data-ttu-id="deba6-163">Lidar com falhas de teste</span><span class="sxs-lookup"><span data-stu-id="deba6-163">Handle test failures</span></span>

<span data-ttu-id="deba6-164">Se você estiver fazendo o TDD (desenvolvimento controlado por teste), você escreverá testes primeiro e eles falharão na primeira vez em que forem executados.</span><span class="sxs-lookup"><span data-stu-id="deba6-164">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="deba6-165">Em seguida, você adiciona código ao aplicativo que torna o teste com sucesso.</span><span class="sxs-lookup"><span data-stu-id="deba6-165">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="deba6-166">Para este tutorial, você criou o teste depois de gravar o código do aplicativo que ele valida, para que você não tenha visto o teste falhar.</span><span class="sxs-lookup"><span data-stu-id="deba6-166">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="deba6-167">Para validar que um teste falha quando você espera que ele falhe, adicione um valor inválido para a entrada de teste.</span><span class="sxs-lookup"><span data-stu-id="deba6-167">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="deba6-168">Modifique a matriz `words` no método `TestDoesNotStartWithUpper` para incluir a cadeia de caracteres “Error”.</span><span class="sxs-lookup"><span data-stu-id="deba6-168">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="deba6-169">Execute os testes:</span><span class="sxs-lookup"><span data-stu-id="deba6-169">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="deba6-170">A saída do terminal mostra que um teste falha e fornece uma mensagem de erro para o teste com falha: "Assert. IsFalse falhou.</span><span class="sxs-lookup"><span data-stu-id="deba6-170">The terminal output shows that one test fails, and it provides an error message for the failed test: "Assert.IsFalse failed.</span></span> <span data-ttu-id="deba6-171">Esperado para 'Error': false, real: True".</span><span class="sxs-lookup"><span data-stu-id="deba6-171">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="deba6-172">Devido à falha, nenhuma cadeia de caracteres na matriz após o "erro" foi testada.</span><span class="sxs-lookup"><span data-stu-id="deba6-172">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   ```output
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.
     X TestDoesNotStartWithUpper [283ms]
     Error Message:
      Assert.IsFalse failed. Expected for 'Error': false; Actual: True
     Stack Trace:
     at StringLibraryTest.UnitTest1.TestDoesNotStartWithUpper()
       in C:\Projects\ClassLibraryProjects\StringLibraryTest\UnitTest1.cs:line 33

   Test Run Failed.
   Total tests: 3
        Passed: 2
        Failed: 1
   Total time: 1.7825 Seconds
   ```

1. <span data-ttu-id="deba6-173">Remova a cadeia de caracteres "Error" que você adicionou na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="deba6-173">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="deba6-174">Execute novamente o teste e os testes são aprovados.</span><span class="sxs-lookup"><span data-stu-id="deba6-174">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="deba6-175">Testar a versão de lançamento da biblioteca</span><span class="sxs-lookup"><span data-stu-id="deba6-175">Test the Release version of the library</span></span>

<span data-ttu-id="deba6-176">Agora que todos os testes passaram durante a execução da compilação de depuração da biblioteca, execute o testa um tempo adicional em relação à compilação da versão da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="deba6-176">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="deba6-177">Vários fatores, incluindo as otimizações do compilador, podem produzir um comportamento diferente entre as compilações de Depuração e Lançamento.</span><span class="sxs-lookup"><span data-stu-id="deba6-177">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

1. <span data-ttu-id="deba6-178">Execute os testes com a configuração de Build de versão:</span><span class="sxs-lookup"><span data-stu-id="deba6-178">Run the tests with the Release build configuration:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   <span data-ttu-id="deba6-179">Os testes são aprovados.</span><span class="sxs-lookup"><span data-stu-id="deba6-179">The tests pass.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="deba6-180">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="deba6-180">Additional resources</span></span>

* [<span data-ttu-id="deba6-181">Teste de unidade no .NET Core e no .NET Standard</span><span class="sxs-lookup"><span data-stu-id="deba6-181">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="deba6-182">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="deba6-182">Next steps</span></span>

<span data-ttu-id="deba6-183">Neste tutorial, você testou uma unidade de biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="deba6-183">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="deba6-184">Você pode tornar a biblioteca disponível para outras pessoas publicando-a no [NuGet](https://nuget.org) como um pacote.</span><span class="sxs-lookup"><span data-stu-id="deba6-184">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="deba6-185">Para saber como, siga um tutorial do NuGet:</span><span class="sxs-lookup"><span data-stu-id="deba6-185">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="deba6-186">Criar e publicar um pacote usando a CLI dotnet</span><span class="sxs-lookup"><span data-stu-id="deba6-186">Create and publish a package using the dotnet CLI</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="deba6-187">Se você publicar uma biblioteca como um pacote NuGet, outras pessoas poderão instalá-la e usá-la.</span><span class="sxs-lookup"><span data-stu-id="deba6-187">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="deba6-188">Para saber como, siga um tutorial do NuGet:</span><span class="sxs-lookup"><span data-stu-id="deba6-188">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="deba6-189">Instalar e usar um pacote usando a CLI do dotnet</span><span class="sxs-lookup"><span data-stu-id="deba6-189">Install and use a package using the dotnet CLI</span></span>](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

<span data-ttu-id="deba6-190">Uma biblioteca não precisa ser distribuída como um pacote.</span><span class="sxs-lookup"><span data-stu-id="deba6-190">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="deba6-191">Ele pode ser agrupado com um aplicativo de console que o utiliza.</span><span class="sxs-lookup"><span data-stu-id="deba6-191">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="deba6-192">Para saber como publicar um aplicativo de console, consulte o tutorial anterior nesta série:</span><span class="sxs-lookup"><span data-stu-id="deba6-192">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="deba6-193">Publicar um aplicativo de console do .NET Core com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="deba6-193">Publish a .NET Core console application with Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
