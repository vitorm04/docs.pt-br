---
title: Comando dotnet test
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
ms.date: 02/27/2020
ms.openlocfilehash: 69b8101f9b1052f4726dce8a86234da99f5dc89c
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102731"
---
# <a name="dotnet-test"></a><span data-ttu-id="2391b-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="2391b-103">dotnet test</span></span>

<span data-ttu-id="2391b-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="2391b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2391b-105">Nome</span><span class="sxs-lookup"><span data-stu-id="2391b-105">Name</span></span>

<span data-ttu-id="2391b-106">`dotnet test` - driver de teste do .NET usado para executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="2391b-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2391b-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="2391b-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="2391b-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="2391b-108">Description</span></span>

<span data-ttu-id="2391b-109">O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="2391b-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="2391b-110">O comando `dotnet test` inicia o aplicativo de console executor de teste especificado para um projeto.</span><span class="sxs-lookup"><span data-stu-id="2391b-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="2391b-111">O executor de teste realiza os testes definidos para uma estrutura de teste de unidade (por exemplo, MSTest, NUnit ou xUnit) e relata o êxito ou a falha de cada teste.</span><span class="sxs-lookup"><span data-stu-id="2391b-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="2391b-112">Se todos os testes forem bem-sucedidos, o executor de testes retornará 0 como um código de saída; caso contrário, se algum teste falhar, retornará 1.</span><span class="sxs-lookup"><span data-stu-id="2391b-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="2391b-113">O executor de teste e a biblioteca de teste de unidade são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.</span><span class="sxs-lookup"><span data-stu-id="2391b-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="2391b-114">Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:</span><span class="sxs-lookup"><span data-stu-id="2391b-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a><span data-ttu-id="2391b-115">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="2391b-115">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="2391b-116">Argumentos</span><span class="sxs-lookup"><span data-stu-id="2391b-116">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="2391b-117">Caminho para o projeto ou solução de teste.</span><span class="sxs-lookup"><span data-stu-id="2391b-117">Path to the test project or solution.</span></span> <span data-ttu-id="2391b-118">Se não é especificado, usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="2391b-118">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="2391b-119">Opções</span><span class="sxs-lookup"><span data-stu-id="2391b-119">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="2391b-120">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="2391b-120">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="2391b-121">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="2391b-121">Runs the tests in blame mode.</span></span> <span data-ttu-id="2391b-122">Esta opção é útil para isolar testes problemáticos que causam a falha do hospedeiro de teste.</span><span class="sxs-lookup"><span data-stu-id="2391b-122">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="2391b-123">Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.</span><span class="sxs-lookup"><span data-stu-id="2391b-123">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="2391b-124">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="2391b-124">Defines the build configuration.</span></span> <span data-ttu-id="2391b-125">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="2391b-125">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="2391b-126">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="2391b-126">Enables data collector for the test run.</span></span> <span data-ttu-id="2391b-127">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="2391b-127">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="2391b-128">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="2391b-128">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2391b-129">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="2391b-129">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="2391b-130">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="2391b-130">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="2391b-131">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="2391b-131">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="2391b-132">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="2391b-132">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="2391b-133">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="2391b-133">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="2391b-134">Permite que o comando pare e aguarde entrada ou ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="2391b-134">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="2391b-135">Por exemplo, para concluir a autenticação.</span><span class="sxs-lookup"><span data-stu-id="2391b-135">For example, to complete authentication.</span></span> <span data-ttu-id="2391b-136">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2391b-136">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="2391b-137">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="2391b-137">Specifies a logger for test results.</span></span> <span data-ttu-id="2391b-138">Ao contrário do MSBuild, o teste dotnet não `-l "console;v=d"` aceita `-l "console;verbosity=detailed"`abreviaturas: em vez de usar .</span><span class="sxs-lookup"><span data-stu-id="2391b-138">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="2391b-139">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="2391b-139">Doesn't build the test project before running it.</span></span> <span data-ttu-id="2391b-140">Ele também define implicitamente a `--no-restore` bandeira.</span><span class="sxs-lookup"><span data-stu-id="2391b-140">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="2391b-141">Execute testes sem exibir o banner microsoft testplatform.</span><span class="sxs-lookup"><span data-stu-id="2391b-141">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="2391b-142">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2391b-142">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="2391b-143">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="2391b-143">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="2391b-144">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="2391b-144">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="2391b-145">Se não for especificado, o caminho padrão será `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="2391b-145">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="2391b-146">Para projetos com vários frameworks `TargetFrameworks` de destino (via `--framework` propriedade), você também precisa definir quando você especifica essa opção.</span><span class="sxs-lookup"><span data-stu-id="2391b-146">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="2391b-147">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="2391b-147">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="2391b-148">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="2391b-148">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="2391b-149">O padrão `TestResults` está no diretório que contém o arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="2391b-149">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="2391b-150">O tempo de execução do alvo para testar.</span><span class="sxs-lookup"><span data-stu-id="2391b-150">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="2391b-151">O arquivo `.runsettings` a ser usado para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="2391b-151">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="2391b-152">Configurar testes de unidade usando um arquivo `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="2391b-152">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="2391b-153">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="2391b-153">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="2391b-154">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="2391b-154">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2391b-155">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2391b-155">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="2391b-156">O padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="2391b-156">The default is `minimal`.</span></span> <span data-ttu-id="2391b-157">Para obter mais informações, consulte <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="2391b-157">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="2391b-158">**`RunSettings`** Argumentos</span><span class="sxs-lookup"><span data-stu-id="2391b-158">**`RunSettings`** arguments</span></span>

  <span data-ttu-id="2391b-159">Os argumentos `RunSettings` são passados como configurações para o teste.</span><span class="sxs-lookup"><span data-stu-id="2391b-159">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="2391b-160">Os argumentos são especificados como pares `[name]=[value]` após "-- " (observe o espaço após --).</span><span class="sxs-lookup"><span data-stu-id="2391b-160">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="2391b-161">Um espaço é usado para separar vários pares `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="2391b-161">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="2391b-162">Exemplo: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="2391b-162">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="2391b-163">Para obter mais informações, consulte ['''Configurações de execução' argumentos através da linha de comando](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="2391b-163">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="2391b-164">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2391b-164">Examples</span></span>

- <span data-ttu-id="2391b-165">Execute os testes no projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="2391b-165">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="2391b-166">Execute os testes no projeto `test1`:</span><span class="sxs-lookup"><span data-stu-id="2391b-166">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="2391b-167">Execute os testes no projeto no diretório atual e gere um arquivo de resultados de teste no formato trx:</span><span class="sxs-lookup"><span data-stu-id="2391b-167">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="2391b-168">Execute os testes no projeto no diretório atual e registre com verbosidade detalhada para o console:</span><span class="sxs-lookup"><span data-stu-id="2391b-168">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a><span data-ttu-id="2391b-169">Filtrar detalhes da opção</span><span class="sxs-lookup"><span data-stu-id="2391b-169">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="2391b-170">`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="2391b-170">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="2391b-171">`<property>` é um atributo de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="2391b-171">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="2391b-172">A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:</span><span class="sxs-lookup"><span data-stu-id="2391b-172">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="2391b-173">Estrutura de teste</span><span class="sxs-lookup"><span data-stu-id="2391b-173">Test Framework</span></span> | <span data-ttu-id="2391b-174">Propriedades com suporte</span><span class="sxs-lookup"><span data-stu-id="2391b-174">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="2391b-175">MSTest</span><span class="sxs-lookup"><span data-stu-id="2391b-175">MSTest</span></span>         | <ul><li><span data-ttu-id="2391b-176">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="2391b-176">FullyQualifiedName</span></span></li><li><span data-ttu-id="2391b-177">Nome</span><span class="sxs-lookup"><span data-stu-id="2391b-177">Name</span></span></li><li><span data-ttu-id="2391b-178">ClassName</span><span class="sxs-lookup"><span data-stu-id="2391b-178">ClassName</span></span></li><li><span data-ttu-id="2391b-179">Prioridade</span><span class="sxs-lookup"><span data-stu-id="2391b-179">Priority</span></span></li><li><span data-ttu-id="2391b-180">TestCategory</span><span class="sxs-lookup"><span data-stu-id="2391b-180">TestCategory</span></span></li></ul> |
| <span data-ttu-id="2391b-181">xUnit</span><span class="sxs-lookup"><span data-stu-id="2391b-181">xUnit</span></span>          | <ul><li><span data-ttu-id="2391b-182">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="2391b-182">FullyQualifiedName</span></span></li><li><span data-ttu-id="2391b-183">DisplayName</span><span class="sxs-lookup"><span data-stu-id="2391b-183">DisplayName</span></span></li><li><span data-ttu-id="2391b-184">Características</span><span class="sxs-lookup"><span data-stu-id="2391b-184">Traits</span></span></li></ul>                                   |

