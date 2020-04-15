---
title: Comando dotnet vstest
description: O comando dotnet vstest compila um projeto e todas as suas dependências.
ms.date: 02/27/2020
ms.openlocfilehash: 4941a6d08d45953039eb406a30f0ff984128ba1c
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389625"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="f0857-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="f0857-103">dotnet vstest</span></span>

<span data-ttu-id="f0857-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="f0857-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f0857-105">Nome</span><span class="sxs-lookup"><span data-stu-id="f0857-105">Name</span></span>

<span data-ttu-id="f0857-106">`dotnet-vstest` - Executa testes a partir de arquivos especificados.</span><span class="sxs-lookup"><span data-stu-id="f0857-106">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f0857-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="f0857-107">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Blame] [--Diag]
    [--Framework] [--InIsolation] [-lt|--ListTests] [--logger]
    [--Parallel] [--ParentProcessId] [--Platform] [--Port]
    [--ResultsDirectory] [--Settings] [--TestAdapterPath]
    [--TestCaseFilter] [--Tests] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a><span data-ttu-id="f0857-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="f0857-108">Description</span></span>

<span data-ttu-id="f0857-109">O comando `dotnet-vstest` executa o aplicativo de linha de comando `VSTest.Console` para executar testes automatizados de unidade.</span><span class="sxs-lookup"><span data-stu-id="f0857-109">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="f0857-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="f0857-110">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="f0857-111">Execute testes a partir de assemblies especificados.</span><span class="sxs-lookup"><span data-stu-id="f0857-111">Run tests from the specified assemblies.</span></span> <span data-ttu-id="f0857-112">Separe vários nomes de assembly de teste com espaços.</span><span class="sxs-lookup"><span data-stu-id="f0857-112">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="f0857-113">Há suporte para caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="f0857-113">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="f0857-114">Opções</span><span class="sxs-lookup"><span data-stu-id="f0857-114">Options</span></span>

