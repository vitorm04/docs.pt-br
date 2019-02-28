---
title: Comando dotnet vstest
description: O comando dotnet vstest compila um projeto e todas as suas dependências.
author: guardrex
ms.date: 05/30/2018
ms.openlocfilehash: d41e901f70b4a3d0647c693fdd8076f771466073
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747723"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="19f59-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="19f59-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="19f59-104">Nome</span><span class="sxs-lookup"><span data-stu-id="19f59-104">Name</span></span>

<span data-ttu-id="19f59-105">`dotnet-vstest` - Executa testes a partir de arquivos especificados.</span><span class="sxs-lookup"><span data-stu-id="19f59-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="19f59-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="19f59-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="19f59-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="19f59-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="19f59-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="19f59-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="19f59-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="19f59-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
---

## <a name="description"></a><span data-ttu-id="19f59-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="19f59-110">Description</span></span>

<span data-ttu-id="19f59-111">O comando `dotnet-vstest` executa o aplicativo de linha de comando `VSTest.Console` para executar testes automatizados de unidade.</span><span class="sxs-lookup"><span data-stu-id="19f59-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="19f59-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="19f59-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="19f59-113">Execute testes a partir de assemblies especificados.</span><span class="sxs-lookup"><span data-stu-id="19f59-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="19f59-114">Separe vários nomes de assembly de teste com espaços.</span><span class="sxs-lookup"><span data-stu-id="19f59-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="19f59-115">Opções</span><span class="sxs-lookup"><span data-stu-id="19f59-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="19f59-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="19f59-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="19f59-117">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="19f59-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="19f59-118">Execute testes com nomes que correspondam aos valores fornecidos.</span><span class="sxs-lookup"><span data-stu-id="19f59-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="19f59-119">Separe vários valores com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="19f59-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="19f59-120">Use adaptadores de teste personalizados para um determinado caminho (se houver) na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="19f59-121">Arquitetura da plataforma de destino usada para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="19f59-122">Os valores válidos são `x86`, `x64` e `ARM`.</span><span class="sxs-lookup"><span data-stu-id="19f59-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="19f59-123">Versão do .NET Framework de destino usada na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="19f59-124">Alguns exemplos de valores válidos são `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="19f59-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="19f59-125">Outros valores com suporte são `Framework40`, `Framework45`, `FrameworkCore10` e `FrameworkUap10`.</span><span class="sxs-lookup"><span data-stu-id="19f59-125">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="19f59-126">Execute testes em paralelo.</span><span class="sxs-lookup"><span data-stu-id="19f59-126">Execute tests in parallel.</span></span> <span data-ttu-id="19f59-127">Por padrão, todos os núcleos disponíveis no computador estão disponíveis para uso.</span><span class="sxs-lookup"><span data-stu-id="19f59-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="19f59-128">Especifique um número explícito de núcleos definindo a propriedade MaxCpuCount sob o nó RunConfiguration no arquivo runsettings.</span><span class="sxs-lookup"><span data-stu-id="19f59-128">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="19f59-129">Execute testes que correspondam à expressão fornecida.</span><span class="sxs-lookup"><span data-stu-id="19f59-129">Run tests that match the given expression.</span></span> <span data-ttu-id="19f59-130">`<Expression>` está no formato `<property>Operator<value>[|&<Expression>]`, onde Operator pode ser `=`, `!=` ou `~`.</span><span class="sxs-lookup"><span data-stu-id="19f59-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="19f59-131">O operador `~` tem a semântica 'contains' e é aplicável para propriedades de cadeia de caracteres como `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="19f59-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="19f59-132">Os parênteses `()` são usados para agrupar subexpressões.</span><span class="sxs-lookup"><span data-stu-id="19f59-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="19f59-133">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="19f59-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="19f59-134">Especificar um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="19f59-135">Para publicar resultados do teste no Team Foundation Server, use o provedor de agente `TfsPublisher`:</span><span class="sxs-lookup"><span data-stu-id="19f59-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="19f59-136">Para registrar os resultados em um arquivo TRX (Resultados do teste) do Visual Studio, use o provedor de agente `trx`.</span><span class="sxs-lookup"><span data-stu-id="19f59-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="19f59-137">Essa opção cria um arquivo no diretório dos resultados do teste com o nome de arquivo de log determinado.</span><span class="sxs-lookup"><span data-stu-id="19f59-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="19f59-138">Se `LogFileName` não for fornecido, será criado um nome de arquivo exclusivo para armazenar os resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="19f59-139">Lista todos os testes descobertos do contêiner de teste fornecido.</span><span class="sxs-lookup"><span data-stu-id="19f59-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="19f59-140">ID do processo pai responsável por iniciar o processo atual.</span><span class="sxs-lookup"><span data-stu-id="19f59-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="19f59-141">Especifica a porta para a conexão de soquete e recebimento das mensagens do evento.</span><span class="sxs-lookup"><span data-stu-id="19f59-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="19f59-142">Permite logs detalhados na plataforma de teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="19f59-143">Os logs são gravados no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="19f59-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="19f59-144">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="19f59-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="19f59-145">Essa opção é útil para isolar os testes problemáticos que causam uma falha do host de teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="19f59-146">Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.</span><span class="sxs-lookup"><span data-stu-id="19f59-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="19f59-147">Executa os testes em um processo isolado.</span><span class="sxs-lookup"><span data-stu-id="19f59-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="19f59-148">Isso torna o processo *vstest.console.exe* menos suscetível a ser interrompido por engano nos testes. Entretanto, os testes podem ser executados de forma mais lenta.</span><span class="sxs-lookup"><span data-stu-id="19f59-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="19f59-149">Lê um arquivo de resposta para obter mais opções.</span><span class="sxs-lookup"><span data-stu-id="19f59-149">Reads response file for more options.</span></span>


