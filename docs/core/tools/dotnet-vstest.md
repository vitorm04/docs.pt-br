---
title: Comando dotnet vstest
description: O comando dotnet vstest compila um projeto e todas as suas dependências.
ms.date: 02/27/2020
ms.openlocfilehash: f7db58f4aab59354b8c69ce0371324c23482dafe
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975388"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="5e4a7-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="5e4a7-103">dotnet vstest</span></span>

<span data-ttu-id="5e4a7-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="5e4a7-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e4a7-105">O `dotnet vstest` comando é substituído por `dotnet test`, que agora pode ser usado para executar assemblies.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-105">The `dotnet vstest` command is superseded by `dotnet test`, which can now be used to run assemblies.</span></span> <span data-ttu-id="5e4a7-106">Confira [`dotnet test`](dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="5e4a7-106">See [`dotnet test`](dotnet-test.md).</span></span>

## <a name="name"></a><span data-ttu-id="5e4a7-107">Nome</span><span class="sxs-lookup"><span data-stu-id="5e4a7-107">Name</span></span>

<span data-ttu-id="5e4a7-108">`dotnet-vstest`– Executa testes a partir dos assemblies especificados.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-108">`dotnet-vstest` - Runs tests from the specified assemblies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5e4a7-109">Sinopse</span><span class="sxs-lookup"><span data-stu-id="5e4a7-109">Synopsis</span></span>

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Blame] [--Diag <PATH_TO_LOG_FILE>]
    [--Framework <FRAMEWORK>] [--InIsolation] [-lt|--ListTests <FILE_NAME>]
    [--logger <LOGGER_URI/FRIENDLY_NAME>] [--Parallel]
    [--ParentProcessId <PROCESS_ID>] [--Platform] <PLATFORM_TYPE>
    [--Port <PORT>] [--ResultsDirectory<PATH>] [--Settings <SETTINGS_FILE>]
    [--TestAdapterPath <PATH>] [--TestCaseFilter <EXPRESSION>]
    [--Tests <TEST_NAMES>] [[--] <args>...]]

dotnet vstest -?|--Help
```

## <a name="description"></a><span data-ttu-id="5e4a7-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e4a7-110">Description</span></span>

<span data-ttu-id="5e4a7-111">O comando `dotnet-vstest` executa o aplicativo de linha de comando `VSTest.Console` para executar testes automatizados de unidade.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="5e4a7-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="5e4a7-112">Arguments</span></span>

- **`TEST_FILE_NAMES`**

  <span data-ttu-id="5e4a7-113">Execute testes a partir de assemblies especificados.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="5e4a7-114">Separe vários nomes de assembly de teste com espaços.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-114">Separate multiple test assembly names with spaces.</span></span> <span data-ttu-id="5e4a7-115">Há suporte para caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-115">Wildcards are supported.</span></span>

## <a name="options"></a><span data-ttu-id="5e4a7-116">Opções</span><span class="sxs-lookup"><span data-stu-id="5e4a7-116">Options</span></span>

- **`--Blame`**

  <span data-ttu-id="5e4a7-117">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-117">Runs the tests in blame mode.</span></span> <span data-ttu-id="5e4a7-118">Essa opção é útil para isolar os testes problemáticos que causam uma falha do host de teste.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-118">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="5e4a7-119">Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-119">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`--Diag <PATH_TO_LOG_FILE>`**

  <span data-ttu-id="5e4a7-120">Permite logs detalhados na plataforma de teste.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-120">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="5e4a7-121">Os logs são gravados no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-121">Logs are written to the provided file.</span></span>

- **`--Framework <FRAMEWORK>`**

  <span data-ttu-id="5e4a7-122">Versão do .NET Framework de destino usada na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-122">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="5e4a7-123">Alguns exemplos de valores válidos são `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-123">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="5e4a7-124">Outros valores com suporte são `Framework40`, `Framework45`, `FrameworkCore10` e `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-124">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

- **`--InIsolation`**

  <span data-ttu-id="5e4a7-125">Executa os testes em um processo isolado.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-125">Runs the tests in an isolated process.</span></span> <span data-ttu-id="5e4a7-126">Isso torna o processo *vstest.console.exe* menos suscetível a ser interrompido por engano nos testes. Entretanto, os testes podem ser executados de forma mais lenta.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-126">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

- **`-lt|--ListTests <FILE_NAME>`**

  <span data-ttu-id="5e4a7-127">Lista todos os testes descobertos do contêiner de teste fornecido.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-127">Lists all discovered tests from the given test container.</span></span>

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="5e4a7-128">Especificar um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-128">Specify a logger for test results.</span></span>

  - <span data-ttu-id="5e4a7-129">Para publicar resultados do teste no Team Foundation Server, use o provedor de agente `TfsPublisher`:</span><span class="sxs-lookup"><span data-stu-id="5e4a7-129">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - <span data-ttu-id="5e4a7-130">Para registrar os resultados em um arquivo TRX (Resultados do teste) do Visual Studio, use o provedor de agente `trx`.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-130">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="5e4a7-131">Essa opção cria um arquivo no diretório dos resultados do teste com o nome de arquivo de log determinado.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-131">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="5e4a7-132">Se `LogFileName` não for fornecido, será criado um nome de arquivo exclusivo para armazenar os resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-132">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  <span data-ttu-id="5e4a7-133">Execute testes em paralelo.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-133">Run tests in parallel.</span></span> <span data-ttu-id="5e4a7-134">Por padrão, todos os núcleos disponíveis no computador estão disponíveis para uso.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-134">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="5e4a7-135">Especifique um número explícito de núcleos definindo a `MaxCpuCount` Propriedade sob o `RunConfiguration` nó no arquivo *RunSettings* .</span><span class="sxs-lookup"><span data-stu-id="5e4a7-135">Specify an explicit number of cores by setting the `MaxCpuCount` property under the `RunConfiguration` node in the *runsettings* file.</span></span>

