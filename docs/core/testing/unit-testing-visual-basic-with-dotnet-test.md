---
title: Teste de unidade do Visual Basic no .NET Core com dotnet test e xUnit
description: Aprenda os conceitos de teste de unidade no .NET Core por meio de uma experiência interativa de criação passo a passo de uma solução de exemplo do Visual Basic usando dotnet test e xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 05/18/2020
ms.openlocfilehash: d87550d692e0b7f3bfee1633bd00cbf501cc2e67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502750"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="88831-103">Bibliotecas do .NET Core no Visual Basic de teste de unidade usando dotnet test e xUnit</span><span class="sxs-lookup"><span data-stu-id="88831-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="88831-104">Este tutorial mostra como criar uma solução que contém um projeto de teste de unidade e um projeto de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="88831-104">This tutorial shows how to build a solution containing a unit test project and library project.</span></span> <span data-ttu-id="88831-105">Para seguir o tutorial usando uma solução predefinida, [exiba ou baixe o código de exemplo](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span><span class="sxs-lookup"><span data-stu-id="88831-105">To follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span></span> <span data-ttu-id="88831-106">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="88831-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="88831-107">Criar a solução</span><span class="sxs-lookup"><span data-stu-id="88831-107">Create the solution</span></span>

<span data-ttu-id="88831-108">Nesta seção, é criada uma solução que contém os projetos de origem e de teste.</span><span class="sxs-lookup"><span data-stu-id="88831-108">In this section, a solution is created that contains the source and test projects.</span></span> <span data-ttu-id="88831-109">A solução concluída tem a seguinte estrutura de diretório:</span><span class="sxs-lookup"><span data-stu-id="88831-109">The completed solution has the following directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.vb
        PrimeService.vbproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.vb
        PrimeServiceTests.vbproj
```

<span data-ttu-id="88831-110">As instruções a seguir fornecem as etapas para criar a solução de teste.</span><span class="sxs-lookup"><span data-stu-id="88831-110">The following instructions provide the steps to create the test solution.</span></span> <span data-ttu-id="88831-111">Consulte [comandos para criar solução de teste](#create-test-cmd) para obter instruções para criar a solução de teste em uma única etapa.</span><span class="sxs-lookup"><span data-stu-id="88831-111">See [Commands to create test solution](#create-test-cmd) for instructions to create the test solution in one step.</span></span>

* <span data-ttu-id="88831-112">Abra uma janela do shell.</span><span class="sxs-lookup"><span data-stu-id="88831-112">Open a shell window.</span></span>
* <span data-ttu-id="88831-113">Execute o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="88831-113">Run the following command:</span></span>

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  <span data-ttu-id="88831-114">O [`dotnet new sln`](../tools/dotnet-new.md) comando cria uma nova solução no diretório *Unit-Testing-using-dotnet-Test* .</span><span class="sxs-lookup"><span data-stu-id="88831-114">The [`dotnet new sln`](../tools/dotnet-new.md) command creates a new solution in the *unit-testing-using-dotnet-test* directory.</span></span>
* <span data-ttu-id="88831-115">Altere o diretório para a pasta *Unit-Testing-using-dotnet-Test* .</span><span class="sxs-lookup"><span data-stu-id="88831-115">Change directory to the *unit-testing-using-dotnet-test* folder.</span></span>
* <span data-ttu-id="88831-116">Execute o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="88831-116">Run the following command:</span></span>

  ```dotnetcli
  dotnet new classlib -o PrimeService --lang VB
  ```

   <span data-ttu-id="88831-117">O [`dotnet new classlib`](../tools/dotnet-new.md) comando cria um novo projeto de biblioteca de classes na pasta *PrimeService* .</span><span class="sxs-lookup"><span data-stu-id="88831-117">The [`dotnet new classlib`](../tools/dotnet-new.md) command creates a new class library project  in the *PrimeService* folder.</span></span> <span data-ttu-id="88831-118">A nova biblioteca de classes conterá o código a ser testado.</span><span class="sxs-lookup"><span data-stu-id="88831-118">The new class library will contain the code to be tested.</span></span>
* <span data-ttu-id="88831-119">Renomeie *Class1. vb* para *PrimeService. vb*.</span><span class="sxs-lookup"><span data-stu-id="88831-119">Rename *Class1.vb* to *PrimeService.vb*.</span></span>
* <span data-ttu-id="88831-120">Substitua o código em *PrimeService. vb* pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="88831-120">Replace the code in *PrimeService.vb* with the following code:</span></span>
  
  ```vb
  Imports System
  
  Namespace Prime.Services
      Public Class PrimeService
          Public Function IsPrime(candidate As Integer) As Boolean
              Throw New NotImplementedException("Not implemented.")
          End Function
      End Class
  End Namespace
  ```

* <span data-ttu-id="88831-121">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="88831-121">The preceding code:</span></span>
  * <span data-ttu-id="88831-122">Gera um <xref:System.NotImplementedException> com uma mensagem indicando que não está implementado.</span><span class="sxs-lookup"><span data-stu-id="88831-122">Throws a <xref:System.NotImplementedException> with a message indicating it's not implemented.</span></span>
  * <span data-ttu-id="88831-123">Será atualizado posteriormente no tutorial.</span><span class="sxs-lookup"><span data-stu-id="88831-123">Is updated later in the tutorial.</span></span>

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* <span data-ttu-id="88831-124">No diretório *Unit-Testing-using-dotnet-Test* , execute o seguinte comando para adicionar o projeto de biblioteca de classes à solução:</span><span class="sxs-lookup"><span data-stu-id="88831-124">In the *unit-testing-using-dotnet-test* directory, run the following command to add the class library project to the solution:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.vbproj
  ```

* <span data-ttu-id="88831-125">Crie o projeto *PrimeService. Tests* executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="88831-125">Create the *PrimeService.Tests* project by running the following command:</span></span>

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* <span data-ttu-id="88831-126">O comando anterior:</span><span class="sxs-lookup"><span data-stu-id="88831-126">The preceding command:</span></span>
  * <span data-ttu-id="88831-127">Cria o projeto *PrimeService. Tests* no diretório *PrimeService. Tests* .</span><span class="sxs-lookup"><span data-stu-id="88831-127">Creates the *PrimeService.Tests* project in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="88831-128">O projeto de teste usa [xUnit](https://xunit.net/) como a biblioteca de teste.</span><span class="sxs-lookup"><span data-stu-id="88831-128">The test project uses [xUnit](https://xunit.net/) as the test library.</span></span>
  * <span data-ttu-id="88831-129">Configura o executor de teste adicionando os seguintes `<PackageReference />` elementos ao arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="88831-129">Configures the test runner by adding the following `<PackageReference />`elements to the project file:</span></span>
    * <span data-ttu-id="88831-130">"Microsoft. NET. Test. SDK"</span><span class="sxs-lookup"><span data-stu-id="88831-130">"Microsoft.NET.Test.Sdk"</span></span>
    * <span data-ttu-id="88831-131">xUnit</span><span class="sxs-lookup"><span data-stu-id="88831-131">"xunit"</span></span>
    * <span data-ttu-id="88831-132">"xUnit. Runner. VisualStudio"</span><span class="sxs-lookup"><span data-stu-id="88831-132">"xunit.runner.visualstudio"</span></span>

* <span data-ttu-id="88831-133">Adicione o projeto de teste ao arquivo de solução executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="88831-133">Add the test project to the solution file by running the following command:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
  ```

* <span data-ttu-id="88831-134">Adicione a `PrimeService` biblioteca de classes como uma dependência ao projeto *PrimeService. Tests* :</span><span class="sxs-lookup"><span data-stu-id="88831-134">Add the `PrimeService` class library as a dependency to the *PrimeService.Tests* project:</span></span>

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a><span data-ttu-id="88831-135">Comandos para criar a solução</span><span class="sxs-lookup"><span data-stu-id="88831-135">Commands to create the solution</span></span>

<span data-ttu-id="88831-136">Esta seção resume todos os comandos na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="88831-136">This section summarizes all the commands in the previous section.</span></span> <span data-ttu-id="88831-137">Ignore esta seção se você tiver concluído as etapas na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="88831-137">Skip this section if you've completed the steps in the previous section.</span></span>

<span data-ttu-id="88831-138">Os comandos a seguir criam a solução de teste em um computador Windows.</span><span class="sxs-lookup"><span data-stu-id="88831-138">The following commands create the test solution on a windows machine.</span></span> <span data-ttu-id="88831-139">Para macOS e UNIX, atualize o `ren` comando para a versão do sistema operacional do `ren` para renomear um arquivo:</span><span class="sxs-lookup"><span data-stu-id="88831-139">For macOS and Unix, update the `ren` command to the OS version of `ren` to rename a file:</span></span>

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.vb PrimeService.vb
dotnet sln add ./PrimeService/PrimeService.vbproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
```

<span data-ttu-id="88831-140">Siga as instruções para "substituir o código em *PrimeService. vb* pelo código a seguir" na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="88831-140">Follow the instructions for "Replace the code in *PrimeService.vb* with the following code" in the previous section.</span></span>

## <a name="create-a-test"></a><span data-ttu-id="88831-141">Criar um teste</span><span class="sxs-lookup"><span data-stu-id="88831-141">Create a test</span></span>

<span data-ttu-id="88831-142">Uma abordagem popular no TDD (desenvolvimento controlado por teste) é escrever um teste antes de implementar o código de destino.</span><span class="sxs-lookup"><span data-stu-id="88831-142">A popular approach in test driven development (TDD) is to write a test before implementing the target code.</span></span> <span data-ttu-id="88831-143">Este tutorial usa a abordagem TDD.</span><span class="sxs-lookup"><span data-stu-id="88831-143">This tutorial uses the TDD approach.</span></span> <span data-ttu-id="88831-144">O `IsPrime` método é chamável, mas não implementado.</span><span class="sxs-lookup"><span data-stu-id="88831-144">The `IsPrime` method is callable, but not implemented.</span></span> <span data-ttu-id="88831-145">Uma chamada de teste para `IsPrime` falha.</span><span class="sxs-lookup"><span data-stu-id="88831-145">A test call to `IsPrime` fails.</span></span> <span data-ttu-id="88831-146">Com o TDD, um teste é escrito que é conhecido como falha.</span><span class="sxs-lookup"><span data-stu-id="88831-146">With TDD, a test is written that is known to fail.</span></span> <span data-ttu-id="88831-147">O código de destino é atualizado para fazer o teste passar.</span><span class="sxs-lookup"><span data-stu-id="88831-147">The target code is updated to make the test pass.</span></span> <span data-ttu-id="88831-148">Você continua repetindo essa abordagem, escrevendo um teste com falha e, em seguida, atualizando o código de destino para passar.</span><span class="sxs-lookup"><span data-stu-id="88831-148">You keep repeating this approach, writing a failing test and then updating the target code to pass.</span></span>

<span data-ttu-id="88831-149">Atualize o projeto *PrimeService. Tests* :</span><span class="sxs-lookup"><span data-stu-id="88831-149">Update the *PrimeService.Tests* project:</span></span>

* <span data-ttu-id="88831-150">Exclua *PrimeService. Tests/UnitTest1. vb*.</span><span class="sxs-lookup"><span data-stu-id="88831-150">Delete *PrimeService.Tests/UnitTest1.vb*.</span></span>
* <span data-ttu-id="88831-151">Crie um arquivo *PrimeService. Tests/PrimeService_IsPrimeShould. vb* .</span><span class="sxs-lookup"><span data-stu-id="88831-151">Create a *PrimeService.Tests/PrimeService_IsPrimeShould.vb*  file.</span></span>
* <span data-ttu-id="88831-152">Substitua o código em *PrimeService_IsPrimeShould. vb* pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="88831-152">Replace the code in *PrimeService_IsPrimeShould.vb* with the following code:</span></span>

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private ReadOnly _primeService As Prime.Services.PrimeService

        Public Sub New()
            _primeService = New Prime.Services.PrimeService()
        End Sub


        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="88831-153">O `[Fact]` atributo declara um método de teste que é executado pelo executor de teste.</span><span class="sxs-lookup"><span data-stu-id="88831-153">The `[Fact]` attribute declares a test method that's run by the test runner.</span></span> <span data-ttu-id="88831-154">Na pasta *PrimeService. Tests* , execute `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="88831-154">From the *PrimeService.Tests* folder, run `dotnet test`.</span></span> <span data-ttu-id="88831-155">O comando [dotnet Test](../tools/dotnet-test.md) compila ambos os projetos e executa os testes.</span><span class="sxs-lookup"><span data-stu-id="88831-155">The [dotnet test](../tools/dotnet-test.md) command builds both projects and runs the tests.</span></span> <span data-ttu-id="88831-156">O executor de teste do xUnit contém o ponto de entrada do programa para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="88831-156">The xUnit test runner contains the program entry point to run the tests.</span></span> <span data-ttu-id="88831-157">`dotnet test`inicia o executor de teste usando o projeto de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="88831-157">`dotnet test` starts the test runner using the unit test project.</span></span>

<span data-ttu-id="88831-158">O teste falha porque não `IsPrime` foi implementado.</span><span class="sxs-lookup"><span data-stu-id="88831-158">The test fails because `IsPrime` hasn't been implemented.</span></span> <span data-ttu-id="88831-159">Usando a abordagem TDD, escreva apenas código suficiente para que esse teste passe.</span><span class="sxs-lookup"><span data-stu-id="88831-159">Using the TDD approach, write only enough code so this test passes.</span></span> <span data-ttu-id="88831-160">Atualize `IsPrime` com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="88831-160">Update `IsPrime` with the following code:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Not implemented.")
End Function
```

<span data-ttu-id="88831-161">Execute `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="88831-161">Run `dotnet test`.</span></span> <span data-ttu-id="88831-162">O teste é aprovado.</span><span class="sxs-lookup"><span data-stu-id="88831-162">The test passes.</span></span>

### <a name="add-more-tests"></a><span data-ttu-id="88831-163">Adicionar mais testes</span><span class="sxs-lookup"><span data-stu-id="88831-163">Add more tests</span></span>

<span data-ttu-id="88831-164">Adicionar testes de número primo para 0 e-1.</span><span class="sxs-lookup"><span data-stu-id="88831-164">Add prime number tests for 0 and -1.</span></span> <span data-ttu-id="88831-165">Você pode copiar o teste anterior e alterar o código a seguir para usar 0 e-1:</span><span class="sxs-lookup"><span data-stu-id="88831-165">You could copy the preceding test and change the following code to use 0 and -1:</span></span>

```vb
Dim result As Boolean = _primeService.IsPrime(1)

Assert.False(result, "1 should not be prime")
```

<span data-ttu-id="88831-166">Copiar o código de teste quando apenas um parâmetro altera os resultados na duplicação de código e no inchar de teste.</span><span class="sxs-lookup"><span data-stu-id="88831-166">Copying test code when only a parameter changes results in code duplication and test bloat.</span></span> <span data-ttu-id="88831-167">Os seguintes atributos xUnit permitem escrever um conjunto de testes semelhantes:</span><span class="sxs-lookup"><span data-stu-id="88831-167">The following xUnit attributes enable writing a suite of similar tests:</span></span>

- <span data-ttu-id="88831-168">O `[Theory]` representa um pacote de testes que executa o mesmo código, mas têm diferentes argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="88831-168">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>
- <span data-ttu-id="88831-169">O atributo `[InlineData]` especifica valores para essas entradas.</span><span class="sxs-lookup"><span data-stu-id="88831-169">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="88831-170">Em vez de criar novos testes, aplique os atributos xUnit anteriores para criar uma única teoria.</span><span class="sxs-lookup"><span data-stu-id="88831-170">Rather than creating new tests, apply the preceding xUnit attributes to create a single theory.</span></span> <span data-ttu-id="88831-171">Substitua o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="88831-171">Replace the following code:</span></span>

```vb
<Fact>
Sub IsPrime_InputIs1_ReturnFalse()
    Dim result As Boolean = _primeService.IsPrime(1)

    Assert.False(result, "1 should not be prime")
End Sub
```

<span data-ttu-id="88831-172">pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="88831-172">with the following code:</span></span>

```vb
<Theory>
<InlineData(-1)>
<InlineData(0)>
<InlineData(1)>
Sub IsPrime_ValuesLessThan2_ReturnFalse(ByVal value As Integer)
    Dim result As Boolean = _primeService.IsPrime(value)

    Assert.False(result, $"{value} should not be prime")
End Sub
```

<span data-ttu-id="88831-173">No código anterior, `[Theory]` e `[InlineData]` habilite o teste de vários valores menores que dois.</span><span class="sxs-lookup"><span data-stu-id="88831-173">In the preceding code, `[Theory]` and `[InlineData]` enable testing several values less than two.</span></span> <span data-ttu-id="88831-174">Dois é o menor número de primo.</span><span class="sxs-lookup"><span data-stu-id="88831-174">Two is the smallest prime number.</span></span>

<span data-ttu-id="88831-175">Executar `dotnet test` , dois dos testes falham.</span><span class="sxs-lookup"><span data-stu-id="88831-175">Run `dotnet test`, two of the tests fail.</span></span> <span data-ttu-id="88831-176">Para fazer todos os testes serem aprovados, atualize o `IsPrime` método com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="88831-176">To make all of the tests pass, update the `IsPrime` method with the following code:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate < 2 Then
        Return False
    End If
    Throw New NotImplementedException("Not fully implemented.")
End Function
```

<span data-ttu-id="88831-177">Após a abordagem TDD, adicione mais testes com falha e, em seguida, atualize o código de destino.</span><span class="sxs-lookup"><span data-stu-id="88831-177">Following the TDD approach, add more failing tests, then update the target code.</span></span> <span data-ttu-id="88831-178">Consulte a [versão concluída dos testes](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) e a [implementação completa da biblioteca](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="88831-178">See the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="88831-179">O `IsPrime` método concluído não é um algoritmo eficiente para testar primality.</span><span class="sxs-lookup"><span data-stu-id="88831-179">The completed `IsPrime` method is not an efficient algorithm for testing primality.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="88831-180">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="88831-180">Additional resources</span></span>

- [<span data-ttu-id="88831-181">Site oficial do xUnit.net</span><span class="sxs-lookup"><span data-stu-id="88831-181">xUnit.net official site</span></span>](https://xunit.net/)
- [<span data-ttu-id="88831-182">Lógica do controlador de teste no ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="88831-182">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
