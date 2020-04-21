---
title: Comando dotnet test
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
ms.date: 02/27/2020
ms.openlocfilehash: 2eebcbe2e4a1660da4ffa4ea9a68190c8443463a
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739097"
---
# <a name="dotnet-test"></a><span data-ttu-id="ac851-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="ac851-103">dotnet test</span></span>

<span data-ttu-id="ac851-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="ac851-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ac851-105">Nome</span><span class="sxs-lookup"><span data-stu-id="ac851-105">Name</span></span>

<span data-ttu-id="ac851-106">`dotnet test` - driver de teste do .NET usado para executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="ac851-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ac851-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="ac851-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="ac851-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac851-108">Description</span></span>

<span data-ttu-id="ac851-109">O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="ac851-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="ac851-110">O comando `dotnet test` inicia o aplicativo de console executor de teste especificado para um projeto.</span><span class="sxs-lookup"><span data-stu-id="ac851-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="ac851-111">O executor de teste realiza os testes definidos para uma estrutura de teste de unidade (por exemplo, MSTest, NUnit ou xUnit) e relata o êxito ou a falha de cada teste.</span><span class="sxs-lookup"><span data-stu-id="ac851-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="ac851-112">Se todos os testes forem bem-sucedidos, o executor de testes retornará 0 como um código de saída; caso contrário, se algum teste falhar, retornará 1.</span><span class="sxs-lookup"><span data-stu-id="ac851-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="ac851-113">O executor de teste e a biblioteca de teste de unidade são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.</span><span class="sxs-lookup"><span data-stu-id="ac851-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="ac851-114">Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:</span><span class="sxs-lookup"><span data-stu-id="ac851-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="ac851-115">Argumentos</span><span class="sxs-lookup"><span data-stu-id="ac851-115">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="ac851-116">Caminho para o projeto ou solução de teste.</span><span class="sxs-lookup"><span data-stu-id="ac851-116">Path to the test project or solution.</span></span> <span data-ttu-id="ac851-117">Se não é especificado, usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="ac851-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="ac851-118">Opções</span><span class="sxs-lookup"><span data-stu-id="ac851-118">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="ac851-119">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="ac851-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`--blame`**

  <span data-ttu-id="ac851-120">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="ac851-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="ac851-121">Esta opção é útil para isolar testes problemáticos que causam a falha do hospedeiro de teste.</span><span class="sxs-lookup"><span data-stu-id="ac851-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="ac851-122">Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.</span><span class="sxs-lookup"><span data-stu-id="ac851-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="ac851-123">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="ac851-123">Defines the build configuration.</span></span> <span data-ttu-id="ac851-124">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="ac851-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="ac851-125">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="ac851-125">Enables data collector for the test run.</span></span> <span data-ttu-id="ac851-126">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="ac851-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="ac851-127">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="ac851-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ac851-128">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="ac851-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="ac851-129">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="ac851-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="ac851-130">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="ac851-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="ac851-131">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ac851-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="ac851-132">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="ac851-132">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="ac851-133">Permite que o comando pare e aguarde entrada ou ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="ac851-133">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="ac851-134">Por exemplo, para concluir a autenticação.</span><span class="sxs-lookup"><span data-stu-id="ac851-134">For example, to complete authentication.</span></span> <span data-ttu-id="ac851-135">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ac851-135">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="ac851-136">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="ac851-136">Specifies a logger for test results.</span></span> <span data-ttu-id="ac851-137">Ao contrário do MSBuild, o teste dotnet não `-l "console;v=d"` aceita `-l "console;verbosity=detailed"`abreviaturas: em vez de usar .</span><span class="sxs-lookup"><span data-stu-id="ac851-137">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="ac851-138">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="ac851-138">Doesn't build the test project before running it.</span></span> <span data-ttu-id="ac851-139">Ele também define implicitamente a `--no-restore` bandeira.</span><span class="sxs-lookup"><span data-stu-id="ac851-139">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="ac851-140">Execute testes sem exibir o banner microsoft testplatform.</span><span class="sxs-lookup"><span data-stu-id="ac851-140">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="ac851-141">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ac851-141">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ac851-142">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="ac851-142">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="ac851-143">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="ac851-143">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="ac851-144">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="ac851-144">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="ac851-145">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="ac851-145">If the specified directory doesn't exist, it's created.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="ac851-146">O tempo de execução do alvo para testar.</span><span class="sxs-lookup"><span data-stu-id="ac851-146">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="ac851-147">O arquivo `.runsettings` a ser usado para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="ac851-147">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="ac851-148">Configurar testes de unidade usando um arquivo `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="ac851-148">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="ac851-149">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="ac851-149">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="ac851-150">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="ac851-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ac851-151">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ac851-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ac851-152">O padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="ac851-152">The default is `minimal`.</span></span> <span data-ttu-id="ac851-153">Para obter mais informações, consulte <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="ac851-153">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="ac851-154">`RunSettings`Argumentos</span><span class="sxs-lookup"><span data-stu-id="ac851-154">`RunSettings` arguments</span></span>

  <span data-ttu-id="ac851-155">Os argumentos `RunSettings` são passados como configurações para o teste.</span><span class="sxs-lookup"><span data-stu-id="ac851-155">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="ac851-156">Os argumentos são especificados como pares `[name]=[value]` após "-- " (observe o espaço após --).</span><span class="sxs-lookup"><span data-stu-id="ac851-156">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="ac851-157">Um espaço é usado para separar vários pares `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="ac851-157">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="ac851-158">Exemplo: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="ac851-158">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="ac851-159">Para obter mais informações, consulte [vstest.console.exe: Passando RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="ac851-159">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="ac851-160">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ac851-160">Examples</span></span>

- <span data-ttu-id="ac851-161">Execute os testes no projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="ac851-161">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="ac851-162">Execute os testes no projeto `test1`:</span><span class="sxs-lookup"><span data-stu-id="ac851-162">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="ac851-163">Execute os testes no projeto no diretório atual e gere um arquivo de resultados de teste no formato trx:</span><span class="sxs-lookup"><span data-stu-id="ac851-163">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="ac851-164">Execute os testes no projeto no diretório atual e registre com verbosidade detalhada para o console:</span><span class="sxs-lookup"><span data-stu-id="ac851-164">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a><span data-ttu-id="ac851-165">Filtrar detalhes da opção</span><span class="sxs-lookup"><span data-stu-id="ac851-165">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="ac851-166">`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="ac851-166">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="ac851-167">`<property>` é um atributo de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="ac851-167">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="ac851-168">A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:</span><span class="sxs-lookup"><span data-stu-id="ac851-168">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="ac851-169">Estrutura de teste</span><span class="sxs-lookup"><span data-stu-id="ac851-169">Test Framework</span></span> | <span data-ttu-id="ac851-170">Propriedades com suporte</span><span class="sxs-lookup"><span data-stu-id="ac851-170">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="ac851-171">MSTest</span><span class="sxs-lookup"><span data-stu-id="ac851-171">MSTest</span></span>         | <ul><li><span data-ttu-id="ac851-172">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="ac851-172">FullyQualifiedName</span></span></li><li><span data-ttu-id="ac851-173">Nome</span><span class="sxs-lookup"><span data-stu-id="ac851-173">Name</span></span></li><li><span data-ttu-id="ac851-174">ClassName</span><span class="sxs-lookup"><span data-stu-id="ac851-174">ClassName</span></span></li><li><span data-ttu-id="ac851-175">Prioridade</span><span class="sxs-lookup"><span data-stu-id="ac851-175">Priority</span></span></li><li><span data-ttu-id="ac851-176">TestCategory</span><span class="sxs-lookup"><span data-stu-id="ac851-176">TestCategory</span></span></li></ul> |
| <span data-ttu-id="ac851-177">xUnit</span><span class="sxs-lookup"><span data-stu-id="ac851-177">xUnit</span></span>          | <ul><li><span data-ttu-id="ac851-178">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="ac851-178">FullyQualifiedName</span></span></li><li><span data-ttu-id="ac851-179">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ac851-179">DisplayName</span></span></li><li><span data-ttu-id="ac851-180">Características</span><span class="sxs-lookup"><span data-stu-id="ac851-180">Traits</span></span></li></ul>                                   |

