---
title: Comando dotnet test
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
ms.date: 04/29/2020
ms.openlocfilehash: 22b27007d26c98cff40733ef8d449ce334f87848
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802687"
---
# <a name="dotnet-test"></a><span data-ttu-id="e6097-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="e6097-103">dotnet test</span></span>

<span data-ttu-id="e6097-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="e6097-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e6097-105">Nome</span><span class="sxs-lookup"><span data-stu-id="e6097-105">Name</span></span>

<span data-ttu-id="e6097-106">`dotnet test` - driver de teste do .NET usado para executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="e6097-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e6097-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e6097-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="e6097-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6097-108">Description</span></span>

<span data-ttu-id="e6097-109">O `dotnet test` comando é usado para executar testes de unidade em uma determinada solução.</span><span class="sxs-lookup"><span data-stu-id="e6097-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="e6097-110">O `dotnet test` comando cria a solução e executa um aplicativo de host de teste para cada projeto de teste na solução.</span><span class="sxs-lookup"><span data-stu-id="e6097-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="e6097-111">O host de teste executa testes no projeto fornecido usando uma estrutura de teste, por exemplo: MSTest, NUnit ou xUnit, e relata o êxito ou a falha de cada teste.</span><span class="sxs-lookup"><span data-stu-id="e6097-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="e6097-112">Se todos os testes forem bem-sucedidos, o executor de testes retornará 0 como um código de saída; caso contrário, se algum teste falhar, retornará 1.</span><span class="sxs-lookup"><span data-stu-id="e6097-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="e6097-113">Para projetos de vários destinos, os testes são executados para cada estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="e6097-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="e6097-114">O host de teste e a estrutura de teste de unidade são empacotados como pacotes NuGet e restaurados como dependências comuns para o projeto.</span><span class="sxs-lookup"><span data-stu-id="e6097-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="e6097-115">Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:</span><span class="sxs-lookup"><span data-stu-id="e6097-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="e6097-116">Onde `Microsoft.NET.Test.Sdk` é o host de teste, `xunit` é a estrutura de teste.</span><span class="sxs-lookup"><span data-stu-id="e6097-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="e6097-117">E `xunit.runner.visualstudio` é um adaptador de teste, que permite que a estrutura xUnit funcione com o host de teste.</span><span class="sxs-lookup"><span data-stu-id="e6097-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="e6097-118">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="e6097-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="e6097-119">Argumentos</span><span class="sxs-lookup"><span data-stu-id="e6097-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="e6097-120">Caminho para o projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="e6097-120">Path to the test project.</span></span>
  - <span data-ttu-id="e6097-121">Caminho para a solução.</span><span class="sxs-lookup"><span data-stu-id="e6097-121">Path to the solution.</span></span>
  - <span data-ttu-id="e6097-122">Caminho para um diretório que contém um projeto ou uma solução.</span><span class="sxs-lookup"><span data-stu-id="e6097-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="e6097-123">Caminho para um arquivo *. dll* do projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="e6097-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="e6097-124">Se não for especificado, ele pesquisará um projeto ou uma solução no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="e6097-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="e6097-125">Opções</span><span class="sxs-lookup"><span data-stu-id="e6097-125">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="e6097-126">Caminho para um diretório a ser procurado para os adaptadores de teste adicionais.</span><span class="sxs-lookup"><span data-stu-id="e6097-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="e6097-127">Somente arquivos *. dll* com sufixo `.TestAdapter.dll` são inspecionados.</span><span class="sxs-lookup"><span data-stu-id="e6097-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="e6097-128">Se não for especificado, o diretório do test *. dll* será pesquisado.</span><span class="sxs-lookup"><span data-stu-id="e6097-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="e6097-129">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="e6097-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="e6097-130">Essa opção é útil para isolar testes problemáticos que causam falha no host de teste.</span><span class="sxs-lookup"><span data-stu-id="e6097-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="e6097-131">Quando uma falha é detectada, ela cria um arquivo de sequência no `TestResults/<Guid>/<Guid>_Sequence.xml` que captura a ordem dos testes que foram executados antes da falha.</span><span class="sxs-lookup"><span data-stu-id="e6097-131">When a crash is detected, it creates an sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="e6097-132">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="e6097-132">Defines the build configuration.</span></span> <span data-ttu-id="e6097-133">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="e6097-133">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="e6097-134">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="e6097-134">Enables data collector for the test run.</span></span> <span data-ttu-id="e6097-135">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="e6097-135">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="e6097-136">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico no arquivo especificado e nos arquivos ao lado dele.</span><span class="sxs-lookup"><span data-stu-id="e6097-136">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="e6097-137">O processo que está registrando as mensagens determina quais arquivos são criados, como `*.host_<date>.txt` para o log do host de teste e `*.datacollector_<date>.txt` para o log do coletor de dados.</span><span class="sxs-lookup"><span data-stu-id="e6097-137">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e6097-138">Força o uso de `dotnet` ou .NET Framework host de teste para os binários de teste.</span><span class="sxs-lookup"><span data-stu-id="e6097-138">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="e6097-139">Essa opção determina apenas o tipo de host a ser usado.</span><span class="sxs-lookup"><span data-stu-id="e6097-139">This option only determines which type of host to use.</span></span> <span data-ttu-id="e6097-140">A versão real do Framework a ser usada é determinada pelo *runtimeconfig. JSON* do projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="e6097-140">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="e6097-141">Quando não especificado, o [atributo de assembly TargetFramework](/dotnet/api/system.runtime.versioning.targetframeworkattribute) é usado para determinar o tipo de host.</span><span class="sxs-lookup"><span data-stu-id="e6097-141">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="e6097-142">Quando esse atributo é removido do *. dll*, o host de .NET Framework é usado.</span><span class="sxs-lookup"><span data-stu-id="e6097-142">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="e6097-143">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="e6097-143">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="e6097-144">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="e6097-144">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="e6097-145">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="e6097-145">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="e6097-146">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="e6097-146">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="e6097-147">Permite que o comando pare e aguarde entrada ou ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="e6097-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="e6097-148">Por exemplo, para concluir a autenticação.</span><span class="sxs-lookup"><span data-stu-id="e6097-148">For example, to complete authentication.</span></span> <span data-ttu-id="e6097-149">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e6097-149">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="e6097-150">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="e6097-150">Specifies a logger for test results.</span></span> <span data-ttu-id="e6097-151">Ao contrário do MSBuild, o teste dotnet não aceita abreviações: em vez de `-l "console;v=d"` usar `-l "console;verbosity=detailed"` .</span><span class="sxs-lookup"><span data-stu-id="e6097-151">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="e6097-152">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="e6097-152">Doesn't build the test project before running it.</span></span> <span data-ttu-id="e6097-153">Ele também define implicitamente o- `--no-restore` Flag.</span><span class="sxs-lookup"><span data-stu-id="e6097-153">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="e6097-154">Executar testes sem exibir o banner do Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="e6097-154">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="e6097-155">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e6097-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="e6097-156">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="e6097-156">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="e6097-157">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="e6097-157">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="e6097-158">Se não for especificado, o caminho padrão será `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="e6097-158">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="e6097-159">Para projetos com várias estruturas de destino (por meio da `TargetFrameworks` Propriedade), também é necessário definir `--framework` quando você especifica essa opção.</span><span class="sxs-lookup"><span data-stu-id="e6097-159">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="e6097-160">`dotnet test`sempre executa testes do diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="e6097-160">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="e6097-161">Você pode usar <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> para consumir ativos de teste no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="e6097-161">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="e6097-162">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="e6097-162">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="e6097-163">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="e6097-163">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="e6097-164">O padrão é `TestResults` o diretório que contém o arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="e6097-164">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="e6097-165">O tempo de execução de destino para o qual testar.</span><span class="sxs-lookup"><span data-stu-id="e6097-165">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="e6097-166">O arquivo `.runsettings` a ser usado para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="e6097-166">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="e6097-167">Observe que o `TargetPlatform` elemento (x86 | x64) não tem nenhum efeito para `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="e6097-167">Note that the `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="e6097-168">Para executar testes direcionados para x86, instale a versão x86 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e6097-168">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="e6097-169">O bit de bits do *dotnet. exe* que está no caminho é o que será usado para executar testes.</span><span class="sxs-lookup"><span data-stu-id="e6097-169">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="e6097-170">Para saber mais, consulte os recursos a seguir:</span><span class="sxs-lookup"><span data-stu-id="e6097-170">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="e6097-171">Configurar testes de unidade usando um arquivo `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="e6097-171">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="e6097-172">Configurar uma execução de teste</span><span class="sxs-lookup"><span data-stu-id="e6097-172">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="e6097-173">Lista todos os testes descobertos no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="e6097-173">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="e6097-174">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="e6097-174">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e6097-175">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e6097-175">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e6097-176">O padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="e6097-176">The default is `minimal`.</span></span> <span data-ttu-id="e6097-177">Para obter mais informações, consulte <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="e6097-177">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="e6097-178">**`RunSettings`** argumentos</span><span class="sxs-lookup"><span data-stu-id="e6097-178">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="e6097-179">Inline `RunSettings` são passados como os últimos argumentos na linha de comando após "--" (Observe o espaço após--).</span><span class="sxs-lookup"><span data-stu-id="e6097-179">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="e6097-180">Inline `RunSettings` são especificados como `[name]=[value]` pares.</span><span class="sxs-lookup"><span data-stu-id="e6097-180">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="e6097-181">Um espaço é usado para separar vários pares `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="e6097-181">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="e6097-182">Exemplo: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="e6097-182">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="e6097-183">Para obter mais informações, consulte [passando argumentos RunSettings por meio da linha de comando](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="e6097-183">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="e6097-184">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e6097-184">Examples</span></span>

- <span data-ttu-id="e6097-185">Execute os testes no projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="e6097-185">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="e6097-186">Execute os testes no projeto `test1`:</span><span class="sxs-lookup"><span data-stu-id="e6097-186">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="e6097-187">Execute os testes no projeto no diretório atual e gere um arquivo de resultados de teste no formato TRX:</span><span class="sxs-lookup"><span data-stu-id="e6097-187">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="e6097-188">Execute os testes no projeto no diretório atual e faça logon com detalhes detalhados no console:</span><span class="sxs-lookup"><span data-stu-id="e6097-188">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```
  
  - <span data-ttu-id="e6097-189">Execute os testes no projeto no diretório atual e relate os testes que estavam em andamento quando o host de teste falhou:</span><span class="sxs-lookup"><span data-stu-id="e6097-189">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="e6097-190">Filtrar detalhes da opção</span><span class="sxs-lookup"><span data-stu-id="e6097-190">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="e6097-191">`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="e6097-191">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="e6097-192">`<property>` é um atributo de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="e6097-192">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="e6097-193">A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:</span><span class="sxs-lookup"><span data-stu-id="e6097-193">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="e6097-194">Estrutura de teste</span><span class="sxs-lookup"><span data-stu-id="e6097-194">Test Framework</span></span> | <span data-ttu-id="e6097-195">Propriedades com suporte</span><span class="sxs-lookup"><span data-stu-id="e6097-195">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e6097-196">MSTest</span><span class="sxs-lookup"><span data-stu-id="e6097-196">MSTest</span></span>         | <ul><li><span data-ttu-id="e6097-197">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="e6097-197">FullyQualifiedName</span></span></li><li><span data-ttu-id="e6097-198">Nome</span><span class="sxs-lookup"><span data-stu-id="e6097-198">Name</span></span></li><li><span data-ttu-id="e6097-199">ClassName</span><span class="sxs-lookup"><span data-stu-id="e6097-199">ClassName</span></span></li><li><span data-ttu-id="e6097-200">Prioridade</span><span class="sxs-lookup"><span data-stu-id="e6097-200">Priority</span></span></li><li><span data-ttu-id="e6097-201">TestCategory</span><span class="sxs-lookup"><span data-stu-id="e6097-201">TestCategory</span></span></li></ul> |
| <span data-ttu-id="e6097-202">xUnit</span><span class="sxs-lookup"><span data-stu-id="e6097-202">xUnit</span></span>          | <ul><li><span data-ttu-id="e6097-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="e6097-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="e6097-204">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e6097-204">DisplayName</span></span></li><li><span data-ttu-id="e6097-205">Características</span><span class="sxs-lookup"><span data-stu-id="e6097-205">Traits</span></span></li></ul>                                   |

<span data-ttu-id="e6097-206">O `<operator>` descreve a relação entre a propriedade o valor:</span><span class="sxs-lookup"><span data-stu-id="e6097-206">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="e6097-207">Operador</span><span class="sxs-lookup"><span data-stu-id="e6097-207">Operator</span></span> | <span data-ttu-id="e6097-208">Função</span><span class="sxs-lookup"><span data-stu-id="e6097-208">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="e6097-209">Correspondência exata</span><span class="sxs-lookup"><span data-stu-id="e6097-209">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="e6097-210">Sem correspondência exata</span><span class="sxs-lookup"><span data-stu-id="e6097-210">Not exact match</span></span> |
| `~`      | <span data-ttu-id="e6097-211">Contém</span><span class="sxs-lookup"><span data-stu-id="e6097-211">Contains</span></span>        |
| `!~`     | <span data-ttu-id="e6097-212">Não contém</span><span class="sxs-lookup"><span data-stu-id="e6097-212">Not contains</span></span>    |

<span data-ttu-id="e6097-213">`<value>` é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e6097-213">`<value>` is a string.</span></span> <span data-ttu-id="e6097-214">As pesquisas não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="e6097-214">All the lookups are case insensitive.</span></span>

<span data-ttu-id="e6097-215">Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="e6097-215">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="e6097-216">As expressões podem ser associadas a operadores condicionais:</span><span class="sxs-lookup"><span data-stu-id="e6097-216">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="e6097-217">Operador</span><span class="sxs-lookup"><span data-stu-id="e6097-217">Operator</span></span>            | <span data-ttu-id="e6097-218">Função</span><span class="sxs-lookup"><span data-stu-id="e6097-218">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="e6097-219">OU</span><span class="sxs-lookup"><span data-stu-id="e6097-219">OR</span></span>       |
| `&`                 | <span data-ttu-id="e6097-220">AND</span><span class="sxs-lookup"><span data-stu-id="e6097-220">AND</span></span>      |

<span data-ttu-id="e6097-221">Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="e6097-221">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="e6097-222">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="e6097-222">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e6097-223">Confira também</span><span class="sxs-lookup"><span data-stu-id="e6097-223">See also</span></span>

- [<span data-ttu-id="e6097-224">Estruturas e destinos</span><span class="sxs-lookup"><span data-stu-id="e6097-224">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="e6097-225">Catálogo do Identificador de Runtime do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e6097-225">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="e6097-226">Passando argumentos RunSettings por meio de linha de comando</span><span class="sxs-lookup"><span data-stu-id="e6097-226">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