- **`--ParentProcessId <PROCESS_ID>`**

  <span data-ttu-id="5e4a7-136">ID do processo pai responsável por iniciar o processo atual.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-136">Process ID of the parent process responsible for launching the current process.</span></span>

- **`--Platform <PLATFORM_TYPE>`**

  <span data-ttu-id="5e4a7-137">Arquitetura da plataforma de destino usada para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-137">Target platform architecture used for test execution.</span></span> <span data-ttu-id="5e4a7-138">Os valores válidos são `x86`, `x64` e `ARM`.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-138">Valid values are `x86`, `x64`, and `ARM`.</span></span>

- **`--Port <PORT>`**

  <span data-ttu-id="5e4a7-139">Especifica a porta para a conexão de soquete e recebimento das mensagens do evento.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-139">Specifies the port for the socket connection and receiving the event messages.</span></span>

- **`--ResultsDirectory:<PATH>`**

  <span data-ttu-id="5e4a7-140">O diretório de resultados de teste será criado no caminho especificado, se não existir.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-140">Test results directory will be created in specified path if not exists.</span></span>

- **`--Settings <SETTINGS_FILE>`**

  <span data-ttu-id="5e4a7-141">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-141">Settings to use when running tests.</span></span>

- **`--TestAdapterPath <PATH>`**

  <span data-ttu-id="5e4a7-142">Use adaptadores de teste personalizados para um determinado caminho (se houver) na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-142">Use custom test adapters from a given path (if any) in the test run.</span></span>

- **`--TestCaseFilter <EXPRESSION>`**

  <span data-ttu-id="5e4a7-143">Execute testes que correspondam à expressão fornecida.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-143">Run tests that match the given expression.</span></span> <span data-ttu-id="5e4a7-144">`<EXPRESSION>` está no formato `<property>Operator<value>[|&<EXPRESSION>]`, onde Operator pode ser `=`, `!=` ou `~`.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-144">`<EXPRESSION>` is of the format `<property>Operator<value>[|&<EXPRESSION>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="5e4a7-145">O operador `~` tem a semântica 'contains' e é aplicável para propriedades de cadeia de caracteres como `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-145">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="5e4a7-146">Os parênteses `()` são usados para agrupar subexpressões.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-146">Parentheses `()` are used to group subexpressions.</span></span> <span data-ttu-id="5e4a7-147">Para obter mais informações, consulte [filtro TestCase](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="5e4a7-147">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

- **`--Tests <TEST_NAMES>`**

  <span data-ttu-id="5e4a7-148">Execute testes com nomes que correspondam aos valores fornecidos.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-148">Run tests with names that match the provided values.</span></span> <span data-ttu-id="5e4a7-149">Separar vários valores com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-149">Separate multiple values with commas.</span></span>

- **`-?|--Help`**

  <span data-ttu-id="5e4a7-150">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-150">Prints out a short help for the command.</span></span>

- **`@<file>`**

  <span data-ttu-id="5e4a7-151">Lê um arquivo de resposta para obter mais opções.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-151">Reads response file for more options.</span></span>

- **`args`**

  <span data-ttu-id="5e4a7-152">Especifica argumentos extras para passar ao adaptador.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-152">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="5e4a7-153">Os argumentos são especificados como pares de nome-valor no formato `<n>=<v>`, em que `<n>` é o nome de argumento e `<v>` é o valor do argumento.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-153">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="5e4a7-154">Use um espaço para separar vários argumentos.</span><span class="sxs-lookup"><span data-stu-id="5e4a7-154">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="5e4a7-155">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5e4a7-155">Examples</span></span>

<span data-ttu-id="5e4a7-156">Executar testes em *MyTestProject. dll*:</span><span class="sxs-lookup"><span data-stu-id="5e4a7-156">Run tests in *mytestproject.dll*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll
```

<span data-ttu-id="5e4a7-157">Execute testes em *MyTestProject. dll*, exportando para a pasta personalizada com o nome personalizado:</span><span class="sxs-lookup"><span data-stu-id="5e4a7-157">Run tests in *mytestproject.dll*, exporting to custom folder with custom name:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

<span data-ttu-id="5e4a7-158">Execute testes em *MyTestProject. dll* e *myothertestproject. exe*:</span><span class="sxs-lookup"><span data-stu-id="5e4a7-158">Run tests in *mytestproject.dll* and *myothertestproject.exe*:</span></span>

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

<span data-ttu-id="5e4a7-159">Execute testes `TestMethod1`:</span><span class="sxs-lookup"><span data-stu-id="5e4a7-159">Run `TestMethod1` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

<span data-ttu-id="5e4a7-160">Execute testes `TestMethod1` e `TestMethod2`:</span><span class="sxs-lookup"><span data-stu-id="5e4a7-160">Run `TestMethod1` and `TestMethod2` tests:</span></span>

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a><span data-ttu-id="5e4a7-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e4a7-161">See also</span></span>

- [<span data-ttu-id="5e4a7-162">Opções da linha de comando de VSTest.Console.exe</span><span class="sxs-lookup"><span data-stu-id="5e4a7-162">VSTest.Console.exe command-line options</span></span>](/visualstudio/test/vstest-console-options)
