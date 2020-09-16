---
title: Comando dotnet test
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
ms.date: 04/29/2020
ms.openlocfilehash: 5ecfa24905537a663cd967142b765c258495fb22
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537725"
---
# <a name="dotnet-test"></a><span data-ttu-id="85435-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="85435-103">dotnet test</span></span>

<span data-ttu-id="85435-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="85435-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="85435-105">Name</span><span class="sxs-lookup"><span data-stu-id="85435-105">Name</span></span>

<span data-ttu-id="85435-106">`dotnet test` - driver de teste do .NET usado para executar testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="85435-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="85435-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="85435-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <ADAPTER_PATH>] [--blame] [--blame-crash]
    [--blame-crash-dump-type <DUMP_TYPE>] [--blame-crash-collect-always]
    [--blame-hang] [--blame-hang-dump-type <DUMP_TYPE>]
    [--blame-hang-timeout <TIMESPAN>]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_NAME>]
    [-d|--diag <LOG_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <RESULTS_DIR>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="85435-108">Description</span><span class="sxs-lookup"><span data-stu-id="85435-108">Description</span></span>

<span data-ttu-id="85435-109">O `dotnet test` comando é usado para executar testes de unidade em uma determinada solução.</span><span class="sxs-lookup"><span data-stu-id="85435-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="85435-110">O `dotnet test` comando cria a solução e executa um aplicativo de host de teste para cada projeto de teste na solução.</span><span class="sxs-lookup"><span data-stu-id="85435-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="85435-111">O host de teste executa testes no projeto fornecido usando uma estrutura de teste, por exemplo: MSTest, NUnit ou xUnit, e relata o êxito ou a falha de cada teste.</span><span class="sxs-lookup"><span data-stu-id="85435-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="85435-112">Se todos os testes forem bem-sucedidos, o executor de testes retornará 0 como um código de saída; caso contrário, se algum teste falhar, retornará 1.</span><span class="sxs-lookup"><span data-stu-id="85435-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="85435-113">Para projetos de vários destinos, os testes são executados para cada estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="85435-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="85435-114">O host de teste e a estrutura de teste de unidade são empacotados como pacotes NuGet e restaurados como dependências comuns para o projeto.</span><span class="sxs-lookup"><span data-stu-id="85435-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="85435-115">Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:</span><span class="sxs-lookup"><span data-stu-id="85435-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="85435-116">Onde `Microsoft.NET.Test.Sdk` é o host de teste, `xunit` é a estrutura de teste.</span><span class="sxs-lookup"><span data-stu-id="85435-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="85435-117">E `xunit.runner.visualstudio` é um adaptador de teste, que permite que a estrutura xUnit funcione com o host de teste.</span><span class="sxs-lookup"><span data-stu-id="85435-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="85435-118">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="85435-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="85435-119">Argumentos</span><span class="sxs-lookup"><span data-stu-id="85435-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="85435-120">Caminho para o projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="85435-120">Path to the test project.</span></span>
  - <span data-ttu-id="85435-121">Caminho para a solução.</span><span class="sxs-lookup"><span data-stu-id="85435-121">Path to the solution.</span></span>
  - <span data-ttu-id="85435-122">Caminho para um diretório que contém um projeto ou uma solução.</span><span class="sxs-lookup"><span data-stu-id="85435-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="85435-123">Caminho para um arquivo *. dll* do projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="85435-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="85435-124">Se não for especificado, ele pesquisará um projeto ou uma solução no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="85435-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="85435-125">Opções</span><span class="sxs-lookup"><span data-stu-id="85435-125">Options</span></span>

- **`-a|--test-adapter-path <ADAPTER_PATH>`**

  <span data-ttu-id="85435-126">Caminho para um diretório a ser procurado para os adaptadores de teste adicionais.</span><span class="sxs-lookup"><span data-stu-id="85435-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="85435-127">Somente arquivos *. dll* com sufixo `.TestAdapter.dll` são inspecionados.</span><span class="sxs-lookup"><span data-stu-id="85435-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="85435-128">Se não for especificado, o diretório do test *. dll* será pesquisado.</span><span class="sxs-lookup"><span data-stu-id="85435-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="85435-129">Executa os testes no modo blame.</span><span class="sxs-lookup"><span data-stu-id="85435-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="85435-130">Essa opção é útil para isolar testes problemáticos que causam falha no host de teste.</span><span class="sxs-lookup"><span data-stu-id="85435-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="85435-131">Quando uma falha é detectada, ela cria um arquivo de sequência no `TestResults/<Guid>/<Guid>_Sequence.xml` que captura a ordem dos testes que foram executados antes da falha.</span><span class="sxs-lookup"><span data-stu-id="85435-131">When a crash is detected, it creates a sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- <span data-ttu-id="85435-132">**`--blame-crash`** (Disponível desde o SDK da versão prévia do .NET 5,0)</span><span class="sxs-lookup"><span data-stu-id="85435-132">**`--blame-crash`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="85435-133">Executa os testes no modo de culpa e coleta um despejo de memória quando o host de teste sai inesperadamente.</span><span class="sxs-lookup"><span data-stu-id="85435-133">Runs the tests in blame mode and collects a crash dump when the test host exits unexpectedly.</span></span> <span data-ttu-id="85435-134">Essa opção só tem suporte no Windows.</span><span class="sxs-lookup"><span data-stu-id="85435-134">This option is only supported on Windows.</span></span> <span data-ttu-id="85435-135">Um diretório que contém *procdump.exe* e *procdump64.exe* deve estar no caminho ou na PROCDUMP_PATH variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="85435-135">A directory that contains *procdump.exe* and *procdump64.exe* must be in the PATH or PROCDUMP_PATH environment variable.</span></span> <span data-ttu-id="85435-136">[Baixe as ferramentas](/sysinternals/downloads/procdump).</span><span class="sxs-lookup"><span data-stu-id="85435-136">[Download the tools](/sysinternals/downloads/procdump).</span></span> <span data-ttu-id="85435-137">Implica `--blame` .</span><span class="sxs-lookup"><span data-stu-id="85435-137">Implies `--blame`.</span></span>

- <span data-ttu-id="85435-138">**`--blame-crash-dump-type <DUMP_TYPE>`** (Disponível desde o SDK da versão prévia do .NET 5,0)</span><span class="sxs-lookup"><span data-stu-id="85435-138">**`--blame-crash-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="85435-139">O tipo de despejo de memória a ser coletado.</span><span class="sxs-lookup"><span data-stu-id="85435-139">The type of crash dump to be collected.</span></span> <span data-ttu-id="85435-140">Implica `--blame-crash` .</span><span class="sxs-lookup"><span data-stu-id="85435-140">Implies `--blame-crash`.</span></span>

- <span data-ttu-id="85435-141">**`--blame-crash-collect-always`** (Disponível desde o SDK da versão prévia do .NET 5,0)</span><span class="sxs-lookup"><span data-stu-id="85435-141">**`--blame-crash-collect-always`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="85435-142">Coleta um despejo de memória em espera e saída de host de teste inesperado.</span><span class="sxs-lookup"><span data-stu-id="85435-142">Collects a crash dump on expected as well as unexpected test host exit.</span></span>

- <span data-ttu-id="85435-143">**`--blame-hang`** (Disponível desde o SDK da versão prévia do .NET 5,0)</span><span class="sxs-lookup"><span data-stu-id="85435-143">**`--blame-hang`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="85435-144">Execute os testes no modo de culpa e coleta um despejo de travamento quando um teste excede o tempo limite especificado.</span><span class="sxs-lookup"><span data-stu-id="85435-144">Run the tests in blame mode and collects a hang dump when a test exceeds the given timeout.</span></span>

- <span data-ttu-id="85435-145">**`--blame-hang-dump-type <DUMP_TYPE>`** (Disponível desde o SDK da versão prévia do .NET 5,0)</span><span class="sxs-lookup"><span data-stu-id="85435-145">**`--blame-hang-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="85435-146">O tipo de despejo de memória a ser coletado.</span><span class="sxs-lookup"><span data-stu-id="85435-146">The type of crash dump to be collected.</span></span> <span data-ttu-id="85435-147">Deve ser `full` , `mini` ou `none` .</span><span class="sxs-lookup"><span data-stu-id="85435-147">It should be `full`, `mini`, or `none`.</span></span> <span data-ttu-id="85435-148">Quando `none` é especificado, o host de teste é encerrado no tempo limite, mas nenhum despejo é coletado.</span><span class="sxs-lookup"><span data-stu-id="85435-148">When `none` is specified, test host is terminated on timeout, but no dump is collected.</span></span> <span data-ttu-id="85435-149">Implica `--blame-hang` .</span><span class="sxs-lookup"><span data-stu-id="85435-149">Implies `--blame-hang`.</span></span>

- <span data-ttu-id="85435-150">**`--blame-hang-timeout <TIMESPAN>`** (Disponível desde o SDK da versão prévia do .NET 5,0)</span><span class="sxs-lookup"><span data-stu-id="85435-150">**`--blame-hang-timeout <TIMESPAN>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="85435-151">Tempo limite por teste, após o qual um despejo de travamento é disparado e o processo de host de teste é encerrado.</span><span class="sxs-lookup"><span data-stu-id="85435-151">Per-test timeout, after which a hang dump is triggered and the test host process is terminated.</span></span> <span data-ttu-id="85435-152">O valor de tempo limite é especificado em um dos seguintes formatos:</span><span class="sxs-lookup"><span data-stu-id="85435-152">The timeout value is specified in one of the following formats:</span></span>
  
  - <span data-ttu-id="85435-153">1,5 h</span><span class="sxs-lookup"><span data-stu-id="85435-153">1.5h</span></span>
  - <span data-ttu-id="85435-154">próximos</span><span class="sxs-lookup"><span data-stu-id="85435-154">90m</span></span>
  - <span data-ttu-id="85435-155">5400</span><span class="sxs-lookup"><span data-stu-id="85435-155">5400s</span></span>
  - <span data-ttu-id="85435-156">5400000ms</span><span class="sxs-lookup"><span data-stu-id="85435-156">5400000ms</span></span>

  <span data-ttu-id="85435-157">Quando nenhuma unidade é usada (por exemplo, 5,4 milhões), presume-se que o valor esteja em milissegundos.</span><span class="sxs-lookup"><span data-stu-id="85435-157">When no unit is used (for example, 5400000), the value is assumed to be in milliseconds.</span></span> <span data-ttu-id="85435-158">Quando usado junto com testes controlados por dados, o comportamento de tempo limite depende do adaptador de teste usado.</span><span class="sxs-lookup"><span data-stu-id="85435-158">When used together with data driven tests, the timeout behavior depends on the test adapter used.</span></span> <span data-ttu-id="85435-159">Para xUnit e NUnit, o tempo limite é renovado após cada caso de teste.</span><span class="sxs-lookup"><span data-stu-id="85435-159">For xUnit and NUnit the timeout is renewed after every test case.</span></span> <span data-ttu-id="85435-160">Para MSTest, o tempo limite é usado para todos os casos de teste.</span><span class="sxs-lookup"><span data-stu-id="85435-160">For MSTest, the timeout is used for all test cases.</span></span> <span data-ttu-id="85435-161">Essa opção tem suporte no Windows com o netcoreapp 2.1 e posterior e no Linux com o netcoreapp 3.1 e posterior.</span><span class="sxs-lookup"><span data-stu-id="85435-161">This option is supported on Windows with netcoreapp2.1 and later, and on Linux with netcoreapp3.1 and later.</span></span> <span data-ttu-id="85435-162">Não há suporte para macOS.</span><span class="sxs-lookup"><span data-stu-id="85435-162">macOS is not supported.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="85435-163">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="85435-163">Defines the build configuration.</span></span> <span data-ttu-id="85435-164">O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.</span><span class="sxs-lookup"><span data-stu-id="85435-164">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_NAME>`**

  <span data-ttu-id="85435-165">Habilita o coletor de dados para a execução de teste.</span><span class="sxs-lookup"><span data-stu-id="85435-165">Enables data collector for the test run.</span></span> <span data-ttu-id="85435-166">Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).</span><span class="sxs-lookup"><span data-stu-id="85435-166">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>
  
  <span data-ttu-id="85435-167">Para coletar cobertura de código em qualquer plataforma com suporte no .NET Core, instale o [coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) e use a `--collect:"XPlat Code Coverage"` opção.</span><span class="sxs-lookup"><span data-stu-id="85435-167">To collect code coverage on any platform that is supported by .NET Core, install [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) and use the `--collect:"XPlat Code Coverage"` option.</span></span>

  <span data-ttu-id="85435-168">No Windows, você pode coletar cobertura de código usando a `--collect "Code Coverage"` opção.</span><span class="sxs-lookup"><span data-stu-id="85435-168">On Windows, you can collect code coverage by using the `--collect "Code Coverage"` option.</span></span> <span data-ttu-id="85435-169">Essa opção gera um arquivo *. coverage* , que pode ser aberto no Visual Studio 2019 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="85435-169">This option generates a *.coverage* file, which can be opened in Visual Studio 2019 Enterprise.</span></span> <span data-ttu-id="85435-170">Para obter mais informações, consulte [usar cobertura de código](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) e [Personalizar análise de cobertura de código](/visualstudio/test/customizing-code-coverage-analysis).</span><span class="sxs-lookup"><span data-stu-id="85435-170">For more information, see [Use code coverage](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) and [Customize code coverage analysis](/visualstudio/test/customizing-code-coverage-analysis).</span></span>

