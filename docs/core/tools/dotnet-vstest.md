---
title: Comando dotnet vstest
description: O comando dotnet vstest compila um projeto e todas as suas dependências.
ms.date: 05/30/2018
ms.openlocfilehash: fc0aa4f9abf069f78e27692ee84aea2559109c98
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626015"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="5cea5-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="5cea5-103">dotnet vstest</span></span>

<span data-ttu-id="5cea5-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="5cea5-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5cea5-105">{1&gt;Nome&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5cea5-105">Name</span></span>

<span data-ttu-id="5cea5-106">`dotnet-vstest` - Executa testes a partir de arquivos especificados.</span><span class="sxs-lookup"><span data-stu-id="5cea5-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5cea5-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="5cea5-107">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a><span data-ttu-id="5cea5-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="5cea5-108">Description</span></span>

<span data-ttu-id="5cea5-109">O comando `dotnet-vstest` executa o aplicativo de linha de comando `VSTest.Console` para executar testes automatizados de unidade.</span><span class="sxs-lookup"><span data-stu-id="5cea5-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="5cea5-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="5cea5-110">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="5cea5-111">Execute testes a partir de assemblies especificados.</span><span class="sxs-lookup"><span data-stu-id="5cea5-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="5cea5-112">Separe vários nomes de assembly de teste com espaços.</span><span class="sxs-lookup"><span data-stu-id="5cea5-112">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="5cea5-113">Há suporte para caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="5cea5-113">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="5cea5-114">{1&gt;Opções&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5cea5-114">Options</span></span>

- **`--Settings <Settings File>`**

  <span data-ttu-id="5cea5-115">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="5cea5-115">Settings to use when running tests.</span></span>

- **`--Tests <Test Names>`**

  <span data-ttu-id="5cea5-116">Execute testes com nomes que correspondam aos valores fornecidos.</span><span class="sxs-lookup"><span data-stu-id="5cea5-116">Run tests with names that match the provided values.</span></span> <span data-ttu-id="5cea5-117">Separe vários valores com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="5cea5-117">Separate multiple values with commas.</span></span>