<span data-ttu-id="2391b-185">O `<operator>` descreve a relação entre a propriedade o valor:</span><span class="sxs-lookup"><span data-stu-id="2391b-185">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="2391b-186">Operador</span><span class="sxs-lookup"><span data-stu-id="2391b-186">Operator</span></span> | <span data-ttu-id="2391b-187">Função</span><span class="sxs-lookup"><span data-stu-id="2391b-187">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="2391b-188">Correspondência exata</span><span class="sxs-lookup"><span data-stu-id="2391b-188">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="2391b-189">Sem correspondência exata</span><span class="sxs-lookup"><span data-stu-id="2391b-189">Not exact match</span></span> |
| `~`      | <span data-ttu-id="2391b-190">Contém</span><span class="sxs-lookup"><span data-stu-id="2391b-190">Contains</span></span>        |
| `!~`     | <span data-ttu-id="2391b-191">Não contém</span><span class="sxs-lookup"><span data-stu-id="2391b-191">Not contains</span></span>    |

<span data-ttu-id="2391b-192">`<value>` é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2391b-192">`<value>` is a string.</span></span> <span data-ttu-id="2391b-193">As pesquisas não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="2391b-193">All the lookups are case insensitive.</span></span>

<span data-ttu-id="2391b-194">Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="2391b-194">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="2391b-195">As expressões podem ser associadas a operadores condicionais:</span><span class="sxs-lookup"><span data-stu-id="2391b-195">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="2391b-196">Operador</span><span class="sxs-lookup"><span data-stu-id="2391b-196">Operator</span></span>            | <span data-ttu-id="2391b-197">Função</span><span class="sxs-lookup"><span data-stu-id="2391b-197">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="2391b-198">OU</span><span class="sxs-lookup"><span data-stu-id="2391b-198">OR</span></span>       |
| `&`                 | <span data-ttu-id="2391b-199">AND</span><span class="sxs-lookup"><span data-stu-id="2391b-199">AND</span></span>      |

<span data-ttu-id="2391b-200">Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="2391b-200">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="2391b-201">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="2391b-201">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2391b-202">Confira também</span><span class="sxs-lookup"><span data-stu-id="2391b-202">See also</span></span>

- [<span data-ttu-id="2391b-203">Frameworks e Metas</span><span class="sxs-lookup"><span data-stu-id="2391b-203">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="2391b-204">Catálogo do Identificador de Runtime do .NET Core</span><span class="sxs-lookup"><span data-stu-id="2391b-204">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="2391b-205">Passando argumentos de runsettings através da linha de comando</span><span class="sxs-lookup"><span data-stu-id="2391b-205">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
