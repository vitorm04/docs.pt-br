---
title: Comando dotnet test – CLI do .NET Core
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 7946196b27489870da1c16b15cbf5f078ae89c61
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44137194"
---
# <a name="dotnet-test"></a><span data-ttu-id="bab23-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="bab23-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="bab23-104">Nome</span><span class="sxs-lookup"><span data-stu-id="bab23-104">Name</span></span>

<span data-ttu-id="bab23-105">`dotnet test` - driver de teste do .NET usado para executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="bab23-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bab23-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="bab23-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="bab23-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bab23-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="bab23-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="bab23-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bab23-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bab23-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="bab23-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab23-110">Description</span></span>

<span data-ttu-id="bab23-111">O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="bab23-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="bab23-112">O comando `dotnet test` inicia o aplicativo de console executor de teste especificado para um projeto.</span><span class="sxs-lookup"><span data-stu-id="bab23-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="bab23-113">O executor de teste realiza os testes definidos para uma estrutura de teste de unidade (por exemplo, MSTest, NUnit ou xUnit) e relata o êxito ou a falha de cada teste.</span><span class="sxs-lookup"><span data-stu-id="bab23-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="bab23-114">O executor de teste e a biblioteca de teste de unidade são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.</span><span class="sxs-lookup"><span data-stu-id="bab23-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="bab23-115">Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:</span><span class="sxs-lookup"><span data-stu-id="bab23-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="bab23-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="bab23-116">Arguments</span></span>

`PROJECT`

<span data-ttu-id="bab23-117">Caminho para o projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="bab23-117">Path to the test project.</span></span> <span data-ttu-id="bab23-118">Se não é especificado, usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="bab23-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="bab23-119">Opções</span><span class="sxs-lookup"><span data-stu-id="bab23-119">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="bab23-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bab23-120">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="bab23-121">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="bab23-121">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="bab23-122">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="bab23-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="bab23-123">Essa opção é útil para isolar os testes problemáticos que causam uma falha do host de teste.</span><span class="sxs-lookup"><span data-stu-id="bab23-123">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="bab23-124">Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.</span><span class="sxs-lookup"><span data-stu-id="bab23-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="bab23-125">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="bab23-125">Defines the build configuration.</span></span> <span data-ttu-id="bab23-126">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="bab23-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="bab23-127">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="bab23-127">Enables data collector for the test run.</span></span> <span data-ttu-id="bab23-128">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="bab23-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="bab23-129">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="bab23-129">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="bab23-130">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="bab23-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="bab23-131">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="bab23-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="bab23-132">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="bab23-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="bab23-133">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="bab23-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="bab23-134">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="bab23-134">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="bab23-135">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="bab23-135">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="bab23-136">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="bab23-136">Doesn't build the test project before running it.</span></span> <span data-ttu-id="bab23-137">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="bab23-137">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="bab23-138">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="bab23-138">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="bab23-139">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="bab23-139">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="bab23-140">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="bab23-140">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="bab23-141">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="bab23-141">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="bab23-142">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="bab23-142">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="bab23-143">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="bab23-143">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="bab23-144">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="bab23-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bab23-145">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="bab23-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="bab23-146">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="bab23-146">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="bab23-147">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="bab23-147">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="bab23-148">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="bab23-148">Defines the build configuration.</span></span> <span data-ttu-id="bab23-149">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="bab23-149">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="bab23-150">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="bab23-150">Enables data collector for the test run.</span></span> <span data-ttu-id="bab23-151">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="bab23-151">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="bab23-152">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="bab23-152">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="bab23-153">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="bab23-153">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="bab23-154">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="bab23-154">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="bab23-155">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="bab23-155">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="bab23-156">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="bab23-156">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="bab23-157">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="bab23-157">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="bab23-158">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="bab23-158">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="bab23-159">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="bab23-159">Doesn't build the test project before running it.</span></span> <span data-ttu-id="bab23-160">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="bab23-160">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="bab23-161">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="bab23-161">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="bab23-162">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="bab23-162">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="bab23-163">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="bab23-163">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="bab23-164">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="bab23-164">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="bab23-165">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="bab23-165">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="bab23-166">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="bab23-166">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="bab23-167">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="bab23-167">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bab23-168">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="bab23-168">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bab23-169">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bab23-169">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="bab23-170">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="bab23-170">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="bab23-171">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="bab23-171">Defines the build configuration.</span></span> <span data-ttu-id="bab23-172">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="bab23-172">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="bab23-173">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="bab23-173">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="bab23-174">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="bab23-174">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="bab23-175">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="bab23-175">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="bab23-176">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="bab23-176">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="bab23-177">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="bab23-177">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="bab23-178">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="bab23-178">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="bab23-179">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="bab23-179">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="bab23-180">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="bab23-180">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="bab23-181">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="bab23-181">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="bab23-182">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="bab23-182">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="bab23-183">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="bab23-183">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="bab23-184">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="bab23-184">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bab23-185">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="bab23-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="bab23-186">Exemplos</span><span class="sxs-lookup"><span data-stu-id="bab23-186">Examples</span></span>

