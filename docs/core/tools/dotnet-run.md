---
title: "Comando dotnet run – CLI do .NET Core"
description: "O comando dotnet run oferece uma opção conveniente para executar o aplicativo do código-fonte."
author: mairaw
ms.author: mairaw
ms.date: 09/24/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 1f5a3927859f89bef6c50d3d31b73de43cd1cd31
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-run"></a><span data-ttu-id="467b6-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="467b6-103">dotnet run</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="467b6-104">Nome</span><span class="sxs-lookup"><span data-stu-id="467b6-104">Name</span></span>

<span data-ttu-id="467b6-105">`dotnet run` – Executa o código-fonte sem qualquer comando de compilação ou inicialização explícito.</span><span class="sxs-lookup"><span data-stu-id="467b6-105">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="467b6-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="467b6-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="467b6-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="467b6-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="467b6-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="467b6-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="467b6-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="467b6-109">Description</span></span>

<span data-ttu-id="467b6-110">O comando `dotnet run` fornece uma opção conveniente para executar o aplicativo do código-fonte com um comando.</span><span class="sxs-lookup"><span data-stu-id="467b6-110">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="467b6-111">Ele é útil para o desenvolvimento iterativo rápido a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="467b6-111">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="467b6-112">O comando depende do comando [`dotnet build`](dotnet-build.md) para compilar o código.</span><span class="sxs-lookup"><span data-stu-id="467b6-112">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="467b6-113">Os requisitos para a compilação, como o projeto, devem ser restaurado primeiro, e se aplicam a `dotnet run` também.</span><span class="sxs-lookup"><span data-stu-id="467b6-113">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span> 

<span data-ttu-id="467b6-114">Os arquivos de saída são gravados no local padrão, que é `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="467b6-114">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="467b6-115">Por exemplo, se você tiver um aplicativo `netcoreapp1.0` e executar `dotnet run`, a saída será colocada em `bin/Debug/netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="467b6-115">For example if you have a `netcoreapp1.0` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp1.0`.</span></span> <span data-ttu-id="467b6-116">Os arquivos são substituídos conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="467b6-116">Files are overwritten as needed.</span></span> <span data-ttu-id="467b6-117">Os arquivos temporários são colocados no diretório `obj`.</span><span class="sxs-lookup"><span data-stu-id="467b6-117">Temporary files are placed in the `obj` directory.</span></span> 

<span data-ttu-id="467b6-118">Se o projeto especificar várias estruturas, a execução de `dotnet run` resultará em um erro, a menos que a opção `-f|--framework <FRAMEWORK>` seja usada para especificar a estrutura.</span><span class="sxs-lookup"><span data-stu-id="467b6-118">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="467b6-119">O comando `dotnet run` é usado no contexto de projetos, não assemblies compilados.</span><span class="sxs-lookup"><span data-stu-id="467b6-119">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="467b6-120">Se, em vez disso, você estiver tentando executar uma DLL de aplicativo dependente da estrutura, use [dotnet](dotnet.md) sem um comando.</span><span class="sxs-lookup"><span data-stu-id="467b6-120">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="467b6-121">Por exemplo, para executar `myapp.dll`, use:</span><span class="sxs-lookup"><span data-stu-id="467b6-121">For example, to run `myapp.dll`, use:</span></span>

```
dotnet myapp.dll
```

<span data-ttu-id="467b6-122">Para saber mais sobre o driver `dotnet`, veja o tópico [CLI (Ferramentas de Linha de Comando) do .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="467b6-122">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="467b6-123">Para executar o aplicativo, o comando `dotnet run` resolve as dependências do aplicativo que estão fora do tempo de execução compartilhado do cache NuGet.</span><span class="sxs-lookup"><span data-stu-id="467b6-123">In order to run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="467b6-124">Como ele usa as dependências em cache, não recomendamos usar `dotnet run` para executar aplicativos em produção.</span><span class="sxs-lookup"><span data-stu-id="467b6-124">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="467b6-125">Em vez disso, [crie uma implantação](../deploying/index.md) usando o comando [`dotnet publish`](dotnet-publish.md) e implante a saída publicada.</span><span class="sxs-lookup"><span data-stu-id="467b6-125">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

## <a name="options"></a><span data-ttu-id="467b6-126">Opções</span><span class="sxs-lookup"><span data-stu-id="467b6-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="467b6-127">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="467b6-127">.NET Core 2.x</span></span>](#tab/netcore2x)

`--`

<span data-ttu-id="467b6-128">Delimita os argumentos para `dotnet run` dos argumentos para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="467b6-128">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="467b6-129">Todos os argumentos depois desse serão passados para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="467b6-129">All arguments after this one are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="467b6-130">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="467b6-130">Defines the build configuration.</span></span> <span data-ttu-id="467b6-131">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="467b6-131">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="467b6-132">Compila e executa o aplicativo usando a [estrutura](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="467b6-132">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="467b6-133">A estrutura deve ser especificada no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="467b6-133">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="467b6-134">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="467b6-134">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="467b6-135">Isso é equivalente a excluir *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="467b6-135">This is equivalent to deleting *project.assets.json*.</span></span>

`-h|--help`

<span data-ttu-id="467b6-136">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="467b6-136">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="467b6-137">O nome do perfil de inicialização (se houver) a ser usado ao iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="467b6-137">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="467b6-138">Os perfis de inicialização são definidos no arquivo *launchSettings.json* e normalmente são chamados `Development`, `Staging` e `Production`.</span><span class="sxs-lookup"><span data-stu-id="467b6-138">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging` and `Production`.</span></span> <span data-ttu-id="467b6-139">Para obter mais informações, consulte [Working with multiple environments](/aspnet/core/fundamentals/environments) (Trabalhando com vários ambientes).</span><span class="sxs-lookup"><span data-stu-id="467b6-139">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="467b6-140">Não compila o projeto antes da execução.</span><span class="sxs-lookup"><span data-stu-id="467b6-140">Doesn't build the project before running.</span></span>

