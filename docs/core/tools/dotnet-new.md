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
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: 335902f26148d8201b7311b57370fd37280c68dd
ms.contentlocale: pt-br
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-new"></a><span data-ttu-id="223bc-104">dotnet new</span><span class="sxs-lookup"><span data-stu-id="223bc-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="223bc-105">Nome</span><span class="sxs-lookup"><span data-stu-id="223bc-105">Name</span></span>

<span data-ttu-id="223bc-106">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="223bc-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="223bc-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="223bc-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="223bc-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="223bc-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="223bc-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="223bc-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="223bc-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="223bc-110">Description</span></span>

<span data-ttu-id="223bc-111">O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido.</span><span class="sxs-lookup"><span data-stu-id="223bc-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="223bc-112">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="223bc-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="223bc-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="223bc-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="223bc-114">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="223bc-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="223bc-115">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="223bc-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="223bc-116">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="223bc-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="223bc-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="223bc-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="223bc-118">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="223bc-118">The command contains a default list of templates.</span></span> <span data-ttu-id="223bc-119">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="223bc-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="223bc-120">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="223bc-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="223bc-121">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="223bc-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="223bc-122">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="223bc-122">Template description</span></span>                          | <span data-ttu-id="223bc-123">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="223bc-123">Template name</span></span>  | <span data-ttu-id="223bc-124">Linguagens</span><span class="sxs-lookup"><span data-stu-id="223bc-124">Languages</span></span>     |
|----------------------------------------------|----------------|---------------|
| <span data-ttu-id="223bc-125">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="223bc-125">Console application</span></span>                          | <span data-ttu-id="223bc-126">console</span><span class="sxs-lookup"><span data-stu-id="223bc-126">console</span></span>        | <span data-ttu-id="223bc-127">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="223bc-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="223bc-128">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="223bc-128">Class library</span></span>                                | <span data-ttu-id="223bc-129">classlib</span><span class="sxs-lookup"><span data-stu-id="223bc-129">classlib</span></span>       | <span data-ttu-id="223bc-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="223bc-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="223bc-131">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="223bc-131">Unit test project</span></span>                            | <span data-ttu-id="223bc-132">mstest</span><span class="sxs-lookup"><span data-stu-id="223bc-132">mstest</span></span>         | <span data-ttu-id="223bc-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="223bc-133">[C#], F#, VB</span></span>  |
| <span data-ttu-id="223bc-134">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="223bc-134">xUnit test project</span></span>                           | <span data-ttu-id="223bc-135">xunit</span><span class="sxs-lookup"><span data-stu-id="223bc-135">xunit</span></span>          | <span data-ttu-id="223bc-136">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="223bc-136">[C#], F#, VB</span></span>  |
| <span data-ttu-id="223bc-137">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="223bc-137">ASP.NET Core empty</span></span>                           | <span data-ttu-id="223bc-138">web</span><span class="sxs-lookup"><span data-stu-id="223bc-138">web</span></span>            | <span data-ttu-id="223bc-139">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="223bc-139">[C#], F#</span></span>      |
| <span data-ttu-id="223bc-140">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="223bc-140">ASP.NET Core Web App (Model-View-Controller)</span></span> | <span data-ttu-id="223bc-141">mvc</span><span class="sxs-lookup"><span data-stu-id="223bc-141">mvc</span></span>            | <span data-ttu-id="223bc-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="223bc-142">[C#], F#</span></span>      |
| <span data-ttu-id="223bc-143">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="223bc-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="223bc-144">razor</span><span class="sxs-lookup"><span data-stu-id="223bc-144">razor</span></span>          | <span data-ttu-id="223bc-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="223bc-145">[C#]</span></span>          |
| <span data-ttu-id="223bc-146">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="223bc-146">ASP.NET Core with Angular</span></span>                    | <span data-ttu-id="223bc-147">angular</span><span class="sxs-lookup"><span data-stu-id="223bc-147">angular</span></span>        | <span data-ttu-id="223bc-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="223bc-148">[C#]</span></span>          |
| <span data-ttu-id="223bc-149">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="223bc-149">ASP.NET Core with React.js</span></span>                   | <span data-ttu-id="223bc-150">react</span><span class="sxs-lookup"><span data-stu-id="223bc-150">react</span></span>          | <span data-ttu-id="223bc-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="223bc-151">[C#]</span></span>          |
| <span data-ttu-id="223bc-152">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="223bc-152">ASP.NET Core with React.js and Redux</span></span>         | <span data-ttu-id="223bc-153">reactredux</span><span class="sxs-lookup"><span data-stu-id="223bc-153">reactredux</span></span>     | <span data-ttu-id="223bc-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="223bc-154">[C#]</span></span>          |
| <span data-ttu-id="223bc-155">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="223bc-155">ASP.NET Core Web API</span></span>                         | <span data-ttu-id="223bc-156">webapi</span><span class="sxs-lookup"><span data-stu-id="223bc-156">webapi</span></span>         | <span data-ttu-id="223bc-157">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="223bc-157">[C#], F#</span></span>      |
| <span data-ttu-id="223bc-158">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="223bc-158">global.json file</span></span>                             | <span data-ttu-id="223bc-159">globaljson</span><span class="sxs-lookup"><span data-stu-id="223bc-159">globaljson</span></span>     |               |
| <span data-ttu-id="223bc-160">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="223bc-160">Nuget config</span></span>                                 | <span data-ttu-id="223bc-161">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="223bc-161">nugetconfig</span></span>    |               |
| <span data-ttu-id="223bc-162">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="223bc-162">Web config</span></span>                                   | <span data-ttu-id="223bc-163">webconfig</span><span class="sxs-lookup"><span data-stu-id="223bc-163">webconfig</span></span>      |               |
| <span data-ttu-id="223bc-164">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="223bc-164">Solution file</span></span>                                | <span data-ttu-id="223bc-165">sln</span><span class="sxs-lookup"><span data-stu-id="223bc-165">sln</span></span>            |               |
| <span data-ttu-id="223bc-166">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="223bc-166">Razor page</span></span>                                   | <span data-ttu-id="223bc-167">página</span><span class="sxs-lookup"><span data-stu-id="223bc-167">page</span></span>           |               |
| <span data-ttu-id="223bc-168">MVC/ViewImports</span><span class="sxs-lookup"><span data-stu-id="223bc-168">MVC/ViewImports</span></span>                              | <span data-ttu-id="223bc-169">viewimports</span><span class="sxs-lookup"><span data-stu-id="223bc-169">viewimports</span></span>    |               |
| <span data-ttu-id="223bc-170">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="223bc-170">MVC ViewStart</span></span>                                | <span data-ttu-id="223bc-171">viewstart</span><span class="sxs-lookup"><span data-stu-id="223bc-171">viewstart</span></span>      |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="223bc-172">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="223bc-172">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="223bc-173">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="223bc-173">The command contains a default list of templates.</span></span> <span data-ttu-id="223bc-174">Use `dotnet new -all` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="223bc-174">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="223bc-175">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="223bc-175">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="223bc-176">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="223bc-176">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="223bc-177">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="223bc-177">Template description</span></span>  | <span data-ttu-id="223bc-178">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="223bc-178">Template name</span></span>  | <span data-ttu-id="223bc-179">Linguagens</span><span class="sxs-lookup"><span data-stu-id="223bc-179">Languages</span></span> |
|----------------------|----------------|-----------|
| <span data-ttu-id="223bc-180">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="223bc-180">Console application</span></span>  | <span data-ttu-id="223bc-181">console</span><span class="sxs-lookup"><span data-stu-id="223bc-181">console</span></span>        | <span data-ttu-id="223bc-182">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="223bc-182">[C#], F#</span></span>  |
| <span data-ttu-id="223bc-183">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="223bc-183">Class library</span></span>        | <span data-ttu-id="223bc-184">classlib</span><span class="sxs-lookup"><span data-stu-id="223bc-184">classlib</span></span>       | <span data-ttu-id="223bc-185">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="223bc-185">[C#], F#</span></span>  |
| <span data-ttu-id="223bc-186">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="223bc-186">Unit test project</span></span>    | <span data-ttu-id="223bc-187">mstest</span><span class="sxs-lookup"><span data-stu-id="223bc-187">mstest</span></span>         | <span data-ttu-id="223bc-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="223bc-188">[C#], F#</span></span>  |
| <span data-ttu-id="223bc-189">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="223bc-189">xUnit test project</span></span>   | <span data-ttu-id="223bc-190">xunit</span><span class="sxs-lookup"><span data-stu-id="223bc-190">xunit</span></span>          | <span data-ttu-id="223bc-191">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="223bc-191">[C#], F#</span></span>  |
| <span data-ttu-id="223bc-192">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="223bc-192">ASP.NET Core empty</span></span>   | <span data-ttu-id="223bc-193">web</span><span class="sxs-lookup"><span data-stu-id="223bc-193">web</span></span>            | <span data-ttu-id="223bc-194">[C#]</span><span class="sxs-lookup"><span data-stu-id="223bc-194">[C#]</span></span>      |
| <span data-ttu-id="223bc-195">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="223bc-195">ASP.NET Core Web App</span></span> | <span data-ttu-id="223bc-196">mvc</span><span class="sxs-lookup"><span data-stu-id="223bc-196">mvc</span></span>            | <span data-ttu-id="223bc-197">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="223bc-197">[C#], F#</span></span>  |
| <span data-ttu-id="223bc-198">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="223bc-198">ASP.NET Core Web API</span></span> | <span data-ttu-id="223bc-199">webapi</span><span class="sxs-lookup"><span data-stu-id="223bc-199">webapi</span></span>         | <span data-ttu-id="223bc-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="223bc-200">[C#]</span></span>      |
| <span data-ttu-id="223bc-201">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="223bc-201">Nuget config</span></span>         | <span data-ttu-id="223bc-202">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="223bc-202">nugetconfig</span></span>    |           |
| <span data-ttu-id="223bc-203">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="223bc-203">Web config</span></span>           | <span data-ttu-id="223bc-204">webconfig</span><span class="sxs-lookup"><span data-stu-id="223bc-204">webconfig</span></span>      |           |
| <span data-ttu-id="223bc-205">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="223bc-205">Solution file</span></span>        | <span data-ttu-id="223bc-206">sln</span><span class="sxs-lookup"><span data-stu-id="223bc-206">sln</span></span>            |           |

---

## <a name="options"></a><span data-ttu-id="223bc-207">Opções</span><span class="sxs-lookup"><span data-stu-id="223bc-207">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="223bc-208">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="223bc-208">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="223bc-209">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="223bc-209">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="223bc-210">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-210">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="223bc-211">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="223bc-211">Prints out help for the command.</span></span> <span data-ttu-id="223bc-212">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="223bc-212">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="223bc-213">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="223bc-213">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="223bc-214">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="223bc-214">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="223bc-215">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="223bc-215">Lists templates containing the specified name.</span></span> <span data-ttu-id="223bc-216">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="223bc-216">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="223bc-217">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-217">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="223bc-218">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="223bc-218">The language of the template to create.</span></span> <span data-ttu-id="223bc-219">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="223bc-219">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="223bc-220">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="223bc-220">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="223bc-221">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="223bc-221">The name for the created output.</span></span> <span data-ttu-id="223bc-222">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="223bc-222">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="223bc-223">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="223bc-223">Location to place the generated output.</span></span> <span data-ttu-id="223bc-224">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="223bc-224">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="223bc-225">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="223bc-225">Filters templates based on available types.</span></span> <span data-ttu-id="223bc-226">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="223bc-226">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="223bc-227">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="223bc-227">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="223bc-228">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="223bc-228">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="223bc-229">Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado.</span><span class="sxs-lookup"><span data-stu-id="223bc-229">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="223bc-230">Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força.</span><span class="sxs-lookup"><span data-stu-id="223bc-230">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="223bc-231">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-231">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="223bc-232">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="223bc-232">Prints out help for the command.</span></span> <span data-ttu-id="223bc-233">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="223bc-233">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="223bc-234">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="223bc-234">Lists templates containing the specified name.</span></span> <span data-ttu-id="223bc-235">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="223bc-235">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="223bc-236">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-236">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="223bc-237">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="223bc-237">The language of the template to create.</span></span> <span data-ttu-id="223bc-238">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="223bc-238">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="223bc-239">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="223bc-239">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="223bc-240">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="223bc-240">The name for the created output.</span></span> <span data-ttu-id="223bc-241">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="223bc-241">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="223bc-242">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="223bc-242">Location to place the generated output.</span></span> <span data-ttu-id="223bc-243">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="223bc-243">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="223bc-244">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="223bc-244">Template options</span></span>

<span data-ttu-id="223bc-245">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="223bc-245">Each project template may have additional options available.</span></span> <span data-ttu-id="223bc-246">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="223bc-246">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="223bc-247">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="223bc-247">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="223bc-248">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="223bc-248">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="223bc-249">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-249">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="223bc-250">**classlib**</span><span class="sxs-lookup"><span data-stu-id="223bc-250">**classlib**</span></span>

<span data-ttu-id="223bc-251">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="223bc-251">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="223bc-252">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="223bc-252">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="223bc-253">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="223bc-253">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="223bc-254">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-254">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="223bc-255">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="223bc-255">**mstest, xunit**</span></span>

<span data-ttu-id="223bc-256">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="223bc-256">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="223bc-257">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-257">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="223bc-258">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="223bc-258">**globaljson**</span></span>

<span data-ttu-id="223bc-259">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="223bc-259">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="223bc-260">**web**</span><span class="sxs-lookup"><span data-stu-id="223bc-260">**web**</span></span>

<span data-ttu-id="223bc-261">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="223bc-261">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="223bc-262">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-262">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="223bc-263">**webapi**</span><span class="sxs-lookup"><span data-stu-id="223bc-263">**webapi**</span></span>

<span data-ttu-id="223bc-264">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="223bc-264">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="223bc-265">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="223bc-265">The possible values are:</span></span>

- <span data-ttu-id="223bc-266">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="223bc-266">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="223bc-267">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="223bc-267">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="223bc-268">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="223bc-268">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="223bc-269">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="223bc-269">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="223bc-270">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="223bc-270">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="223bc-271">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="223bc-271">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="223bc-272">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="223bc-272">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="223bc-273">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-273">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="223bc-274">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="223bc-274">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="223bc-275">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="223bc-275">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="223bc-276">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="223bc-276">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="223bc-277">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="223bc-277">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="223bc-278">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-278">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="223bc-279">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="223bc-279">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="223bc-280">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="223bc-280">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="223bc-281">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="223bc-281">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="223bc-282">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="223bc-282">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="223bc-283">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="223bc-283">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="223bc-284">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="223bc-284">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="223bc-285">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="223bc-285">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="223bc-286">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="223bc-286">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="223bc-287">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="223bc-287">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="223bc-288">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="223bc-288">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="223bc-289">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="223bc-289">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="223bc-290">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="223bc-290">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="223bc-291">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="223bc-291">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="223bc-292">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-292">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="223bc-293">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="223bc-293">**mvc, razor**</span></span>

<span data-ttu-id="223bc-294">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="223bc-294">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="223bc-295">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="223bc-295">The possible values are:</span></span>

- <span data-ttu-id="223bc-296">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="223bc-296">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="223bc-297">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="223bc-297">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="223bc-298">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="223bc-298">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="223bc-299">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="223bc-299">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="223bc-300">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="223bc-300">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="223bc-301">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="223bc-301">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="223bc-302">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="223bc-302">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="223bc-303">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="223bc-303">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="223bc-304">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="223bc-304">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="223bc-305">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-305">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="223bc-306">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="223bc-306">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="223bc-307">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-307">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="223bc-308">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="223bc-308">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="223bc-309">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-309">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="223bc-310">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="223bc-310">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="223bc-311">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="223bc-311">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="223bc-312">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="223bc-312">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="223bc-313">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="223bc-313">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="223bc-314">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-314">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="223bc-315">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="223bc-315">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="223bc-316">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="223bc-316">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="223bc-317">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="223bc-317">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="223bc-318">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="223bc-318">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="223bc-319">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="223bc-319">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="223bc-320">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="223bc-320">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="223bc-321">Use com a autenticação `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="223bc-321">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="223bc-322">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="223bc-322">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="223bc-323">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="223bc-323">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="223bc-324">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="223bc-324">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="223bc-325">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="223bc-325">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="223bc-326">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="223bc-326">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="223bc-327">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="223bc-327">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="223bc-328">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="223bc-328">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="223bc-329">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-329">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="223bc-330">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="223bc-330">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="223bc-331">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="223bc-331">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="223bc-332">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="223bc-332">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="223bc-333">**page**</span><span class="sxs-lookup"><span data-stu-id="223bc-333">**page**</span></span>

<span data-ttu-id="223bc-334">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="223bc-334">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="223bc-335">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="223bc-335">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="223bc-336">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="223bc-336">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="223bc-337">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="223bc-337">**viewimports**</span></span>

<span data-ttu-id="223bc-338">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="223bc-338">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="223bc-339">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="223bc-339">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="223bc-340">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="223bc-340">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="223bc-341">**console, xunit, mstest, web, webapi** </span><span class="sxs-lookup"><span data-stu-id="223bc-341">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="223bc-342">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="223bc-342">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="223bc-343">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="223bc-343">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="223bc-344">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="223bc-344">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="223bc-345">**classlib**</span><span class="sxs-lookup"><span data-stu-id="223bc-345">**classlib**</span></span>

<span data-ttu-id="223bc-346">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="223bc-346">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="223bc-347">Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="223bc-347">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="223bc-348">O valor padrão é `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="223bc-348">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="223bc-349">**mvc**</span><span class="sxs-lookup"><span data-stu-id="223bc-349">**mvc**</span></span>

<span data-ttu-id="223bc-350">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="223bc-350">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="223bc-351">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="223bc-351">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="223bc-352">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="223bc-352">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="223bc-353">`-au|--auth` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="223bc-353">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="223bc-354">Valores: `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="223bc-354">Values: `None` or `Individual`.</span></span> <span data-ttu-id="223bc-355">O valor padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="223bc-355">The default value is `None`.</span></span>

<span data-ttu-id="223bc-356">`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="223bc-356">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="223bc-357">Valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="223bc-357">Values: `true` or `false`.</span></span> <span data-ttu-id="223bc-358">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="223bc-358">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="223bc-359">Exemplos</span><span class="sxs-lookup"><span data-stu-id="223bc-359">Examples</span></span>

<span data-ttu-id="223bc-360">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="223bc-360">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="223bc-361">Crie um projeto de biblioteca de classes do .NET Standard no diretório especificado (disponível somente com o SDK do .NET Core 2.0 ou versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="223bc-361">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="223bc-362">Crie um novo projeto de aplicativo de MVC C# do ASP.NET Core no diretório atual sem autenticação direcionando o .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="223bc-362">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="223bc-363">Crie um novo aplicativo xUnit direcionando o .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="223bc-363">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="223bc-364">Lista todos os modelos disponíveis para o MVC:</span><span class="sxs-lookup"><span data-stu-id="223bc-364">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="223bc-365">Consulte também</span><span class="sxs-lookup"><span data-stu-id="223bc-365">See also</span></span>

[<span data-ttu-id="223bc-366">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="223bc-366">Custom templates for dotnet new</span></span>](custom-templates.md)  
<span data-ttu-id="223bc-367">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="223bc-367">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md)</span></span>  
[<span data-ttu-id="223bc-368">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="223bc-368">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="223bc-369">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="223bc-369">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)

