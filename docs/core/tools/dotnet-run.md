---
title: Comando dotnet run
description: O comando dotnet run oferece uma opção conveniente para executar o aplicativo do código-fonte.
ms.date: 02/19/2020
ms.openlocfilehash: 415d7079db6a3da80c4fcf2074307ea760e84982
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503613"
---
# <a name="dotnet-run"></a><span data-ttu-id="709ef-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="709ef-103">dotnet run</span></span>

<span data-ttu-id="709ef-104">**Este artigo aplica-se a:** ✔️ SDK do .NET Core 2. x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="709ef-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="709ef-105">Nome</span><span class="sxs-lookup"><span data-stu-id="709ef-105">Name</span></span>

<span data-ttu-id="709ef-106">`dotnet run` – Executa o código-fonte sem qualquer comando de compilação ou inicialização explícito.</span><span class="sxs-lookup"><span data-stu-id="709ef-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="709ef-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="709ef-107">Synopsis</span></span>

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile] 
    [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project] 
    [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

## <a name="description"></a><span data-ttu-id="709ef-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="709ef-108">Description</span></span>

<span data-ttu-id="709ef-109">O comando `dotnet run` fornece uma opção conveniente para executar o aplicativo do código-fonte com um comando.</span><span class="sxs-lookup"><span data-stu-id="709ef-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="709ef-110">Ele é útil para o desenvolvimento iterativo rápido a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="709ef-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="709ef-111">O comando depende do comando [`dotnet build`](dotnet-build.md) para compilar o código.</span><span class="sxs-lookup"><span data-stu-id="709ef-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="709ef-112">Os requisitos para a compilação, como o projeto, devem ser restaurado primeiro, e se aplicam a `dotnet run` também.</span><span class="sxs-lookup"><span data-stu-id="709ef-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="709ef-113">Os arquivos de saída são gravados no local padrão, que é `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="709ef-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="709ef-114">Por exemplo, se você tiver um aplicativo `netcoreapp2.1` e executar `dotnet run`, a saída será colocada em `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="709ef-114">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="709ef-115">Os arquivos são substituídos conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="709ef-115">Files are overwritten as needed.</span></span> <span data-ttu-id="709ef-116">Os arquivos temporários são colocados no diretório `obj`.</span><span class="sxs-lookup"><span data-stu-id="709ef-116">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="709ef-117">Se o projeto especificar várias estruturas, a execução de `dotnet run` resultará em um erro, a menos que a opção `-f|--framework <FRAMEWORK>` seja usada para especificar a estrutura.</span><span class="sxs-lookup"><span data-stu-id="709ef-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="709ef-118">O comando `dotnet run` é usado no contexto de projetos, não assemblies compilados.</span><span class="sxs-lookup"><span data-stu-id="709ef-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="709ef-119">Se, em vez disso, você estiver tentando executar uma DLL de aplicativo dependente da estrutura, use [dotnet](dotnet.md) sem um comando.</span><span class="sxs-lookup"><span data-stu-id="709ef-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="709ef-120">Por exemplo, para executar `myapp.dll`, use:</span><span class="sxs-lookup"><span data-stu-id="709ef-120">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="709ef-121">Para saber mais sobre o driver `dotnet`, veja o tópico [CLI (Ferramentas de Linha de Comando) do .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="709ef-121">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="709ef-122">Para executar o aplicativo, o comando `dotnet run` resolve as dependências do aplicativo que estão fora do runtime compartilhado por meio do cache NuGet.</span><span class="sxs-lookup"><span data-stu-id="709ef-122">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="709ef-123">Como ele usa as dependências em cache, não recomendamos usar `dotnet run` para executar aplicativos em produção.</span><span class="sxs-lookup"><span data-stu-id="709ef-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="709ef-124">Em vez disso, [crie uma implantação](../deploying/index.md) usando o comando [`dotnet publish`](dotnet-publish.md) e implante a saída publicada.</span><span class="sxs-lookup"><span data-stu-id="709ef-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="709ef-125">Opções</span><span class="sxs-lookup"><span data-stu-id="709ef-125">Options</span></span>

- **`--`**

  <span data-ttu-id="709ef-126">Delimita os argumentos para `dotnet run` dos argumentos para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="709ef-126">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="709ef-127">Todos os argumentos após esse delimitador são passados para o aplicativo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="709ef-127">All arguments after this delimiter are passed to the application run.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="709ef-128">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="709ef-128">Defines the build configuration.</span></span> <span data-ttu-id="709ef-129">O padrão para a maioria dos projetos é `Debug`, mas você pode substituir as definições de configuração de compilação em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="709ef-129">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="709ef-130">Compila e executa o aplicativo usando a [estrutura](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="709ef-130">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="709ef-131">A estrutura deve ser especificada no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="709ef-131">The framework must be specified in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="709ef-132">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="709ef-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="709ef-133">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="709ef-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="709ef-134">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="709ef-134">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="709ef-135">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="709ef-135">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="709ef-136">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="709ef-136">Available since .NET Core 3.0 SDK.</span></span>

- **`--launch-profile <NAME>`**

  <span data-ttu-id="709ef-137">O nome do perfil de inicialização (se houver) a ser usado ao iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="709ef-137">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="709ef-138">Os perfis de inicialização são definidos no arquivo *launchSettings.json* e, normalmente, são chamados `Development`, `Staging` e `Production`.</span><span class="sxs-lookup"><span data-stu-id="709ef-138">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="709ef-139">Para obter mais informações, consulte [Working with multiple environments](/aspnet/core/fundamentals/environments) (Trabalhando com vários ambientes).</span><span class="sxs-lookup"><span data-stu-id="709ef-139">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

- **`--no-build`**

  <span data-ttu-id="709ef-140">Não compila o projeto antes da execução.</span><span class="sxs-lookup"><span data-stu-id="709ef-140">Doesn't build the project before running.</span></span> <span data-ttu-id="709ef-141">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="709ef-141">It also implicit sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="709ef-142">Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.</span><span class="sxs-lookup"><span data-stu-id="709ef-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--no-launch-profile`**

  <span data-ttu-id="709ef-143">Não tenta usar *launchSettings.json* para configurar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="709ef-143">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

- **`--no-restore`**

  <span data-ttu-id="709ef-144">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="709ef-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-p|--project <PATH>`**

  <span data-ttu-id="709ef-145">Especifica o caminho do arquivo de projeto a ser executado (nome da pasta ou caminho completo).</span><span class="sxs-lookup"><span data-stu-id="709ef-145">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="709ef-146">Se não é especificado, ele usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="709ef-146">If not specified, it defaults to the current directory.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="709ef-147">Especifica o runtime de destino para o qual restaurar os pacotes.</span><span class="sxs-lookup"><span data-stu-id="709ef-147">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="709ef-148">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="709ef-148">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="709ef-149">`-r` opção curta disponível desde o SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="709ef-149">`-r` short option available since .NET Core 3.0 SDK.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="709ef-150">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="709ef-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="709ef-151">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="709ef-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="709ef-152">O valor padrão é `m`.</span><span class="sxs-lookup"><span data-stu-id="709ef-152">The default value is `m`.</span></span> <span data-ttu-id="709ef-153">Disponível desde o SDK do .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="709ef-153">Available since .NET Core 2.1 SDK.</span></span> 

## <a name="examples"></a><span data-ttu-id="709ef-154">Exemplos</span><span class="sxs-lookup"><span data-stu-id="709ef-154">Examples</span></span>

- <span data-ttu-id="709ef-155">Execute o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="709ef-155">Run the project in the current directory:</span></span>

  ```dotnetcli
  dotnet run
  ```

- <span data-ttu-id="709ef-156">Execute o projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="709ef-156">Run the specified project:</span></span>

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- <span data-ttu-id="709ef-157">Execute o projeto no diretório atual (o argumento `--help` neste exemplo é passado para o aplicativo, visto que a opção vazia `--` foi usada):</span><span class="sxs-lookup"><span data-stu-id="709ef-157">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- <span data-ttu-id="709ef-158">Restaure as dependências e as ferramentas para o projeto no diretório atual, apenas mostrando uma saída mínima e, em seguida, execute o projeto (SDK do .NET Core 2.0 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="709ef-158">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

  ```dotnetcli
  dotnet run --verbosity m
  ```
