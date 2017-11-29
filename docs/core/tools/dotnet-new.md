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
ms.openlocfilehash: d64881380febee08414f57a36ed92079e8d69ed6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-new"></a><span data-ttu-id="c6e63-104">dotnet new</span><span class="sxs-lookup"><span data-stu-id="c6e63-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c6e63-105">Nome</span><span class="sxs-lookup"><span data-stu-id="c6e63-105">Name</span></span>

<span data-ttu-id="c6e63-106">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c6e63-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="c6e63-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c6e63-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c6e63-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c6e63-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c6e63-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="c6e63-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6e63-110">Description</span></span>

<span data-ttu-id="c6e63-111">O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido.</span><span class="sxs-lookup"><span data-stu-id="c6e63-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="c6e63-112">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="c6e63-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="c6e63-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="c6e63-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="c6e63-114">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="c6e63-115">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="c6e63-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="c6e63-116">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="c6e63-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c6e63-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c6e63-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="c6e63-118">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="c6e63-118">The command contains a default list of templates.</span></span> <span data-ttu-id="c6e63-119">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c6e63-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="c6e63-120">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="c6e63-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="c6e63-121">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="c6e63-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="c6e63-122">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="c6e63-122">Template description</span></span>                          | <span data-ttu-id="c6e63-123">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="c6e63-123">Template name</span></span>  | <span data-ttu-id="c6e63-124">Linguagens</span><span class="sxs-lookup"><span data-stu-id="c6e63-124">Languages</span></span>     |
|----------------------------------------------|----------------|---------------|
| <span data-ttu-id="c6e63-125">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="c6e63-125">Console application</span></span>                          | <span data-ttu-id="c6e63-126">console</span><span class="sxs-lookup"><span data-stu-id="c6e63-126">console</span></span>        | <span data-ttu-id="c6e63-127">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6e63-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c6e63-128">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="c6e63-128">Class library</span></span>                                | <span data-ttu-id="c6e63-129">classlib</span><span class="sxs-lookup"><span data-stu-id="c6e63-129">classlib</span></span>       | <span data-ttu-id="c6e63-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6e63-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c6e63-131">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="c6e63-131">Unit test project</span></span>                            | <span data-ttu-id="c6e63-132">mstest</span><span class="sxs-lookup"><span data-stu-id="c6e63-132">mstest</span></span>         | <span data-ttu-id="c6e63-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6e63-133">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c6e63-134">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="c6e63-134">xUnit test project</span></span>                           | <span data-ttu-id="c6e63-135">xunit</span><span class="sxs-lookup"><span data-stu-id="c6e63-135">xunit</span></span>          | <span data-ttu-id="c6e63-136">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c6e63-136">[C#], F#, VB</span></span>  |
| <span data-ttu-id="c6e63-137">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="c6e63-137">ASP.NET Core empty</span></span>                           | <span data-ttu-id="c6e63-138">web</span><span class="sxs-lookup"><span data-stu-id="c6e63-138">web</span></span>            | <span data-ttu-id="c6e63-139">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c6e63-139">[C#], F#</span></span>      |
| <span data-ttu-id="c6e63-140">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="c6e63-140">ASP.NET Core Web App (Model-View-Controller)</span></span> | <span data-ttu-id="c6e63-141">mvc</span><span class="sxs-lookup"><span data-stu-id="c6e63-141">mvc</span></span>            | <span data-ttu-id="c6e63-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c6e63-142">[C#], F#</span></span>      |
| <span data-ttu-id="c6e63-143">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c6e63-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="c6e63-144">razor</span><span class="sxs-lookup"><span data-stu-id="c6e63-144">razor</span></span>          | <span data-ttu-id="c6e63-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6e63-145">[C#]</span></span>          |
| <span data-ttu-id="c6e63-146">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="c6e63-146">ASP.NET Core with Angular</span></span>                    | <span data-ttu-id="c6e63-147">angular</span><span class="sxs-lookup"><span data-stu-id="c6e63-147">angular</span></span>        | <span data-ttu-id="c6e63-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6e63-148">[C#]</span></span>          |
| <span data-ttu-id="c6e63-149">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="c6e63-149">ASP.NET Core with React.js</span></span>                   | <span data-ttu-id="c6e63-150">react</span><span class="sxs-lookup"><span data-stu-id="c6e63-150">react</span></span>          | <span data-ttu-id="c6e63-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6e63-151">[C#]</span></span>          |
| <span data-ttu-id="c6e63-152">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="c6e63-152">ASP.NET Core with React.js and Redux</span></span>         | <span data-ttu-id="c6e63-153">reactredux</span><span class="sxs-lookup"><span data-stu-id="c6e63-153">reactredux</span></span>     | <span data-ttu-id="c6e63-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6e63-154">[C#]</span></span>          |
| <span data-ttu-id="c6e63-155">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c6e63-155">ASP.NET Core Web API</span></span>                         | <span data-ttu-id="c6e63-156">webapi</span><span class="sxs-lookup"><span data-stu-id="c6e63-156">webapi</span></span>         | <span data-ttu-id="c6e63-157">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c6e63-157">[C#], F#</span></span>      |
| <span data-ttu-id="c6e63-158">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="c6e63-158">global.json file</span></span>                             | <span data-ttu-id="c6e63-159">globaljson</span><span class="sxs-lookup"><span data-stu-id="c6e63-159">globaljson</span></span>     |               |
| <span data-ttu-id="c6e63-160">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="c6e63-160">Nuget config</span></span>                                 | <span data-ttu-id="c6e63-161">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="c6e63-161">nugetconfig</span></span>    |               |
| <span data-ttu-id="c6e63-162">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="c6e63-162">Web config</span></span>                                   | <span data-ttu-id="c6e63-163">webconfig</span><span class="sxs-lookup"><span data-stu-id="c6e63-163">webconfig</span></span>      |               |
| <span data-ttu-id="c6e63-164">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="c6e63-164">Solution file</span></span>                                | <span data-ttu-id="c6e63-165">sln</span><span class="sxs-lookup"><span data-stu-id="c6e63-165">sln</span></span>            |               |
| <span data-ttu-id="c6e63-166">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="c6e63-166">Razor page</span></span>                                   | <span data-ttu-id="c6e63-167">página</span><span class="sxs-lookup"><span data-stu-id="c6e63-167">page</span></span>           |               |
| <span data-ttu-id="c6e63-168">MVC/ViewImports</span><span class="sxs-lookup"><span data-stu-id="c6e63-168">MVC/ViewImports</span></span>                              | <span data-ttu-id="c6e63-169">viewimports</span><span class="sxs-lookup"><span data-stu-id="c6e63-169">viewimports</span></span>    |               |
| <span data-ttu-id="c6e63-170">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="c6e63-170">MVC ViewStart</span></span>                                | <span data-ttu-id="c6e63-171">viewstart</span><span class="sxs-lookup"><span data-stu-id="c6e63-171">viewstart</span></span>      |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c6e63-172">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c6e63-172">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="c6e63-173">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="c6e63-173">The command contains a default list of templates.</span></span> <span data-ttu-id="c6e63-174">Use `dotnet new -all` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c6e63-174">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="c6e63-175">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="c6e63-175">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="c6e63-176">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="c6e63-176">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="c6e63-177">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="c6e63-177">Template description</span></span>  | <span data-ttu-id="c6e63-178">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="c6e63-178">Template name</span></span>  | <span data-ttu-id="c6e63-179">Linguagens</span><span class="sxs-lookup"><span data-stu-id="c6e63-179">Languages</span></span> |
|----------------------|----------------|-----------|
| <span data-ttu-id="c6e63-180">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="c6e63-180">Console application</span></span>  | <span data-ttu-id="c6e63-181">console</span><span class="sxs-lookup"><span data-stu-id="c6e63-181">console</span></span>        | <span data-ttu-id="c6e63-182">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c6e63-182">[C#], F#</span></span>  |
| <span data-ttu-id="c6e63-183">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="c6e63-183">Class library</span></span>        | <span data-ttu-id="c6e63-184">classlib</span><span class="sxs-lookup"><span data-stu-id="c6e63-184">classlib</span></span>       | <span data-ttu-id="c6e63-185">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c6e63-185">[C#], F#</span></span>  |
| <span data-ttu-id="c6e63-186">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="c6e63-186">Unit test project</span></span>    | <span data-ttu-id="c6e63-187">mstest</span><span class="sxs-lookup"><span data-stu-id="c6e63-187">mstest</span></span>         | <span data-ttu-id="c6e63-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c6e63-188">[C#], F#</span></span>  |
| <span data-ttu-id="c6e63-189">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="c6e63-189">xUnit test project</span></span>   | <span data-ttu-id="c6e63-190">xunit</span><span class="sxs-lookup"><span data-stu-id="c6e63-190">xunit</span></span>          | <span data-ttu-id="c6e63-191">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c6e63-191">[C#], F#</span></span>  |
| <span data-ttu-id="c6e63-192">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="c6e63-192">ASP.NET Core empty</span></span>   | <span data-ttu-id="c6e63-193">web</span><span class="sxs-lookup"><span data-stu-id="c6e63-193">web</span></span>            | <span data-ttu-id="c6e63-194">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6e63-194">[C#]</span></span>      |
| <span data-ttu-id="c6e63-195">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c6e63-195">ASP.NET Core Web App</span></span> | <span data-ttu-id="c6e63-196">mvc</span><span class="sxs-lookup"><span data-stu-id="c6e63-196">mvc</span></span>            | <span data-ttu-id="c6e63-197">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c6e63-197">[C#], F#</span></span>  |
| <span data-ttu-id="c6e63-198">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c6e63-198">ASP.NET Core Web API</span></span> | <span data-ttu-id="c6e63-199">webapi</span><span class="sxs-lookup"><span data-stu-id="c6e63-199">webapi</span></span>         | <span data-ttu-id="c6e63-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="c6e63-200">[C#]</span></span>      |
| <span data-ttu-id="c6e63-201">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="c6e63-201">Nuget config</span></span>         | <span data-ttu-id="c6e63-202">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="c6e63-202">nugetconfig</span></span>    |           |
| <span data-ttu-id="c6e63-203">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="c6e63-203">Web config</span></span>           | <span data-ttu-id="c6e63-204">webconfig</span><span class="sxs-lookup"><span data-stu-id="c6e63-204">webconfig</span></span>      |           |
| <span data-ttu-id="c6e63-205">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="c6e63-205">Solution file</span></span>        | <span data-ttu-id="c6e63-206">sln</span><span class="sxs-lookup"><span data-stu-id="c6e63-206">sln</span></span>            |           |

---

## <a name="options"></a><span data-ttu-id="c6e63-207">Opções</span><span class="sxs-lookup"><span data-stu-id="c6e63-207">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c6e63-208">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c6e63-208">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="c6e63-209">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="c6e63-209">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="c6e63-210">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-210">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="c6e63-211">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="c6e63-211">Prints out help for the command.</span></span> <span data-ttu-id="c6e63-212">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-212">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="c6e63-213">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="c6e63-213">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c6e63-214">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="c6e63-214">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="c6e63-215">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-215">Lists templates containing the specified name.</span></span> <span data-ttu-id="c6e63-216">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-216">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="c6e63-217">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-217">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="c6e63-218">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="c6e63-218">The language of the template to create.</span></span> <span data-ttu-id="c6e63-219">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="c6e63-219">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c6e63-220">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="c6e63-220">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="c6e63-221">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="c6e63-221">The name for the created output.</span></span> <span data-ttu-id="c6e63-222">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-222">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c6e63-223">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="c6e63-223">Location to place the generated output.</span></span> <span data-ttu-id="c6e63-224">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="c6e63-224">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="c6e63-225">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c6e63-225">Filters templates based on available types.</span></span> <span data-ttu-id="c6e63-226">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="c6e63-226">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="c6e63-227">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="c6e63-227">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e63-228">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="c6e63-228">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="c6e63-229">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="c6e63-229">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="c6e63-230">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="c6e63-230">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c6e63-231">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c6e63-231">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="c6e63-232">Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-232">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="c6e63-233">Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força.</span><span class="sxs-lookup"><span data-stu-id="c6e63-233">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="c6e63-234">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-234">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="c6e63-235">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="c6e63-235">Prints out help for the command.</span></span> <span data-ttu-id="c6e63-236">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-236">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="c6e63-237">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-237">Lists templates containing the specified name.</span></span> <span data-ttu-id="c6e63-238">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-238">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="c6e63-239">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-239">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="c6e63-240">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="c6e63-240">The language of the template to create.</span></span> <span data-ttu-id="c6e63-241">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="c6e63-241">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c6e63-242">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="c6e63-242">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="c6e63-243">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="c6e63-243">The name for the created output.</span></span> <span data-ttu-id="c6e63-244">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-244">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c6e63-245">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="c6e63-245">Location to place the generated output.</span></span> <span data-ttu-id="c6e63-246">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="c6e63-246">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="c6e63-247">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="c6e63-247">Template options</span></span>

<span data-ttu-id="c6e63-248">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c6e63-248">Each project template may have additional options available.</span></span> <span data-ttu-id="c6e63-249">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="c6e63-249">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c6e63-250">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c6e63-250">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="c6e63-251">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="c6e63-251">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="c6e63-252">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-252">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="c6e63-253">**classlib**</span><span class="sxs-lookup"><span data-stu-id="c6e63-253">**classlib**</span></span>

<span data-ttu-id="c6e63-254">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="c6e63-254">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6e63-255">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c6e63-255">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="c6e63-256">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-256">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="c6e63-257">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-257">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="c6e63-258">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="c6e63-258">**mstest, xunit**</span></span>

<span data-ttu-id="c6e63-259">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c6e63-259">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="c6e63-260">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-260">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="c6e63-261">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="c6e63-261">**globaljson**</span></span>

<span data-ttu-id="c6e63-262">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="c6e63-262">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="c6e63-263">**web**</span><span class="sxs-lookup"><span data-stu-id="c6e63-263">**web**</span></span>

<span data-ttu-id="c6e63-264">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="c6e63-265">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-265">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="c6e63-266">**webapi**</span><span class="sxs-lookup"><span data-stu-id="c6e63-266">**webapi**</span></span>

<span data-ttu-id="c6e63-267">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-267">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c6e63-268">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="c6e63-268">The possible values are:</span></span>

- <span data-ttu-id="c6e63-269">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="c6e63-269">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c6e63-270">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c6e63-270">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c6e63-271">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="c6e63-271">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c6e63-272">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="c6e63-272">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c6e63-273">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c6e63-273">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c6e63-274">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-274">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6e63-275">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-275">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c6e63-276">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-276">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c6e63-277">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-277">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6e63-278">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c6e63-278">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c6e63-279">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-279">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c6e63-280">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-280">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c6e63-281">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-281">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c6e63-282">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-282">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c6e63-283">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-283">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c6e63-284">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="c6e63-284">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c6e63-285">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-285">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6e63-286">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-286">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c6e63-287">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c6e63-287">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c6e63-288">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-288">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c6e63-289">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-289">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c6e63-290">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="c6e63-290">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c6e63-291">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-291">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c6e63-292">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-292">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="c6e63-293">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="c6e63-293">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c6e63-294">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-294">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6e63-295">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-295">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="c6e63-296">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="c6e63-296">**mvc, razor**</span></span>

<span data-ttu-id="c6e63-297">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-297">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c6e63-298">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="c6e63-298">The possible values are:</span></span>

- <span data-ttu-id="c6e63-299">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="c6e63-299">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c6e63-300">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="c6e63-300">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="c6e63-301">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c6e63-301">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c6e63-302">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="c6e63-302">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c6e63-303">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="c6e63-303">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="c6e63-304">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="c6e63-304">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c6e63-305">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c6e63-305">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c6e63-306">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-306">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c6e63-307">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-307">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="c6e63-308">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-308">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c6e63-309">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-309">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6e63-310">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-310">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="c6e63-311">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-311">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6e63-312">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-312">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="c6e63-313">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-313">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6e63-314">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c6e63-314">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c6e63-315">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-315">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c6e63-316">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-316">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c6e63-317">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-317">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c6e63-318">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-318">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c6e63-319">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-319">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c6e63-320">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="c6e63-320">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c6e63-321">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-321">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="c6e63-322">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-322">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c6e63-323">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c6e63-323">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c6e63-324">Use com a autenticação `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-324">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="c6e63-325">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-325">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c6e63-326">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="c6e63-326">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c6e63-327">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-327">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="c6e63-328">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-328">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="c6e63-329">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="c6e63-329">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c6e63-330">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-330">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c6e63-331">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-331">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="c6e63-332">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-332">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="c6e63-333">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="c6e63-333">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c6e63-334">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-334">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c6e63-335">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c6e63-335">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="c6e63-336">**page**</span><span class="sxs-lookup"><span data-stu-id="c6e63-336">**page**</span></span>

<span data-ttu-id="c6e63-337">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-337">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="c6e63-338">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-338">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="c6e63-339">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="c6e63-339">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="c6e63-340">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="c6e63-340">**viewimports**</span></span>

<span data-ttu-id="c6e63-341">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-341">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="c6e63-342">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-342">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c6e63-343">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c6e63-343">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="c6e63-344">**console, xunit, mstest, web, webapi** </span><span class="sxs-lookup"><span data-stu-id="c6e63-344">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="c6e63-345">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="c6e63-345">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6e63-346">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-346">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="c6e63-347">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-347">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="c6e63-348">**classlib**</span><span class="sxs-lookup"><span data-stu-id="c6e63-348">**classlib**</span></span>

<span data-ttu-id="c6e63-349">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="c6e63-349">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6e63-350">Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-350">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="c6e63-351">O valor padrão é `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-351">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="c6e63-352">**mvc**</span><span class="sxs-lookup"><span data-stu-id="c6e63-352">**mvc**</span></span>

<span data-ttu-id="c6e63-353">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="c6e63-353">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c6e63-354">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-354">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="c6e63-355">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-355">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="c6e63-356">`-au|--auth` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="c6e63-356">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="c6e63-357">Valores: `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-357">Values: `None` or `Individual`.</span></span> <span data-ttu-id="c6e63-358">O valor padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-358">The default value is `None`.</span></span>

<span data-ttu-id="c6e63-359">`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="c6e63-359">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="c6e63-360">Valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-360">Values: `true` or `false`.</span></span> <span data-ttu-id="c6e63-361">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="c6e63-361">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="c6e63-362">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c6e63-362">Examples</span></span>

<span data-ttu-id="c6e63-363">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="c6e63-363">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="c6e63-364">Crie um projeto de biblioteca de classes do .NET Standard no diretório especificado (disponível somente com o SDK do .NET Core 2.0 ou versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="c6e63-364">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="c6e63-365">Crie um novo projeto de aplicativo de MVC C# do ASP.NET Core no diretório atual sem autenticação direcionando o .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="c6e63-365">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="c6e63-366">Crie um novo aplicativo xUnit direcionando o .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="c6e63-366">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="c6e63-367">Lista todos os modelos disponíveis para o MVC:</span><span class="sxs-lookup"><span data-stu-id="c6e63-367">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="c6e63-368">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6e63-368">See also</span></span>

[<span data-ttu-id="c6e63-369">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="c6e63-369">Custom templates for dotnet new</span></span>](custom-templates.md)  
<span data-ttu-id="c6e63-370">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="c6e63-370">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md)</span></span>  
[<span data-ttu-id="c6e63-371">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="c6e63-371">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="c6e63-372">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="c6e63-372">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
