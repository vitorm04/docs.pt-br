---
title: Comando dotnet test
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
ms.date: 02/27/2020
ms.openlocfilehash: bac2f0e613c34bc9f657551a5eac4038207a93ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847892"
---
# <a name="dotnet-test"></a><span data-ttu-id="9f802-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="9f802-103">dotnet test</span></span>

<span data-ttu-id="9f802-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="9f802-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9f802-105">Nome</span><span class="sxs-lookup"><span data-stu-id="9f802-105">Name</span></span>

<span data-ttu-id="9f802-106">`dotnet test` - driver de teste do .NET usado para executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="9f802-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9f802-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="9f802-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path] [--blame] [-c|--configuration]
    [--collect] [-d|--diag] [-f|--framework] [--filter]
    [--interactive] [-l|--logger] [--no-build] [--nologo]
    [--no-restore] [-o|--output] [-r|--results-directory]
    [--runtime] [-s|--settings] [-t|--list-tests]
    [-v|--verbosity] [[--] <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a><span data-ttu-id="9f802-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f802-108">Description</span></span>

<span data-ttu-id="9f802-109">O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="9f802-109">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="9f802-110">O comando `dotnet test` inicia o aplicativo de console executor de teste especificado para um projeto.</span><span class="sxs-lookup"><span data-stu-id="9f802-110">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="9f802-111">O executor de teste realiza os testes definidos para uma estrutura de teste de unidade (por exemplo, MSTest, NUnit ou xUnit) e relata o êxito ou a falha de cada teste.</span><span class="sxs-lookup"><span data-stu-id="9f802-111">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="9f802-112">Se todos os testes forem bem-sucedidos, o executor de testes retornará 0 como um código de saída; caso contrário, se algum teste falhar, retornará 1.</span><span class="sxs-lookup"><span data-stu-id="9f802-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span> <span data-ttu-id="9f802-113">O executor de teste e a biblioteca de teste de unidade são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.</span><span class="sxs-lookup"><span data-stu-id="9f802-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="9f802-114">Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:</span><span class="sxs-lookup"><span data-stu-id="9f802-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="9f802-115">Argumentos</span><span class="sxs-lookup"><span data-stu-id="9f802-115">Arguments</span></span>

- **`PROJECT | SOLUTION`**

  <span data-ttu-id="9f802-116">Caminho para o projeto ou solução de teste.</span><span class="sxs-lookup"><span data-stu-id="9f802-116">Path to the test project or solution.</span></span> <span data-ttu-id="9f802-117">Se não é especificado, usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="9f802-117">If not specified, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="9f802-118">Opções</span><span class="sxs-lookup"><span data-stu-id="9f802-118">Options</span></span>

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="9f802-119">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="9f802-119">Use the custom test adapters from the specified path in the test run.</span></span>

- **`-blame`**

  <span data-ttu-id="9f802-120">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="9f802-120">Runs the tests in blame mode.</span></span> <span data-ttu-id="9f802-121">Esta opção é útil para isolar testes problemáticos que causam a falha do hospedeiro de teste.</span><span class="sxs-lookup"><span data-stu-id="9f802-121">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="9f802-122">Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.</span><span class="sxs-lookup"><span data-stu-id="9f802-122">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

- **`c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="9f802-123">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="9f802-123">Defines the build configuration.</span></span> <span data-ttu-id="9f802-124">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="9f802-124">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="9f802-125">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="9f802-125">Enables data collector for the test run.</span></span> <span data-ttu-id="9f802-126">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="9f802-126">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="9f802-127">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="9f802-127">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

- **`f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9f802-128">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="9f802-128">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="9f802-129">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="9f802-129">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="9f802-130">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="9f802-130">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="9f802-131">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="9f802-131">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`h|--help`**

  <span data-ttu-id="9f802-132">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="9f802-132">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="9f802-133">Permite que o comando pare e aguarde entrada ou ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="9f802-133">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="9f802-134">Por exemplo, para concluir a autenticação.</span><span class="sxs-lookup"><span data-stu-id="9f802-134">For example, to complete authentication.</span></span> <span data-ttu-id="9f802-135">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="9f802-135">Available since .NET Core 3.0 SDK.</span></span>

- **`l|--logger <LoggerUri/FriendlyName>`**

  <span data-ttu-id="9f802-136">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="9f802-136">Specifies a logger for test results.</span></span>

- **`--no-build`**

  <span data-ttu-id="9f802-137">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="9f802-137">Doesn't build the test project before running it.</span></span> <span data-ttu-id="9f802-138">Ele também define implicitamente a `--no-restore` bandeira.</span><span class="sxs-lookup"><span data-stu-id="9f802-138">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="9f802-139">Execute testes sem exibir o banner microsoft testplatform.</span><span class="sxs-lookup"><span data-stu-id="9f802-139">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="9f802-140">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="9f802-140">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="9f802-141">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="9f802-141">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="9f802-142">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="9f802-142">Directory in which to find the binaries to run.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="9f802-143">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="9f802-143">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="9f802-144">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="9f802-144">If the specified directory doesn't exist, it's created.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="9f802-145">O tempo de execução do alvo para testar.</span><span class="sxs-lookup"><span data-stu-id="9f802-145">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="9f802-146">O arquivo `.runsettings` a ser usado para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="9f802-146">The `.runsettings` file to use for running the tests.</span></span> [<span data-ttu-id="9f802-147">Configurar testes de unidade usando um arquivo `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="9f802-147">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  <span data-ttu-id="9f802-148">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="9f802-148">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="9f802-149">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="9f802-149">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9f802-150">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9f802-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- <span data-ttu-id="9f802-151">`RunSettings`Argumentos</span><span class="sxs-lookup"><span data-stu-id="9f802-151">`RunSettings` arguments</span></span>

  <span data-ttu-id="9f802-152">Os argumentos `RunSettings` são passados como configurações para o teste.</span><span class="sxs-lookup"><span data-stu-id="9f802-152">Arguments are passed as `RunSettings` configurations for the test.</span></span> <span data-ttu-id="9f802-153">Os argumentos são especificados como pares `[name]=[value]` após "-- " (observe o espaço após --).</span><span class="sxs-lookup"><span data-stu-id="9f802-153">Arguments are specified as `[name]=[value]` pairs after "-- " (note the space after --).</span></span> <span data-ttu-id="9f802-154">Um espaço é usado para separar vários pares `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="9f802-154">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="9f802-155">Exemplo: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="9f802-155">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="9f802-156">Para obter mais informações, consulte [vstest.console.exe: Passando RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="9f802-156">For more information, see [vstest.console.exe: Passing RunSettings args](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="9f802-157">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9f802-157">Examples</span></span>

- <span data-ttu-id="9f802-158">Execute os testes no projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="9f802-158">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="9f802-159">Execute os testes no projeto `test1`:</span><span class="sxs-lookup"><span data-stu-id="9f802-159">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="9f802-160">Execute os testes no projeto no diretório atual e gere um arquivo de resultados de teste no formato trx:</span><span class="sxs-lookup"><span data-stu-id="9f802-160">Run the tests in the project in the current directory and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a><span data-ttu-id="9f802-161">Filtrar detalhes da opção</span><span class="sxs-lookup"><span data-stu-id="9f802-161">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="9f802-162">`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="9f802-162">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="9f802-163">`<property>` é um atributo de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="9f802-163">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="9f802-164">A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:</span><span class="sxs-lookup"><span data-stu-id="9f802-164">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="9f802-165">Estrutura de teste</span><span class="sxs-lookup"><span data-stu-id="9f802-165">Test Framework</span></span> | <span data-ttu-id="9f802-166">Propriedades com suporte</span><span class="sxs-lookup"><span data-stu-id="9f802-166">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="9f802-167">MSTest</span><span class="sxs-lookup"><span data-stu-id="9f802-167">MSTest</span></span>         | <ul><li><span data-ttu-id="9f802-168">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="9f802-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="9f802-169">Nome</span><span class="sxs-lookup"><span data-stu-id="9f802-169">Name</span></span></li><li><span data-ttu-id="9f802-170">ClassName</span><span class="sxs-lookup"><span data-stu-id="9f802-170">ClassName</span></span></li><li><span data-ttu-id="9f802-171">Prioridade</span><span class="sxs-lookup"><span data-stu-id="9f802-171">Priority</span></span></li><li><span data-ttu-id="9f802-172">TestCategory</span><span class="sxs-lookup"><span data-stu-id="9f802-172">TestCategory</span></span></li></ul> |
| <span data-ttu-id="9f802-173">xUnit</span><span class="sxs-lookup"><span data-stu-id="9f802-173">xUnit</span></span>          | <ul><li><span data-ttu-id="9f802-174">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="9f802-174">FullyQualifiedName</span></span></li><li><span data-ttu-id="9f802-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="9f802-175">DisplayName</span></span></li><li><span data-ttu-id="9f802-176">Características</span><span class="sxs-lookup"><span data-stu-id="9f802-176">Traits</span></span></li></ul>                                   |

<span data-ttu-id="9f802-177">O `<operator>` descreve a relação entre a propriedade o valor:</span><span class="sxs-lookup"><span data-stu-id="9f802-177">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="9f802-178">Operador</span><span class="sxs-lookup"><span data-stu-id="9f802-178">Operator</span></span> | <span data-ttu-id="9f802-179">Função</span><span class="sxs-lookup"><span data-stu-id="9f802-179">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="9f802-180">Correspondência exata</span><span class="sxs-lookup"><span data-stu-id="9f802-180">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="9f802-181">Sem correspondência exata</span><span class="sxs-lookup"><span data-stu-id="9f802-181">Not exact match</span></span> |
| `~`      | <span data-ttu-id="9f802-182">Contém</span><span class="sxs-lookup"><span data-stu-id="9f802-182">Contains</span></span>        |
| `!~`     | <span data-ttu-id="9f802-183">Não contém</span><span class="sxs-lookup"><span data-stu-id="9f802-183">Not contains</span></span>    |

<span data-ttu-id="9f802-184">`<value>` é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9f802-184">`<value>` is a string.</span></span> <span data-ttu-id="9f802-185">As pesquisas não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="9f802-185">All the lookups are case insensitive.</span></span>

<span data-ttu-id="9f802-186">Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="9f802-186">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="9f802-187">As expressões podem ser associadas a operadores condicionais:</span><span class="sxs-lookup"><span data-stu-id="9f802-187">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="9f802-188">Operador</span><span class="sxs-lookup"><span data-stu-id="9f802-188">Operator</span></span>            | <span data-ttu-id="9f802-189">Função</span><span class="sxs-lookup"><span data-stu-id="9f802-189">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="9f802-190">OU</span><span class="sxs-lookup"><span data-stu-id="9f802-190">OR</span></span>       |
| `&`                 | <span data-ttu-id="9f802-191">AND</span><span class="sxs-lookup"><span data-stu-id="9f802-191">AND</span></span>      |

<span data-ttu-id="9f802-192">Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="9f802-192">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="9f802-193">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="9f802-193">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9f802-194">Confira também</span><span class="sxs-lookup"><span data-stu-id="9f802-194">See also</span></span>

- [<span data-ttu-id="9f802-195">Frameworks e Metas</span><span class="sxs-lookup"><span data-stu-id="9f802-195">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="9f802-196">Catálogo do Identificador de Runtime do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9f802-196">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
