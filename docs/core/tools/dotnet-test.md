---
title: Comando dotnet test
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
ms.date: 05/29/2018
ms.openlocfilehash: 890d1fc3fd9d47f2bdcd63f2a25248c3edd705e4
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626041"
---
# <a name="dotnet-test"></a><span data-ttu-id="10cc5-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="10cc5-103">dotnet test</span></span>

<span data-ttu-id="10cc5-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="10cc5-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="10cc5-105">{1&gt;Nome&lt;1}</span><span class="sxs-lookup"><span data-stu-id="10cc5-105">Name</span></span>

<span data-ttu-id="10cc5-106">`dotnet test` - driver de teste do .NET usado para executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="10cc5-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="10cc5-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="10cc5-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame]
    [-c|--configuration] [--collect] [-d|--diag] [-f|--framework]
    [--filter] [-l|--logger] [--no-build] [--no-restore]
    [-o|--output] [-r|--results-directory] [-s|--settings]
    [-t|--list-tests] [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a><span data-ttu-id="10cc5-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="10cc5-108">Description</span></span>

<span data-ttu-id="10cc5-109">O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="10cc5-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="10cc5-110">O comando `dotnet test` inicia o aplicativo de console executor de teste especificado para um projeto.</span><span class="sxs-lookup"><span data-stu-id="10cc5-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="10cc5-111">O executor de teste realiza os testes definidos para uma estrutura de teste de unidade (por exemplo, MSTest, NUnit ou xUnit) e relata o êxito ou a falha de cada teste.</span><span class="sxs-lookup"><span data-stu-id="10cc5-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="10cc5-112">Se todos os testes forem bem-sucedidos, o executor de testes retornará 0 como um código de saída; caso contrário, se algum teste falhar, retornará 1.</span><span class="sxs-lookup"><span data-stu-id="10cc5-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="10cc5-113">O executor de teste e a biblioteca de teste de unidade são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.</span><span class="sxs-lookup"><span data-stu-id="10cc5-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="10cc5-114">Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:</span><span class="sxs-lookup"><span data-stu-id="10cc5-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="10cc5-115">Argumentos</span><span class="sxs-lookup"><span data-stu-id="10cc5-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="10cc5-116">Caminho para o projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="10cc5-116">Path to the test project.</span></span> <span data-ttu-id="10cc5-117">Se não é especificado, usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="10cc5-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="10cc5-118">{1&gt;Opções&lt;1}</span><span class="sxs-lookup"><span data-stu-id="10cc5-118">Options</span></span>

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="10cc5-119">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="10cc5-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`-blame`**

  <span data-ttu-id="10cc5-120">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="10cc5-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="10cc5-121">Essa opção é útil para isolar testes problemáticos que causam falha no host de teste.</span><span class="sxs-lookup"><span data-stu-id="10cc5-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="10cc5-122">Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.</span><span class="sxs-lookup"><span data-stu-id="10cc5-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`c|--configuration {Debug|Release}`**

  <span data-ttu-id="10cc5-123">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="10cc5-123">Defines the build configuration.</span></span> <span data-ttu-id="10cc5-124">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="10cc5-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="10cc5-125">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="10cc5-125">Enables data collector for the test run.</span></span> <span data-ttu-id="10cc5-126">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="10cc5-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="10cc5-127">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="10cc5-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`f|--framework <FRAMEWORK>`**

  <span data-ttu-id="10cc5-128">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="10cc5-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="10cc5-129">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="10cc5-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="10cc5-130">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="10cc5-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="10cc5-131">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="10cc5-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`h|--help`**

  <span data-ttu-id="10cc5-132">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="10cc5-132">Prints out a short help for the command.</span></span>

- **`l|--logger <LoggerUri/FriendlyName>`**

  <span data-ttu-id="10cc5-133">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="10cc5-133">Specifies a logger for test results.</span></span>

- **`--no-build`**

  <span data-ttu-id="10cc5-134">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="10cc5-134">Doesn't build the test project before running it.</span></span> <span data-ttu-id="10cc5-135">Ele também define implicitamente o sinalizador-`--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="10cc5-135">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--no-restore`**

  <span data-ttu-id="10cc5-136">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="10cc5-136">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="10cc5-137">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="10cc5-137">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="10cc5-138">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="10cc5-138">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="10cc5-139">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="10cc5-139">If the specified directory doesn't exist, it's created.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="10cc5-140">O arquivo `.runsettings` a ser usado para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="10cc5-140">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="10cc5-141">Configurar testes de unidade usando um arquivo `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="10cc5-141">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="10cc5-142">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="10cc5-142">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="10cc5-143">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="10cc5-143">Sets the verbosity level of the command.</span></span> <span data-ttu-id="10cc5-144">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="10cc5-144">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- <span data-ttu-id="10cc5-145">argumentos de `RunSettings`</span><span class="sxs-lookup"><span data-stu-id="10cc5-145">`RunSettings` arguments</span></span>

  <span data-ttu-id="10cc5-146">Os argumentos são passados como `RunSettings` configurações para o teste.</span><span class="sxs-lookup"><span data-stu-id="10cc5-146">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="10cc5-147">Os argumentos são especificados como pares `[name]=[value]` após "-- " (observe o espaço após --).</span><span class="sxs-lookup"><span data-stu-id="10cc5-147">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="10cc5-148">Um espaço é usado para separar vários pares `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="10cc5-148">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="10cc5-149">Exemplo: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="10cc5-149">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="10cc5-150">Para obter mais informações, consulte [VSTest. console. exe: Pass RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="10cc5-150">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="10cc5-151">Exemplos</span><span class="sxs-lookup"><span data-stu-id="10cc5-151">Examples</span></span>

- <span data-ttu-id="10cc5-152">Execute os testes no projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="10cc5-152">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="10cc5-153">Execute os testes no projeto `test1`:</span><span class="sxs-lookup"><span data-stu-id="10cc5-153">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="10cc5-154">Execute os testes no projeto no diretório atual e gere um arquivo de resultados de teste no formato trx:</span><span class="sxs-lookup"><span data-stu-id="10cc5-154">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a><span data-ttu-id="10cc5-155">Filtrar detalhes da opção</span><span class="sxs-lookup"><span data-stu-id="10cc5-155">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="10cc5-156">`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="10cc5-156">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="10cc5-157">`<property>` é um atributo de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="10cc5-157">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="10cc5-158">A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:</span><span class="sxs-lookup"><span data-stu-id="10cc5-158">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="10cc5-159">Estrutura de teste</span><span class="sxs-lookup"><span data-stu-id="10cc5-159">Test Framework</span></span> | <span data-ttu-id="10cc5-160">Propriedades com suporte</span><span class="sxs-lookup"><span data-stu-id="10cc5-160">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="10cc5-161">MSTest</span><span class="sxs-lookup"><span data-stu-id="10cc5-161">MSTest</span></span>         | <ul><li><span data-ttu-id="10cc5-162">Nome Totalmente Qualificado</span><span class="sxs-lookup"><span data-stu-id="10cc5-162">FullyQualifiedName</span></span></li><li><span data-ttu-id="10cc5-163">{1&gt;Nome&lt;1}</span><span class="sxs-lookup"><span data-stu-id="10cc5-163">Name</span></span></li><li><span data-ttu-id="10cc5-164">ClassName</span><span class="sxs-lookup"><span data-stu-id="10cc5-164">ClassName</span></span></li><li><span data-ttu-id="10cc5-165">Prioridade</span><span class="sxs-lookup"><span data-stu-id="10cc5-165">Priority</span></span></li><li><span data-ttu-id="10cc5-166">TestCategory</span><span class="sxs-lookup"><span data-stu-id="10cc5-166">TestCategory</span></span></li></ul> |
| <span data-ttu-id="10cc5-167">xUnit</span><span class="sxs-lookup"><span data-stu-id="10cc5-167">xUnit</span></span>          | <ul><li><span data-ttu-id="10cc5-168">Nome Totalmente Qualificado</span><span class="sxs-lookup"><span data-stu-id="10cc5-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="10cc5-169">DisplayName</span><span class="sxs-lookup"><span data-stu-id="10cc5-169">DisplayName</span></span></li><li><span data-ttu-id="10cc5-170">Características</span><span class="sxs-lookup"><span data-stu-id="10cc5-170">Traits</span></span></li></ul>                                   |

<span data-ttu-id="10cc5-171">O `<operator>` descreve a relação entre a propriedade o valor:</span><span class="sxs-lookup"><span data-stu-id="10cc5-171">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="10cc5-172">Operador</span><span class="sxs-lookup"><span data-stu-id="10cc5-172">Operator</span></span> | <span data-ttu-id="10cc5-173">Função</span><span class="sxs-lookup"><span data-stu-id="10cc5-173">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="10cc5-174">Correspondência exata</span><span class="sxs-lookup"><span data-stu-id="10cc5-174">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="10cc5-175">Sem correspondência exata</span><span class="sxs-lookup"><span data-stu-id="10cc5-175">Not exact match</span></span> |
| `~`      | <span data-ttu-id="10cc5-176">Contém</span><span class="sxs-lookup"><span data-stu-id="10cc5-176">Contains</span></span>        |
| `!~`     | <span data-ttu-id="10cc5-177">Não contém</span><span class="sxs-lookup"><span data-stu-id="10cc5-177">Not contains</span></span>    |

<span data-ttu-id="10cc5-178">`<value>` é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="10cc5-178">`<value>` is a string.</span></span> <span data-ttu-id="10cc5-179">As pesquisas não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="10cc5-179">All the lookups are case insensitive.</span></span>

<span data-ttu-id="10cc5-180">Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="10cc5-180">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="10cc5-181">As expressões podem ser associadas a operadores condicionais:</span><span class="sxs-lookup"><span data-stu-id="10cc5-181">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="10cc5-182">Operador</span><span class="sxs-lookup"><span data-stu-id="10cc5-182">Operator</span></span>            | <span data-ttu-id="10cc5-183">Função</span><span class="sxs-lookup"><span data-stu-id="10cc5-183">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="10cc5-184">OR</span><span class="sxs-lookup"><span data-stu-id="10cc5-184">OR</span></span>       |
| `&`                 | <span data-ttu-id="10cc5-185">AND</span><span class="sxs-lookup"><span data-stu-id="10cc5-185">AND</span></span>      |

<span data-ttu-id="10cc5-186">Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="10cc5-186">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="10cc5-187">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="10cc5-187">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="10cc5-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10cc5-188">See also</span></span>

- [<span data-ttu-id="10cc5-189">Estruturas e destinos</span><span class="sxs-lookup"><span data-stu-id="10cc5-189">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="10cc5-190">Catálogo do Identificador de Runtime do .NET Core</span><span class="sxs-lookup"><span data-stu-id="10cc5-190">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
