---
title: Comando dotnet test – CLI do .NET Core
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 2bee78ca44026f28c51fac3bcf87d976b53e48a7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43390684"
---
# <a name="dotnet-test"></a><span data-ttu-id="aefed-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="aefed-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="aefed-104">Nome</span><span class="sxs-lookup"><span data-stu-id="aefed-104">Name</span></span>

<span data-ttu-id="aefed-105">`dotnet test` - driver de teste do .NET usado para executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="aefed-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="aefed-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="aefed-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="aefed-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="aefed-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="aefed-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="aefed-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="aefed-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="aefed-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="aefed-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="aefed-110">Description</span></span>

<span data-ttu-id="aefed-111">O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="aefed-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="aefed-112">O comando `dotnet test` inicia o aplicativo de console executor de teste especificado para um projeto.</span><span class="sxs-lookup"><span data-stu-id="aefed-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="aefed-113">O executor de teste realiza os testes definidos para uma estrutura de teste de unidade (por exemplo, MSTest, NUnit ou xUnit) e relata o êxito ou a falha de cada teste.</span><span class="sxs-lookup"><span data-stu-id="aefed-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="aefed-114">O executor de teste e a biblioteca de teste de unidade são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.</span><span class="sxs-lookup"><span data-stu-id="aefed-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="aefed-115">Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:</span><span class="sxs-lookup"><span data-stu-id="aefed-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="aefed-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="aefed-116">Arguments</span></span>

`PROJECT`

<span data-ttu-id="aefed-117">Caminho para o projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="aefed-117">Path to the test project.</span></span> <span data-ttu-id="aefed-118">Se não é especificado, usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="aefed-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="aefed-119">Opções</span><span class="sxs-lookup"><span data-stu-id="aefed-119">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="aefed-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="aefed-120">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="aefed-121">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="aefed-121">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="aefed-122">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="aefed-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="aefed-123">Essa opção é útil para isolar os testes problemáticos que causam uma falha do host de teste.</span><span class="sxs-lookup"><span data-stu-id="aefed-123">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="aefed-124">Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.</span><span class="sxs-lookup"><span data-stu-id="aefed-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="aefed-125">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="aefed-125">Defines the build configuration.</span></span> <span data-ttu-id="aefed-126">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="aefed-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="aefed-127">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="aefed-127">Enables data collector for the test run.</span></span> <span data-ttu-id="aefed-128">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="aefed-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="aefed-129">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="aefed-129">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="aefed-130">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="aefed-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="aefed-131">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="aefed-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="aefed-132">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="aefed-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="aefed-133">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="aefed-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="aefed-134">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="aefed-134">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="aefed-135">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="aefed-135">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="aefed-136">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="aefed-136">Doesn't build the test project before running it.</span></span> <span data-ttu-id="aefed-137">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="aefed-137">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="aefed-138">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="aefed-138">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="aefed-139">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="aefed-139">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="aefed-140">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="aefed-140">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="aefed-141">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="aefed-141">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="aefed-142">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="aefed-142">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="aefed-143">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="aefed-143">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="aefed-144">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="aefed-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="aefed-145">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="aefed-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="aefed-146">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="aefed-146">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="aefed-147">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="aefed-147">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="aefed-148">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="aefed-148">Defines the build configuration.</span></span> <span data-ttu-id="aefed-149">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="aefed-149">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="aefed-150">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="aefed-150">Enables data collector for the test run.</span></span> <span data-ttu-id="aefed-151">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="aefed-151">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="aefed-152">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="aefed-152">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="aefed-153">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="aefed-153">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="aefed-154">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="aefed-154">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="aefed-155">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="aefed-155">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="aefed-156">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="aefed-156">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="aefed-157">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="aefed-157">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="aefed-158">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="aefed-158">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="aefed-159">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="aefed-159">Doesn't build the test project before running it.</span></span> <span data-ttu-id="aefed-160">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="aefed-160">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="aefed-161">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="aefed-161">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="aefed-162">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="aefed-162">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="aefed-163">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="aefed-163">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="aefed-164">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="aefed-164">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="aefed-165">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="aefed-165">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="aefed-166">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="aefed-166">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="aefed-167">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="aefed-167">Sets the verbosity level of the command.</span></span> <span data-ttu-id="aefed-168">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="aefed-168">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="aefed-169">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="aefed-169">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="aefed-170">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="aefed-170">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="aefed-171">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="aefed-171">Defines the build configuration.</span></span> <span data-ttu-id="aefed-172">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="aefed-172">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="aefed-173">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="aefed-173">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="aefed-174">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="aefed-174">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="aefed-175">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="aefed-175">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="aefed-176">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="aefed-176">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="aefed-177">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="aefed-177">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="aefed-178">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="aefed-178">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="aefed-179">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="aefed-179">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="aefed-180">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="aefed-180">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="aefed-181">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="aefed-181">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="aefed-182">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="aefed-182">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="aefed-183">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="aefed-183">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="aefed-184">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="aefed-184">Sets the verbosity level of the command.</span></span> <span data-ttu-id="aefed-185">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="aefed-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="aefed-186">Exemplos</span><span class="sxs-lookup"><span data-stu-id="aefed-186">Examples</span></span>

