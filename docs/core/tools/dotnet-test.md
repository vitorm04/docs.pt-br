---
title: Comando dotnet test – CLI do .NET Core
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 04af96bb53cc4fdac2e52311f9197eb1ee2b112d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-test"></a><span data-ttu-id="6d6f6-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="6d6f6-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="6d6f6-104">Nome</span><span class="sxs-lookup"><span data-stu-id="6d6f6-104">Name</span></span>

<span data-ttu-id="6d6f6-105">`dotnet test` - driver de teste do .NET usado para executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6d6f6-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="6d6f6-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6d6f6-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6d6f6-107">.NET Core 2.x</span></span>](#tab/netcore2x)


```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6d6f6-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6d6f6-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="6d6f6-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d6f6-109">Description</span></span>

<span data-ttu-id="6d6f6-110">O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-110">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="6d6f6-111">O comando `dotnet test` inicia o aplicativo de console executor de teste especificado para um projeto.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-111">The `dotnet test` command launches the test runner console application specified for a project.</span></span> <span data-ttu-id="6d6f6-112">O executor de teste realiza os testes definidos para uma estrutura de teste de unidade (por exemplo, MSTest, NUnit ou xUnit) e relata o êxito ou a falha de cada teste.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-112">The test runner executes the tests defined for a unit test framework (for example, MSTest, NUnit, or xUnit) and reports the success or failure of each test.</span></span> <span data-ttu-id="6d6f6-113">O executor de teste e a biblioteca de teste de unidade são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-113">The test runner and the unit test library are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="6d6f6-114">Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:</span><span class="sxs-lookup"><span data-stu-id="6d6f6-114">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="6d6f6-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="6d6f6-115">Arguments</span></span>

`PROJECT`

<span data-ttu-id="6d6f6-116">Especifica um caminho para o projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-116">Specifies a path to the test project.</span></span> <span data-ttu-id="6d6f6-117">Se for omitido, o padrão será o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-117">If omitted, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="6d6f6-118">Opções</span><span class="sxs-lookup"><span data-stu-id="6d6f6-118">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6d6f6-119">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6d6f6-119">.NET Core 2.x</span></span>](#tab/netcore2x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="6d6f6-120">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-120">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="6d6f6-121">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-121">Defines the build configuration.</span></span> <span data-ttu-id="6d6f6-122">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-122">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="6d6f6-123">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-123">Enables data collector for the test run.</span></span> <span data-ttu-id="6d6f6-124">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="6d6f6-124">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="6d6f6-125">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-125">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6d6f6-126">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-126">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="6d6f6-127">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-127">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="6d6f6-128">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="6d6f6-128">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="6d6f6-129">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executar testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="6d6f6-129">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="6d6f6-130">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-130">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="6d6f6-131">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-131">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="6d6f6-132">Não compila o projeto de teste antes de executá-lo.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-132">Does not build the test project prior to running it.</span></span>

`--no-restore`

<span data-ttu-id="6d6f6-133">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-133">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6d6f6-134">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-134">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="6d6f6-135">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-135">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="6d6f6-136">O diretório especificado será criado se ele não existir.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-136">The specified directory will be created if it doesn't exist.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="6d6f6-137">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-137">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="6d6f6-138">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-138">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6d6f6-139">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-139">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6d6f6-140">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-140">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6d6f6-141">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6d6f6-141">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="6d6f6-142">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-142">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="6d6f6-143">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-143">Defines the build configuration.</span></span> <span data-ttu-id="6d6f6-144">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-144">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="6d6f6-145">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-145">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6d6f6-146">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-146">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="6d6f6-147">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-147">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="6d6f6-148">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="6d6f6-148">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="6d6f6-149">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executar testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="6d6f6-149">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="6d6f6-150">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-150">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="6d6f6-151">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-151">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="6d6f6-152">Não compila o projeto de teste antes de executá-lo.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-152">Does not build the test project prior to running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6d6f6-153">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-153">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="6d6f6-154">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-154">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="6d6f6-155">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-155">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6d6f6-156">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6d6f6-157">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="6d6f6-158">Exemplos</span><span class="sxs-lookup"><span data-stu-id="6d6f6-158">Examples</span></span>

<span data-ttu-id="6d6f6-159">Execute os testes no projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="6d6f6-159">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="6d6f6-160">Execute os testes no projeto `test1`:</span><span class="sxs-lookup"><span data-stu-id="6d6f6-160">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="6d6f6-161">Filtrar detalhes da opção</span><span class="sxs-lookup"><span data-stu-id="6d6f6-161">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="6d6f6-162">`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-162">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="6d6f6-163">`<property>` é um atributo de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-163">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="6d6f6-164">A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:</span><span class="sxs-lookup"><span data-stu-id="6d6f6-164">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="6d6f6-165">Estrutura de teste</span><span class="sxs-lookup"><span data-stu-id="6d6f6-165">Test Framework</span></span> | <span data-ttu-id="6d6f6-166">Propriedades com suporte</span><span class="sxs-lookup"><span data-stu-id="6d6f6-166">Supported properties</span></span>                                                                                      |
| :------------: | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="6d6f6-167">MSTest</span><span class="sxs-lookup"><span data-stu-id="6d6f6-167">MSTest</span></span>         | <ul><li><span data-ttu-id="6d6f6-168">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="6d6f6-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="6d6f6-169">Nome</span><span class="sxs-lookup"><span data-stu-id="6d6f6-169">Name</span></span></li><li><span data-ttu-id="6d6f6-170">ClassName</span><span class="sxs-lookup"><span data-stu-id="6d6f6-170">ClassName</span></span></li><li><span data-ttu-id="6d6f6-171">Prioridade</span><span class="sxs-lookup"><span data-stu-id="6d6f6-171">Priority</span></span></li><li><span data-ttu-id="6d6f6-172">TestCategory</span><span class="sxs-lookup"><span data-stu-id="6d6f6-172">TestCategory</span></span></li></ul> |
| <span data-ttu-id="6d6f6-173">Xunit</span><span class="sxs-lookup"><span data-stu-id="6d6f6-173">Xunit</span></span>          | <ul><li><span data-ttu-id="6d6f6-174">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="6d6f6-174">FullyQualifiedName</span></span></li><li><span data-ttu-id="6d6f6-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="6d6f6-175">DisplayName</span></span></li><li><span data-ttu-id="6d6f6-176">Características</span><span class="sxs-lookup"><span data-stu-id="6d6f6-176">Traits</span></span></li></ul>                                   |

<span data-ttu-id="6d6f6-177">O `<operator>` descreve a relação entre a propriedade o valor:</span><span class="sxs-lookup"><span data-stu-id="6d6f6-177">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="6d6f6-178">Operador</span><span class="sxs-lookup"><span data-stu-id="6d6f6-178">Operator</span></span> | <span data-ttu-id="6d6f6-179">Função</span><span class="sxs-lookup"><span data-stu-id="6d6f6-179">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="6d6f6-180">Correspondência exata</span><span class="sxs-lookup"><span data-stu-id="6d6f6-180">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="6d6f6-181">Sem correspondência exata</span><span class="sxs-lookup"><span data-stu-id="6d6f6-181">Not exact match</span></span> |
| `~`      | <span data-ttu-id="6d6f6-182">Contém</span><span class="sxs-lookup"><span data-stu-id="6d6f6-182">Contains</span></span>        |

<span data-ttu-id="6d6f6-183">`<value>` é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-183">`<value>` is a string.</span></span> <span data-ttu-id="6d6f6-184">As pesquisas não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="6d6f6-184">All the lookups are case insensitive.</span></span>

<span data-ttu-id="6d6f6-185">Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="6d6f6-185">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="6d6f6-186">As expressões podem ser associadas a operadores condicionais:</span><span class="sxs-lookup"><span data-stu-id="6d6f6-186">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="6d6f6-187">Operador</span><span class="sxs-lookup"><span data-stu-id="6d6f6-187">Operator</span></span> | <span data-ttu-id="6d6f6-188">Função</span><span class="sxs-lookup"><span data-stu-id="6d6f6-188">Function</span></span> |
| :------: | :------: |
| <code>&#124;</code>      | <span data-ttu-id="6d6f6-189">OU</span><span class="sxs-lookup"><span data-stu-id="6d6f6-189">OR</span></span>       |
| `&`      | <span data-ttu-id="6d6f6-190">AND</span><span class="sxs-lookup"><span data-stu-id="6d6f6-190">AND</span></span>      |

<span data-ttu-id="6d6f6-191">Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="6d6f6-191">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="6d6f6-192">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executar testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="6d6f6-192">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6d6f6-193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d6f6-193">See also</span></span>

 [<span data-ttu-id="6d6f6-194">Estruturas e Destinos</span><span class="sxs-lookup"><span data-stu-id="6d6f6-194">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
 [<span data-ttu-id="6d6f6-195">Catálogo do Identificador de Tempo de Execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="6d6f6-195">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
