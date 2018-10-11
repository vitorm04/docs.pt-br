---
title: Comando dotnet test – CLI do .NET Core
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: e80ba874ec8d0fbc49858719dc3b9b6e02254c78
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46696450"
---
# <a name="dotnet-test"></a><span data-ttu-id="d598a-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="d598a-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d598a-104">Nome</span><span class="sxs-lookup"><span data-stu-id="d598a-104">Name</span></span>

<span data-ttu-id="d598a-105">`dotnet test` - driver de teste do .NET usado para executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="d598a-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d598a-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="d598a-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d598a-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d598a-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d598a-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d598a-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d598a-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d598a-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="d598a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d598a-110">Description</span></span>

<span data-ttu-id="d598a-111">O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="d598a-111">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="d598a-112">O comando `dotnet test` inicia o aplicativo de console executor de teste especificado para um projeto.</span><span class="sxs-lookup"><span data-stu-id="d598a-112">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="d598a-113">O executor de teste realiza os testes definidos para uma estrutura de teste de unidade (por exemplo, MSTest, NUnit ou xUnit) e relata o êxito ou a falha de cada teste.</span><span class="sxs-lookup"><span data-stu-id="d598a-113">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="d598a-114">Se todos os testes forem bem-sucedidos, o executor de testes retornará 0 como um código de saída; caso contrário, se algum teste falhar, retornará 1.</span><span class="sxs-lookup"><span data-stu-id="d598a-114">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="d598a-115">O executor de teste e a biblioteca de teste de unidade são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.</span><span class="sxs-lookup"><span data-stu-id="d598a-115">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="d598a-116">Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:</span><span class="sxs-lookup"><span data-stu-id="d598a-116">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="d598a-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="d598a-117">Arguments</span></span>

`PROJECT`

