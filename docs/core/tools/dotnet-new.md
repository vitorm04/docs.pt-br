---
title: "Comando dotnet new – CLI do .NET Core"
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
keywords: dotnet-new, CLI, comando da CLI, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.workload: dotnetcore
ms.openlocfilehash: f5815e1ad2a36a8ef3279f6ff83465dba9ec5d50
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-new"></a><span data-ttu-id="d504a-104">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d504a-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d504a-105">Nome</span><span class="sxs-lookup"><span data-stu-id="d504a-105">Name</span></span>

<span data-ttu-id="d504a-106">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="d504a-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d504a-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="d504a-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d504a-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d504a-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d504a-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d504a-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="d504a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d504a-110">Description</span></span>

<span data-ttu-id="d504a-111">O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido.</span><span class="sxs-lookup"><span data-stu-id="d504a-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="d504a-112">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="d504a-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="d504a-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="d504a-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="d504a-114">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="d504a-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="d504a-115">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="d504a-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="d504a-116">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="d504a-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d504a-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d504a-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="d504a-118">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="d504a-118">The command contains a default list of templates.</span></span> <span data-ttu-id="d504a-119">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d504a-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="d504a-120">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="d504a-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="d504a-121">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="d504a-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="d504a-122">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="d504a-122">Template description</span></span>                          | <span data-ttu-id="d504a-123">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="d504a-123">Template name</span></span>  | <span data-ttu-id="d504a-124">Linguagens</span><span class="sxs-lookup"><span data-stu-id="d504a-124">Languages</span></span>     |
|----------------------------------------------|----------------|---------------|
| <span data-ttu-id="d504a-125">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="d504a-125">Console application</span></span>                          | <span data-ttu-id="d504a-126">console</span><span class="sxs-lookup"><span data-stu-id="d504a-126">console</span></span>        | <span data-ttu-id="d504a-127">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d504a-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="d504a-128">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="d504a-128">Class library</span></span>                                | <span data-ttu-id="d504a-129">classlib</span><span class="sxs-lookup"><span data-stu-id="d504a-129">classlib</span></span>       | <span data-ttu-id="d504a-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d504a-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="d504a-131">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="d504a-131">Unit test project</span></span>                            | <span data-ttu-id="d504a-132">mstest</span><span class="sxs-lookup"><span data-stu-id="d504a-132">mstest</span></span>         | <span data-ttu-id="d504a-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d504a-133">[C#], F#, VB</span></span>  |
| <span data-ttu-id="d504a-134">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="d504a-134">xUnit test project</span></span>                           | <span data-ttu-id="d504a-135">xunit</span><span class="sxs-lookup"><span data-stu-id="d504a-135">xunit</span></span>          | <span data-ttu-id="d504a-136">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d504a-136">[C#], F#, VB</span></span>  |
| <span data-ttu-id="d504a-137">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="d504a-137">ASP.NET Core empty</span></span>                           | <span data-ttu-id="d504a-138">web</span><span class="sxs-lookup"><span data-stu-id="d504a-138">web</span></span>            | <span data-ttu-id="d504a-139">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d504a-139">[C#], F#</span></span>      |
| <span data-ttu-id="d504a-140">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="d504a-140">ASP.NET Core Web App (Model-View-Controller)</span></span> | <span data-ttu-id="d504a-141">mvc</span><span class="sxs-lookup"><span data-stu-id="d504a-141">mvc</span></span>            | <span data-ttu-id="d504a-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d504a-142">[C#], F#</span></span>      |
| <span data-ttu-id="d504a-143">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d504a-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="d504a-144">razor</span><span class="sxs-lookup"><span data-stu-id="d504a-144">razor</span></span>          | <span data-ttu-id="d504a-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="d504a-145">[C#]</span></span>          |
| <span data-ttu-id="d504a-146">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="d504a-146">ASP.NET Core with Angular</span></span>                    | <span data-ttu-id="d504a-147">angular</span><span class="sxs-lookup"><span data-stu-id="d504a-147">angular</span></span>        | <span data-ttu-id="d504a-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="d504a-148">[C#]</span></span>          |
| <span data-ttu-id="d504a-149">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="d504a-149">ASP.NET Core with React.js</span></span>                   | <span data-ttu-id="d504a-150">react</span><span class="sxs-lookup"><span data-stu-id="d504a-150">react</span></span>          | <span data-ttu-id="d504a-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="d504a-151">[C#]</span></span>          |
| <span data-ttu-id="d504a-152">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="d504a-152">ASP.NET Core with React.js and Redux</span></span>         | <span data-ttu-id="d504a-153">reactredux</span><span class="sxs-lookup"><span data-stu-id="d504a-153">reactredux</span></span>     | <span data-ttu-id="d504a-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="d504a-154">[C#]</span></span>          |
| <span data-ttu-id="d504a-155">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d504a-155">ASP.NET Core Web API</span></span>                         | <span data-ttu-id="d504a-156">webapi</span><span class="sxs-lookup"><span data-stu-id="d504a-156">webapi</span></span>         | <span data-ttu-id="d504a-157">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d504a-157">[C#], F#</span></span>      |
| <span data-ttu-id="d504a-158">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="d504a-158">global.json file</span></span>                             | <span data-ttu-id="d504a-159">globaljson</span><span class="sxs-lookup"><span data-stu-id="d504a-159">globaljson</span></span>     |               |
| <span data-ttu-id="d504a-160">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="d504a-160">Nuget config</span></span>                                 | <span data-ttu-id="d504a-161">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="d504a-161">nugetconfig</span></span>    |               |
| <span data-ttu-id="d504a-162">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="d504a-162">Web config</span></span>                                   | <span data-ttu-id="d504a-163">webconfig</span><span class="sxs-lookup"><span data-stu-id="d504a-163">webconfig</span></span>      |               |
| <span data-ttu-id="d504a-164">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="d504a-164">Solution file</span></span>                                | <span data-ttu-id="d504a-165">sln</span><span class="sxs-lookup"><span data-stu-id="d504a-165">sln</span></span>            |               |
| <span data-ttu-id="d504a-166">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="d504a-166">Razor page</span></span>                                   | <span data-ttu-id="d504a-167">página</span><span class="sxs-lookup"><span data-stu-id="d504a-167">page</span></span>           |               |
| <span data-ttu-id="d504a-168">MVC/ViewImports</span><span class="sxs-lookup"><span data-stu-id="d504a-168">MVC/ViewImports</span></span>                              | <span data-ttu-id="d504a-169">viewimports</span><span class="sxs-lookup"><span data-stu-id="d504a-169">viewimports</span></span>    |               |
| <span data-ttu-id="d504a-170">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="d504a-170">MVC ViewStart</span></span>                                | <span data-ttu-id="d504a-171">viewstart</span><span class="sxs-lookup"><span data-stu-id="d504a-171">viewstart</span></span>      |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d504a-172">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d504a-172">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="d504a-173">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="d504a-173">The command contains a default list of templates.</span></span> <span data-ttu-id="d504a-174">Use `dotnet new -all` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d504a-174">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="d504a-175">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="d504a-175">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="d504a-176">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="d504a-176">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="d504a-177">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="d504a-177">Template description</span></span>  | <span data-ttu-id="d504a-178">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="d504a-178">Template name</span></span>  | <span data-ttu-id="d504a-179">Linguagens</span><span class="sxs-lookup"><span data-stu-id="d504a-179">Languages</span></span> |
|----------------------|----------------|-----------|
| <span data-ttu-id="d504a-180">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="d504a-180">Console application</span></span>  | <span data-ttu-id="d504a-181">console</span><span class="sxs-lookup"><span data-stu-id="d504a-181">console</span></span>        | <span data-ttu-id="d504a-182">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d504a-182">[C#], F#</span></span>  |
| <span data-ttu-id="d504a-183">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="d504a-183">Class library</span></span>        | <span data-ttu-id="d504a-184">classlib</span><span class="sxs-lookup"><span data-stu-id="d504a-184">classlib</span></span>       | <span data-ttu-id="d504a-185">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d504a-185">[C#], F#</span></span>  |
| <span data-ttu-id="d504a-186">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="d504a-186">Unit test project</span></span>    | <span data-ttu-id="d504a-187">mstest</span><span class="sxs-lookup"><span data-stu-id="d504a-187">mstest</span></span>         | <span data-ttu-id="d504a-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d504a-188">[C#], F#</span></span>  |
| <span data-ttu-id="d504a-189">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="d504a-189">xUnit test project</span></span>   | <span data-ttu-id="d504a-190">xunit</span><span class="sxs-lookup"><span data-stu-id="d504a-190">xunit</span></span>          | <span data-ttu-id="d504a-191">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d504a-191">[C#], F#</span></span>  |
| <span data-ttu-id="d504a-192">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="d504a-192">ASP.NET Core empty</span></span>   | <span data-ttu-id="d504a-193">web</span><span class="sxs-lookup"><span data-stu-id="d504a-193">web</span></span>            | <span data-ttu-id="d504a-194">[C#]</span><span class="sxs-lookup"><span data-stu-id="d504a-194">[C#]</span></span>      |
| <span data-ttu-id="d504a-195">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d504a-195">ASP.NET Core Web App</span></span> | <span data-ttu-id="d504a-196">mvc</span><span class="sxs-lookup"><span data-stu-id="d504a-196">mvc</span></span>            | <span data-ttu-id="d504a-197">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d504a-197">[C#], F#</span></span>  |
| <span data-ttu-id="d504a-198">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d504a-198">ASP.NET Core Web API</span></span> | <span data-ttu-id="d504a-199">webapi</span><span class="sxs-lookup"><span data-stu-id="d504a-199">webapi</span></span>         | <span data-ttu-id="d504a-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="d504a-200">[C#]</span></span>      |
| <span data-ttu-id="d504a-201">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="d504a-201">Nuget config</span></span>         | <span data-ttu-id="d504a-202">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="d504a-202">nugetconfig</span></span>    |           |
| <span data-ttu-id="d504a-203">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="d504a-203">Web config</span></span>           | <span data-ttu-id="d504a-204">webconfig</span><span class="sxs-lookup"><span data-stu-id="d504a-204">webconfig</span></span>      |           |
| <span data-ttu-id="d504a-205">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="d504a-205">Solution file</span></span>        | <span data-ttu-id="d504a-206">sln</span><span class="sxs-lookup"><span data-stu-id="d504a-206">sln</span></span>            |           |

---

## <a name="options"></a><span data-ttu-id="d504a-207">Opções</span><span class="sxs-lookup"><span data-stu-id="d504a-207">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d504a-208">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d504a-208">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="d504a-209">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="d504a-209">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="d504a-210">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-210">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="d504a-211">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="d504a-211">Prints out help for the command.</span></span> <span data-ttu-id="d504a-212">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="d504a-212">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="d504a-213">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="d504a-213">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="d504a-214">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="d504a-214">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="d504a-215">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="d504a-215">Lists templates containing the specified name.</span></span> <span data-ttu-id="d504a-216">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="d504a-216">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="d504a-217">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-217">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="d504a-218">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="d504a-218">The language of the template to create.</span></span> <span data-ttu-id="d504a-219">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="d504a-219">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="d504a-220">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="d504a-220">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="d504a-221">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="d504a-221">The name for the created output.</span></span> <span data-ttu-id="d504a-222">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="d504a-222">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d504a-223">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="d504a-223">Location to place the generated output.</span></span> <span data-ttu-id="d504a-224">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="d504a-224">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="d504a-225">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d504a-225">Filters templates based on available types.</span></span> <span data-ttu-id="d504a-226">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="d504a-226">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="d504a-227">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="d504a-227">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="d504a-228">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="d504a-228">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="d504a-229">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="d504a-229">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="d504a-230">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="d504a-230">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d504a-231">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d504a-231">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="d504a-232">Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado.</span><span class="sxs-lookup"><span data-stu-id="d504a-232">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="d504a-233">Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força.</span><span class="sxs-lookup"><span data-stu-id="d504a-233">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="d504a-234">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-234">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="d504a-235">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="d504a-235">Prints out help for the command.</span></span> <span data-ttu-id="d504a-236">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="d504a-236">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="d504a-237">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="d504a-237">Lists templates containing the specified name.</span></span> <span data-ttu-id="d504a-238">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="d504a-238">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="d504a-239">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-239">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="d504a-240">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="d504a-240">The language of the template to create.</span></span> <span data-ttu-id="d504a-241">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="d504a-241">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="d504a-242">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="d504a-242">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="d504a-243">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="d504a-243">The name for the created output.</span></span> <span data-ttu-id="d504a-244">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="d504a-244">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d504a-245">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="d504a-245">Location to place the generated output.</span></span> <span data-ttu-id="d504a-246">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="d504a-246">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="d504a-247">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="d504a-247">Template options</span></span>

<span data-ttu-id="d504a-248">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d504a-248">Each project template may have additional options available.</span></span> <span data-ttu-id="d504a-249">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="d504a-249">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d504a-250">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d504a-250">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="d504a-251">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="d504a-251">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="d504a-252">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-252">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="d504a-253">**classlib**</span><span class="sxs-lookup"><span data-stu-id="d504a-253">**classlib**</span></span>

<span data-ttu-id="d504a-254">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="d504a-254">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d504a-255">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d504a-255">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="d504a-256">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="d504a-256">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="d504a-257">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-257">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="d504a-258">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="d504a-258">**mstest, xunit**</span></span>

<span data-ttu-id="d504a-259">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="d504a-259">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="d504a-260">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-260">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="d504a-261">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="d504a-261">**globaljson**</span></span>

<span data-ttu-id="d504a-262">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="d504a-262">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="d504a-263">**web**</span><span class="sxs-lookup"><span data-stu-id="d504a-263">**web**</span></span>

<span data-ttu-id="d504a-264">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d504a-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="d504a-265">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-265">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="d504a-266">**webapi**</span><span class="sxs-lookup"><span data-stu-id="d504a-266">**webapi**</span></span>

<span data-ttu-id="d504a-267">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="d504a-267">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="d504a-268">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="d504a-268">The possible values are:</span></span>

- <span data-ttu-id="d504a-269">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="d504a-269">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="d504a-270">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="d504a-270">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="d504a-271">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="d504a-271">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="d504a-272">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="d504a-272">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="d504a-273">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d504a-273">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d504a-274">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d504a-274">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d504a-275">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="d504a-275">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="d504a-276">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-276">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d504a-277">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d504a-277">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d504a-278">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d504a-278">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d504a-279">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d504a-279">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d504a-280">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="d504a-280">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="d504a-281">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-281">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="d504a-282">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d504a-282">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="d504a-283">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="d504a-283">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="d504a-284">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="d504a-284">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="d504a-285">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d504a-285">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d504a-286">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="d504a-286">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="d504a-287">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d504a-287">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d504a-288">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d504a-288">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d504a-289">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="d504a-289">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="d504a-290">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="d504a-290">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="d504a-291">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d504a-291">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="d504a-292">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d504a-292">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="d504a-293">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="d504a-293">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d504a-294">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d504a-294">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d504a-295">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-295">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="d504a-296">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="d504a-296">**mvc, razor**</span></span>

<span data-ttu-id="d504a-297">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="d504a-297">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="d504a-298">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="d504a-298">The possible values are:</span></span>

- <span data-ttu-id="d504a-299">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="d504a-299">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="d504a-300">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="d504a-300">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="d504a-301">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="d504a-301">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="d504a-302">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="d504a-302">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="d504a-303">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="d504a-303">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="d504a-304">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="d504a-304">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="d504a-305">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d504a-305">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d504a-306">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d504a-306">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d504a-307">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="d504a-307">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="d504a-308">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-308">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d504a-309">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d504a-309">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d504a-310">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-310">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="d504a-311">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d504a-311">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d504a-312">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-312">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="d504a-313">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d504a-313">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d504a-314">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d504a-314">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d504a-315">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d504a-315">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="d504a-316">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="d504a-316">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="d504a-317">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-317">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="d504a-318">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d504a-318">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="d504a-319">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="d504a-319">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="d504a-320">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="d504a-320">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="d504a-321">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d504a-321">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="d504a-322">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="d504a-322">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="d504a-323">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d504a-323">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d504a-324">Use com a autenticação `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d504a-324">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="d504a-325">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="d504a-325">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="d504a-326">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="d504a-326">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="d504a-327">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d504a-327">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="d504a-328">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="d504a-328">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="d504a-329">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="d504a-329">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="d504a-330">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d504a-330">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="d504a-331">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d504a-331">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="d504a-332">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-332">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="d504a-333">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="d504a-333">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d504a-334">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d504a-334">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d504a-335">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d504a-335">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="d504a-336">**page**</span><span class="sxs-lookup"><span data-stu-id="d504a-336">**page**</span></span>

<span data-ttu-id="d504a-337">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="d504a-337">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="d504a-338">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="d504a-338">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="d504a-339">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="d504a-339">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="d504a-340">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="d504a-340">**viewimports**</span></span>

<span data-ttu-id="d504a-341">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="d504a-341">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="d504a-342">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="d504a-342">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d504a-343">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d504a-343">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="d504a-344">**console, xunit, mstest, web, webapi** </span><span class="sxs-lookup"><span data-stu-id="d504a-344">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="d504a-345">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="d504a-345">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d504a-346">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="d504a-346">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="d504a-347">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="d504a-347">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="d504a-348">**classlib**</span><span class="sxs-lookup"><span data-stu-id="d504a-348">**classlib**</span></span>

<span data-ttu-id="d504a-349">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="d504a-349">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d504a-350">Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="d504a-350">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="d504a-351">O valor padrão é `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="d504a-351">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="d504a-352">**mvc**</span><span class="sxs-lookup"><span data-stu-id="d504a-352">**mvc**</span></span>

<span data-ttu-id="d504a-353">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="d504a-353">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d504a-354">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="d504a-354">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="d504a-355">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="d504a-355">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="d504a-356">`-au|--auth` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="d504a-356">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="d504a-357">Valores: `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="d504a-357">Values: `None` or `Individual`.</span></span> <span data-ttu-id="d504a-358">O valor padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="d504a-358">The default value is `None`.</span></span>

<span data-ttu-id="d504a-359">`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="d504a-359">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="d504a-360">Valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="d504a-360">Values: `true` or `false`.</span></span> <span data-ttu-id="d504a-361">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="d504a-361">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="d504a-362">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d504a-362">Examples</span></span>

<span data-ttu-id="d504a-363">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="d504a-363">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="d504a-364">Crie um projeto de biblioteca de classes do .NET Standard no diretório especificado (disponível somente com o SDK do .NET Core 2.0 ou versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="d504a-364">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="d504a-365">Crie um novo projeto de aplicativo de MVC C# do ASP.NET Core no diretório atual sem autenticação direcionando o .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="d504a-365">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="d504a-366">Crie um novo aplicativo xUnit direcionando o .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="d504a-366">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="d504a-367">Lista todos os modelos disponíveis para o MVC:</span><span class="sxs-lookup"><span data-stu-id="d504a-367">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="d504a-368">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d504a-368">See also</span></span>

[<span data-ttu-id="d504a-369">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="d504a-369">Custom templates for dotnet new</span></span>](custom-templates.md)  
<span data-ttu-id="d504a-370">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="d504a-370">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md)</span></span>  
[<span data-ttu-id="d504a-371">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="d504a-371">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="d504a-372">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="d504a-372">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