<span data-ttu-id="bab23-187">Execute os testes no projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="bab23-187">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="bab23-188">Execute os testes no projeto `test1`:</span><span class="sxs-lookup"><span data-stu-id="bab23-188">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="bab23-189">Execute os testes no projeto no diretório atual e gere um arquivo de resultados de teste no formato trx:</span><span class="sxs-lookup"><span data-stu-id="bab23-189">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="bab23-190">Filtrar detalhes da opção</span><span class="sxs-lookup"><span data-stu-id="bab23-190">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="bab23-191">`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="bab23-191">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="bab23-192">`<property>` é um atributo de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="bab23-192">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="bab23-193">A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:</span><span class="sxs-lookup"><span data-stu-id="bab23-193">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="bab23-194">Estrutura de teste</span><span class="sxs-lookup"><span data-stu-id="bab23-194">Test Framework</span></span> | <span data-ttu-id="bab23-195">Propriedades com suporte</span><span class="sxs-lookup"><span data-stu-id="bab23-195">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="bab23-196">MSTest</span><span class="sxs-lookup"><span data-stu-id="bab23-196">MSTest</span></span>         | <ul><li><span data-ttu-id="bab23-197">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="bab23-197">FullyQualifiedName</span></span></li><li><span data-ttu-id="bab23-198">Nome</span><span class="sxs-lookup"><span data-stu-id="bab23-198">Name</span></span></li><li><span data-ttu-id="bab23-199">ClassName</span><span class="sxs-lookup"><span data-stu-id="bab23-199">ClassName</span></span></li><li><span data-ttu-id="bab23-200">Prioridade</span><span class="sxs-lookup"><span data-stu-id="bab23-200">Priority</span></span></li><li><span data-ttu-id="bab23-201">TestCategory</span><span class="sxs-lookup"><span data-stu-id="bab23-201">TestCategory</span></span></li></ul> |
| <span data-ttu-id="bab23-202">xUnit</span><span class="sxs-lookup"><span data-stu-id="bab23-202">xUnit</span></span>          | <ul><li><span data-ttu-id="bab23-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="bab23-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="bab23-204">DisplayName</span><span class="sxs-lookup"><span data-stu-id="bab23-204">DisplayName</span></span></li><li><span data-ttu-id="bab23-205">Características</span><span class="sxs-lookup"><span data-stu-id="bab23-205">Traits</span></span></li></ul>                                   |

<span data-ttu-id="bab23-206">O `<operator>` descreve a relação entre a propriedade o valor:</span><span class="sxs-lookup"><span data-stu-id="bab23-206">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="bab23-207">Operador</span><span class="sxs-lookup"><span data-stu-id="bab23-207">Operator</span></span> | <span data-ttu-id="bab23-208">Função</span><span class="sxs-lookup"><span data-stu-id="bab23-208">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="bab23-209">Correspondência exata</span><span class="sxs-lookup"><span data-stu-id="bab23-209">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="bab23-210">Sem correspondência exata</span><span class="sxs-lookup"><span data-stu-id="bab23-210">Not exact match</span></span> |
| `~`      | <span data-ttu-id="bab23-211">Contém</span><span class="sxs-lookup"><span data-stu-id="bab23-211">Contains</span></span>        |

<span data-ttu-id="bab23-212">`<value>` é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bab23-212">`<value>` is a string.</span></span> <span data-ttu-id="bab23-213">As pesquisas não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="bab23-213">All the lookups are case insensitive.</span></span>

<span data-ttu-id="bab23-214">Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="bab23-214">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="bab23-215">As expressões podem ser associadas a operadores condicionais:</span><span class="sxs-lookup"><span data-stu-id="bab23-215">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="bab23-216">Operador</span><span class="sxs-lookup"><span data-stu-id="bab23-216">Operator</span></span>            | <span data-ttu-id="bab23-217">Função</span><span class="sxs-lookup"><span data-stu-id="bab23-217">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="bab23-218">OU</span><span class="sxs-lookup"><span data-stu-id="bab23-218">OR</span></span>       |
| `&`                 | <span data-ttu-id="bab23-219">AND</span><span class="sxs-lookup"><span data-stu-id="bab23-219">AND</span></span>      |

<span data-ttu-id="bab23-220">Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="bab23-220">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="bab23-221">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="bab23-221">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bab23-222">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bab23-222">See also</span></span>

* [<span data-ttu-id="bab23-223">Estruturas e Destinos</span><span class="sxs-lookup"><span data-stu-id="bab23-223">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
* [<span data-ttu-id="bab23-224">Catálogo do Identificador de Tempo de Execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="bab23-224">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