- **`-d|--diag <LOG_FILE>`**

  <span data-ttu-id="85435-171">Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico no arquivo especificado e nos arquivos ao lado dele.</span><span class="sxs-lookup"><span data-stu-id="85435-171">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="85435-172">O processo que está registrando as mensagens determina quais arquivos são criados, como `*.host_<date>.txt` para o log do host de teste e `*.datacollector_<date>.txt` para o log do coletor de dados.</span><span class="sxs-lookup"><span data-stu-id="85435-172">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="85435-173">Força o uso de `dotnet` ou .NET Framework host de teste para os binários de teste.</span><span class="sxs-lookup"><span data-stu-id="85435-173">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="85435-174">Essa opção determina apenas o tipo de host a ser usado.</span><span class="sxs-lookup"><span data-stu-id="85435-174">This option only determines which type of host to use.</span></span> <span data-ttu-id="85435-175">A versão real do Framework a ser usada é determinada pelo *runtimeconfig.jsno* projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="85435-175">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="85435-176">Quando não especificado, o [atributo de assembly TargetFramework](/dotnet/api/system.runtime.versioning.targetframeworkattribute) é usado para determinar o tipo de host.</span><span class="sxs-lookup"><span data-stu-id="85435-176">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="85435-177">Quando esse atributo é removido do *. dll*, o host de .NET Framework é usado.</span><span class="sxs-lookup"><span data-stu-id="85435-177">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="85435-178">Filtra os testes no projeto atual usando a expressão especificada.</span><span class="sxs-lookup"><span data-stu-id="85435-178">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="85435-179">Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="85435-179">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="85435-180">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="85435-180">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="85435-181">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="85435-181">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="85435-182">Permite que o comando pare e aguarde entrada ou ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="85435-182">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="85435-183">Por exemplo, para concluir a autenticação.</span><span class="sxs-lookup"><span data-stu-id="85435-183">For example, to complete authentication.</span></span> <span data-ttu-id="85435-184">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="85435-184">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER>`**

  <span data-ttu-id="85435-185">Especifica um agente para resultados do teste.</span><span class="sxs-lookup"><span data-stu-id="85435-185">Specifies a logger for test results.</span></span> <span data-ttu-id="85435-186">Ao contrário do MSBuild, o teste dotnet não aceita abreviações: em vez de `-l "console;v=d"` usar `-l "console;verbosity=detailed"` .</span><span class="sxs-lookup"><span data-stu-id="85435-186">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="85435-187">Não compila o projeto de teste antes de sua execução.</span><span class="sxs-lookup"><span data-stu-id="85435-187">Doesn't build the test project before running it.</span></span> <span data-ttu-id="85435-188">Ele também define implicitamente o- `--no-restore` Flag.</span><span class="sxs-lookup"><span data-stu-id="85435-188">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="85435-189">Executar testes sem exibir o banner do Microsoft TestPlatform.</span><span class="sxs-lookup"><span data-stu-id="85435-189">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="85435-190">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="85435-190">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="85435-191">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="85435-191">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="85435-192">Diretório no qual encontram-se os binários para execução.</span><span class="sxs-lookup"><span data-stu-id="85435-192">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="85435-193">Se não for especificado, o caminho padrão será `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="85435-193">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="85435-194">Para projetos com várias estruturas de destino (por meio da `TargetFrameworks` Propriedade), também é necessário definir `--framework` quando você especifica essa opção.</span><span class="sxs-lookup"><span data-stu-id="85435-194">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="85435-195">`dotnet test` sempre executa testes do diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="85435-195">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="85435-196">Você pode usar <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> para consumir ativos de teste no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="85435-196">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <RESULTS_DIR>`**

  <span data-ttu-id="85435-197">O diretório em que os resultados de teste serão colocados.</span><span class="sxs-lookup"><span data-stu-id="85435-197">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="85435-198">Se o diretório especificado não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="85435-198">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="85435-199">O padrão é `TestResults` o diretório que contém o arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="85435-199">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="85435-200">O tempo de execução de destino para o qual testar.</span><span class="sxs-lookup"><span data-stu-id="85435-200">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="85435-201">O arquivo `.runsettings` a ser usado para executar os testes.</span><span class="sxs-lookup"><span data-stu-id="85435-201">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="85435-202">O `TargetPlatform` elemento (x86 | x64) não tem nenhum efeito para `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="85435-202">The `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="85435-203">Para executar testes direcionados para x86, instale a versão x86 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="85435-203">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="85435-204">O bit de bits do *dotnet.exe* que está no caminho é o que será usado para executar testes.</span><span class="sxs-lookup"><span data-stu-id="85435-204">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="85435-205">Para saber mais, consulte os recursos a seguir:</span><span class="sxs-lookup"><span data-stu-id="85435-205">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="85435-206">Configurar testes de unidade usando um arquivo `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="85435-206">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="85435-207">Configurar uma execução de teste</span><span class="sxs-lookup"><span data-stu-id="85435-207">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="85435-208">Liste os testes descobertos em vez de executar os testes.</span><span class="sxs-lookup"><span data-stu-id="85435-208">List the discovered tests instead of running the tests.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="85435-209">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="85435-209">Sets the verbosity level of the command.</span></span> <span data-ttu-id="85435-210">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="85435-210">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="85435-211">O padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="85435-211">The default is `minimal`.</span></span> <span data-ttu-id="85435-212">Para obter mais informações, consulte <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="85435-212">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="85435-213">**`RunSettings`** argumentos</span><span class="sxs-lookup"><span data-stu-id="85435-213">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="85435-214">Inline `RunSettings` são passados como os últimos argumentos na linha de comando após "--" (Observe o espaço após--).</span><span class="sxs-lookup"><span data-stu-id="85435-214">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="85435-215">Inline `RunSettings` são especificados como `[name]=[value]` pares.</span><span class="sxs-lookup"><span data-stu-id="85435-215">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="85435-216">Um espaço é usado para separar vários pares `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="85435-216">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="85435-217">Exemplo: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="85435-217">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="85435-218">Para obter mais informações, consulte [passando argumentos RunSettings por meio da linha de comando](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="85435-218">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="85435-219">Exemplos</span><span class="sxs-lookup"><span data-stu-id="85435-219">Examples</span></span>

- <span data-ttu-id="85435-220">Execute os testes no projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="85435-220">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="85435-221">Execute os testes no projeto `test1`:</span><span class="sxs-lookup"><span data-stu-id="85435-221">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="85435-222">Execute os testes no projeto no diretório atual e gere um arquivo de resultados de teste no formato TRX:</span><span class="sxs-lookup"><span data-stu-id="85435-222">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="85435-223">Execute os testes no projeto no diretório atual e gere um arquivo de cobertura de código (depois de instalar a integração de coletores [coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) ):</span><span class="sxs-lookup"><span data-stu-id="85435-223">Run the tests in the project in the current directory, and generate a code coverage file (after installing [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) collectors integration):</span></span>

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- <span data-ttu-id="85435-224">Execute os testes no projeto no diretório atual e gere um arquivo de cobertura de código (somente Windows):</span><span class="sxs-lookup"><span data-stu-id="85435-224">Run the tests in the project in the current directory, and generate a code coverage file (Windows only):</span></span>

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- <span data-ttu-id="85435-225">Execute os testes no projeto no diretório atual e faça logon com detalhes detalhados no console:</span><span class="sxs-lookup"><span data-stu-id="85435-225">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

- <span data-ttu-id="85435-226">Execute os testes no projeto no diretório atual e relate os testes que estavam em andamento quando o host de teste falhou:</span><span class="sxs-lookup"><span data-stu-id="85435-226">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="85435-227">Filtrar detalhes da opção</span><span class="sxs-lookup"><span data-stu-id="85435-227">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="85435-228">`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="85435-228">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="85435-229">`<property>` é um atributo de `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="85435-229">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="85435-230">A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:</span><span class="sxs-lookup"><span data-stu-id="85435-230">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="85435-231">Estrutura de teste</span><span class="sxs-lookup"><span data-stu-id="85435-231">Test Framework</span></span> | <span data-ttu-id="85435-232">Propriedades com suporte</span><span class="sxs-lookup"><span data-stu-id="85435-232">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="85435-233">MSTest</span><span class="sxs-lookup"><span data-stu-id="85435-233">MSTest</span></span>         | <ul><li><span data-ttu-id="85435-234">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="85435-234">FullyQualifiedName</span></span></li><li><span data-ttu-id="85435-235">Name</span><span class="sxs-lookup"><span data-stu-id="85435-235">Name</span></span></li><li><span data-ttu-id="85435-236">ClassName</span><span class="sxs-lookup"><span data-stu-id="85435-236">ClassName</span></span></li><li><span data-ttu-id="85435-237">Prioridade</span><span class="sxs-lookup"><span data-stu-id="85435-237">Priority</span></span></li><li><span data-ttu-id="85435-238">TestCategory</span><span class="sxs-lookup"><span data-stu-id="85435-238">TestCategory</span></span></li></ul> |
| <span data-ttu-id="85435-239">xUnit</span><span class="sxs-lookup"><span data-stu-id="85435-239">xUnit</span></span>          | <ul><li><span data-ttu-id="85435-240">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="85435-240">FullyQualifiedName</span></span></li><li><span data-ttu-id="85435-241">DisplayName</span><span class="sxs-lookup"><span data-stu-id="85435-241">DisplayName</span></span></li><li><span data-ttu-id="85435-242">Características</span><span class="sxs-lookup"><span data-stu-id="85435-242">Traits</span></span></li></ul>                                   |
| <span data-ttu-id="85435-243">NUnit</span><span class="sxs-lookup"><span data-stu-id="85435-243">NUnit</span></span>          | <ul><li><span data-ttu-id="85435-244">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="85435-244">FullyQualifiedName</span></span></li><li><span data-ttu-id="85435-245">Name</span><span class="sxs-lookup"><span data-stu-id="85435-245">Name</span></span></li><li><span data-ttu-id="85435-246">TestCategory</span><span class="sxs-lookup"><span data-stu-id="85435-246">TestCategory</span></span></li><li><span data-ttu-id="85435-247">Prioridade</span><span class="sxs-lookup"><span data-stu-id="85435-247">Priority</span></span></li></ul>                                   |

<span data-ttu-id="85435-248">O `<operator>` descreve a relação entre a propriedade o valor:</span><span class="sxs-lookup"><span data-stu-id="85435-248">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="85435-249">Operador</span><span class="sxs-lookup"><span data-stu-id="85435-249">Operator</span></span> | <span data-ttu-id="85435-250">Função</span><span class="sxs-lookup"><span data-stu-id="85435-250">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="85435-251">Correspondência exata</span><span class="sxs-lookup"><span data-stu-id="85435-251">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="85435-252">Sem correspondência exata</span><span class="sxs-lookup"><span data-stu-id="85435-252">Not exact match</span></span> |
| `~`      | <span data-ttu-id="85435-253">Contém</span><span class="sxs-lookup"><span data-stu-id="85435-253">Contains</span></span>        |
| `!~`     | <span data-ttu-id="85435-254">Não contém</span><span class="sxs-lookup"><span data-stu-id="85435-254">Not contains</span></span>    |

<span data-ttu-id="85435-255">`<value>` é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="85435-255">`<value>` is a string.</span></span> <span data-ttu-id="85435-256">As pesquisas não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="85435-256">All the lookups are case insensitive.</span></span>

<span data-ttu-id="85435-257">Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="85435-257">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="85435-258">As expressões podem ser associadas a operadores condicionais:</span><span class="sxs-lookup"><span data-stu-id="85435-258">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="85435-259">Operador</span><span class="sxs-lookup"><span data-stu-id="85435-259">Operator</span></span>            | <span data-ttu-id="85435-260">Função</span><span class="sxs-lookup"><span data-stu-id="85435-260">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="85435-261">OU</span><span class="sxs-lookup"><span data-stu-id="85435-261">OR</span></span>       |
| `&`                 | <span data-ttu-id="85435-262">AND</span><span class="sxs-lookup"><span data-stu-id="85435-262">AND</span></span>      |

<span data-ttu-id="85435-263">Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="85435-263">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="85435-264">Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="85435-264">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="85435-265">Confira também</span><span class="sxs-lookup"><span data-stu-id="85435-265">See also</span></span>

- [<span data-ttu-id="85435-266">Estruturas e destinos</span><span class="sxs-lookup"><span data-stu-id="85435-266">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="85435-267">Catálogo de RID (identificador de tempo de execução) do .NET Core</span><span class="sxs-lookup"><span data-stu-id="85435-267">.NET Core Runtime Identifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="85435-268">Passando argumentos RunSettings por meio de linha de comando</span><span class="sxs-lookup"><span data-stu-id="85435-268">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
