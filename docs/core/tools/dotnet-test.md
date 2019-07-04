---
title: Comando dotnet test
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
ms.date: 05/29/2018
ms.openlocfilehash: 6b67273f549edd7712237756a5aba13d5cb59a61
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410361"
---
# <a name="dotnet-test"></a><span data-ttu-id="925cb-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="925cb-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="925cb-104">Nome</span><span class="sxs-lookup"><span data-stu-id="925cb-104">Name</span></span>

<span data-ttu-id="925cb-105">`dotnet test` - driver de teste do .NET usado para executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="925cb-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="925cb-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="925cb-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="925cb-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="925cb-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="925cb-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="925cb-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="925cb-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="925cb-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="925cb-110">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="925cb-110">Description</span></span>

<span data-ttu-id="925cb-111">O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="925cb-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="925cb-112">O comando `dotnet test` inicia o aplicativo de console executor de teste especificado para um projeto.</span><span class="sxs-lookup"><span data-stu-id="925cb-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="925cb-113">O executor de teste realiza os testes definidos para uma estrutura de teste de unidade (por exemplo, MSTest, NUnit ou xUnit) e relata o êxito ou a falha de cada teste.</span><span class="sxs-lookup"><span data-stu-id="925cb-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="925cb-114">Se todos os testes forem bem-sucedidos, o executor de testes retornará 0 como um código de saída; caso contrário, se algum teste falhar, retornará 1.</span><span class="sxs-lookup"><span data-stu-id="925cb-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="925cb-115">O executor de teste e a biblioteca de teste de unidade são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.</span><span class="sxs-lookup"><span data-stu-id="925cb-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="925cb-116">Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:</span><span class="sxs-lookup"><span data-stu-id="925cb-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="925cb-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="925cb-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="925cb-118">Caminho para o projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="925cb-118">Path to the test project.</span></span> <span data-ttu-id="925cb-119">Se não é especificado, usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="925cb-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="925cb-120">Opções</span><span class="sxs-lookup"><span data-stu-id="925cb-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="925cb-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="925cb-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="925cb-122">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="925cb-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="925cb-123">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="925cb-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="925cb-124">Essa opção é útil para isolar os testes problemáticos que causam uma falha do host de teste.</span><span class="sxs-lookup"><span data-stu-id="925cb-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="925cb-125">Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.</span><span class="sxs-lookup"><span data-stu-id="925cb-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="925cb-126">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="925cb-126">Defines the build configuration.</span></span> <span data-ttu-id="925cb-127">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="925cb-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="925cb-128">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="925cb-128">Enables data collector for the test run.</span></span> <span data-ttu-id="925cb-129">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="925cb-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="925cb-130">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="925cb-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="925cb-131">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="925cb-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="925cb-132">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="925cb-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="925cb-133">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="925cb-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="925cb-134">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="925cb-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="925cb-135">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="925cb-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="925cb-136">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="925cb-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="925cb-137">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="925cb-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="925cb-138">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="925cb-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="925cb-139">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="925cb-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="925cb-140">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="925cb-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="925cb-141">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="925cb-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="925cb-142">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="925cb-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="925cb-143">O arquivo `.runsettings` a ser usado para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="925cb-143">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="925cb-144">Configurar testes de unidade usando um arquivo `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="925cb-144">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="925cb-145">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="925cb-145">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="925cb-146">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="925cb-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="925cb-147">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="925cb-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="925cb-148">Argumentos passados como configurações RunSettings para o teste.</span><span class="sxs-lookup"><span data-stu-id="925cb-148">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="925cb-149">Os argumentos são especificados como pares `[name]=[value]` após "-- " (observe o espaço após --).</span><span class="sxs-lookup"><span data-stu-id="925cb-149">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="925cb-150">Um espaço é usado para separar vários pares `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="925cb-150">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="925cb-151">Exemplo: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="925cb-151">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="925cb-152">Para obter mais informações sobre RunSettings, confira [vstest.console.exe: Passando args de RunSettings](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="925cb-152">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="925cb-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="925cb-153">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="925cb-154">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="925cb-154">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="925cb-155">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="925cb-155">Defines the build configuration.</span></span> <span data-ttu-id="925cb-156">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="925cb-156">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="925cb-157">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="925cb-157">Enables data collector for the test run.</span></span> <span data-ttu-id="925cb-158">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="925cb-158">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="925cb-159">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="925cb-159">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="925cb-160">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="925cb-160">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="925cb-161">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="925cb-161">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="925cb-162">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="925cb-162">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="925cb-163">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="925cb-163">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="925cb-164">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="925cb-164">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="925cb-165">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="925cb-165">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="925cb-166">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="925cb-166">Doesn't build the test project before running it.</span></span> <span data-ttu-id="925cb-167">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="925cb-167">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="925cb-168">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="925cb-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="925cb-169">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="925cb-169">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="925cb-170">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="925cb-170">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="925cb-171">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="925cb-171">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="925cb-172">O arquivo `.runsettings` a ser usado para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="925cb-172">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="925cb-173">Configurar testes de unidade usando um arquivo `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="925cb-173">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="925cb-174">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="925cb-174">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="925cb-175">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="925cb-175">Sets the verbosity level of the command.</span></span> <span data-ttu-id="925cb-176">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="925cb-176">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="925cb-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="925cb-177">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="925cb-178">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="925cb-178">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="925cb-179">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="925cb-179">Defines the build configuration.</span></span> <span data-ttu-id="925cb-180">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="925cb-180">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="925cb-181">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="925cb-181">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="925cb-182">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="925cb-182">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="925cb-183">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="925cb-183">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="925cb-184">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="925cb-184">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="925cb-185">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="925cb-185">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="925cb-186">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="925cb-186">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="925cb-187">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="925cb-187">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="925cb-188">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="925cb-188">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="925cb-189">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="925cb-189">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="925cb-190">O arquivo `.runsettings` a ser usado para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="925cb-190">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="925cb-191">Configurar testes de unidade usando um arquivo `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="925cb-191">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

