---
title: Comando dotnet test
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
ms.date: 04/29/2020
ms.openlocfilehash: ef71e48daa7c4a6f33961d05a2f3def122087b0e
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975427"
---
# <a name="dotnet-test"></a><span data-ttu-id="5b2a2-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="5b2a2-103">dotnet test</span></span>

<span data-ttu-id="5b2a2-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="5b2a2-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5b2a2-105">Nome</span><span class="sxs-lookup"><span data-stu-id="5b2a2-105">Name</span></span>

<span data-ttu-id="5b2a2-106">`dotnet test` - driver de teste do .NET usado para executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5b2a2-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="5b2a2-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
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

## <a name="description"></a><span data-ttu-id="5b2a2-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b2a2-108">Description</span></span>

<span data-ttu-id="5b2a2-109">O `dotnet test` comando é usado para executar testes de unidade em uma determinada solução.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="5b2a2-110">O `dotnet test` comando cria a solução e executa um aplicativo de host de teste para cada projeto de teste na solução.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="5b2a2-111">O host de teste executa testes no projeto fornecido usando uma estrutura de teste, por exemplo: MSTest, NUnit ou xUnit, e relata o êxito ou a falha de cada teste.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="5b2a2-112">Se todos os testes forem bem-sucedidos, o executor de testes retornará 0 como um código de saída; caso contrário, se algum teste falhar, retornará 1.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="5b2a2-113">Para projetos de vários destinos, os testes são executados para cada estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="5b2a2-114">O host de teste e a estrutura de teste de unidade são empacotados como pacotes NuGet e restaurados como dependências comuns para o projeto.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="5b2a2-115">Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:</span><span class="sxs-lookup"><span data-stu-id="5b2a2-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="5b2a2-116">Onde `Microsoft.NET.Test.Sdk` é o host de teste `xunit` , é a estrutura de teste.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="5b2a2-117">E `xunit.runner.visualstudio` é um adaptador de teste, que permite que a estrutura xUnit funcione com o host de teste.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="5b2a2-118">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="5b2a2-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="5b2a2-119">Arguments</span><span class="sxs-lookup"><span data-stu-id="5b2a2-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="5b2a2-120">Caminho para o projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-120">Path to the test project.</span></span>
  - <span data-ttu-id="5b2a2-121">Caminho para a solução.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-121">Path to the solution.</span></span>
  - <span data-ttu-id="5b2a2-122">Caminho para um diretório que contém um projeto ou uma solução.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="5b2a2-123">Caminho para um arquivo *. dll* do projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="5b2a2-124">Se não for especificado, ele pesquisará um projeto ou uma solução no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="5b2a2-125">Opções</span><span class="sxs-lookup"><span data-stu-id="5b2a2-125">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="5b2a2-126">Caminho para um diretório a ser procurado para os adaptadores de teste adicionais.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="5b2a2-127">Somente arquivos *. dll* com sufixo `.TestAdapter.dll` são inspecionados.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="5b2a2-128">Se não for especificado, o diretório do test *. dll* será pesquisado.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="5b2a2-129">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="5b2a2-130">Essa opção é útil para isolar testes problemáticos que causam falha no host de teste.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="5b2a2-131">Quando uma falha é detectada, ela cria um arquivo de `TestResults/<Guid>/<Guid>_Sequence.xml` sequência no que captura a ordem dos testes que foram executados antes da falha.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-131">When a crash is detected, it creates an sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="5b2a2-132">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-132">Defines the build configuration.</span></span> <span data-ttu-id="5b2a2-133">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-133">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="5b2a2-134">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-134">Enables data collector for the test run.</span></span> <span data-ttu-id="5b2a2-135">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="5b2a2-135">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="5b2a2-136">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico no arquivo especificado e nos arquivos ao lado dele.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-136">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="5b2a2-137">O processo que está registrando as mensagens determina quais arquivos são criados, como `*.host_<date>.txt` para o log do host de `*.datacollector_<date>.txt` teste e para o log do coletor de dados.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-137">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5b2a2-138">Força o uso de `dotnet` ou .NET Framework host de teste para os binários de teste.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-138">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="5b2a2-139">Essa opção determina apenas o tipo de host a ser usado.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-139">This option only determines which type of host to use.</span></span> <span data-ttu-id="5b2a2-140">A versão real do Framework a ser usada é determinada pelo *runtimeconfig. JSON* do projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-140">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="5b2a2-141">Quando não especificado, o [atributo de assembly TargetFramework](/dotnet/api/system.runtime.versioning.targetframeworkattribute) é usado para determinar o tipo de host.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-141">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="5b2a2-142">Quando esse atributo é removido do *. dll*, o host de .NET Framework é usado.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-142">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="5b2a2-143">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-143">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="5b2a2-144">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="5b2a2-144">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="5b2a2-145">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="5b2a2-145">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="5b2a2-146">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-146">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="5b2a2-147">Permite que o comando pare e aguarde entrada ou ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="5b2a2-148">Por exemplo, para concluir a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-148">For example, to complete authentication.</span></span> <span data-ttu-id="5b2a2-149">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-149">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="5b2a2-150">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-150">Specifies a logger for test results.</span></span> <span data-ttu-id="5b2a2-151">Ao contrário do MSBuild, o teste dotnet não aceita abreviações `-l "console;v=d"` : `-l "console;verbosity=detailed"`em vez de usar.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-151">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="5b2a2-152">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-152">Doesn't build the test project before running it.</span></span> <span data-ttu-id="5b2a2-153">Ele também define implicitamente o- `--no-restore` Flag.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-153">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="5b2a2-154">Executar testes sem exibir o banner do Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-154">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="5b2a2-155">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="5b2a2-156">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-156">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="5b2a2-157">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-157">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="5b2a2-158">Se não for especificado, o caminho padrão será `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-158">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="5b2a2-159">Para projetos com várias estruturas de destino (por meio `TargetFrameworks` da propriedade), também é necessário definir `--framework` quando você especifica essa opção.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-159">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="5b2a2-160">`dotnet test`sempre execute testes do diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-160">`dotnet test` always run tests from the output directory.</span></span> <span data-ttu-id="5b2a2-161">Você pode usar <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> para consumir ativos de teste no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-161">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="5b2a2-162">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-162">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="5b2a2-163">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-163">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="5b2a2-164">O padrão é `TestResults` o diretório que contém o arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-164">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="5b2a2-165">O tempo de execução de destino para o qual testar.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-165">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="5b2a2-166">O arquivo `.runsettings` a ser usado para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-166">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="5b2a2-167">Observe que o `TargetPlatform` elemento (x86 | x64) não tem nenhum efeito `dotnet test`para.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-167">Note that the `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="5b2a2-168">Para executar testes direcionados para x86, instale a versão x86 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-168">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="5b2a2-169">O bit de bits do *dotnet. exe* que está no caminho é o que será usado para executar testes.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-169">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="5b2a2-170">Para saber mais, consulte os recursos a seguir:</span><span class="sxs-lookup"><span data-stu-id="5b2a2-170">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="5b2a2-171">Configurar testes de unidade usando um arquivo `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-171">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="5b2a2-172">Configurar uma execução de teste</span><span class="sxs-lookup"><span data-stu-id="5b2a2-172">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="5b2a2-173">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-173">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="5b2a2-174">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-174">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5b2a2-175">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-175">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="5b2a2-176">O padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-176">The default is `minimal`.</span></span> <span data-ttu-id="5b2a2-177">Para obter mais informações, consulte <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-177">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="5b2a2-178">**`RunSettings`** argumentos</span><span class="sxs-lookup"><span data-stu-id="5b2a2-178">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="5b2a2-179">Inline `RunSettings` são passados como os últimos argumentos na linha de comando após "--" (Observe o espaço após--).</span><span class="sxs-lookup"><span data-stu-id="5b2a2-179">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="5b2a2-180">Inline `RunSettings` são especificados como `[name]=[value]` pares.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-180">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="5b2a2-181">Um espaço é usado para separar vários pares `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-181">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="5b2a2-182">Exemplo: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="5b2a2-182">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="5b2a2-183">Para obter mais informações, consulte [passando argumentos RunSettings por meio da linha de comando](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="5b2a2-183">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="5b2a2-184">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5b2a2-184">Examples</span></span>

- <span data-ttu-id="5b2a2-185">Execute os testes no projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="5b2a2-185">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="5b2a2-186">Execute os testes no projeto `test1`:</span><span class="sxs-lookup"><span data-stu-id="5b2a2-186">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="5b2a2-187">Execute os testes no projeto no diretório atual e gere um arquivo de resultados de teste no formato TRX:</span><span class="sxs-lookup"><span data-stu-id="5b2a2-187">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="5b2a2-188">Execute os testes no projeto no diretório atual e faça logon com detalhes detalhados no console:</span><span class="sxs-lookup"><span data-stu-id="5b2a2-188">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```
  
  - <span data-ttu-id="5b2a2-189">Execute os testes no projeto no diretório atual e relate os testes que estavam em andamento quando o host de teste falhou:</span><span class="sxs-lookup"><span data-stu-id="5b2a2-189">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="5b2a2-190">Filtrar detalhes da opção</span><span class="sxs-lookup"><span data-stu-id="5b2a2-190">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="5b2a2-191">`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-191">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="5b2a2-192">`<property>` é um atributo de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-192">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="5b2a2-193">A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:</span><span class="sxs-lookup"><span data-stu-id="5b2a2-193">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="5b2a2-194">Estrutura de teste</span><span class="sxs-lookup"><span data-stu-id="5b2a2-194">Test Framework</span></span> | <span data-ttu-id="5b2a2-195">Propriedades com suporte</span><span class="sxs-lookup"><span data-stu-id="5b2a2-195">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="5b2a2-196">MSTest</span><span class="sxs-lookup"><span data-stu-id="5b2a2-196">MSTest</span></span>         | <ul><li><span data-ttu-id="5b2a2-197">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="5b2a2-197">FullyQualifiedName</span></span></li><li><span data-ttu-id="5b2a2-198">Nome</span><span class="sxs-lookup"><span data-stu-id="5b2a2-198">Name</span></span></li><li><span data-ttu-id="5b2a2-199">ClassName</span><span class="sxs-lookup"><span data-stu-id="5b2a2-199">ClassName</span></span></li><li><span data-ttu-id="5b2a2-200">Prioridade</span><span class="sxs-lookup"><span data-stu-id="5b2a2-200">Priority</span></span></li><li><span data-ttu-id="5b2a2-201">TestCategory</span><span class="sxs-lookup"><span data-stu-id="5b2a2-201">TestCategory</span></span></li></ul> |
| <span data-ttu-id="5b2a2-202">xUnit</span><span class="sxs-lookup"><span data-stu-id="5b2a2-202">xUnit</span></span>          | <ul><li><span data-ttu-id="5b2a2-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="5b2a2-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="5b2a2-204">DisplayName</span><span class="sxs-lookup"><span data-stu-id="5b2a2-204">DisplayName</span></span></li><li><span data-ttu-id="5b2a2-205">Características</span><span class="sxs-lookup"><span data-stu-id="5b2a2-205">Traits</span></span></li></ul>                                   |

<span data-ttu-id="5b2a2-206">O `<operator>` descreve a relação entre a propriedade o valor:</span><span class="sxs-lookup"><span data-stu-id="5b2a2-206">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="5b2a2-207">Operador</span><span class="sxs-lookup"><span data-stu-id="5b2a2-207">Operator</span></span> | <span data-ttu-id="5b2a2-208">Função</span><span class="sxs-lookup"><span data-stu-id="5b2a2-208">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="5b2a2-209">Correspondência exata</span><span class="sxs-lookup"><span data-stu-id="5b2a2-209">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="5b2a2-210">Sem correspondência exata</span><span class="sxs-lookup"><span data-stu-id="5b2a2-210">Not exact match</span></span> |
| `~`      | <span data-ttu-id="5b2a2-211">Contém</span><span class="sxs-lookup"><span data-stu-id="5b2a2-211">Contains</span></span>        |
| `!~`     | <span data-ttu-id="5b2a2-212">Não contém</span><span class="sxs-lookup"><span data-stu-id="5b2a2-212">Not contains</span></span>    |

<span data-ttu-id="5b2a2-213">`<value>` é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-213">`<value>` is a string.</span></span> <span data-ttu-id="5b2a2-214">As pesquisas não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="5b2a2-214">All the lookups are case insensitive.</span></span>

<span data-ttu-id="5b2a2-215">Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="5b2a2-215">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="5b2a2-216">As expressões podem ser associadas a operadores condicionais:</span><span class="sxs-lookup"><span data-stu-id="5b2a2-216">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="5b2a2-217">Operador</span><span class="sxs-lookup"><span data-stu-id="5b2a2-217">Operator</span></span>            | <span data-ttu-id="5b2a2-218">Função</span><span class="sxs-lookup"><span data-stu-id="5b2a2-218">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="5b2a2-219">OU</span><span class="sxs-lookup"><span data-stu-id="5b2a2-219">OR</span></span>       |
| `&`                 | <span data-ttu-id="5b2a2-220">AND</span><span class="sxs-lookup"><span data-stu-id="5b2a2-220">AND</span></span>      |

<span data-ttu-id="5b2a2-221">Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="5b2a2-221">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="5b2a2-222">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="5b2a2-222">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5b2a2-223">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b2a2-223">See also</span></span>

- [<span data-ttu-id="5b2a2-224">Estruturas e destinos</span><span class="sxs-lookup"><span data-stu-id="5b2a2-224">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="5b2a2-225">Catálogo do Identificador de Runtime do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5b2a2-225">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="5b2a2-226">Passando argumentos RunSettings por meio de linha de comando</span><span class="sxs-lookup"><span data-stu-id="5b2a2-226">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
