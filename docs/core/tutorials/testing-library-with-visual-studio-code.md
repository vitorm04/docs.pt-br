---
title: Testar um .NET Standard biblioteca de classes com o .NET Core no Visual Studio Code
description: Crie um projeto de teste de unidade para uma biblioteca de classes do .NET Core. Verifique se uma biblioteca de classes do .NET Core funciona corretamente com testes de unidade.
ms.date: 05/29/2020
ms.openlocfilehash: be227453bd441028cc6ce348c00fad944140238f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292185"
---
# <a name="tutorial-test-a-net-standard-library-with-net-core-in-visual-studio-code"></a><span data-ttu-id="b7ee4-104">Tutorial: testar uma biblioteca de .NET Standard com o .NET Core no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b7ee4-104">Tutorial: Test a .NET Standard library with .NET Core in Visual Studio Code</span></span>

<span data-ttu-id="b7ee4-105">Este tutorial mostra como automatizar o teste de unidade adicionando um projeto de teste a uma solução.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b7ee4-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b7ee4-106">Prerequisites</span></span>

- <span data-ttu-id="b7ee4-107">Este tutorial funciona com a solução que você cria em [criar uma .net Standard biblioteca no Visual Studio Code](library-with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="b7ee4-107">This tutorial works with the solution that you create in [Create a .NET Standard library in Visual Studio Code](library-with-visual-studio-code.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="b7ee4-108">Crie um projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="b7ee4-108">Create a unit test project</span></span>

1. <span data-ttu-id="b7ee4-109">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-109">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="b7ee4-110">Abra a `ClassLibraryProjects` solução que você criou em [criar uma .net Standard biblioteca no Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="b7ee4-110">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="b7ee4-111">Crie um projeto de teste de unidade chamado "StringLibraryTest".</span><span class="sxs-lookup"><span data-stu-id="b7ee4-111">Create a unit test project named "StringLibraryTest".</span></span>

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   <span data-ttu-id="b7ee4-112">O modelo de projeto cria um arquivo UnitTest1.cs com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="b7ee4-112">The project template creates a UnitTest1.cs file with the following code:</span></span>

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

   <span data-ttu-id="b7ee4-113">O código-fonte criado pelo modelo de teste de unidade faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b7ee4-113">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="b7ee4-114">Ele importa o namespace <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, que contém os tipos usados para o teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-114">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="b7ee4-115">Ele aplica o atributo<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> à classe `UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-115">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="b7ee4-116">Ele aplica o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributo a ser definido `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="b7ee4-116">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1`.</span></span>

   <span data-ttu-id="b7ee4-117">Cada método marcado com [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) em uma classe de teste marcada com [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) é executado automaticamente quando o teste de unidade é executado.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-117">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

   > [!NOTE]
   > <span data-ttu-id="b7ee4-118">MSTest é uma das três estruturas de teste que você pode escolher.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-118">MSTest is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="b7ee4-119">Os outros são xUnit e nUnit.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-119">The others are xUnit and nUnit.</span></span>

1. <span data-ttu-id="b7ee4-120">Adicione o projeto de teste à solução.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-120">Add the test project to the solution.</span></span>

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

1. <span data-ttu-id="b7ee4-121">Crie uma referência de projeto para o projeto de biblioteca de classes executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b7ee4-121">Create a project reference to the class library project by running the following command:</span></span>

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="b7ee4-122">Adicionar e executar métodos de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="b7ee4-122">Add and run unit test methods</span></span>

<span data-ttu-id="b7ee4-123">Quando o Visual Studio executa um teste de unidade, ele executa cada método marcado com o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributo em uma classe marcada com o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-123">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="b7ee4-124">Um método de teste termina quando a primeira falha é encontrada ou quando todos os testes contidos no método foram bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-124">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="b7ee4-125">Os testes mais comuns chamam membros da classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-125">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="b7ee4-126">Muitos métodos assert incluem pelo menos dois parâmetros, um deles é o resultado esperado do teste, e o outro é o resultado real do teste.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-126">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="b7ee4-127">Alguns dos `Assert` métodos chamados mais frequentemente da classe são mostrados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="b7ee4-127">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="b7ee4-128">Métodos assert</span><span class="sxs-lookup"><span data-stu-id="b7ee4-128">Assert methods</span></span>     | <span data-ttu-id="b7ee4-129">Função</span><span class="sxs-lookup"><span data-stu-id="b7ee4-129">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="b7ee4-130">Verifica se os dois valores ou objetos são iguais.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-130">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="b7ee4-131">A declaração falhará se os valores ou objetos não forem iguais.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-131">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="b7ee4-132">Verifica se duas variáveis de objeto se referem ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-132">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="b7ee4-133">A assert falhará se as variáveis se referirem a objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-133">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="b7ee4-134">Verifica se uma condição é `false`.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-134">Verifies that a condition is `false`.</span></span> <span data-ttu-id="b7ee4-135">O assert falhará se a condição for `true`.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-135">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="b7ee4-136">Verifica se um objeto não está `null` .</span><span class="sxs-lookup"><span data-stu-id="b7ee4-136">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="b7ee4-137">A assert falhará se o objeto for `null`.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-137">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="b7ee4-138">Você também pode usar o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> método em um método de teste para indicar o tipo de exceção que ele deve lançar.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-138">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="b7ee4-139">O teste falhará se a exceção especificada não for lançada.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-139">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="b7ee4-140">Ao testar o método `StringLibrary.StartsWithUpper`, você quer fornecer um número de cadeias de caracteres que comecem com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-140">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="b7ee4-141">Você espera que o método retorne `true` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-141">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b7ee4-142">Da mesma forma, você deseja fornecer um número de cadeias de caracteres que comecem com algo diferente de um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-142">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="b7ee4-143">Você espera que o método retorne `false` nesses casos, para que possa chamar o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-143">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="b7ee4-144">Como o método de biblioteca lida com cadeias de caracteres, você também deseja certificar-se de que ele manipula com êxito uma [cadeia de caracteres vazia ( `String.Empty` )](xref:System.String.Empty) e uma `null` cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-144">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty) and a and a `null` string.</span></span> <span data-ttu-id="b7ee4-145">Uma cadeia de caracteres vazia é aquela que não tem caracteres e cujo número <xref:System.String.Length> é 0.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-145">An empty string is one that has no characters and whose <xref:System.String.Length> is 0.</span></span> <span data-ttu-id="b7ee4-146">Uma `null` cadeia de caracteres é aquela que não foi inicializada.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-146">A `null` string is one that hasn't been initialized.</span></span> <span data-ttu-id="b7ee4-147">Você pode chamar `StartsWithUpper` diretamente como um método estático e passar um único <xref:System.String> argumento.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-147">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="b7ee4-148">Ou você pode chamar `StartsWithUpper` como um método de extensão em uma `string` variável atribuída a `null` .</span><span class="sxs-lookup"><span data-stu-id="b7ee4-148">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="b7ee4-149">Você definirá três métodos, cada um deles chamará um <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> método repetidamente para cada elemento em uma matriz de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-149">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="b7ee4-150">Como o método de teste falha assim que encontra a primeira falha, você chamará uma sobrecarga de método que permite passar uma cadeia de caracteres que indica o valor da cadeia de caracteres usado na chamada do método.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-150">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="b7ee4-151">Para criar os métodos de teste:</span><span class="sxs-lookup"><span data-stu-id="b7ee4-151">To create the test methods:</span></span>

1. <span data-ttu-id="b7ee4-152">Abra *StringLibraryTest/UnitTest1. cs* e substitua todo o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-152">Open *StringLibraryTest/UnitTest1.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="b7ee4-153">O teste de caracteres maiúsculos no `TestStartsWithUpper` método inclui a letra maiúscula grega alfa (u + 0391) e a letra maiúscula cirílica em (u + 041C).</span><span class="sxs-lookup"><span data-stu-id="b7ee4-153">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="b7ee4-154">O teste de caracteres minúsculos no `TestDoesNotStartWithUpper` método inclui a letra grega pequena alfa (u + 03B1) e a letra cirílica minúscula Ghe (u + 0433).</span><span class="sxs-lookup"><span data-stu-id="b7ee4-154">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="b7ee4-155">Salve suas alterações.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-155">Save your changes.</span></span>

1. <span data-ttu-id="b7ee4-156">Execute os testes:</span><span class="sxs-lookup"><span data-stu-id="b7ee4-156">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="b7ee4-157">A saída do terminal mostra que todos os testes passaram.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-157">The terminal output shows that all tests passed.</span></span>

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.

   Test Run Successful.
   Total tests: 3
        Passed: 3
   Total time: 5.1116 Seconds
   ```

## <a name="handle-test-failures"></a><span data-ttu-id="b7ee4-158">Lidar com falhas de teste</span><span class="sxs-lookup"><span data-stu-id="b7ee4-158">Handle test failures</span></span>

<span data-ttu-id="b7ee4-159">Se você estiver fazendo o TDD (desenvolvimento controlado por teste), você escreverá testes primeiro e eles falharão na primeira vez em que forem executados.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-159">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="b7ee4-160">Em seguida, você adiciona código ao aplicativo que torna o teste com sucesso.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-160">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="b7ee4-161">Nesse caso, você criou o teste depois de gravar o código do aplicativo que ele valida, para que você não tenha visto o teste falhar.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-161">In this case, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="b7ee4-162">Para validar que um teste falha quando você espera que ele falhe, adicione um valor inválido para a entrada de teste.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-162">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="b7ee4-163">Modifique a matriz `words` no método `TestDoesNotStartWithUpper` para incluir a cadeia de caracteres “Error”.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-163">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="b7ee4-164">Execute os testes:</span><span class="sxs-lookup"><span data-stu-id="b7ee4-164">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="b7ee4-165">A saída do terminal mostra que um teste falha e fornece uma mensagem de erro para o teste com falha.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-165">The terminal output shows that one test fails, and it provides an error message for the failed test.</span></span>

   ```
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

1. <span data-ttu-id="b7ee4-166">Desfaça as modificações feitas na etapa 1 e remova a cadeia de caracteres "Error".</span><span class="sxs-lookup"><span data-stu-id="b7ee4-166">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="b7ee4-167">Execute novamente o teste e os testes são aprovados.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-167">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="b7ee4-168">Testar a versão de lançamento da biblioteca</span><span class="sxs-lookup"><span data-stu-id="b7ee4-168">Test the Release version of the library</span></span>

<span data-ttu-id="b7ee4-169">Agora que todos os testes passaram ao executar a versão de depuração da biblioteca, execute o testa um tempo adicional em relação à compilação da versão da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-169">Now that the tests have all passed when running the Debug version of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="b7ee4-170">Vários fatores, incluindo as otimizações do compilador, podem produzir um comportamento diferente entre as compilações de Depuração e Lançamento.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-170">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

1. <span data-ttu-id="b7ee4-171">Execute os testes com a configuração de Build de versão:</span><span class="sxs-lookup"><span data-stu-id="b7ee4-171">Run the tests with the Release build configuration:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   <span data-ttu-id="b7ee4-172">Os testes são aprovados.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-172">The tests pass.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b7ee4-173">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="b7ee4-173">Additional resources</span></span>

- [<span data-ttu-id="b7ee4-174">Teste de unidade no .NET Core e no .NET Standard</span><span class="sxs-lookup"><span data-stu-id="b7ee4-174">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="b7ee4-175">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="b7ee4-175">Next steps</span></span>

<span data-ttu-id="b7ee4-176">Neste tutorial, você testou uma unidade de biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-176">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="b7ee4-177">Você pode tornar a biblioteca disponível para outras pessoas publicando-a no [NuGet](https://nuget.org) como um pacote.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-177">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="b7ee4-178">Para saber como, siga um tutorial do NuGet:</span><span class="sxs-lookup"><span data-stu-id="b7ee4-178">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b7ee4-179">Criar e publicar um pacote usando a CLI dotnet</span><span class="sxs-lookup"><span data-stu-id="b7ee4-179">Create and publish a package using the dotnet CLI</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="b7ee4-180">Se você publicar uma biblioteca como um pacote NuGet, outras pessoas poderão instalá-la e usá-la.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-180">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="b7ee4-181">Para saber como, siga um tutorial do NuGet:</span><span class="sxs-lookup"><span data-stu-id="b7ee4-181">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b7ee4-182">Instalar e usar um pacote usando a CLI do dotnet</span><span class="sxs-lookup"><span data-stu-id="b7ee4-182">Install and use a package using the dotnet CLI</span></span>](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

<span data-ttu-id="b7ee4-183">Uma biblioteca não precisa ser distribuída como um pacote.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-183">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="b7ee4-184">Ele pode ser agrupado com um aplicativo de console que o utiliza.</span><span class="sxs-lookup"><span data-stu-id="b7ee4-184">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="b7ee4-185">Para saber como publicar um aplicativo de console, consulte o tutorial anterior nesta série:</span><span class="sxs-lookup"><span data-stu-id="b7ee4-185">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b7ee4-186">Publicar um aplicativo de console do .NET Core com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b7ee4-186">Publish a .NET Core console application with Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