<span data-ttu-id="925cb-192">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="925cb-192">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="925cb-193">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="925cb-193">Sets the verbosity level of the command.</span></span> <span data-ttu-id="925cb-194">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="925cb-194">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="925cb-195">Exemplos</span><span class="sxs-lookup"><span data-stu-id="925cb-195">Examples</span></span>

<span data-ttu-id="925cb-196">Execute os testes no projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="925cb-196">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="925cb-197">Execute os testes no projeto `test1`:</span><span class="sxs-lookup"><span data-stu-id="925cb-197">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="925cb-198">Execute os testes no projeto no diretório atual e gere um arquivo de resultados de teste no formato trx:</span><span class="sxs-lookup"><span data-stu-id="925cb-198">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="925cb-199">Filtrar detalhes da opção</span><span class="sxs-lookup"><span data-stu-id="925cb-199">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="925cb-200">`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="925cb-200">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="925cb-201">`<property>` é um atributo de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="925cb-201">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="925cb-202">A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:</span><span class="sxs-lookup"><span data-stu-id="925cb-202">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="925cb-203">Estrutura de teste</span><span class="sxs-lookup"><span data-stu-id="925cb-203">Test Framework</span></span> | <span data-ttu-id="925cb-204">Propriedades com suporte</span><span class="sxs-lookup"><span data-stu-id="925cb-204">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="925cb-205">MSTest</span><span class="sxs-lookup"><span data-stu-id="925cb-205">MSTest</span></span>         | <ul><li><span data-ttu-id="925cb-206">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="925cb-206">FullyQualifiedName</span></span></li><li><span data-ttu-id="925cb-207">Nome</span><span class="sxs-lookup"><span data-stu-id="925cb-207">Name</span></span></li><li><span data-ttu-id="925cb-208">ClassName</span><span class="sxs-lookup"><span data-stu-id="925cb-208">ClassName</span></span></li><li><span data-ttu-id="925cb-209">Prioridade</span><span class="sxs-lookup"><span data-stu-id="925cb-209">Priority</span></span></li><li><span data-ttu-id="925cb-210">TestCategory</span><span class="sxs-lookup"><span data-stu-id="925cb-210">TestCategory</span></span></li></ul> |
| <span data-ttu-id="925cb-211">xUnit</span><span class="sxs-lookup"><span data-stu-id="925cb-211">xUnit</span></span>          | <ul><li><span data-ttu-id="925cb-212">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="925cb-212">FullyQualifiedName</span></span></li><li><span data-ttu-id="925cb-213">DisplayName</span><span class="sxs-lookup"><span data-stu-id="925cb-213">DisplayName</span></span></li><li><span data-ttu-id="925cb-214">Características</span><span class="sxs-lookup"><span data-stu-id="925cb-214">Traits</span></span></li></ul>                                   |

<span data-ttu-id="925cb-215">O `<operator>` descreve a relação entre a propriedade o valor:</span><span class="sxs-lookup"><span data-stu-id="925cb-215">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="925cb-216">Operador</span><span class="sxs-lookup"><span data-stu-id="925cb-216">Operator</span></span> | <span data-ttu-id="925cb-217">Função</span><span class="sxs-lookup"><span data-stu-id="925cb-217">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="925cb-218">Correspondência exata</span><span class="sxs-lookup"><span data-stu-id="925cb-218">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="925cb-219">Sem correspondência exata</span><span class="sxs-lookup"><span data-stu-id="925cb-219">Not exact match</span></span> |
| `~`      | <span data-ttu-id="925cb-220">Contém</span><span class="sxs-lookup"><span data-stu-id="925cb-220">Contains</span></span>        |

<span data-ttu-id="925cb-221">`<value>` é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="925cb-221">`<value>` is a string.</span></span> <span data-ttu-id="925cb-222">As pesquisas não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="925cb-222">All the lookups are case insensitive.</span></span>

<span data-ttu-id="925cb-223">Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="925cb-223">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="925cb-224">As expressões podem ser associadas a operadores condicionais:</span><span class="sxs-lookup"><span data-stu-id="925cb-224">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="925cb-225">Operador</span><span class="sxs-lookup"><span data-stu-id="925cb-225">Operator</span></span>            | <span data-ttu-id="925cb-226">Função</span><span class="sxs-lookup"><span data-stu-id="925cb-226">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="925cb-227">OU</span><span class="sxs-lookup"><span data-stu-id="925cb-227">OR</span></span>       |
| `&`                 | <span data-ttu-id="925cb-228">AND</span><span class="sxs-lookup"><span data-stu-id="925cb-228">AND</span></span>      |

<span data-ttu-id="925cb-229">Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="925cb-229">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="925cb-230">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="925cb-230">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="925cb-231">Consulte também</span><span class="sxs-lookup"><span data-stu-id="925cb-231">See also</span></span>

- [<span data-ttu-id="925cb-232">Estruturas e Destinos</span><span class="sxs-lookup"><span data-stu-id="925cb-232">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="925cb-233">Catálogo do Identificador de Tempo de Execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="925cb-233">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