`--no-dependencies`

<span data-ttu-id="467b6-141">Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.</span><span class="sxs-lookup"><span data-stu-id="467b6-141">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="467b6-142">Não tenta usar *launchSettings.json* para configurar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="467b6-142">Doesn't attempt to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="467b6-143">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="467b6-143">Doesn't perform an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="467b6-144">Especifica o caminho do arquivo de projeto a ser executado (nome da pasta ou caminho completo).</span><span class="sxs-lookup"><span data-stu-id="467b6-144">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="467b6-145">Se não for especificado, o padrão será o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="467b6-145">It defaults to the current directory if not specified.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="467b6-146">Especifica o tempo de execução de destino para o qual restaurar os pacotes.</span><span class="sxs-lookup"><span data-stu-id="467b6-146">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="467b6-147">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="467b6-147">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="467b6-148">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="467b6-148">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="467b6-149">Delimita os argumentos para `dotnet run` dos argumentos para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="467b6-149">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="467b6-150">Todos os argumentos depois desse serão passados para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="467b6-150">All arguments after this one are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="467b6-151">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="467b6-151">Defines the build configuration.</span></span> <span data-ttu-id="467b6-152">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="467b6-152">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="467b6-153">Compila e executa o aplicativo usando a [estrutura](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="467b6-153">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="467b6-154">A estrutura deve ser especificada no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="467b6-154">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="467b6-155">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="467b6-155">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="467b6-156">Especifica o caminho e o nome do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="467b6-156">Specifies the path and name of the project file.</span></span> <span data-ttu-id="467b6-157">(Consulte a OBSERVAÇÃO.) Se não for especificado, o padrão será o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="467b6-157">(See the NOTE.) It defaults to the current directory if not specified.</span></span>

> [!NOTE]
> <span data-ttu-id="467b6-158">Use o caminho e o nome do arquivo de projeto com a opção `-p|--project`.</span><span class="sxs-lookup"><span data-stu-id="467b6-158">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="467b6-159">Uma regressão na CLI impede o fornecimento de um caminho de pasta com o SDK do .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="467b6-159">A regression in the CLI prevents providing a folder path with .NET Core 1.x SDK.</span></span> <span data-ttu-id="467b6-160">Para obter mais informações sobre esse problema, consulte [dotnet run -p, não é possível iniciar um projeto (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="467b6-160">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="467b6-161">Exemplos</span><span class="sxs-lookup"><span data-stu-id="467b6-161">Examples</span></span>

<span data-ttu-id="467b6-162">Execute o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="467b6-162">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="467b6-163">Execute o projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="467b6-163">Run the specified project:</span></span>

`dotnet run --project /projects/proj1/proj1.csproj`

<span data-ttu-id="467b6-164">Execute o projeto no diretório atual (o argumento `--help` neste exemplo é passado para o aplicativo, visto que o argumento `--` foi usado):</span><span class="sxs-lookup"><span data-stu-id="467b6-164">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the `--` argument is used):</span></span>

`dotnet run --configuration Release -- --help`
