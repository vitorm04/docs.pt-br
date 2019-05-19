---
title: Comando dotnet run
description: O comando dotnet run oferece uma opção conveniente para executar o aplicativo do código-fonte.
ms.date: 05/29/2018
ms.openlocfilehash: 489429e2371c807e09f9fb8c2de6f96d091edc6d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631999"
---
# <a name="dotnet-run"></a><span data-ttu-id="bf281-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="bf281-103">dotnet run</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="bf281-104">Nome</span><span class="sxs-lookup"><span data-stu-id="bf281-104">Name</span></span>

<span data-ttu-id="bf281-105">`dotnet run` – Executa o código-fonte sem qualquer comando de compilação ou inicialização explícito.</span><span class="sxs-lookup"><span data-stu-id="bf281-105">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bf281-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="bf281-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="bf281-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bf281-107">.NET Core 2.1</span></span>](#tab/netcore21)

```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="bf281-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="bf281-108">.NET Core 2.0</span></span>](#tab/netcore20)

```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bf281-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bf281-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="bf281-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf281-110">Description</span></span>

<span data-ttu-id="bf281-111">O comando `dotnet run` fornece uma opção conveniente para executar o aplicativo do código-fonte com um comando.</span><span class="sxs-lookup"><span data-stu-id="bf281-111">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="bf281-112">Ele é útil para o desenvolvimento iterativo rápido a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="bf281-112">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="bf281-113">O comando depende do comando [`dotnet build`](dotnet-build.md) para compilar o código.</span><span class="sxs-lookup"><span data-stu-id="bf281-113">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="bf281-114">Os requisitos para a compilação, como o projeto, devem ser restaurado primeiro, e se aplicam a `dotnet run` também.</span><span class="sxs-lookup"><span data-stu-id="bf281-114">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="bf281-115">Os arquivos de saída são gravados no local padrão, que é `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="bf281-115">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="bf281-116">Por exemplo, se você tiver um aplicativo `netcoreapp2.1` e executar `dotnet run`, a saída será colocada em `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="bf281-116">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="bf281-117">Os arquivos são substituídos conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="bf281-117">Files are overwritten as needed.</span></span> <span data-ttu-id="bf281-118">Os arquivos temporários são colocados no diretório `obj`.</span><span class="sxs-lookup"><span data-stu-id="bf281-118">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="bf281-119">Se o projeto especificar várias estruturas, a execução de `dotnet run` resultará em um erro, a menos que a opção `-f|--framework <FRAMEWORK>` seja usada para especificar a estrutura.</span><span class="sxs-lookup"><span data-stu-id="bf281-119">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="bf281-120">O comando `dotnet run` é usado no contexto de projetos, não assemblies compilados.</span><span class="sxs-lookup"><span data-stu-id="bf281-120">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="bf281-121">Se, em vez disso, você estiver tentando executar uma DLL de aplicativo dependente da estrutura, use [dotnet](dotnet.md) sem um comando.</span><span class="sxs-lookup"><span data-stu-id="bf281-121">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="bf281-122">Por exemplo, para executar `myapp.dll`, use:</span><span class="sxs-lookup"><span data-stu-id="bf281-122">For example, to run `myapp.dll`, use:</span></span>

```console
dotnet myapp.dll
```

