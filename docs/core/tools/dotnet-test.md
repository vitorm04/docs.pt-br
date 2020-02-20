---
title: Comando dotnet test
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
ms.date: 05/29/2018
ms.openlocfilehash: 909815151265117395c6d8d13b4443a245c05f9e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451188"
---
# <a name="dotnet-test"></a><span data-ttu-id="422dc-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="422dc-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="422dc-104">Nome</span><span class="sxs-lookup"><span data-stu-id="422dc-104">Name</span></span>

<span data-ttu-id="422dc-105">`dotnet test` - driver de teste do .NET usado para executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="422dc-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="422dc-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="422dc-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[<span data-ttu-id="422dc-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="422dc-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20"></a>[<span data-ttu-id="422dc-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="422dc-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1x"></a>[<span data-ttu-id="422dc-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="422dc-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="422dc-110">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="422dc-110">Description</span></span>

<span data-ttu-id="422dc-111">O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="422dc-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="422dc-112">O comando `dotnet test` inicia o aplicativo de console executor de teste especificado para um projeto.</span><span class="sxs-lookup"><span data-stu-id="422dc-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="422dc-113">O executor de teste realiza os testes definidos para uma estrutura de teste de unidade (por exemplo, MSTest, NUnit ou xUnit) e relata o êxito ou a falha de cada teste.</span><span class="sxs-lookup"><span data-stu-id="422dc-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="422dc-114">Se todos os testes forem bem-sucedidos, o executor de testes retornará 0 como um código de saída; caso contrário, se algum teste falhar, retornará 1.</span><span class="sxs-lookup"><span data-stu-id="422dc-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="422dc-115">O executor de teste e a biblioteca de teste de unidade são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.</span><span class="sxs-lookup"><span data-stu-id="422dc-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="422dc-116">Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:</span><span class="sxs-lookup"><span data-stu-id="422dc-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="422dc-117">Argumentos</span><span class="sxs-lookup"><span data-stu-id="422dc-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="422dc-118">Caminho para o projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="422dc-118">Path to the test project.</span></span> <span data-ttu-id="422dc-119">Se não é especificado, usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="422dc-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="422dc-120">Opções</span><span class="sxs-lookup"><span data-stu-id="422dc-120">Options</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="422dc-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="422dc-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="422dc-122">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="422dc-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="422dc-123">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="422dc-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="422dc-124">Essa opção é útil para isolar os testes problemáticos que causam uma falha do host de teste.</span><span class="sxs-lookup"><span data-stu-id="422dc-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="422dc-125">Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.</span><span class="sxs-lookup"><span data-stu-id="422dc-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="422dc-126">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="422dc-126">Defines the build configuration.</span></span> <span data-ttu-id="422dc-127">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="422dc-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="422dc-128">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="422dc-128">Enables data collector for the test run.</span></span> <span data-ttu-id="422dc-129">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="422dc-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="422dc-130">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="422dc-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="422dc-131">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="422dc-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="422dc-132">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="422dc-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="422dc-133">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="422dc-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="422dc-134">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="422dc-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="422dc-135">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="422dc-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="422dc-136">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="422dc-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="422dc-137">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="422dc-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="422dc-138">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="422dc-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="422dc-139">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="422dc-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="422dc-140">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="422dc-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="422dc-141">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="422dc-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="422dc-142">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="422dc-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="422dc-143">O arquivo `.runsettings` a ser usado para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="422dc-143">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="422dc-144">Configurar testes de unidade usando um arquivo `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="422dc-144">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

<span data-ttu-id="422dc-145">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="422dc-145">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="422dc-146">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="422dc-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="422dc-147">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="422dc-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`RunSettings arguments`

<span data-ttu-id="422dc-148">Argumentos passados como configurações RunSettings para o teste.</span><span class="sxs-lookup"><span data-stu-id="422dc-148">Arguments passed as RunSettings configurations for the test.</span></span> <span data-ttu-id="422dc-149">Os argumentos são especificados como pares `[name]=[value]` após "-- " (observe o espaço após --).</span><span class="sxs-lookup"><span data-stu-id="422dc-149">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="422dc-150">Um espaço é usado para separar vários pares `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="422dc-150">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

<span data-ttu-id="422dc-151">Exemplo: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="422dc-151">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

<span data-ttu-id="422dc-152">Confira mais informações sobre RunSettings em [vstest.console.exe: passando args RunSettings](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="422dc-152">For more information about RunSettings, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="422dc-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="422dc-153">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="422dc-154">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="422dc-154">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="422dc-155">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="422dc-155">Defines the build configuration.</span></span> <span data-ttu-id="422dc-156">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="422dc-156">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="422dc-157">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="422dc-157">Enables data collector for the test run.</span></span> <span data-ttu-id="422dc-158">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="422dc-158">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="422dc-159">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="422dc-159">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="422dc-160">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="422dc-160">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="422dc-161">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="422dc-161">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="422dc-162">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="422dc-162">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="422dc-163">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="422dc-163">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="422dc-164">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="422dc-164">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="422dc-165">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="422dc-165">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="422dc-166">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="422dc-166">Doesn't build the test project before running it.</span></span> <span data-ttu-id="422dc-167">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="422dc-167">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="422dc-168">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="422dc-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="422dc-169">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="422dc-169">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="422dc-170">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="422dc-170">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="422dc-171">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="422dc-171">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="422dc-172">O arquivo `.runsettings` a ser usado para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="422dc-172">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="422dc-173">Configurar testes de unidade usando um arquivo `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="422dc-173">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

<span data-ttu-id="422dc-174">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="422dc-174">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="422dc-175">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="422dc-175">Sets the verbosity level of the command.</span></span> <span data-ttu-id="422dc-176">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="422dc-176">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="422dc-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="422dc-177">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="422dc-178">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="422dc-178">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="422dc-179">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="422dc-179">Defines the build configuration.</span></span> <span data-ttu-id="422dc-180">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="422dc-180">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="422dc-181">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="422dc-181">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="422dc-182">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="422dc-182">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="422dc-183">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="422dc-183">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="422dc-184">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="422dc-184">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="422dc-185">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="422dc-185">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="422dc-186">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="422dc-186">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="422dc-187">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="422dc-187">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="422dc-188">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="422dc-188">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="422dc-189">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="422dc-189">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="422dc-190">O arquivo `.runsettings` a ser usado para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="422dc-190">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="422dc-191">Configurar testes de unidade usando um arquivo `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="422dc-191">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

<span data-ttu-id="422dc-192">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="422dc-192">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="422dc-193">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="422dc-193">Sets the verbosity level of the command.</span></span> <span data-ttu-id="422dc-194">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="422dc-194">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="422dc-195">Exemplos</span><span class="sxs-lookup"><span data-stu-id="422dc-195">Examples</span></span>

<span data-ttu-id="422dc-196">Execute os testes no projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="422dc-196">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="422dc-197">Execute os testes no projeto `test1`:</span><span class="sxs-lookup"><span data-stu-id="422dc-197">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="422dc-198">Execute os testes no projeto no diretório atual e gere um arquivo de resultados de teste no formato trx:</span><span class="sxs-lookup"><span data-stu-id="422dc-198">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger trx`

## <a name="filter-option-details"></a><span data-ttu-id="422dc-199">Filtrar detalhes da opção</span><span class="sxs-lookup"><span data-stu-id="422dc-199">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="422dc-200">`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="422dc-200">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="422dc-201">`<property>` é um atributo de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="422dc-201">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="422dc-202">A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:</span><span class="sxs-lookup"><span data-stu-id="422dc-202">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="422dc-203">Estrutura de teste</span><span class="sxs-lookup"><span data-stu-id="422dc-203">Test Framework</span></span> | <span data-ttu-id="422dc-204">Propriedades com suporte</span><span class="sxs-lookup"><span data-stu-id="422dc-204">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="422dc-205">MSTest</span><span class="sxs-lookup"><span data-stu-id="422dc-205">MSTest</span></span>         | <ul><li><span data-ttu-id="422dc-206">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="422dc-206">FullyQualifiedName</span></span></li><li><span data-ttu-id="422dc-207">Nome</span><span class="sxs-lookup"><span data-stu-id="422dc-207">Name</span></span></li><li><span data-ttu-id="422dc-208">ClassName</span><span class="sxs-lookup"><span data-stu-id="422dc-208">ClassName</span></span></li><li><span data-ttu-id="422dc-209">Prioridade</span><span class="sxs-lookup"><span data-stu-id="422dc-209">Priority</span></span></li><li><span data-ttu-id="422dc-210">TestCategory</span><span class="sxs-lookup"><span data-stu-id="422dc-210">TestCategory</span></span></li></ul> |
| <span data-ttu-id="422dc-211">xUnit</span><span class="sxs-lookup"><span data-stu-id="422dc-211">xUnit</span></span>          | <ul><li><span data-ttu-id="422dc-212">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="422dc-212">FullyQualifiedName</span></span></li><li><span data-ttu-id="422dc-213">DisplayName</span><span class="sxs-lookup"><span data-stu-id="422dc-213">DisplayName</span></span></li><li><span data-ttu-id="422dc-214">Características</span><span class="sxs-lookup"><span data-stu-id="422dc-214">Traits</span></span></li></ul>                                   |

<span data-ttu-id="422dc-215">O `<operator>` descreve a relação entre a propriedade o valor:</span><span class="sxs-lookup"><span data-stu-id="422dc-215">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="422dc-216">Operador</span><span class="sxs-lookup"><span data-stu-id="422dc-216">Operator</span></span> | <span data-ttu-id="422dc-217">Função</span><span class="sxs-lookup"><span data-stu-id="422dc-217">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="422dc-218">Correspondência exata</span><span class="sxs-lookup"><span data-stu-id="422dc-218">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="422dc-219">Sem correspondência exata</span><span class="sxs-lookup"><span data-stu-id="422dc-219">Not exact match</span></span> |
| `~`      | <span data-ttu-id="422dc-220">Contém</span><span class="sxs-lookup"><span data-stu-id="422dc-220">Contains</span></span>        |
| `!~`     | <span data-ttu-id="422dc-221">Não contém</span><span class="sxs-lookup"><span data-stu-id="422dc-221">Not contains</span></span>    |

<span data-ttu-id="422dc-222">`<value>` é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="422dc-222">`<value>` is a string.</span></span> <span data-ttu-id="422dc-223">As pesquisas não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="422dc-223">All the lookups are case insensitive.</span></span>

<span data-ttu-id="422dc-224">Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="422dc-224">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="422dc-225">As expressões podem ser associadas a operadores condicionais:</span><span class="sxs-lookup"><span data-stu-id="422dc-225">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="422dc-226">Operador</span><span class="sxs-lookup"><span data-stu-id="422dc-226">Operator</span></span>            | <span data-ttu-id="422dc-227">Função</span><span class="sxs-lookup"><span data-stu-id="422dc-227">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="422dc-228">OU</span><span class="sxs-lookup"><span data-stu-id="422dc-228">OR</span></span>       |
| `&`                 | <span data-ttu-id="422dc-229">AND</span><span class="sxs-lookup"><span data-stu-id="422dc-229">AND</span></span>      |

<span data-ttu-id="422dc-230">Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="422dc-230">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="422dc-231">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="422dc-231">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="422dc-232">Confira também</span><span class="sxs-lookup"><span data-stu-id="422dc-232">See also</span></span>

- [<span data-ttu-id="422dc-233">Estruturas e destinos</span><span class="sxs-lookup"><span data-stu-id="422dc-233">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="422dc-234">Catálogo do Identificador de Runtime do .NET Core</span><span class="sxs-lookup"><span data-stu-id="422dc-234">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