<span data-ttu-id="aefed-187">Execute os testes no projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="aefed-187">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="aefed-188">Execute os testes no projeto `test1`:</span><span class="sxs-lookup"><span data-stu-id="aefed-188">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="aefed-189">Filtrar detalhes da opção</span><span class="sxs-lookup"><span data-stu-id="aefed-189">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="aefed-190">`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="aefed-190">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="aefed-191">`<property>` é um atributo de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="aefed-191">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="aefed-192">A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:</span><span class="sxs-lookup"><span data-stu-id="aefed-192">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="aefed-193">Estrutura de teste</span><span class="sxs-lookup"><span data-stu-id="aefed-193">Test Framework</span></span> | <span data-ttu-id="aefed-194">Propriedades com suporte</span><span class="sxs-lookup"><span data-stu-id="aefed-194">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="aefed-195">MSTest</span><span class="sxs-lookup"><span data-stu-id="aefed-195">MSTest</span></span>         | <ul><li><span data-ttu-id="aefed-196">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="aefed-196">FullyQualifiedName</span></span></li><li><span data-ttu-id="aefed-197">Nome</span><span class="sxs-lookup"><span data-stu-id="aefed-197">Name</span></span></li><li><span data-ttu-id="aefed-198">ClassName</span><span class="sxs-lookup"><span data-stu-id="aefed-198">ClassName</span></span></li><li><span data-ttu-id="aefed-199">Prioridade</span><span class="sxs-lookup"><span data-stu-id="aefed-199">Priority</span></span></li><li><span data-ttu-id="aefed-200">TestCategory</span><span class="sxs-lookup"><span data-stu-id="aefed-200">TestCategory</span></span></li></ul> |
| <span data-ttu-id="aefed-201">xUnit</span><span class="sxs-lookup"><span data-stu-id="aefed-201">xUnit</span></span>          | <ul><li><span data-ttu-id="aefed-202">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="aefed-202">FullyQualifiedName</span></span></li><li><span data-ttu-id="aefed-203">DisplayName</span><span class="sxs-lookup"><span data-stu-id="aefed-203">DisplayName</span></span></li><li><span data-ttu-id="aefed-204">Características</span><span class="sxs-lookup"><span data-stu-id="aefed-204">Traits</span></span></li></ul>                                   |

<span data-ttu-id="aefed-205">O `<operator>` descreve a relação entre a propriedade o valor:</span><span class="sxs-lookup"><span data-stu-id="aefed-205">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="aefed-206">Operador</span><span class="sxs-lookup"><span data-stu-id="aefed-206">Operator</span></span> | <span data-ttu-id="aefed-207">Função</span><span class="sxs-lookup"><span data-stu-id="aefed-207">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="aefed-208">Correspondência exata</span><span class="sxs-lookup"><span data-stu-id="aefed-208">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="aefed-209">Sem correspondência exata</span><span class="sxs-lookup"><span data-stu-id="aefed-209">Not exact match</span></span> |
| `~`      | <span data-ttu-id="aefed-210">Contém</span><span class="sxs-lookup"><span data-stu-id="aefed-210">Contains</span></span>        |

<span data-ttu-id="aefed-211">`<value>` é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="aefed-211">`<value>` is a string.</span></span> <span data-ttu-id="aefed-212">As pesquisas não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="aefed-212">All the lookups are case insensitive.</span></span>

<span data-ttu-id="aefed-213">Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="aefed-213">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="aefed-214">As expressões podem ser associadas a operadores condicionais:</span><span class="sxs-lookup"><span data-stu-id="aefed-214">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="aefed-215">Operador</span><span class="sxs-lookup"><span data-stu-id="aefed-215">Operator</span></span>            | <span data-ttu-id="aefed-216">Função</span><span class="sxs-lookup"><span data-stu-id="aefed-216">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="aefed-217">OU</span><span class="sxs-lookup"><span data-stu-id="aefed-217">OR</span></span>       |
| `&`                 | <span data-ttu-id="aefed-218">AND</span><span class="sxs-lookup"><span data-stu-id="aefed-218">AND</span></span>      |

<span data-ttu-id="aefed-219">Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="aefed-219">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="aefed-220">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="aefed-220">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aefed-221">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aefed-221">See also</span></span>

* [<span data-ttu-id="aefed-222">Estruturas e Destinos</span><span class="sxs-lookup"><span data-stu-id="aefed-222">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
* [<span data-ttu-id="aefed-223">Catálogo do Identificador de Tempo de Execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="aefed-223">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
