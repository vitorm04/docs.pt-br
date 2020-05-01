---
title: Comando dotnet test
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
ms.date: 04/29/2020
ms.openlocfilehash: a8218b6596601069b89a60ad018adf89a1f47cf6
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624885"
---
# <a name="dotnet-test"></a><span data-ttu-id="14671-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="14671-103">dotnet test</span></span>

<span data-ttu-id="14671-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="14671-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="14671-105">Nome</span><span class="sxs-lookup"><span data-stu-id="14671-105">Name</span></span>

<span data-ttu-id="14671-106">`dotnet test` - driver de teste do .NET usado para executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="14671-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="14671-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="14671-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path <PATH_TO_ADAPTER>] [--blame]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_FRIENDLY_NAME>]
    [-d|--diag <PATH_TO_DIAGNOSTICS_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER_URI/FRIENDLY_NAME>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <PATH>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="14671-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="14671-108">Description</span></span>

<span data-ttu-id="14671-109">O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="14671-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="14671-110">O comando `dotnet test` inicia o aplicativo de console executor de teste especificado para um projeto.</span><span class="sxs-lookup"><span data-stu-id="14671-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="14671-111">O executor de teste realiza os testes definidos para uma estrutura de teste de unidade (por exemplo, MSTest, NUnit ou xUnit) e relata o êxito ou a falha de cada teste.</span><span class="sxs-lookup"><span data-stu-id="14671-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="14671-112">Se todos os testes forem bem-sucedidos, o executor de testes retornará 0 como um código de saída; caso contrário, se algum teste falhar, retornará 1.</span><span class="sxs-lookup"><span data-stu-id="14671-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="14671-113">Para projetos de vários destinos, os testes são executados para cada estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="14671-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="14671-114">O executor de teste e a biblioteca de teste de unidade são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.</span><span class="sxs-lookup"><span data-stu-id="14671-114">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="14671-115">Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:</span><span class="sxs-lookup"><span data-stu-id="14671-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a><span data-ttu-id="14671-116">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="14671-116">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="14671-117">Argumentos</span><span class="sxs-lookup"><span data-stu-id="14671-117">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="14671-118">Caminho para o projeto de teste ou solução.</span><span class="sxs-lookup"><span data-stu-id="14671-118">Path to the test project or solution.</span></span> <span data-ttu-id="14671-119">Se não é especificado, usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="14671-119">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="14671-120">Opções</span><span class="sxs-lookup"><span data-stu-id="14671-120">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="14671-121">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="14671-121">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="14671-122">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="14671-122">Runs the tests in blame mode.</span></span> <span data-ttu-id="14671-123">Essa opção é útil para isolar testes problemáticos que causam falha no host de teste.</span><span class="sxs-lookup"><span data-stu-id="14671-123">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="14671-124">Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.</span><span class="sxs-lookup"><span data-stu-id="14671-124">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="14671-125">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="14671-125">Defines the build configuration.</span></span> <span data-ttu-id="14671-126">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="14671-126">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="14671-127">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="14671-127">Enables data collector for the test run.</span></span> <span data-ttu-id="14671-128">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="14671-128">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="14671-129">Habilita o modo de diagnóstico para a plataforma de teste e grava as mensagens de diagnóstico no arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="14671-129">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="14671-130">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="14671-130">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="14671-131">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="14671-131">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="14671-132">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="14671-132">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="14671-133">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="14671-133">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="14671-134">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="14671-134">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="14671-135">Permite que o comando pare e aguarde entrada ou ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="14671-135">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="14671-136">Por exemplo, para concluir a autenticação.</span><span class="sxs-lookup"><span data-stu-id="14671-136">For example, to complete authentication.</span></span> <span data-ttu-id="14671-137">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="14671-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="14671-138">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="14671-138">Specifies a logger for test results.</span></span> <span data-ttu-id="14671-139">Ao contrário do MSBuild, o teste dotnet não aceita abreviações `-l "console;v=d"` : `-l "console;verbosity=detailed"`em vez de usar.</span><span class="sxs-lookup"><span data-stu-id="14671-139">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="14671-140">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="14671-140">Doesn't build the test project before running it.</span></span> <span data-ttu-id="14671-141">Ele também define implicitamente o- `--no-restore` Flag.</span><span class="sxs-lookup"><span data-stu-id="14671-141">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="14671-142">Executar testes sem exibir o banner do Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="14671-142">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="14671-143">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="14671-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="14671-144">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="14671-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="14671-145">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="14671-145">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="14671-146">Se não for especificado, o caminho padrão será `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="14671-146">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="14671-147">Para projetos com várias estruturas de destino (por meio `TargetFrameworks` da propriedade), também é necessário definir `--framework` quando você especifica essa opção.</span><span class="sxs-lookup"><span data-stu-id="14671-147">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="14671-148">`dotnet test`sempre execute testes do diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="14671-148">`dotnet test` always run tests from the output directory.</span></span> <span data-ttu-id="14671-149">Você pode usar <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> para consumir ativos de teste no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="14671-149">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="14671-150">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="14671-150">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="14671-151">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="14671-151">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="14671-152">O padrão é `TestResults` o diretório que contém o arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="14671-152">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="14671-153">O tempo de execução de destino para o qual testar.</span><span class="sxs-lookup"><span data-stu-id="14671-153">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="14671-154">O arquivo `.runsettings` a ser usado para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="14671-154">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="14671-155">Observe que o `TargetPlatform` elemento (x86 | x64) não tem nenhum efeito `dotnet test`para.</span><span class="sxs-lookup"><span data-stu-id="14671-155">Note that the `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="14671-156">Para executar testes direcionados para x86, instale a versão x86 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="14671-156">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="14671-157">O bit de bits do *dotnet. exe* que está no caminho é o que será usado para executar testes.</span><span class="sxs-lookup"><span data-stu-id="14671-157">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="14671-158">para obter mais informações, consulte os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="14671-158">for more information, see the following resources:</span></span>

  - [<span data-ttu-id="14671-159">Configurar testes de unidade usando um arquivo `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="14671-159">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="14671-160">Configurar uma execução de teste</span><span class="sxs-lookup"><span data-stu-id="14671-160">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="14671-161">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="14671-161">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="14671-162">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="14671-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="14671-163">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="14671-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="14671-164">O padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="14671-164">The default is `minimal`.</span></span> <span data-ttu-id="14671-165">Para obter mais informações, consulte <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="14671-165">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="14671-166">**`RunSettings`** argumentos</span><span class="sxs-lookup"><span data-stu-id="14671-166">**`RunSettings`** arguments</span></span>

  <span data-ttu-id="14671-167">Os argumentos são passados `RunSettings` como configurações para o teste.</span><span class="sxs-lookup"><span data-stu-id="14671-167">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="14671-168">Os argumentos são especificados como pares `[name]=[value]` após "-- " (observe o espaço após --).</span><span class="sxs-lookup"><span data-stu-id="14671-168">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="14671-169">Um espaço é usado para separar vários pares `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="14671-169">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="14671-170">Exemplo: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="14671-170">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="14671-171">Para obter mais informações, consulte [passando argumentos RunSettings por meio da linha de comando](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="14671-171">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="14671-172">Exemplos</span><span class="sxs-lookup"><span data-stu-id="14671-172">Examples</span></span>

- <span data-ttu-id="14671-173">Execute os testes no projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="14671-173">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="14671-174">Execute os testes no projeto `test1`:</span><span class="sxs-lookup"><span data-stu-id="14671-174">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="14671-175">Execute os testes no projeto no diretório atual e gere um arquivo de resultados de teste no formato TRX:</span><span class="sxs-lookup"><span data-stu-id="14671-175">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="14671-176">Execute os testes no projeto no diretório atual e faça logon com detalhes detalhados no console:</span><span class="sxs-lookup"><span data-stu-id="14671-176">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a><span data-ttu-id="14671-177">Filtrar detalhes da opção</span><span class="sxs-lookup"><span data-stu-id="14671-177">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="14671-178">`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="14671-178">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="14671-179">`<property>` é um atributo de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="14671-179">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="14671-180">A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:</span><span class="sxs-lookup"><span data-stu-id="14671-180">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="14671-181">Estrutura de teste</span><span class="sxs-lookup"><span data-stu-id="14671-181">Test Framework</span></span> | <span data-ttu-id="14671-182">Propriedades com suporte</span><span class="sxs-lookup"><span data-stu-id="14671-182">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="14671-183">MSTest</span><span class="sxs-lookup"><span data-stu-id="14671-183">MSTest</span></span>         | <ul><li><span data-ttu-id="14671-184">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="14671-184">FullyQualifiedName</span></span></li><li><span data-ttu-id="14671-185">Nome</span><span class="sxs-lookup"><span data-stu-id="14671-185">Name</span></span></li><li><span data-ttu-id="14671-186">ClassName</span><span class="sxs-lookup"><span data-stu-id="14671-186">ClassName</span></span></li><li><span data-ttu-id="14671-187">Prioridade</span><span class="sxs-lookup"><span data-stu-id="14671-187">Priority</span></span></li><li><span data-ttu-id="14671-188">TestCategory</span><span class="sxs-lookup"><span data-stu-id="14671-188">TestCategory</span></span></li></ul> |
| <span data-ttu-id="14671-189">xUnit</span><span class="sxs-lookup"><span data-stu-id="14671-189">xUnit</span></span>          | <ul><li><span data-ttu-id="14671-190">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="14671-190">FullyQualifiedName</span></span></li><li><span data-ttu-id="14671-191">DisplayName</span><span class="sxs-lookup"><span data-stu-id="14671-191">DisplayName</span></span></li><li><span data-ttu-id="14671-192">Características</span><span class="sxs-lookup"><span data-stu-id="14671-192">Traits</span></span></li></ul>                                   |

<span data-ttu-id="14671-193">O `<operator>` descreve a relação entre a propriedade o valor:</span><span class="sxs-lookup"><span data-stu-id="14671-193">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="14671-194">Operador</span><span class="sxs-lookup"><span data-stu-id="14671-194">Operator</span></span> | <span data-ttu-id="14671-195">Função</span><span class="sxs-lookup"><span data-stu-id="14671-195">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="14671-196">Correspondência exata</span><span class="sxs-lookup"><span data-stu-id="14671-196">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="14671-197">Sem correspondência exata</span><span class="sxs-lookup"><span data-stu-id="14671-197">Not exact match</span></span> |
| `~`      | <span data-ttu-id="14671-198">Contém</span><span class="sxs-lookup"><span data-stu-id="14671-198">Contains</span></span>        |
| `!~`     | <span data-ttu-id="14671-199">Não contém</span><span class="sxs-lookup"><span data-stu-id="14671-199">Not contains</span></span>    |

<span data-ttu-id="14671-200">`<value>` é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="14671-200">`<value>` is a string.</span></span> <span data-ttu-id="14671-201">As pesquisas não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="14671-201">All the lookups are case insensitive.</span></span>

<span data-ttu-id="14671-202">Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="14671-202">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="14671-203">As expressões podem ser associadas a operadores condicionais:</span><span class="sxs-lookup"><span data-stu-id="14671-203">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="14671-204">Operador</span><span class="sxs-lookup"><span data-stu-id="14671-204">Operator</span></span>            | <span data-ttu-id="14671-205">Função</span><span class="sxs-lookup"><span data-stu-id="14671-205">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="14671-206">OU</span><span class="sxs-lookup"><span data-stu-id="14671-206">OR</span></span>       |
| `&`                 | <span data-ttu-id="14671-207">AND</span><span class="sxs-lookup"><span data-stu-id="14671-207">AND</span></span>      |

<span data-ttu-id="14671-208">Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="14671-208">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="14671-209">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="14671-209">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="14671-210">Confira também</span><span class="sxs-lookup"><span data-stu-id="14671-210">See also</span></span>

- [<span data-ttu-id="14671-211">Estruturas e destinos</span><span class="sxs-lookup"><span data-stu-id="14671-211">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="14671-212">Catálogo do Identificador de Runtime do .NET Core</span><span class="sxs-lookup"><span data-stu-id="14671-212">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="14671-213">Passando argumentos RunSettings por meio de linha de comando</span><span class="sxs-lookup"><span data-stu-id="14671-213">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