- **`--Blame`**

  <span data-ttu-id="f0857-115">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="f0857-115">Runs the tests in blame mode.</span></span> <span data-ttu-id="f0857-116">Essa opção é útil para isolar os testes problemáticos que causam uma falha do host de teste.</span><span class="sxs-lookup"><span data-stu-id="f0857-116">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="f0857-117">Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.</span><span class="sxs-lookup"><span data-stu-id="f0857-117">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--Diag <Path to log file>`**

  <span data-ttu-id="f0857-118">Permite logs detalhados na plataforma de teste.</span><span class="sxs-lookup"><span data-stu-id="f0857-118">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="f0857-119">Os logs são gravados no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="f0857-119">Logs are written to the provided file.</span></span>

- **`--Framework <Framework Version>`**

  <span data-ttu-id="f0857-120">Versão do .NET Framework de destino usada na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="f0857-120">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="f0857-121">Alguns exemplos de valores válidos são `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="f0857-121">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="f0857-122">Outros valores com suporte são `Framework40`, `Framework45`, `FrameworkCore10` e `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="f0857-122">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="f0857-123">Executa os testes em um processo isolado.</span><span class="sxs-lookup"><span data-stu-id="f0857-123">Runs the tests in an isolated process.</span></span> <span data-ttu-id="f0857-124">Isso torna o processo *vstest.console.exe* menos suscetível a ser interrompido por engano nos testes. Entretanto, os testes podem ser executados de forma mais lenta.</span><span class="sxs-lookup"><span data-stu-id="f0857-124">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`-lt|--ListTests <File Name>`**

  <span data-ttu-id="f0857-125">Lista todos os testes descobertos do contêiner de teste fornecido.</span><span class="sxs-lookup"><span data-stu-id="f0857-125">Lists all discovered tests from the given test container.</span></span>

- **`--logger <Logger Uri/FriendlyName>`**

  <span data-ttu-id="f0857-126">Especificar um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="f0857-126">Specify a logger for test results.</span></span>

  - <span data-ttu-id="f0857-127">Para publicar resultados do teste no Team Foundation Server, use o provedor de agente `TfsPublisher`:</span><span class="sxs-lookup"><span data-stu-id="f0857-127">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="f0857-128">Para registrar os resultados em um arquivo TRX (Resultados do teste) do Visual Studio, use o provedor de agente `trx`.</span><span class="sxs-lookup"><span data-stu-id="f0857-128">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="f0857-129">Essa opção cria um arquivo no diretório dos resultados do teste com o nome de arquivo de log determinado.</span><span class="sxs-lookup"><span data-stu-id="f0857-129">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="f0857-130">Se `LogFileName` não for fornecido, será criado um nome de arquivo exclusivo para armazenar os resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="f0857-130">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  <span data-ttu-id="f0857-131">Executar testes em paralelo.</span><span class="sxs-lookup"><span data-stu-id="f0857-131">Run tests in parallel.</span></span> <span data-ttu-id="f0857-132">Por padrão, todos os núcleos disponíveis no computador estão disponíveis para uso.</span><span class="sxs-lookup"><span data-stu-id="f0857-132">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="f0857-133">Especifique um número `MaxCpuCount` explícito de `RunConfiguration` núcleos definindo a propriedade sob o nó no arquivo *de configurações* de execução.</span><span class="sxs-lookup"><span data-stu-id="f0857-133">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--ParentProcessId <ParentProcessId>`**

  <span data-ttu-id="f0857-134">ID do processo pai responsável por iniciar o processo atual.</span><span class="sxs-lookup"><span data-stu-id="f0857-134">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Platform <Platform type>`**

  <span data-ttu-id="f0857-135">Arquitetura da plataforma de destino usada para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="f0857-135">Target platform architecture used for test execution.</span></span> <span data-ttu-id="f0857-136">Os valores válidos são `x86`, `x64` e `ARM`.</span><span class="sxs-lookup"><span data-stu-id="f0857-136">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Port <Port>`**

  <span data-ttu-id="f0857-137">Especifica a porta para a conexão de soquete e recebimento das mensagens do evento.</span><span class="sxs-lookup"><span data-stu-id="f0857-137">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--ResultsDirectory:<PathToResulsDirectory>`**

  <span data-ttu-id="f0857-138">O diretório de resultados de teste será criado no caminho especificado, se não existir.</span><span class="sxs-lookup"><span data-stu-id="f0857-138">Test results directory will be created in specified path if not exists.</span></span>

- **`--Settings <Settings File>`**

  <span data-ttu-id="f0857-139">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="f0857-139">Settings to use when running tests.</span></span>

- **`--TestAdapterPath`**

  <span data-ttu-id="f0857-140">Use adaptadores de teste personalizados para um determinado caminho (se houver) na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="f0857-140">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--TestCaseFilter <Expression>`**

  <span data-ttu-id="f0857-141">Execute testes que correspondam à expressão fornecida.</span><span class="sxs-lookup"><span data-stu-id="f0857-141">Run tests that match the given expression.</span></span> <span data-ttu-id="f0857-142">`<Expression>` está no formato `<property>Operator<value>[|&<Expression>]`, onde Operator pode ser `=`, `!=` ou `~`.</span><span class="sxs-lookup"><span data-stu-id="f0857-142">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="f0857-143">O operador `~` tem a semântica 'contains' e é aplicável para propriedades de cadeia de caracteres como `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="f0857-143">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="f0857-144">Parênteses são usados `()` para agrupar subexpressões.</span><span class="sxs-lookup"><span data-stu-id="f0857-144">Parentheses `()` are used to group subexpressions.</span></span> <span data-ttu-id="f0857-145">Para obter mais informações, consulte [o filtro TestCase](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="f0857-145">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

- **`--Tests <Test Names>`**

  <span data-ttu-id="f0857-146">Execute testes com nomes que correspondam aos valores fornecidos.</span><span class="sxs-lookup"><span data-stu-id="f0857-146">Run tests with names that match the provided values.</span></span> <span data-ttu-id="f0857-147">Separe vários valores com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="f0857-147">Separate multiple values with commas.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="f0857-148">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="f0857-148">Prints out a short help for the command.</span></span>

- **`@<file>`**

  <span data-ttu-id="f0857-149">Lê um arquivo de resposta para obter mais opções.</span><span class="sxs-lookup"><span data-stu-id="f0857-149">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="f0857-150">Especifica argumentos extras para passar ao adaptador.</span><span class="sxs-lookup"><span data-stu-id="f0857-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="f0857-151">Os argumentos são especificados como pares de nome-valor no formato `<n>=<v>`, em que `<n>` é o nome de argumento e `<v>` é o valor do argumento.</span><span class="sxs-lookup"><span data-stu-id="f0857-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="f0857-152">Use um espaço para separar vários argumentos.</span><span class="sxs-lookup"><span data-stu-id="f0857-152">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="f0857-153">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f0857-153">Examples</span></span>

<span data-ttu-id="f0857-154">Executar testes em *mytestproject.dll*:</span><span class="sxs-lookup"><span data-stu-id="f0857-154">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="f0857-155">Executar testes em *mytestproject.dll,* exportando para pasta personalizada com nome personalizado:</span><span class="sxs-lookup"><span data-stu-id="f0857-155">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="f0857-156">Executar testes em *mytestproject.dll* e *myothertestproject.exe*:</span><span class="sxs-lookup"><span data-stu-id="f0857-156">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="f0857-157">Execute testes `TestMethod1`:</span><span class="sxs-lookup"><span data-stu-id="f0857-157">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="f0857-158">Execute testes `TestMethod1` e `TestMethod2`:</span><span class="sxs-lookup"><span data-stu-id="f0857-158">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a><span data-ttu-id="f0857-159">Confira também</span><span class="sxs-lookup"><span data-stu-id="f0857-159">See also</span></span>

- [<span data-ttu-id="f0857-160">Opções da linha de comando de VSTest.Console.exe</span><span class="sxs-lookup"><span data-stu-id="f0857-160">VSTest.Console.exe command-line options</span></span>](/visualstudio/test/vstest-console-options)
