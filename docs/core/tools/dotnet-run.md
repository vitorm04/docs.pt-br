---
title: Comando dotnet run
description: O comando dotnet run oferece uma opção conveniente para executar o aplicativo do código-fonte.
ms.date: 10/31/2019
ms.openlocfilehash: 5920f0d1f04204b286fdf6f51f5fd13644846390
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734109"
---
# <a name="dotnet-run"></a><span data-ttu-id="3d591-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="3d591-103">dotnet run</span></span>

<span data-ttu-id="3d591-104">**Este artigo aplica-se a:** ✔️ SDK do .NET Core 1. x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="3d591-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="3d591-105">Name</span><span class="sxs-lookup"><span data-stu-id="3d591-105">Name</span></span>

<span data-ttu-id="3d591-106">`dotnet run` – Executa o código-fonte sem qualquer comando de compilação ou inicialização explícito.</span><span class="sxs-lookup"><span data-stu-id="3d591-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3d591-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="3d591-107">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="3d591-108">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3d591-108">.NET Core 3.0</span></span>](#tab/netcore30)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="3d591-109">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3d591-109">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="3d591-110">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3d591-110">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3d591-111">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3d591-111">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="3d591-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d591-112">Description</span></span>

<span data-ttu-id="3d591-113">O comando `dotnet run` fornece uma opção conveniente para executar o aplicativo do código-fonte com um comando.</span><span class="sxs-lookup"><span data-stu-id="3d591-113">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="3d591-114">Ele é útil para o desenvolvimento iterativo rápido a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="3d591-114">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="3d591-115">O comando depende do comando [`dotnet build`](dotnet-build.md) para compilar o código.</span><span class="sxs-lookup"><span data-stu-id="3d591-115">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="3d591-116">Os requisitos para a compilação, como o projeto, devem ser restaurado primeiro, e se aplicam a `dotnet run` também.</span><span class="sxs-lookup"><span data-stu-id="3d591-116">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="3d591-117">Os arquivos de saída são gravados no local padrão, que é `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="3d591-117">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="3d591-118">Por exemplo, se você tiver um aplicativo `netcoreapp2.1` e executar `dotnet run`, a saída será colocada em `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="3d591-118">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="3d591-119">Os arquivos são substituídos conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="3d591-119">Files are overwritten as needed.</span></span> <span data-ttu-id="3d591-120">Os arquivos temporários são colocados no diretório `obj`.</span><span class="sxs-lookup"><span data-stu-id="3d591-120">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="3d591-121">Se o projeto especificar várias estruturas, a execução de `dotnet run` resultará em um erro, a menos que a opção `-f|--framework <FRAMEWORK>` seja usada para especificar a estrutura.</span><span class="sxs-lookup"><span data-stu-id="3d591-121">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="3d591-122">O comando `dotnet run` é usado no contexto de projetos, não assemblies compilados.</span><span class="sxs-lookup"><span data-stu-id="3d591-122">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="3d591-123">Se, em vez disso, você estiver tentando executar uma DLL de aplicativo dependente da estrutura, use [dotnet](dotnet.md) sem um comando.</span><span class="sxs-lookup"><span data-stu-id="3d591-123">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="3d591-124">Por exemplo, para executar `myapp.dll`, use:</span><span class="sxs-lookup"><span data-stu-id="3d591-124">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="3d591-125">Para saber mais sobre o driver `dotnet`, veja o tópico [CLI (Ferramentas de Linha de Comando) do .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="3d591-125">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="3d591-126">Para executar o aplicativo, o comando `dotnet run` resolve as dependências do aplicativo que estão fora do runtime compartilhado por meio do cache NuGet.</span><span class="sxs-lookup"><span data-stu-id="3d591-126">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="3d591-127">Como ele usa as dependências em cache, não recomendamos usar `dotnet run` para executar aplicativos em produção.</span><span class="sxs-lookup"><span data-stu-id="3d591-127">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="3d591-128">Em vez disso, [crie uma implantação](../deploying/index.md) usando o comando [`dotnet publish`](dotnet-publish.md) e implante a saída publicada.</span><span class="sxs-lookup"><span data-stu-id="3d591-128">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="3d591-129">Opções</span><span class="sxs-lookup"><span data-stu-id="3d591-129">Options</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="3d591-130">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3d591-130">.NET Core 3.0</span></span>](#tab/netcore30)

`--`

<span data-ttu-id="3d591-131">Delimita os argumentos para `dotnet run` dos argumentos para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="3d591-131">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="3d591-132">Todos os argumentos após esse delimitador são passados para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="3d591-132">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="3d591-133">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="3d591-133">Defines the build configuration.</span></span> <span data-ttu-id="3d591-134">O valor padrão para a maioria dos projetos é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="3d591-134">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="3d591-135">Compila e executa o aplicativo usando a [estrutura](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="3d591-135">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="3d591-136">A estrutura deve ser especificada no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="3d591-136">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="3d591-137">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="3d591-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="3d591-138">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="3d591-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="3d591-139">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="3d591-139">Prints out a short help for the command.</span></span>

`--interactive`

<span data-ttu-id="3d591-140">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="3d591-140">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="3d591-141">O nome do perfil de inicialização (se houver) a ser usado ao iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3d591-141">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="3d591-142">Os perfis de inicialização são definidos no arquivo *launchSettings.json* e, normalmente, são chamados `Development`, `Staging` e `Production`.</span><span class="sxs-lookup"><span data-stu-id="3d591-142">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="3d591-143">Para obter mais informações, consulte [Working with multiple environments](/aspnet/core/fundamentals/environments) (Trabalhando com vários ambientes).</span><span class="sxs-lookup"><span data-stu-id="3d591-143">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="3d591-144">Não compila o projeto antes da execução.</span><span class="sxs-lookup"><span data-stu-id="3d591-144">Doesn't build the project before running.</span></span> <span data-ttu-id="3d591-145">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="3d591-145">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="3d591-146">Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.</span><span class="sxs-lookup"><span data-stu-id="3d591-146">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="3d591-147">Não tenta usar *launchSettings.json* para configurar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3d591-147">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="3d591-148">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="3d591-148">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="3d591-149">Especifica o caminho do arquivo de projeto a ser executado (nome da pasta ou caminho completo).</span><span class="sxs-lookup"><span data-stu-id="3d591-149">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="3d591-150">Se não é especificado, ele usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="3d591-150">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="3d591-151">Especifica o runtime de destino para o qual restaurar os pacotes.</span><span class="sxs-lookup"><span data-stu-id="3d591-151">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="3d591-152">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="3d591-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="3d591-153">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="3d591-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3d591-154">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="3d591-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="3d591-155">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3d591-155">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="3d591-156">Delimita os argumentos para `dotnet run` dos argumentos para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="3d591-156">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="3d591-157">Todos os argumentos após esse delimitador são passados para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="3d591-157">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="3d591-158">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="3d591-158">Defines the build configuration.</span></span> <span data-ttu-id="3d591-159">O valor padrão para a maioria dos projetos é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="3d591-159">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="3d591-160">Compila e executa o aplicativo usando a [estrutura](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="3d591-160">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="3d591-161">A estrutura deve ser especificada no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="3d591-161">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="3d591-162">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="3d591-162">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="3d591-163">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="3d591-163">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="3d591-164">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="3d591-164">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="3d591-165">O nome do perfil de inicialização (se houver) a ser usado ao iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3d591-165">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="3d591-166">Os perfis de inicialização são definidos no arquivo *launchSettings.json* e, normalmente, são chamados `Development`, `Staging` e `Production`.</span><span class="sxs-lookup"><span data-stu-id="3d591-166">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="3d591-167">Para obter mais informações, consulte [Working with multiple environments](/aspnet/core/fundamentals/environments) (Trabalhando com vários ambientes).</span><span class="sxs-lookup"><span data-stu-id="3d591-167">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="3d591-168">Não compila o projeto antes da execução.</span><span class="sxs-lookup"><span data-stu-id="3d591-168">Doesn't build the project before running.</span></span> <span data-ttu-id="3d591-169">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="3d591-169">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="3d591-170">Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.</span><span class="sxs-lookup"><span data-stu-id="3d591-170">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="3d591-171">Não tenta usar *launchSettings.json* para configurar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3d591-171">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="3d591-172">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="3d591-172">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="3d591-173">Especifica o caminho do arquivo de projeto a ser executado (nome da pasta ou caminho completo).</span><span class="sxs-lookup"><span data-stu-id="3d591-173">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="3d591-174">Se não é especificado, ele usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="3d591-174">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="3d591-175">Especifica o runtime de destino para o qual restaurar os pacotes.</span><span class="sxs-lookup"><span data-stu-id="3d591-175">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="3d591-176">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="3d591-176">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="3d591-177">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="3d591-177">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3d591-178">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="3d591-178">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="3d591-179">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3d591-179">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="3d591-180">Delimita os argumentos para `dotnet run` dos argumentos para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="3d591-180">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="3d591-181">Todos os argumentos após esse delimitador são passados para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="3d591-181">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="3d591-182">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="3d591-182">Defines the build configuration.</span></span> <span data-ttu-id="3d591-183">O valor padrão para a maioria dos projetos é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="3d591-183">The default for most projects value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="3d591-184">Compila e executa o aplicativo usando a [estrutura](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="3d591-184">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="3d591-185">A estrutura deve ser especificada no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="3d591-185">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="3d591-186">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="3d591-186">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="3d591-187">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="3d591-187">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="3d591-188">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="3d591-188">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="3d591-189">O nome do perfil de inicialização (se houver) a ser usado ao iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3d591-189">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="3d591-190">Os perfis de inicialização são definidos no arquivo *launchSettings.json* e, normalmente, são chamados `Development`, `Staging` e `Production`.</span><span class="sxs-lookup"><span data-stu-id="3d591-190">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="3d591-191">Para obter mais informações, consulte [Working with multiple environments](/aspnet/core/fundamentals/environments) (Trabalhando com vários ambientes).</span><span class="sxs-lookup"><span data-stu-id="3d591-191">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="3d591-192">Não compila o projeto antes da execução.</span><span class="sxs-lookup"><span data-stu-id="3d591-192">Doesn't build the project before running.</span></span> <span data-ttu-id="3d591-193">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="3d591-193">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="3d591-194">Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.</span><span class="sxs-lookup"><span data-stu-id="3d591-194">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="3d591-195">Não tenta usar *launchSettings.json* para configurar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3d591-195">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="3d591-196">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="3d591-196">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="3d591-197">Especifica o caminho do arquivo de projeto a ser executado (nome da pasta ou caminho completo).</span><span class="sxs-lookup"><span data-stu-id="3d591-197">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="3d591-198">Se não é especificado, ele usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="3d591-198">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="3d591-199">Especifica o runtime de destino para o qual restaurar os pacotes.</span><span class="sxs-lookup"><span data-stu-id="3d591-199">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="3d591-200">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="3d591-200">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3d591-201">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3d591-201">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="3d591-202">Delimita os argumentos para `dotnet run` dos argumentos para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="3d591-202">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="3d591-203">Todos os argumentos após esse delimitador são passados para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="3d591-203">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="3d591-204">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="3d591-204">Defines the build configuration.</span></span> <span data-ttu-id="3d591-205">O valor padrão para a maioria dos projetos é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="3d591-205">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="3d591-206">Compila e executa o aplicativo usando a [estrutura](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="3d591-206">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="3d591-207">A estrutura deve ser especificada no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="3d591-207">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="3d591-208">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="3d591-208">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="3d591-209">Especifica o caminho e o nome do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="3d591-209">Specifies the path and name of the project file.</span></span> <span data-ttu-id="3d591-210">(Consulte a observação.) Se não for especificado, o padrão será o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="3d591-210">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="3d591-211">Use o caminho e o nome do arquivo de projeto com a opção `-p|--project`.</span><span class="sxs-lookup"><span data-stu-id="3d591-211">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="3d591-212">Uma regressão na CLI impede o fornecimento de um caminho de pasta com o SDK do .NET Core 1. x.</span><span class="sxs-lookup"><span data-stu-id="3d591-212">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="3d591-213">Para obter mais informações sobre esse problema, consulte [dotnet run -p, não é possível iniciar um projeto (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="3d591-213">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="3d591-214">Exemplos</span><span class="sxs-lookup"><span data-stu-id="3d591-214">Examples</span></span>

<span data-ttu-id="3d591-215">Execute o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="3d591-215">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="3d591-216">Execute o projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="3d591-216">Run the specified project:</span></span>

`dotnet run --project ./projects/proj1/proj1.csproj`

<span data-ttu-id="3d591-217">Execute o projeto no diretório atual (o argumento `--help` neste exemplo é passado para o aplicativo, visto que a opção vazia `--` foi usada):</span><span class="sxs-lookup"><span data-stu-id="3d591-217">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="3d591-218">Restaure as dependências e as ferramentas para o projeto no diretório atual, apenas mostrando uma saída mínima e, em seguida, execute o projeto (SDK do .NET Core 2.0 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="3d591-218">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`