<span data-ttu-id="ac851-181">O `<operator>` descreve a relação entre a propriedade o valor:</span><span class="sxs-lookup"><span data-stu-id="ac851-181">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="ac851-182">Operador</span><span class="sxs-lookup"><span data-stu-id="ac851-182">Operator</span></span> | <span data-ttu-id="ac851-183">Função</span><span class="sxs-lookup"><span data-stu-id="ac851-183">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="ac851-184">Correspondência exata</span><span class="sxs-lookup"><span data-stu-id="ac851-184">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="ac851-185">Sem correspondência exata</span><span class="sxs-lookup"><span data-stu-id="ac851-185">Not exact match</span></span> |
| `~`      | <span data-ttu-id="ac851-186">Contém</span><span class="sxs-lookup"><span data-stu-id="ac851-186">Contains</span></span>        |
| `!~`     | <span data-ttu-id="ac851-187">Não contém</span><span class="sxs-lookup"><span data-stu-id="ac851-187">Not contains</span></span>    |

<span data-ttu-id="ac851-188">`<value>` é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ac851-188">`<value>` is a string.</span></span> <span data-ttu-id="ac851-189">As pesquisas não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="ac851-189">All the lookups are case insensitive.</span></span>

<span data-ttu-id="ac851-190">Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="ac851-190">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="ac851-191">As expressões podem ser associadas a operadores condicionais:</span><span class="sxs-lookup"><span data-stu-id="ac851-191">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="ac851-192">Operador</span><span class="sxs-lookup"><span data-stu-id="ac851-192">Operator</span></span>            | <span data-ttu-id="ac851-193">Função</span><span class="sxs-lookup"><span data-stu-id="ac851-193">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="ac851-194">OU</span><span class="sxs-lookup"><span data-stu-id="ac851-194">OR</span></span>       |
| `&`                 | <span data-ttu-id="ac851-195">AND</span><span class="sxs-lookup"><span data-stu-id="ac851-195">AND</span></span>      |

<span data-ttu-id="ac851-196">Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="ac851-196">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="ac851-197">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="ac851-197">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ac851-198">Confira também</span><span class="sxs-lookup"><span data-stu-id="ac851-198">See also</span></span>

- [<span data-ttu-id="ac851-199">Frameworks e Metas</span><span class="sxs-lookup"><span data-stu-id="ac851-199">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="ac851-200">Catálogo do Identificador de Runtime do .NET Core</span><span class="sxs-lookup"><span data-stu-id="ac851-200">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="ac851-201">Passando argumentos de runsettings através da linha de comando</span><span class="sxs-lookup"><span data-stu-id="ac851-201">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
