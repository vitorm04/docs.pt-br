---
title: "Comando dotnet test – CLI do .NET Core"
description: "O comando dotnet test é usado para executar testes de unidade em um determinado projeto."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 9eb5be38549711717c11767332bfc84920ea927a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="dotnet-test"></a><span data-ttu-id="795c0-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="795c0-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="795c0-104">Nome</span><span class="sxs-lookup"><span data-stu-id="795c0-104">Name</span></span>

<span data-ttu-id="795c0-105">`dotnet test` - driver de teste do .NET usado para executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="795c0-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="795c0-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="795c0-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="795c0-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="795c0-107">.NET Core 2.x</span></span>](#tab/netcore2x)


```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="795c0-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="795c0-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="795c0-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="795c0-109">Description</span></span>

<span data-ttu-id="795c0-110">O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="795c0-110">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="795c0-111">Testes de unidade são projetos de aplicativo de console que têm dependências na estrutura de teste da unidade (por exemplo, MSTest, NUnit ou xUnit) e no executor de teste dotnet da estrutura de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="795c0-111">Unit tests are console application projects that have dependencies on the unit test framework (for example, MSTest, NUnit, or xUnit) and the dotnet test runner for the unit testing framework.</span></span> <span data-ttu-id="795c0-112">Eles são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.</span><span class="sxs-lookup"><span data-stu-id="795c0-112">These are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="795c0-113">Projetos de teste também precisam especificar o executor de teste.</span><span class="sxs-lookup"><span data-stu-id="795c0-113">Test projects also must specify the test runner.</span></span> <span data-ttu-id="795c0-114">Isso é especificado usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:</span><span class="sxs-lookup"><span data-stu-id="795c0-114">This is specified using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a><span data-ttu-id="795c0-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="795c0-115">Arguments</span></span>

`PROJECT`

<span data-ttu-id="795c0-116">Especifica um caminho para o projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="795c0-116">Specifies a path to the test project.</span></span> <span data-ttu-id="795c0-117">Se for omitido, o padrão será o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="795c0-117">If omitted, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="795c0-118">Opções</span><span class="sxs-lookup"><span data-stu-id="795c0-118">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="795c0-119">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="795c0-119">.NET Core 2.x</span></span>](#tab/netcore2x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="795c0-120">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="795c0-120">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="795c0-121">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="795c0-121">Defines the build configuration.</span></span> <span data-ttu-id="795c0-122">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="795c0-122">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="795c0-123">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="795c0-123">Enables data collector for the test run.</span></span> <span data-ttu-id="795c0-124">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="795c0-124">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="795c0-125">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="795c0-125">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="795c0-126">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="795c0-126">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="795c0-127">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="795c0-127">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="795c0-128">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="795c0-128">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="795c0-129">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executar testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="795c0-129">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="795c0-130">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="795c0-130">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="795c0-131">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="795c0-131">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="795c0-132">Não compila o projeto de teste antes de executá-lo.</span><span class="sxs-lookup"><span data-stu-id="795c0-132">Does not build the test project prior to running it.</span></span>

`--no-restore`

<span data-ttu-id="795c0-133">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="795c0-133">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="795c0-134">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="795c0-134">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="795c0-135">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="795c0-135">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="795c0-136">O diretório especificado será criado se ele não existir.</span><span class="sxs-lookup"><span data-stu-id="795c0-136">The specified directory will be created if it doesn't exist.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="795c0-137">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="795c0-137">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="795c0-138">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="795c0-138">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="795c0-139">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="795c0-139">Sets the verbosity level of the command.</span></span> <span data-ttu-id="795c0-140">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="795c0-140">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="795c0-141">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="795c0-141">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="795c0-142">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="795c0-142">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="795c0-143">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="795c0-143">Defines the build configuration.</span></span> <span data-ttu-id="795c0-144">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="795c0-144">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="795c0-145">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="795c0-145">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="795c0-146">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="795c0-146">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="795c0-147">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="795c0-147">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="795c0-148">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="795c0-148">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="795c0-149">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executar testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="795c0-149">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="795c0-150">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="795c0-150">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="795c0-151">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="795c0-151">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="795c0-152">Não compila o projeto de teste antes de executá-lo.</span><span class="sxs-lookup"><span data-stu-id="795c0-152">Does not build the test project prior to running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="795c0-153">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="795c0-153">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="795c0-154">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="795c0-154">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="795c0-155">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="795c0-155">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="795c0-156">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="795c0-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="795c0-157">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="795c0-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="795c0-158">Exemplos</span><span class="sxs-lookup"><span data-stu-id="795c0-158">Examples</span></span>

<span data-ttu-id="795c0-159">Execute os testes no projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="795c0-159">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="795c0-160">Execute os testes no projeto `test1`:</span><span class="sxs-lookup"><span data-stu-id="795c0-160">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="795c0-161">Filtrar detalhes da opção</span><span class="sxs-lookup"><span data-stu-id="795c0-161">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="795c0-162">`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="795c0-162">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="795c0-163">`<property>` é um atributo de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="795c0-163">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="795c0-164">A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:</span><span class="sxs-lookup"><span data-stu-id="795c0-164">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="795c0-165">Estrutura de teste</span><span class="sxs-lookup"><span data-stu-id="795c0-165">Test Framework</span></span> | <span data-ttu-id="795c0-166">Propriedades com suporte</span><span class="sxs-lookup"><span data-stu-id="795c0-166">Supported properties</span></span>                                                                                      |
| :------------: | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="795c0-167">MSTest</span><span class="sxs-lookup"><span data-stu-id="795c0-167">MSTest</span></span>         | <ul><li><span data-ttu-id="795c0-168">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="795c0-168">FullyQualifiedName</span></span></li><li><span data-ttu-id="795c0-169">Nome</span><span class="sxs-lookup"><span data-stu-id="795c0-169">Name</span></span></li><li><span data-ttu-id="795c0-170">ClassName</span><span class="sxs-lookup"><span data-stu-id="795c0-170">ClassName</span></span></li><li><span data-ttu-id="795c0-171">Prioridade</span><span class="sxs-lookup"><span data-stu-id="795c0-171">Priority</span></span></li><li><span data-ttu-id="795c0-172">TestCategory</span><span class="sxs-lookup"><span data-stu-id="795c0-172">TestCategory</span></span></li></ul> |
| <span data-ttu-id="795c0-173">Xunit</span><span class="sxs-lookup"><span data-stu-id="795c0-173">Xunit</span></span>          | <ul><li><span data-ttu-id="795c0-174">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="795c0-174">FullyQualifiedName</span></span></li><li><span data-ttu-id="795c0-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="795c0-175">DisplayName</span></span></li><li><span data-ttu-id="795c0-176">Características</span><span class="sxs-lookup"><span data-stu-id="795c0-176">Traits</span></span></li></ul>                                   |

<span data-ttu-id="795c0-177">O `<operator>` descreve a relação entre a propriedade o valor:</span><span class="sxs-lookup"><span data-stu-id="795c0-177">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="795c0-178">Operador</span><span class="sxs-lookup"><span data-stu-id="795c0-178">Operator</span></span> | <span data-ttu-id="795c0-179">Função</span><span class="sxs-lookup"><span data-stu-id="795c0-179">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="795c0-180">Correspondência exata</span><span class="sxs-lookup"><span data-stu-id="795c0-180">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="795c0-181">Sem correspondência exata</span><span class="sxs-lookup"><span data-stu-id="795c0-181">Not exact match</span></span> |
| `~`      | <span data-ttu-id="795c0-182">Contém</span><span class="sxs-lookup"><span data-stu-id="795c0-182">Contains</span></span>        |

<span data-ttu-id="795c0-183">`<value>` é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="795c0-183">`<value>` is a string.</span></span> <span data-ttu-id="795c0-184">As pesquisas não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="795c0-184">All the lookups are case insensitive.</span></span>

<span data-ttu-id="795c0-185">Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="795c0-185">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="795c0-186">As expressões podem ser associadas a operadores condicionais:</span><span class="sxs-lookup"><span data-stu-id="795c0-186">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="795c0-187">Operador</span><span class="sxs-lookup"><span data-stu-id="795c0-187">Operator</span></span> | <span data-ttu-id="795c0-188">Função</span><span class="sxs-lookup"><span data-stu-id="795c0-188">Function</span></span> |
| :------: | :------: |
| <code>&#124;</code>      | <span data-ttu-id="795c0-189">OU</span><span class="sxs-lookup"><span data-stu-id="795c0-189">OR</span></span>       |
| `&`      | <span data-ttu-id="795c0-190">AND</span><span class="sxs-lookup"><span data-stu-id="795c0-190">AND</span></span>      |

<span data-ttu-id="795c0-191">Você pode colocar expressões entre parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="795c0-191">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="795c0-192">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executar testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="795c0-192">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="795c0-193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="795c0-193">See also</span></span>

 [<span data-ttu-id="795c0-194">Estruturas e Destinos</span><span class="sxs-lookup"><span data-stu-id="795c0-194">Frameworks and Targets</span></span>](../../standard/frameworks.md)  
 [<span data-ttu-id="795c0-195">Catálogo do Identificador de Tempo de Execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="795c0-195">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
