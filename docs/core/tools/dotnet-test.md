---
title: "Comando dotnet test – CLI do .NET Core"
description: "O comando dotnet test é usado para executar testes de unidade em um determinado projeto."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: 55329bed71be21a787d6e77d8c0ea67d607676b8
ms.contentlocale: pt-br
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-test"></a><span data-ttu-id="feb75-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="feb75-103">dotnet test</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="feb75-104">Nome</span><span class="sxs-lookup"><span data-stu-id="feb75-104">Name</span></span>

<span data-ttu-id="feb75-105">`dotnet test` - driver de teste do .NET usado para executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="feb75-105">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="feb75-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="feb75-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="feb75-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="feb75-107">.NET Core 2.x</span></span>](#tab/netcore2x)


```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="feb75-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="feb75-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="feb75-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="feb75-109">Description</span></span>

<span data-ttu-id="feb75-110">O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="feb75-110">The `dotnet test` command is used to execute unit tests in a given project.</span></span> <span data-ttu-id="feb75-111">Testes de unidade são projetos de aplicativo de console que têm dependências na estrutura de teste da unidade (por exemplo, MSTest, NUnit ou xUnit) e no executor de teste dotnet da estrutura de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="feb75-111">Unit tests are console application projects that have dependencies on the unit test framework (for example, MSTest, NUnit, or xUnit) and the dotnet test runner for the unit testing framework.</span></span> <span data-ttu-id="feb75-112">Eles são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.</span><span class="sxs-lookup"><span data-stu-id="feb75-112">These are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="feb75-113">Projetos de teste também precisam especificar o executor de teste.</span><span class="sxs-lookup"><span data-stu-id="feb75-113">Test projects also must specify the test runner.</span></span> <span data-ttu-id="feb75-114">Isso é especificado usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:</span><span class="sxs-lookup"><span data-stu-id="feb75-114">This is specified using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

<span data-ttu-id="feb75-115">[!code-xml[Modelo Básico do XUnit](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]</span><span class="sxs-lookup"><span data-stu-id="feb75-115">[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]</span></span>

## <a name="arguments"></a><span data-ttu-id="feb75-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="feb75-116">Arguments</span></span>

`PROJECT`

<span data-ttu-id="feb75-117">Especifica um caminho para o projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="feb75-117">Specifies a path to the test project.</span></span> <span data-ttu-id="feb75-118">Se for omitido, o padrão será o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="feb75-118">If omitted, it defaults to current directory.</span></span>

## <a name="options"></a><span data-ttu-id="feb75-119">Opções</span><span class="sxs-lookup"><span data-stu-id="feb75-119">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="feb75-120">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="feb75-120">.NET Core 2.x</span></span>](#tab/netcore2x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="feb75-121">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="feb75-121">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="feb75-122">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="feb75-122">Defines the build configuration.</span></span> <span data-ttu-id="feb75-123">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="feb75-123">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

<span data-ttu-id="feb75-124">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="feb75-124">Enables data collector for the test run.</span></span> <span data-ttu-id="feb75-125">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="feb75-125">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="feb75-126">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="feb75-126">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="feb75-127">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="feb75-127">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="feb75-128">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="feb75-128">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="feb75-129">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="feb75-129">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="feb75-130">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executar testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="feb75-130">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="feb75-131">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="feb75-131">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="feb75-132">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="feb75-132">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="feb75-133">Não compila o projeto de teste antes de executá-lo.</span><span class="sxs-lookup"><span data-stu-id="feb75-133">Does not build the test project prior to running it.</span></span>

`--no-restore`

<span data-ttu-id="feb75-134">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="feb75-134">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="feb75-135">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="feb75-135">Directory in which to find the binaries to run.</span></span>

`-r|--results-directory <PATH>`

<span data-ttu-id="feb75-136">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="feb75-136">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="feb75-137">O diretório especificado será criado se ele não existir.</span><span class="sxs-lookup"><span data-stu-id="feb75-137">The specified directory will be created if it doesn't exist.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="feb75-138">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="feb75-138">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="feb75-139">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="feb75-139">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="feb75-140">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="feb75-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="feb75-141">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="feb75-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="feb75-142">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="feb75-142">.NET Core 1.x</span></span>](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

<span data-ttu-id="feb75-143">Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.</span><span class="sxs-lookup"><span data-stu-id="feb75-143">Use the custom test adapters from the specified path in the test run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="feb75-144">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="feb75-144">Defines the build configuration.</span></span> <span data-ttu-id="feb75-145">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="feb75-145">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

<span data-ttu-id="feb75-146">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="feb75-146">Enables diagnostic mode for the test platform and write diagnostic messages to the specified file.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="feb75-147">Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="feb75-147">Looks for test binaries for a specific [framework](../../standard/frameworks.md).</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="feb75-148">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="feb75-148">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="feb75-149">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="feb75-149">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="feb75-150">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executar testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="feb75-150">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

`-h|--help`

<span data-ttu-id="feb75-151">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="feb75-151">Prints out a short help for the command.</span></span>

`-l|--logger <LoggerUri/FriendlyName>`

<span data-ttu-id="feb75-152">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="feb75-152">Specifies a logger for test results.</span></span>

`--no-build`

<span data-ttu-id="feb75-153">Não compila o projeto de teste antes de executá-lo.</span><span class="sxs-lookup"><span data-stu-id="feb75-153">Does not build the test project prior to running it.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="feb75-154">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="feb75-154">Directory in which to find the binaries to run.</span></span>

`-s|--settings <SETTINGS_FILE>`

<span data-ttu-id="feb75-155">Configurações para usar ao executar testes.</span><span class="sxs-lookup"><span data-stu-id="feb75-155">Settings to use when running tests.</span></span>

`-t|--list-tests`

<span data-ttu-id="feb75-156">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="feb75-156">List all of the discovered tests in the current project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="feb75-157">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="feb75-157">Sets the verbosity level of the command.</span></span> <span data-ttu-id="feb75-158">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="feb75-158">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="feb75-159">Exemplos</span><span class="sxs-lookup"><span data-stu-id="feb75-159">Examples</span></span>

<span data-ttu-id="feb75-160">Execute os testes no projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="feb75-160">Run the tests in the project in the current directory:</span></span>

`dotnet test`

<span data-ttu-id="feb75-161">Execute os testes no projeto `test1`:</span><span class="sxs-lookup"><span data-stu-id="feb75-161">Run the tests in the `test1` project:</span></span>

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a><span data-ttu-id="feb75-162">Filtrar detalhes da opção</span><span class="sxs-lookup"><span data-stu-id="feb75-162">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="feb75-163">`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="feb75-163">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="feb75-164">`<property>` é um atributo de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="feb75-164">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="feb75-165">A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:</span><span class="sxs-lookup"><span data-stu-id="feb75-165">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="feb75-166">Estrutura de teste</span><span class="sxs-lookup"><span data-stu-id="feb75-166">Test Framework</span></span> | <span data-ttu-id="feb75-167">Propriedades com suporte</span><span class="sxs-lookup"><span data-stu-id="feb75-167">Supported properties</span></span>                                                                                      |
| :------------: | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="feb75-168">MSTest</span><span class="sxs-lookup"><span data-stu-id="feb75-168">MSTest</span></span>         | <ul><li><span data-ttu-id="feb75-169">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="feb75-169">FullyQualifiedName</span></span></li><li><span data-ttu-id="feb75-170">Nome</span><span class="sxs-lookup"><span data-stu-id="feb75-170">Name</span></span></li><li><span data-ttu-id="feb75-171">ClassName</span><span class="sxs-lookup"><span data-stu-id="feb75-171">ClassName</span></span></li><li><span data-ttu-id="feb75-172">Prioridade</span><span class="sxs-lookup"><span data-stu-id="feb75-172">Priority</span></span></li><li><span data-ttu-id="feb75-173">TestCategory</span><span class="sxs-lookup"><span data-stu-id="feb75-173">TestCategory</span></span></li></ul> |
| <span data-ttu-id="feb75-174">Xunit</span><span class="sxs-lookup"><span data-stu-id="feb75-174">Xunit</span></span>          | <ul><li><span data-ttu-id="feb75-175">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="feb75-175">FullyQualifiedName</span></span></li><li><span data-ttu-id="feb75-176">DisplayName</span><span class="sxs-lookup"><span data-stu-id="feb75-176">DisplayName</span></span></li><li><span data-ttu-id="feb75-177">Características</span><span class="sxs-lookup"><span data-stu-id="feb75-177">Traits</span></span></li></ul>                                   |