<span data-ttu-id="d598a-118">Caminho para o projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="d598a-118">Path to the test project.</span></span> <span data-ttu-id="d598a-119">Se não é especificado, usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="d598a-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="d598a-120">Opções</span><span class="sxs-lookup"><span data-stu-id="d598a-120">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d598a-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d598a-121">.NET Core 2.1</span></span>](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="d598a-122">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="d598a-122">Use the custom test adapters from the specified path in the test run.</span></span>

`--blame`

<span data-ttu-id="d598a-123">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="d598a-123">Runs the tests in blame mode.</span></span> <span data-ttu-id="d598a-124">Essa opção é útil para isolar os testes problemáticos que causam uma falha do host de teste.</span><span class="sxs-lookup"><span data-stu-id="d598a-124">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="d598a-125">Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.</span><span class="sxs-lookup"><span data-stu-id="d598a-125">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d598a-126">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="d598a-126">Defines the build configuration.</span></span> <span data-ttu-id="d598a-127">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="d598a-127">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="d598a-128">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="d598a-128">Enables data collector for the test run.</span></span> <span data-ttu-id="d598a-129">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="d598a-129">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="d598a-130">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="d598a-130">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d598a-131">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="d598a-131">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="d598a-132">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="d598a-132">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="d598a-133">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="d598a-133">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="d598a-134">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="d598a-134">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="d598a-135">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="d598a-135">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="d598a-136">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="d598a-136">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="d598a-137">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="d598a-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="d598a-138">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="d598a-138">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="d598a-139">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="d598a-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d598a-140">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="d598a-140">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="d598a-141">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="d598a-141">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="d598a-142">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="d598a-142">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="d598a-143">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="d598a-143">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="d598a-144">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="d598a-144">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d598a-145">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="d598a-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d598a-146">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d598a-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d598a-147">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d598a-147">.NET Core 2.0</span></span>](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="d598a-148">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="d598a-148">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d598a-149">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="d598a-149">Defines the build configuration.</span></span> <span data-ttu-id="d598a-150">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="d598a-150">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="d598a-151">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="d598a-151">Enables data collector for the test run.</span></span> <span data-ttu-id="d598a-152">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="d598a-152">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="d598a-153">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="d598a-153">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d598a-154">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="d598a-154">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="d598a-155">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="d598a-155">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="d598a-156">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="d598a-156">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="d598a-157">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="d598a-157">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="d598a-158">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="d598a-158">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="d598a-159">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="d598a-159">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="d598a-160">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="d598a-160">Doesn't build the test project before running it.</span></span> <span data-ttu-id="d598a-161">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="d598a-161">It also implicit sets the `--no-restore` flag.</span></span>

`--no-restore`

<span data-ttu-id="d598a-162">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="d598a-162">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d598a-163">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="d598a-163">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="d598a-164">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="d598a-164">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="d598a-165">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="d598a-165">If the specified directory doesn't exist, it's created.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="d598a-166">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="d598a-166">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="d598a-167">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="d598a-167">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d598a-168">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="d598a-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d598a-169">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d598a-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d598a-170">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d598a-170">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="d598a-171">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="d598a-171">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d598a-172">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="d598a-172">Defines the build configuration.</span></span> <span data-ttu-id="d598a-173">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="d598a-173">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="d598a-174">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="d598a-174">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d598a-175">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="d598a-175">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="d598a-176">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="d598a-176">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="d598a-177">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="d598a-177">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="d598a-178">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="d598a-178">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="d598a-179">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="d598a-179">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="d598a-180">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="d598a-180">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="d598a-181">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="d598a-181">Doesn't build the test project before running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d598a-182">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="d598a-182">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="d598a-183">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="d598a-183">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="d598a-184">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="d598a-184">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d598a-185">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="d598a-185">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d598a-186">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d598a-186">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="d598a-187">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d598a-187">Examples</span></span>

<span data-ttu-id="d598a-188">Execute os testes no projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="d598a-188">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="d598a-189">Execute os testes no projeto `test1`:</span><span class="sxs-lookup"><span data-stu-id="d598a-189">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

<span data-ttu-id="d598a-190">Execute os testes no projeto no diretório atual e gere um arquivo de resultados de teste no formato trx:</span><span class="sxs-lookup"><span data-stu-id="d598a-190">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

`dotnet test --logger:trx`

## <a name="filter-option-details"></a><span data-ttu-id="d598a-191">Filtrar detalhes da opção</span><span class="sxs-lookup"><span data-stu-id="d598a-191">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="d598a-192">`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="d598a-192">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="d598a-193">`<property>` é um atributo de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="d598a-193">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="d598a-194">A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:</span><span class="sxs-lookup"><span data-stu-id="d598a-194">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="d598a-195">Estrutura de teste</span><span class="sxs-lookup"><span data-stu-id="d598a-195">Test Framework</span></span> | <span data-ttu-id="d598a-196">Propriedades com suporte</span><span class="sxs-lookup"><span data-stu-id="d598a-196">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="d598a-197">MSTest</span><span class="sxs-lookup"><span data-stu-id="d598a-197">MSTest</span></span>         | <ul><li><span data-ttu-id="d598a-198">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="d598a-198">FullyQualifiedName</span></span></li><li><span data-ttu-id="d598a-199">Nome</span><span class="sxs-lookup"><span data-stu-id="d598a-199">Name</span></span></li><li><span data-ttu-id="d598a-200">ClassName</span><span class="sxs-lookup"><span data-stu-id="d598a-200">ClassName</span></span></li><li><span data-ttu-id="d598a-201">Prioridade</span><span class="sxs-lookup"><span data-stu-id="d598a-201">Priority</span></span></li><li><span data-ttu-id="d598a-202">TestCategory</span><span class="sxs-lookup"><span data-stu-id="d598a-202">TestCategory</span></span></li></ul> |
| <span data-ttu-id="d598a-203">xUnit</span><span class="sxs-lookup"><span data-stu-id="d598a-203">xUnit</span></span>          | <ul><li><span data-ttu-id="d598a-204">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="d598a-204">FullyQualifiedName</span></span></li><li><span data-ttu-id="d598a-205">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d598a-205">DisplayName</span></span></li><li><span data-ttu-id="d598a-206">Características</span><span class="sxs-lookup"><span data-stu-id="d598a-206">Traits</span></span></li></ul>                                   |

<span data-ttu-id="d598a-207">O `<operator>` descreve a relação entre a propriedade o valor:</span><span class="sxs-lookup"><span data-stu-id="d598a-207">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="d598a-208">Operador</span><span class="sxs-lookup"><span data-stu-id="d598a-208">Operator</span></span> | <span data-ttu-id="d598a-209">Função</span><span class="sxs-lookup"><span data-stu-id="d598a-209">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="d598a-210">Correspondência exata</span><span class="sxs-lookup"><span data-stu-id="d598a-210">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="d598a-211">Sem correspondência exata</span><span class="sxs-lookup"><span data-stu-id="d598a-211">Not exact match</span></span> |
| `~`      | <span data-ttu-id="d598a-212">Contém</span><span class="sxs-lookup"><span data-stu-id="d598a-212">Contains</span></span>        |

<span data-ttu-id="d598a-213">`<value>` é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d598a-213">`<value>` is a string.</span></span> <span data-ttu-id="d598a-214">As pesquisas não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="d598a-214">All the lookups are case insensitive.</span></span>

<span data-ttu-id="d598a-215">Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="d598a-215">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="d598a-216">As expressões podem ser associadas a operadores condicionais:</span><span class="sxs-lookup"><span data-stu-id="d598a-216">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="d598a-217">Operador</span><span class="sxs-lookup"><span data-stu-id="d598a-217">Operator</span></span>            | <span data-ttu-id="d598a-218">Função</span><span class="sxs-lookup"><span data-stu-id="d598a-218">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="d598a-219">OU</span><span class="sxs-lookup"><span data-stu-id="d598a-219">OR</span></span>       |
| `&`                 | <span data-ttu-id="d598a-220">AND</span><span class="sxs-lookup"><span data-stu-id="d598a-220">AND</span></span>      |

<span data-ttu-id="d598a-221">Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="d598a-221">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="d598a-222">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="d598a-222">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d598a-223">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d598a-223">See also</span></span>

* [<span data-ttu-id="d598a-224">Estruturas e Destinos</span><span class="sxs-lookup"><span data-stu-id="d598a-224">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
* [<span data-ttu-id="d598a-225">Catálogo do Identificador de Tempo de Execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="d598a-225">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