<span data-ttu-id="bf281-123">Para saber mais sobre o driver `dotnet`, veja o tópico [CLI (Ferramentas de Linha de Comando) do .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="bf281-123">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="bf281-124">Para executar o aplicativo, o comando `dotnet run` resolve as dependências do aplicativo que estão fora do tempo de execução compartilhado por meio do cache NuGet.</span><span class="sxs-lookup"><span data-stu-id="bf281-124">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="bf281-125">Como ele usa as dependências em cache, não recomendamos usar `dotnet run` para executar aplicativos em produção.</span><span class="sxs-lookup"><span data-stu-id="bf281-125">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="bf281-126">Em vez disso, [crie uma implantação](../deploying/index.md) usando o comando [`dotnet publish`](dotnet-publish.md) e implante a saída publicada.</span><span class="sxs-lookup"><span data-stu-id="bf281-126">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="bf281-127">Opções</span><span class="sxs-lookup"><span data-stu-id="bf281-127">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="bf281-128">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bf281-128">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="bf281-129">Delimita os argumentos para `dotnet run` dos argumentos para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="bf281-129">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="bf281-130">Todos os argumentos após esse delimitador são passados para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="bf281-130">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="bf281-131">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="bf281-131">Defines the build configuration.</span></span> <span data-ttu-id="bf281-132">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="bf281-132">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="bf281-133">Compila e executa o aplicativo usando a [estrutura](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="bf281-133">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="bf281-134">A estrutura deve ser especificada no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="bf281-134">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="bf281-135">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="bf281-135">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="bf281-136">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="bf281-136">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="bf281-137">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="bf281-137">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="bf281-138">O nome do perfil de inicialização (se houver) a ser usado ao iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bf281-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="bf281-139">Os perfis de inicialização são definidos no arquivo *launchSettings.json* e, normalmente, são chamados `Development`, `Staging` e `Production`.</span><span class="sxs-lookup"><span data-stu-id="bf281-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="bf281-140">Para obter mais informações, consulte [Working with multiple environments](/aspnet/core/fundamentals/environments) (Trabalhando com vários ambientes).</span><span class="sxs-lookup"><span data-stu-id="bf281-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="bf281-141">Não compila o projeto antes da execução.</span><span class="sxs-lookup"><span data-stu-id="bf281-141">Doesn't build the project before running.</span></span> <span data-ttu-id="bf281-142">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="bf281-142">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="bf281-143">Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.</span><span class="sxs-lookup"><span data-stu-id="bf281-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="bf281-144">Não tenta usar *launchSettings.json* para configurar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bf281-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="bf281-145">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="bf281-145">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="bf281-146">Especifica o caminho do arquivo de projeto a ser executado (nome da pasta ou caminho completo).</span><span class="sxs-lookup"><span data-stu-id="bf281-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="bf281-147">Se não é especificado, ele usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="bf281-147">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="bf281-148">Especifica o tempo de execução de destino para o qual restaurar os pacotes.</span><span class="sxs-lookup"><span data-stu-id="bf281-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="bf281-149">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="bf281-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="bf281-150">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="bf281-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bf281-151">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="bf281-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="bf281-152">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="bf281-152">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="bf281-153">Delimita os argumentos para `dotnet run` dos argumentos para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="bf281-153">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="bf281-154">Todos os argumentos após esse delimitador são passados para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="bf281-154">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="bf281-155">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="bf281-155">Defines the build configuration.</span></span> <span data-ttu-id="bf281-156">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="bf281-156">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="bf281-157">Compila e executa o aplicativo usando a [estrutura](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="bf281-157">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="bf281-158">A estrutura deve ser especificada no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="bf281-158">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="bf281-159">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="bf281-159">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="bf281-160">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="bf281-160">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="bf281-161">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="bf281-161">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="bf281-162">O nome do perfil de inicialização (se houver) a ser usado ao iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bf281-162">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="bf281-163">Os perfis de inicialização são definidos no arquivo *launchSettings.json* e, normalmente, são chamados `Development`, `Staging` e `Production`.</span><span class="sxs-lookup"><span data-stu-id="bf281-163">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="bf281-164">Para obter mais informações, consulte [Working with multiple environments](/aspnet/core/fundamentals/environments) (Trabalhando com vários ambientes).</span><span class="sxs-lookup"><span data-stu-id="bf281-164">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="bf281-165">Não compila o projeto antes da execução.</span><span class="sxs-lookup"><span data-stu-id="bf281-165">Doesn't build the project before running.</span></span> <span data-ttu-id="bf281-166">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="bf281-166">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="bf281-167">Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.</span><span class="sxs-lookup"><span data-stu-id="bf281-167">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="bf281-168">Não tenta usar *launchSettings.json* para configurar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bf281-168">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="bf281-169">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="bf281-169">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="bf281-170">Especifica o caminho do arquivo de projeto a ser executado (nome da pasta ou caminho completo).</span><span class="sxs-lookup"><span data-stu-id="bf281-170">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="bf281-171">Se não é especificado, ele usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="bf281-171">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="bf281-172">Especifica o tempo de execução de destino para o qual restaurar os pacotes.</span><span class="sxs-lookup"><span data-stu-id="bf281-172">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="bf281-173">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="bf281-173">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bf281-174">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bf281-174">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="bf281-175">Delimita os argumentos para `dotnet run` dos argumentos para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="bf281-175">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="bf281-176">Todos os argumentos após esse delimitador são passados para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="bf281-176">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="bf281-177">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="bf281-177">Defines the build configuration.</span></span> <span data-ttu-id="bf281-178">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="bf281-178">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="bf281-179">Compila e executa o aplicativo usando a [estrutura](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="bf281-179">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="bf281-180">A estrutura deve ser especificada no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="bf281-180">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="bf281-181">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="bf281-181">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="bf281-182">Especifica o caminho e o nome do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="bf281-182">Specifies the path and name of the project file.</span></span> <span data-ttu-id="bf281-183">(Consulte a OBSERVAÇÃO.) Se não é especificado, ele usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="bf281-183">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="bf281-184">Use o caminho e o nome do arquivo de projeto com a opção `-p|--project`.</span><span class="sxs-lookup"><span data-stu-id="bf281-184">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="bf281-185">Uma regressão na CLI impede o fornecimento de um caminho de pasta com o SDK do .NET Core 1. x.</span><span class="sxs-lookup"><span data-stu-id="bf281-185">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="bf281-186">Para obter mais informações sobre esse problema, consulte [dotnet run -p, não é possível iniciar um projeto (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="bf281-186">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="bf281-187">Exemplos</span><span class="sxs-lookup"><span data-stu-id="bf281-187">Examples</span></span>

<span data-ttu-id="bf281-188">Execute o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="bf281-188">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="bf281-189">Execute o projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="bf281-189">Run the specified project:</span></span>

`dotnet run --project ./projects/proj1/proj1.csproj`

<span data-ttu-id="bf281-190">Execute o projeto no diretório atual (o argumento `--help` neste exemplo é passado para o aplicativo, visto que a opção vazia `--` foi usada):</span><span class="sxs-lookup"><span data-stu-id="bf281-190">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="bf281-191">Restaure as dependências e as ferramentas para o projeto no diretório atual, apenas mostrando uma saída mínima e, em seguida, execute o projeto (SDK do .NET Core 2.0 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="bf281-191">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`