<span data-ttu-id="feb75-178">O `<operator>` descreve a relação entre a propriedade o valor:</span><span class="sxs-lookup"><span data-stu-id="feb75-178">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="feb75-179">Operador</span><span class="sxs-lookup"><span data-stu-id="feb75-179">Operator</span></span> | <span data-ttu-id="feb75-180">Função</span><span class="sxs-lookup"><span data-stu-id="feb75-180">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="feb75-181">Correspondência exata</span><span class="sxs-lookup"><span data-stu-id="feb75-181">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="feb75-182">Sem correspondência exata</span><span class="sxs-lookup"><span data-stu-id="feb75-182">Not exact match</span></span> |
| `~`      | <span data-ttu-id="feb75-183">Contém</span><span class="sxs-lookup"><span data-stu-id="feb75-183">Contains</span></span>        |

<span data-ttu-id="feb75-184">`<value>` é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="feb75-184">`<value>` is a string.</span></span> <span data-ttu-id="feb75-185">As pesquisas não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="feb75-185">All the lookups are case insensitive.</span></span>

<span data-ttu-id="feb75-186">Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="feb75-186">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="feb75-187">As expressões podem ser associadas a operadores condicionais:</span><span class="sxs-lookup"><span data-stu-id="feb75-187">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="feb75-188">Operador</span><span class="sxs-lookup"><span data-stu-id="feb75-188">Operator</span></span> | <span data-ttu-id="feb75-189">Função</span><span class="sxs-lookup"><span data-stu-id="feb75-189">Function</span></span> |
| :------: | :------: |
| <code>&#124;</code>      | <span data-ttu-id="feb75-190">OU</span><span class="sxs-lookup"><span data-stu-id="feb75-190">OR</span></span>       |
| `&`      | <span data-ttu-id="feb75-191">AND</span><span class="sxs-lookup"><span data-stu-id="feb75-191">AND</span></span>      |

<span data-ttu-id="feb75-192">Você pode incluir expressões em parênteses ao usar operadores condicionais (por exemplo: `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="feb75-192">You can enclose expressions in paranthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="feb75-193">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executar testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="feb75-193">For additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="feb75-194">Consulte também</span><span class="sxs-lookup"><span data-stu-id="feb75-194">See also</span></span>

 <span data-ttu-id="feb75-195">[Estruturas e Destinos](../../standard/frameworks.md) </span><span class="sxs-lookup"><span data-stu-id="feb75-195">[Frameworks and Targets](../../standard/frameworks.md) </span></span>  
 [<span data-ttu-id="feb75-196">Catálogo do Identificador de Tempo de Execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="feb75-196">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)