`args`

<span data-ttu-id="19f59-150">Especifica argumentos extras para passar ao adaptador.</span><span class="sxs-lookup"><span data-stu-id="19f59-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="19f59-151">Os argumentos são especificados como pares de nome-valor no formato `<n>=<v>`, em que `<n>` é o nome de argumento e `<v>` é o valor do argumento.</span><span class="sxs-lookup"><span data-stu-id="19f59-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="19f59-152">Use um espaço para separar vários argumentos.</span><span class="sxs-lookup"><span data-stu-id="19f59-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="19f59-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="19f59-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="19f59-154">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="19f59-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="19f59-155">Execute testes com nomes que correspondam aos valores fornecidos.</span><span class="sxs-lookup"><span data-stu-id="19f59-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="19f59-156">Separe vários valores com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="19f59-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="19f59-157">Use adaptadores de teste personalizados para um determinado caminho (se houver) na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="19f59-158">Arquitetura da plataforma de destino usada para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="19f59-159">Os valores válidos são `x86`, `x64` e `ARM`.</span><span class="sxs-lookup"><span data-stu-id="19f59-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="19f59-160">Versão do .NET Framework de destino usada na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="19f59-161">Alguns exemplos de valores válidos são `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="19f59-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="19f59-162">Outros valores com suporte são `Framework40`, `Framework45` e `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="19f59-162">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="19f59-163">Execute testes em paralelo.</span><span class="sxs-lookup"><span data-stu-id="19f59-163">Execute tests in parallel.</span></span> <span data-ttu-id="19f59-164">Por padrão, todos os núcleos disponíveis no computador estão disponíveis para uso.</span><span class="sxs-lookup"><span data-stu-id="19f59-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="19f59-165">Especifique um número explícito de núcleos definindo a propriedade MaxCpuCount sob o nó RunConfiguration no arquivo runsettings.</span><span class="sxs-lookup"><span data-stu-id="19f59-165">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="19f59-166">Execute testes que correspondam à expressão fornecida.</span><span class="sxs-lookup"><span data-stu-id="19f59-166">Run tests that match the given expression.</span></span> <span data-ttu-id="19f59-167">`<Expression>` está no formato `<property>Operator<value>[|&<Expression>]`, onde Operator pode ser `=`, `!=` ou `~`.</span><span class="sxs-lookup"><span data-stu-id="19f59-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="19f59-168">O operador `~` tem a semântica 'contains' e é aplicável para propriedades de cadeia de caracteres como `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="19f59-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="19f59-169">Os parênteses `()` são usados para agrupar subexpressões.</span><span class="sxs-lookup"><span data-stu-id="19f59-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="19f59-170">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="19f59-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="19f59-171">Especificar um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="19f59-172">Para publicar resultados do teste no Team Foundation Server, use o provedor de agente `TfsPublisher`:</span><span class="sxs-lookup"><span data-stu-id="19f59-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="19f59-173">Para registrar os resultados em um arquivo TRX (Resultados do teste) do Visual Studio, use o provedor de agente `trx`.</span><span class="sxs-lookup"><span data-stu-id="19f59-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="19f59-174">Essa opção cria um arquivo no diretório dos resultados do teste com o nome de arquivo de log determinado.</span><span class="sxs-lookup"><span data-stu-id="19f59-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="19f59-175">Se `LogFileName` não for fornecido, será criado um nome de arquivo exclusivo para armazenar os resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="19f59-176">Lista todos os testes descobertos do contêiner de teste fornecido.</span><span class="sxs-lookup"><span data-stu-id="19f59-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="19f59-177">ID do processo pai responsável por iniciar o processo atual.</span><span class="sxs-lookup"><span data-stu-id="19f59-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="19f59-178">Especifica a porta para a conexão de soquete e recebimento das mensagens do evento.</span><span class="sxs-lookup"><span data-stu-id="19f59-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="19f59-179">Permite logs detalhados na plataforma de teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="19f59-180">Os logs são gravados no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="19f59-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="19f59-181">Especifica argumentos extras para passar ao adaptador.</span><span class="sxs-lookup"><span data-stu-id="19f59-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="19f59-182">Os argumentos são especificados como pares de nome-valor no formato `<n>=<v>`, em que `<n>` é o nome de argumento e `<v>` é o valor do argumento.</span><span class="sxs-lookup"><span data-stu-id="19f59-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="19f59-183">Use um espaço para separar vários argumentos.</span><span class="sxs-lookup"><span data-stu-id="19f59-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="19f59-184">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="19f59-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="19f59-185">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="19f59-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="19f59-186">Execute testes com nomes que correspondam aos valores fornecidos.</span><span class="sxs-lookup"><span data-stu-id="19f59-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="19f59-187">Separe vários valores com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="19f59-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="19f59-188">Use adaptadores de teste personalizados para um determinado caminho (se houver) na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="19f59-189">Arquitetura da plataforma de destino usada para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="19f59-190">Os valores válidos são `x86`, `x64` e `ARM`.</span><span class="sxs-lookup"><span data-stu-id="19f59-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="19f59-191">Versão do .NET Framework de destino usada na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="19f59-192">Alguns exemplos de valores válidos são `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`.</span><span class="sxs-lookup"><span data-stu-id="19f59-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="19f59-193">Outros valores com suporte são `Framework40`, `Framework45` e `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="19f59-193">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="19f59-194">Execute testes em paralelo.</span><span class="sxs-lookup"><span data-stu-id="19f59-194">Execute tests in parallel.</span></span> <span data-ttu-id="19f59-195">Por padrão, todos os núcleos disponíveis no computador estão disponíveis para uso.</span><span class="sxs-lookup"><span data-stu-id="19f59-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="19f59-196">Especifique um número explícito de núcleos definindo a propriedade MaxCpuCount sob o nó RunConfiguration no arquivo runsettings.</span><span class="sxs-lookup"><span data-stu-id="19f59-196">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="19f59-197">Execute testes que correspondam à expressão fornecida.</span><span class="sxs-lookup"><span data-stu-id="19f59-197">Run tests that match the given expression.</span></span> <span data-ttu-id="19f59-198">`<Expression>` está no formato `<property>Operator<value>[|&<Expression>]`, onde Operator pode ser `=`, `!=` ou `~`.</span><span class="sxs-lookup"><span data-stu-id="19f59-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="19f59-199">O operador `~` tem a semântica 'contains' e é aplicável para propriedades de cadeia de caracteres como `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="19f59-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="19f59-200">Os parênteses `()` são usados para agrupar subexpressões.</span><span class="sxs-lookup"><span data-stu-id="19f59-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="19f59-201">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="19f59-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="19f59-202">Especificar um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="19f59-203">Para publicar resultados do teste no Team Foundation Server, use o provedor de agente `TfsPublisher`:</span><span class="sxs-lookup"><span data-stu-id="19f59-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="19f59-204">Para registrar os resultados em um arquivo TRX (Resultados do teste) do Visual Studio, use o provedor de agente `trx`.</span><span class="sxs-lookup"><span data-stu-id="19f59-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="19f59-205">Essa opção cria um arquivo no diretório dos resultados do teste com o nome de arquivo de log determinado.</span><span class="sxs-lookup"><span data-stu-id="19f59-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="19f59-206">Se `LogFileName` não for fornecido, será criado um nome de arquivo exclusivo para armazenar os resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="19f59-207">Lista todos os testes descobertos do contêiner de teste fornecido.</span><span class="sxs-lookup"><span data-stu-id="19f59-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="19f59-208">ID do processo pai responsável por iniciar o processo atual.</span><span class="sxs-lookup"><span data-stu-id="19f59-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="19f59-209">Especifica a porta para a conexão de soquete e recebimento das mensagens do evento.</span><span class="sxs-lookup"><span data-stu-id="19f59-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="19f59-210">Permite logs detalhados na plataforma de teste.</span><span class="sxs-lookup"><span data-stu-id="19f59-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="19f59-211">Os logs são gravados no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="19f59-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="19f59-212">Especifica argumentos extras para passar ao adaptador.</span><span class="sxs-lookup"><span data-stu-id="19f59-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="19f59-213">Os argumentos são especificados como pares de nome-valor no formato `<n>=<v>`, em que `<n>` é o nome de argumento e `<v>` é o valor do argumento.</span><span class="sxs-lookup"><span data-stu-id="19f59-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="19f59-214">Use um espaço para separar vários argumentos.</span><span class="sxs-lookup"><span data-stu-id="19f59-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="19f59-215">Exemplos</span><span class="sxs-lookup"><span data-stu-id="19f59-215">Examples</span></span>

<span data-ttu-id="19f59-216">Execute testes em `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="19f59-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="19f59-217">Executar testes em `mytestproject.dll`, exportando para uma pasta personalizada com um nome personalizado:</span><span class="sxs-lookup"><span data-stu-id="19f59-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="19f59-218">Execute testes em `mytestproject.dll` e `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="19f59-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="19f59-219">Execute testes `TestMethod1`:</span><span class="sxs-lookup"><span data-stu-id="19f59-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="19f59-220">Execute testes `TestMethod1` e `TestMethod2`:</span><span class="sxs-lookup"><span data-stu-id="19f59-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
