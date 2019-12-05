---
title: Código C# de teste de unidade no .NET Core usando dotnet test e xUnit
description: Aprenda os conceitos de teste de unidade no C# e .NET Core por meio de uma experiência interativa de criação passo a passo de uma solução de exemplo usando dotnet test e xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.custom: seodec18
ms.openlocfilehash: eee8ab675ecc66b842a1447e3f2de1b6b9765c4d
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801909"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="eafd5-103">C# de teste de unidade no .NET Core usando dotnet test e xUnit</span><span class="sxs-lookup"><span data-stu-id="eafd5-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="eafd5-104">Este tutorial mostra como criar uma solução que contém um projeto de teste de unidade e um projeto de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="eafd5-104">This tutorial shows how to build a solution containing a unit test project and source code project.</span></span> <span data-ttu-id="eafd5-105">Para seguir o tutorial usando uma solução predefinida, [exiba ou baixe o código de exemplo](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span><span class="sxs-lookup"><span data-stu-id="eafd5-105">To follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span></span> <span data-ttu-id="eafd5-106">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="eafd5-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="eafd5-107">Criar a solução</span><span class="sxs-lookup"><span data-stu-id="eafd5-107">Create the solution</span></span>

<span data-ttu-id="eafd5-108">Nesta seção, é criada uma solução que contém os projetos de origem e de teste.</span><span class="sxs-lookup"><span data-stu-id="eafd5-108">In this section, a solution is created that contains the source and test projects.</span></span> <span data-ttu-id="eafd5-109">A solução concluída tem a seguinte estrutura de diretório:</span><span class="sxs-lookup"><span data-stu-id="eafd5-109">The completed solution has the following directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.cs
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.cs
        PrimeServiceTests.csproj
```

<span data-ttu-id="eafd5-110">As instruções a seguir fornecem as etapas para criar a solução de teste.</span><span class="sxs-lookup"><span data-stu-id="eafd5-110">The following instructions provide the steps to create the test solution.</span></span> <span data-ttu-id="eafd5-111">Consulte [comandos para criar solução de teste](#create-test-cmd) para obter instruções para criar a solução de teste em uma única etapa.</span><span class="sxs-lookup"><span data-stu-id="eafd5-111">See [Commands to create test solution](#create-test-cmd) for instructions to create the test solution in one step.</span></span>

* <span data-ttu-id="eafd5-112">Abra uma janela do shell.</span><span class="sxs-lookup"><span data-stu-id="eafd5-112">Open a shell window.</span></span>
* <span data-ttu-id="eafd5-113">Execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="eafd5-113">Run the following command:</span></span>

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  <span data-ttu-id="eafd5-114">O comando [`dotnet new sln`](../tools/dotnet-new.md) cria uma nova solução no diretório *Unit-Testing-using-dotnet-Test* .</span><span class="sxs-lookup"><span data-stu-id="eafd5-114">The [`dotnet new sln`](../tools/dotnet-new.md) command creates a new solution in the *unit-testing-using-dotnet-test* directory.</span></span>
* <span data-ttu-id="eafd5-115">Altere o diretório para a pasta *Unit-Testing-using-dotnet-Test* .</span><span class="sxs-lookup"><span data-stu-id="eafd5-115">Change directory to the *unit-testing-using-dotnet-test* folder.</span></span>
* <span data-ttu-id="eafd5-116">Execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="eafd5-116">Run the following command:</span></span>

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   <span data-ttu-id="eafd5-117">O comando [`dotnet new classlib`](../tools/dotnet-new.md) cria um novo projeto de biblioteca de classes na pasta *PrimeService* .</span><span class="sxs-lookup"><span data-stu-id="eafd5-117">The [`dotnet new classlib`](../tools/dotnet-new.md) command creates a new class library project  in the *PrimeService* folder.</span></span> <span data-ttu-id="eafd5-118">A nova biblioteca de classes conterá o código a ser testado.</span><span class="sxs-lookup"><span data-stu-id="eafd5-118">The new class library will contain the code to be tested.</span></span>
* <span data-ttu-id="eafd5-119">Renomeie *Class1.cs* como *PrimeService.cs*.</span><span class="sxs-lookup"><span data-stu-id="eafd5-119">Rename *Class1.cs* to *PrimeService.cs*.</span></span>
* <span data-ttu-id="eafd5-120">Substitua o código em *PrimeService.cs* pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="eafd5-120">Replace the code in *PrimeService.cs* with the following code:</span></span>
  
  ```csharp
    using System;

    namespace Prime.Services
    {
        public class PrimeService
        {
            public bool IsPrime(int candidate)
            {
                throw new NotImplementedException("Not implemented.");
            }
        }
    }
  ```

* <span data-ttu-id="eafd5-121">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="eafd5-121">The preceding code:</span></span>
  * <span data-ttu-id="eafd5-122">Gera uma <xref:System.NotImplementedException> com uma mensagem indicando que ela não está implementada.</span><span class="sxs-lookup"><span data-stu-id="eafd5-122">Throws a <xref:System.NotImplementedException> with a message indicating it's not implemented.</span></span>
  * <span data-ttu-id="eafd5-123">Será atualizado posteriormente no tutorial.</span><span class="sxs-lookup"><span data-stu-id="eafd5-123">Is updated later in the tutorial.</span></span>

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* <span data-ttu-id="eafd5-124">No diretório *Unit-Testing-using-dotnet-Test* , execute o seguinte comando para adicionar o projeto de biblioteca de classes à solução:</span><span class="sxs-lookup"><span data-stu-id="eafd5-124">In the *unit-testing-using-dotnet-test* directory, run the following command to add the class library project to the solution:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* <span data-ttu-id="eafd5-125">Crie o projeto *PrimeService. Tests* executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="eafd5-125">Create the *PrimeService.Tests* project by running the following command:</span></span>

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* <span data-ttu-id="eafd5-126">O comando anterior:</span><span class="sxs-lookup"><span data-stu-id="eafd5-126">The preceding command:</span></span>
  * <span data-ttu-id="eafd5-127">Cria o projeto *PrimeService. Tests* no diretório *PrimeService. Tests* .</span><span class="sxs-lookup"><span data-stu-id="eafd5-127">Creates the *PrimeService.Tests* project in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="eafd5-128">O projeto de teste usa [xUnit](https://xunit.github.io/) como a biblioteca de teste.</span><span class="sxs-lookup"><span data-stu-id="eafd5-128">The test project uses [xUnit](https://xunit.github.io/) as the test library.</span></span>
  * <span data-ttu-id="eafd5-129">Configura o executor de teste adicionando os seguintes elementos de `<PackageReference />`ao arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="eafd5-129">Configures the test runner by adding the following `<PackageReference />`elements to the project file:</span></span>
    * <span data-ttu-id="eafd5-130">"Microsoft. NET. Test. SDK"</span><span class="sxs-lookup"><span data-stu-id="eafd5-130">"Microsoft.NET.Test.Sdk"</span></span>
    * <span data-ttu-id="eafd5-131">xUnit</span><span class="sxs-lookup"><span data-stu-id="eafd5-131">"xunit"</span></span>
    * <span data-ttu-id="eafd5-132">"xUnit. Runner. VisualStudio"</span><span class="sxs-lookup"><span data-stu-id="eafd5-132">"xunit.runner.visualstudio"</span></span>

* <span data-ttu-id="eafd5-133">Adicione o projeto de teste ao arquivo de solução executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="eafd5-133">Add the test project to the solution file by running the following command:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* <span data-ttu-id="eafd5-134">Adicione a biblioteca de classes `PrimeService` como uma dependência ao projeto *PrimeService. Tests* :</span><span class="sxs-lookup"><span data-stu-id="eafd5-134">Add the `PrimeService` class library as a dependency to the *PrimeService.Tests* project:</span></span>

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a><span data-ttu-id="eafd5-135">Comandos para criar a solução</span><span class="sxs-lookup"><span data-stu-id="eafd5-135">Commands to create the solution</span></span>

<span data-ttu-id="eafd5-136">Esta seção resume todos os comandos na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="eafd5-136">This section summarizes all the commands in the previous section.</span></span> <span data-ttu-id="eafd5-137">Ignore esta seção se você tiver concluído as etapas na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="eafd5-137">Skip this section if you've completed the steps in the previous section.</span></span>

<span data-ttu-id="eafd5-138">Os comandos a seguir criam a solução de teste em um computador Windows.</span><span class="sxs-lookup"><span data-stu-id="eafd5-138">The following commands create the test solution on a windows machine.</span></span> <span data-ttu-id="eafd5-139">Para macOS e UNIX, atualize o comando `ren` para a versão do sistema operacional de `ren` para renomear um arquivo:</span><span class="sxs-lookup"><span data-stu-id="eafd5-139">For macOS and Unix, update the `ren` command to the OS version of `ren` to rename a file:</span></span>

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.cs PrimeService.cs
dotnet sln add ./PrimeService/PrimeService.csproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

<span data-ttu-id="eafd5-140">Siga as instruções para "substituir o código em *PrimeService.cs* com o código a seguir" na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="eafd5-140">Follow the instructions for "Replace the code in *PrimeService.cs* with the following code" in the previous section.</span></span>

## <a name="create-a-test"></a><span data-ttu-id="eafd5-141">Criar um teste</span><span class="sxs-lookup"><span data-stu-id="eafd5-141">Create a test</span></span>

<span data-ttu-id="eafd5-142">Uma abordagem popular no TDD (desenvolvimento controlado por teste) é escrever um teste antes de implementar o código de destino.</span><span class="sxs-lookup"><span data-stu-id="eafd5-142">A popular approach in test driven development (TDD) is to write a test before implementing the target code.</span></span> <span data-ttu-id="eafd5-143">Este tutorial usa a abordagem TDD.</span><span class="sxs-lookup"><span data-stu-id="eafd5-143">This tutorial uses the TDD approach.</span></span> <span data-ttu-id="eafd5-144">O método `IsPrime` é chamável, mas não implementado.</span><span class="sxs-lookup"><span data-stu-id="eafd5-144">The `IsPrime` method is callable, but not implemented.</span></span> <span data-ttu-id="eafd5-145">Uma chamada de teste para `IsPrime` falha.</span><span class="sxs-lookup"><span data-stu-id="eafd5-145">A test call to `IsPrime` fails.</span></span> <span data-ttu-id="eafd5-146">Com o TDD, um teste é escrito que é conhecido como falha.</span><span class="sxs-lookup"><span data-stu-id="eafd5-146">With TDD, a test is written that is known to fail.</span></span> <span data-ttu-id="eafd5-147">O código de destino é atualizado para fazer o teste passar.</span><span class="sxs-lookup"><span data-stu-id="eafd5-147">The target code is updated to make the test pass.</span></span> <span data-ttu-id="eafd5-148">Você continua repetindo essa abordagem, escrevendo um teste com falha e, em seguida, atualizando o código de destino para passar.</span><span class="sxs-lookup"><span data-stu-id="eafd5-148">You keep repeating this approach, writing a failing test and then updating the target code to pass.</span></span>

<span data-ttu-id="eafd5-149">Atualize o projeto *PrimeService. Tests* :</span><span class="sxs-lookup"><span data-stu-id="eafd5-149">Update the *PrimeService.Tests* project:</span></span>

* <span data-ttu-id="eafd5-150">Exclua *PrimeService. Tests/UnitTest1. cs*.</span><span class="sxs-lookup"><span data-stu-id="eafd5-150">Delete *PrimeService.Tests/UnitTest1.cs*.</span></span>
* <span data-ttu-id="eafd5-151">Crie um arquivo *PrimeService. Tests/PrimeService_IsPrimeShould. cs* .</span><span class="sxs-lookup"><span data-stu-id="eafd5-151">Create a *PrimeService.Tests/PrimeService_IsPrimeShould.cs*  file.</span></span>
* <span data-ttu-id="eafd5-152">Substitua o código em *PrimeService_IsPrimeShould. cs* pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="eafd5-152">Replace the code in *PrimeService_IsPrimeShould.cs* with the following code:</span></span>

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="eafd5-153">O atributo `[Fact]` declara um método de teste que é executado pelo executor de teste.</span><span class="sxs-lookup"><span data-stu-id="eafd5-153">The `[Fact]` attribute declares a test method that's run by the test runner.</span></span> <span data-ttu-id="eafd5-154">Na pasta *PrimeService. Tests* , execute `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="eafd5-154">From the *PrimeService.Tests* folder, run `dotnet test`.</span></span> <span data-ttu-id="eafd5-155">O comando [dotnet Test](../tools/dotnet-test.md) compila ambos os projetos e executa os testes.</span><span class="sxs-lookup"><span data-stu-id="eafd5-155">The [dotnet test](../tools/dotnet-test.md) command builds both projects and runs the tests.</span></span> <span data-ttu-id="eafd5-156">O executor de teste do xUnit contém o ponto de entrada do programa para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="eafd5-156">The xUnit test runner contains the program entry point to run the tests.</span></span> <span data-ttu-id="eafd5-157">`dotnet test` inicia o executor de teste usando o projeto de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="eafd5-157">`dotnet test` starts the test runner using the unit test project.</span></span>

<span data-ttu-id="eafd5-158">O teste falha porque `IsPrime` não foi implementado.</span><span class="sxs-lookup"><span data-stu-id="eafd5-158">The test fails because `IsPrime` hasn't been implemented.</span></span> <span data-ttu-id="eafd5-159">Usando a abordagem TDD, escreva apenas código suficiente para que esse teste passe.</span><span class="sxs-lookup"><span data-stu-id="eafd5-159">Using the TDD approach, write only enough code so this test passes.</span></span> <span data-ttu-id="eafd5-160">Atualize `IsPrime` com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="eafd5-160">Update `IsPrime` with the following code:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

<span data-ttu-id="eafd5-161">Execute `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="eafd5-161">Run `dotnet test`.</span></span> <span data-ttu-id="eafd5-162">O teste é aprovado.</span><span class="sxs-lookup"><span data-stu-id="eafd5-162">The test passes.</span></span>

### <a name="add-more-tests"></a><span data-ttu-id="eafd5-163">Adicionar mais testes</span><span class="sxs-lookup"><span data-stu-id="eafd5-163">Add more tests</span></span>

<span data-ttu-id="eafd5-164">Adicionar testes de número primo para 0 e-1.</span><span class="sxs-lookup"><span data-stu-id="eafd5-164">Add prime number tests for 0 and -1.</span></span> <span data-ttu-id="eafd5-165">Você pode copiar o teste anterior e alterar o código a seguir para usar 0 e-1:</span><span class="sxs-lookup"><span data-stu-id="eafd5-165">You could copy the preceding test and change the following code to use 0 and -1:</span></span>

```csharp
var result = _primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

<span data-ttu-id="eafd5-166">Copiar o código de teste quando apenas um parâmetro altera os resultados na duplicação de código e no inchar de teste.</span><span class="sxs-lookup"><span data-stu-id="eafd5-166">Copying test code when only a parameter changes results in code duplication and test bloat.</span></span> <span data-ttu-id="eafd5-167">Os seguintes atributos xUnit permitem escrever um conjunto de testes semelhantes:</span><span class="sxs-lookup"><span data-stu-id="eafd5-167">The following xUnit attributes enable writing a suite of similar tests:</span></span>

- <span data-ttu-id="eafd5-168">O `[Theory]` representa um pacote de testes que executa o mesmo código, mas têm diferentes argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="eafd5-168">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>

- <span data-ttu-id="eafd5-169">O atributo `[InlineData]` especifica valores para essas entradas.</span><span class="sxs-lookup"><span data-stu-id="eafd5-169">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="eafd5-170">Em vez de criar novos testes, aplique os atributos xUnit anteriores para criar uma única teoria.</span><span class="sxs-lookup"><span data-stu-id="eafd5-170">Rather than creating new tests, apply the preceding xUnit attributes to create a single theory.</span></span> <span data-ttu-id="eafd5-171">Substitua o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="eafd5-171">Replace the following code:</span></span>

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var result = _primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

<span data-ttu-id="eafd5-172">pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="eafd5-172">with the following code:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="eafd5-173">No código anterior, `[Theory]` e `[InlineData]` permitem testar vários valores menores que dois.</span><span class="sxs-lookup"><span data-stu-id="eafd5-173">In the preceding code, `[Theory]` and `[InlineData]` enable testing several values less than two.</span></span> <span data-ttu-id="eafd5-174">Dois é o menor número de primo.</span><span class="sxs-lookup"><span data-stu-id="eafd5-174">Two is the smallest prime number.</span></span>

<span data-ttu-id="eafd5-175">Execute `dotnet test`, dois dos testes falham.</span><span class="sxs-lookup"><span data-stu-id="eafd5-175">Run `dotnet test`, two of the tests fail.</span></span> <span data-ttu-id="eafd5-176">Para fazer todos os testes serem aprovados, atualize o método `IsPrime` com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="eafd5-176">To make all of the tests pass, update the `IsPrime` method with the following code:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate < 2)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

<span data-ttu-id="eafd5-177">Após a abordagem TDD, adicione mais testes com falha e, em seguida, atualize o código de destino.</span><span class="sxs-lookup"><span data-stu-id="eafd5-177">Following the TDD approach, add more failing tests, then update the target code.</span></span> <span data-ttu-id="eafd5-178">Consulte a [versão concluída dos testes](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) e a [implementação completa da biblioteca](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span><span class="sxs-lookup"><span data-stu-id="eafd5-178">See the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="eafd5-179">O método `IsPrime` concluído não é um algoritmo eficiente para testar primality.</span><span class="sxs-lookup"><span data-stu-id="eafd5-179">The completed `IsPrime` method is not an efficient algorithm for testing primality.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="eafd5-180">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="eafd5-180">Additional resources</span></span>

- [<span data-ttu-id="eafd5-181">Site oficial do xUnit.net</span><span class="sxs-lookup"><span data-stu-id="eafd5-181">xUnit.net official site</span></span>](https://xunit.github.io)
- [<span data-ttu-id="eafd5-182">Lógica do controlador de teste no ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="eafd5-182">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
