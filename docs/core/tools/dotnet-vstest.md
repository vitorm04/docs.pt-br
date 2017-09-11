---
title: "Comando dotnet vstest – CLI do .NET Core"
description: "O comando dotnet vstest compila um projeto e todas as suas dependências."
author: guardrex
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: c5a7ee0ba306cea641b0ff34f0b521c92bd03719
ms.contentlocale: pt-br
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-vstest"></a><span data-ttu-id="f155a-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="f155a-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f155a-104">Nome</span><span class="sxs-lookup"><span data-stu-id="f155a-104">Name</span></span>

<span data-ttu-id="f155a-105">`dotnet-vstest` - Executa testes a partir de arquivos especificados.</span><span class="sxs-lookup"><span data-stu-id="f155a-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f155a-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="f155a-106">Synopsis</span></span>

`dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]`

## <a name="description"></a><span data-ttu-id="f155a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f155a-107">Description</span></span>

<span data-ttu-id="f155a-108">O comando `dotnet-vstest` executa o aplicativo de linha de comando `VSTest.Console` para executar testes automatizados de unidade e testes de aplicativo de IU codificado.</span><span class="sxs-lookup"><span data-stu-id="f155a-108">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit and coded UI application tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="f155a-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="f155a-109">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="f155a-110">Execute testes a partir de assemblies especificados.</span><span class="sxs-lookup"><span data-stu-id="f155a-110">Run tests from the specified assemblies.</span></span> <span data-ttu-id="f155a-111">Separe vários nomes de assembly de teste com espaços.</span><span class="sxs-lookup"><span data-stu-id="f155a-111">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="f155a-112">Opções</span><span class="sxs-lookup"><span data-stu-id="f155a-112">Options</span></span>

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="f155a-113">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="f155a-113">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="f155a-114">Execute testes com nomes que correspondam aos valores fornecidos.</span><span class="sxs-lookup"><span data-stu-id="f155a-114">Run tests with names that match the provided values.</span></span> <span data-ttu-id="f155a-115">Separe vários valores com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="f155a-115">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="f155a-116">Use adaptadores de teste personalizados para um determinado caminho (se houver) na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="f155a-116">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="f155a-117">Arquitetura da plataforma de destino usada para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="f155a-117">Target platform architecture used for test execution.</span></span> <span data-ttu-id="f155a-118">Os valores válidos são `x86`, `x64` e `ARM`.</span><span class="sxs-lookup"><span data-stu-id="f155a-118">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="f155a-119">Versão do .NET Framework de destino usada na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="f155a-119">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="f155a-120">Os exemplos de valores válidos são `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0` etc. Outros valores com suporte são `Framework35`, `Framework40`, `Framework45` e `FrameworkCore10`.</span><span class="sxs-lookup"><span data-stu-id="f155a-120">Examples of valid values are `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0`, etc. Other supported values are `Framework35`, `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="f155a-121">Execute testes em paralelo.</span><span class="sxs-lookup"><span data-stu-id="f155a-121">Execute tests in parallel.</span></span> <span data-ttu-id="f155a-122">Por padrão, todos os núcleos disponíveis no computador estão disponíveis para uso.</span><span class="sxs-lookup"><span data-stu-id="f155a-122">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="f155a-123">Defina um número explícito de núcleos com um arquivo de configurações.</span><span class="sxs-lookup"><span data-stu-id="f155a-123">Set an explicit number of cores with a settings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="f155a-124">Execute testes que correspondam à expressão fornecida.</span><span class="sxs-lookup"><span data-stu-id="f155a-124">Run tests that match the given expression.</span></span> <span data-ttu-id="f155a-125">`<Expression>` está no formato `<property>Operator<value>[|&<Expression>]`, onde Operator pode ser `=`, `!=` ou `~`.</span><span class="sxs-lookup"><span data-stu-id="f155a-125">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span>  <span data-ttu-id="f155a-126">O operador `~` tem a semântica 'contains' e é aplicável para propriedades de cadeia de caracteres como `DisplayName`.</span><span class="sxs-lookup"><span data-stu-id="f155a-126">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="f155a-127">Os parênteses `()` são usados para agrupar subexpressões.</span><span class="sxs-lookup"><span data-stu-id="f155a-127">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="f155a-128">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="f155a-128">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="f155a-129">Especificar um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="f155a-129">Specify a logger for test results.</span></span>  

* <span data-ttu-id="f155a-130">Para publicar resultados do teste no Team Foundation Server, use o provedor de agente `TfsPublisher`:</span><span class="sxs-lookup"><span data-stu-id="f155a-130">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="f155a-131">Para registrar os resultados em um arquivo TRX (Resultados do teste) do Visual Studio, use o provedor de agente `trx`.</span><span class="sxs-lookup"><span data-stu-id="f155a-131">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="f155a-132">Essa opção cria um arquivo no diretório dos resultados do teste com o nome de arquivo de log determinado.</span><span class="sxs-lookup"><span data-stu-id="f155a-132">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="f155a-133">Se `LogFileName` não for fornecido, será criado um nome de arquivo exclusivo para armazenar os resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="f155a-133">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="f155a-134">Lista testes descobertos do contêiner de teste fornecido.</span><span class="sxs-lookup"><span data-stu-id="f155a-134">Lists discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="f155a-135">ID de processo do processo pai responsável por iniciar o processo atual.</span><span class="sxs-lookup"><span data-stu-id="f155a-135">Process Id of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="f155a-136">Especifica a porta para a conexão de soquete e recebimento das mensagens do evento.</span><span class="sxs-lookup"><span data-stu-id="f155a-136">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="f155a-137">Permite logs detalhados na plataforma de teste.</span><span class="sxs-lookup"><span data-stu-id="f155a-137">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="f155a-138">Os logs são gravados no arquivo fornecido.</span><span class="sxs-lookup"><span data-stu-id="f155a-138">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="f155a-139">Especifica argumentos extras para passar ao adaptador.</span><span class="sxs-lookup"><span data-stu-id="f155a-139">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="f155a-140">Os argumentos são especificados como pares de nome-valor no formato `<n>=<v>`, em que `<n>` é o nome de argumento e `<v>` é o valor do argumento.</span><span class="sxs-lookup"><span data-stu-id="f155a-140">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="f155a-141">Use um espaço para separar vários argumentos.</span><span class="sxs-lookup"><span data-stu-id="f155a-141">Use a space to separate multiple arguments.</span></span>

## <a name="examples"></a><span data-ttu-id="f155a-142">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f155a-142">Examples</span></span>

<span data-ttu-id="f155a-143">Execute testes em `mytestproject.dll`:</span><span class="sxs-lookup"><span data-stu-id="f155a-143">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="f155a-144">Execute testes em `mytestproject.dll` e `myothertestproject.exe`:</span><span class="sxs-lookup"><span data-stu-id="f155a-144">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="f155a-145">Execute testes `TestMethod1`:</span><span class="sxs-lookup"><span data-stu-id="f155a-145">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="f155a-146">Execute testes `TestMethod1` e `TestMethod2`:</span><span class="sxs-lookup"><span data-stu-id="f155a-146">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`