- **`--TestAdapterPath`**

  <span data-ttu-id="5cea5-118">Use adaptadores de teste personalizados para um determinado caminho (se houver) na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="5cea5-118">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--Platform <Platform type>`**

  <span data-ttu-id="5cea5-119">Arquitetura da plataforma de destino usada para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="5cea5-119">Target platform architecture used for test execution.</span></span> <span data-ttu-id="5cea5-120">Os valores válidos são `x86`, `x64` e `ARM`.</span><span class="sxs-lookup"><span data-stu-id="5cea5-120">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Framework <Framework Version>`**

  <span data-ttu-id="5cea5-121">Versão do .NET Framework de destino usada na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="5cea5-121">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="5cea5-122">Alguns exemplos de valores válidos são `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="5cea5-122">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="5cea5-123">Outros valores com suporte são `Framework40`, `Framework45`, `FrameworkCore10` e `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="5cea5-123">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--Parallel`**

  <span data-ttu-id="5cea5-124">Execute testes em paralelo.</span><span class="sxs-lookup"><span data-stu-id="5cea5-124">Run tests in parallel.</span></span> <span data-ttu-id="5cea5-125">Por padrão, todos os núcleos disponíveis no computador estão disponíveis para uso.</span><span class="sxs-lookup"><span data-stu-id="5cea5-125">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="5cea5-126">Especifique um número explícito de núcleos definindo a propriedade `MaxCpuCount` sob o nó `RunConfiguration` no arquivo *RunSettings* .</span><span class="sxs-lookup"><span data-stu-id="5cea5-126">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--TestCaseFilter <Expression>`**

  <span data-ttu-id="5cea5-127">Execute testes que correspondam à expressão fornecida.</span><span class="sxs-lookup"><span data-stu-id="5cea5-127">Run tests that match the given expression.</span></span> <span data-ttu-id="5cea5-128">`<Expression>` está no formato `<property>Operator<value>[|&<Expression>]`, onde Operator pode ser `=`, `!=` ou `~`.</span><span class="sxs-lookup"><span data-stu-id="5cea5-128">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="5cea5-129">O operador `~` tem a semântica 'contains' e é aplicável para propriedades de cadeia de caracteres como `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="5cea5-129">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="5cea5-130">Os `()` de parênteses são usados para agrupar subexpressões.</span><span class="sxs-lookup"><span data-stu-id="5cea5-130">Parenthesis `()` are used to group subexpressions.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="5cea5-131">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="5cea5-131">Prints out a short help for the command.</span></span>

- **`--logger <Logger Uri/FriendlyName>`**

  <span data-ttu-id="5cea5-132">Especificar um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="5cea5-132">Specify a logger for test results.</span></span>

  - <span data-ttu-id="5cea5-133">Para publicar resultados do teste no Team Foundation Server, use o provedor de agente `TfsPublisher`:</span><span class="sxs-lookup"><span data-stu-id="5cea5-133">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="5cea5-134">Para registrar os resultados em um arquivo TRX (Resultados do teste) do Visual Studio, use o provedor de agente `trx`.</span><span class="sxs-lookup"><span data-stu-id="5cea5-134">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="5cea5-135">Essa opção cria um arquivo no diretório dos resultados do teste com o nome de arquivo de log determinado.</span><span class="sxs-lookup"><span data-stu-id="5cea5-135">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="5cea5-136">Se `LogFileName` não for fornecido, será criado um nome de arquivo exclusivo para armazenar os resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="5cea5-136">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`-lt|--ListTests <File Name>`**

  <span data-ttu-id="5cea5-137">Lista todos os testes descobertos do contêiner de teste fornecido.</span><span class="sxs-lookup"><span data-stu-id="5cea5-137">Lists all discovered tests from the given test container.</span></span>

- **`--ParentProcessId <ParentProcessId>`**

  <span data-ttu-id="5cea5-138">ID do processo pai responsável por iniciar o processo atual.</span><span class="sxs-lookup"><span data-stu-id="5cea5-138">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Port <Port>`**

  <span data-ttu-id="5cea5-139">Especifica a porta para a conexão de soquete e recebimento das mensagens do evento.</span><span class="sxs-lookup"><span data-stu-id="5cea5-139">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--Diag <Path to log file>`**

  <span data-ttu-id="5cea5-140">Permite logs detalhados na plataforma de teste.</span><span class="sxs-lookup"><span data-stu-id="5cea5-140">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="5cea5-141">Os logs são gravados no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="5cea5-141">Logs are written to the provided file.</span></span>

- **`--Blame`**

  <span data-ttu-id="5cea5-142">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="5cea5-142">Runs the tests in blame mode.</span></span> <span data-ttu-id="5cea5-143">Essa opção é útil para isolar os testes problemáticos que causam uma falha do host de teste.</span><span class="sxs-lookup"><span data-stu-id="5cea5-143">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="5cea5-144">Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.</span><span class="sxs-lookup"><span data-stu-id="5cea5-144">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="5cea5-145">Executa os testes em um processo isolado.</span><span class="sxs-lookup"><span data-stu-id="5cea5-145">Runs the tests in an isolated process.</span></span> <span data-ttu-id="5cea5-146">Isso torna o processo *vstest.console.exe* menos suscetível a ser interrompido por engano nos testes. Entretanto, os testes podem ser executados de forma mais lenta.</span><span class="sxs-lookup"><span data-stu-id="5cea5-146">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`@<file>`**

  <span data-ttu-id="5cea5-147">Lê um arquivo de resposta para obter mais opções.</span><span class="sxs-lookup"><span data-stu-id="5cea5-147">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="5cea5-148">Especifica argumentos extras para passar ao adaptador.</span><span class="sxs-lookup"><span data-stu-id="5cea5-148">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="5cea5-149">Os argumentos são especificados como pares de nome-valor no formato `<n>=<v>`, em que `<n>` é o nome de argumento e `<v>` é o valor do argumento.</span><span class="sxs-lookup"><span data-stu-id="5cea5-149">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="5cea5-150">Use um espaço para separar vários argumentos.</span><span class="sxs-lookup"><span data-stu-id="5cea5-150">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="5cea5-151">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5cea5-151">Examples</span></span>

<span data-ttu-id="5cea5-152">Executar testes em *MyTestProject. dll*:</span><span class="sxs-lookup"><span data-stu-id="5cea5-152">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="5cea5-153">Execute testes em *MyTestProject. dll*, exportando para a pasta personalizada com o nome personalizado:</span><span class="sxs-lookup"><span data-stu-id="5cea5-153">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="5cea5-154">Execute testes em *MyTestProject. dll* e *myothertestproject. exe*:</span><span class="sxs-lookup"><span data-stu-id="5cea5-154">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="5cea5-155">Execute testes `TestMethod1`:</span><span class="sxs-lookup"><span data-stu-id="5cea5-155">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="5cea5-156">Execute testes `TestMethod1` e `TestMethod2`:</span><span class="sxs-lookup"><span data-stu-id="5cea5-156">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```
