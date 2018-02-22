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
ms.workload:
- dotnetcore
ms.openlocfilehash: ea94c875ae6fe82d0e5d35ba8ca3fd47971fbbe6
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="dotnet-new"></a><span data-ttu-id="6c49f-104">dotnet new</span><span class="sxs-lookup"><span data-stu-id="6c49f-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="6c49f-105">Nome</span><span class="sxs-lookup"><span data-stu-id="6c49f-105">Name</span></span>

<span data-ttu-id="6c49f-106">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6c49f-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="6c49f-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6c49f-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6c49f-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6c49f-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6c49f-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="6c49f-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c49f-110">Description</span></span>

<span data-ttu-id="6c49f-111">O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido.</span><span class="sxs-lookup"><span data-stu-id="6c49f-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="6c49f-112">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="6c49f-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="6c49f-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="6c49f-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="6c49f-114">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="6c49f-115">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="6c49f-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="6c49f-116">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="6c49f-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6c49f-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6c49f-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="6c49f-118">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="6c49f-118">The command contains a default list of templates.</span></span> <span data-ttu-id="6c49f-119">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6c49f-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="6c49f-120">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="6c49f-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="6c49f-121">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="6c49f-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="6c49f-122">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="6c49f-122">Template description</span></span>                          | <span data-ttu-id="6c49f-123">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="6c49f-123">Template name</span></span> | <span data-ttu-id="6c49f-124">Linguagens</span><span class="sxs-lookup"><span data-stu-id="6c49f-124">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="6c49f-125">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="6c49f-125">Console application</span></span>                          | `console`     | <span data-ttu-id="6c49f-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c49f-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6c49f-127">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="6c49f-127">Class library</span></span>                                | `classlib`    | <span data-ttu-id="6c49f-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c49f-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6c49f-129">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="6c49f-129">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="6c49f-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c49f-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6c49f-131">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="6c49f-131">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="6c49f-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6c49f-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6c49f-133">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="6c49f-133">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="6c49f-134">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c49f-134">[C#], F#</span></span>      |
| <span data-ttu-id="6c49f-135">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="6c49f-135">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="6c49f-136">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c49f-136">[C#], F#</span></span>      |
| <span data-ttu-id="6c49f-137">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6c49f-137">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="6c49f-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c49f-138">[C#]</span></span>          |
| <span data-ttu-id="6c49f-139">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="6c49f-139">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="6c49f-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c49f-140">[C#]</span></span>          |
| <span data-ttu-id="6c49f-141">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="6c49f-141">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="6c49f-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c49f-142">[C#]</span></span>          |
| <span data-ttu-id="6c49f-143">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="6c49f-143">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="6c49f-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c49f-144">[C#]</span></span>          |
| <span data-ttu-id="6c49f-145">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6c49f-145">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="6c49f-146">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c49f-146">[C#], F#</span></span>      |
| <span data-ttu-id="6c49f-147">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="6c49f-147">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="6c49f-148">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="6c49f-148">Nuget config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="6c49f-149">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="6c49f-149">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="6c49f-150">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="6c49f-150">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="6c49f-151">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="6c49f-151">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="6c49f-152">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="6c49f-152">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="6c49f-153">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="6c49f-153">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6c49f-154">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6c49f-154">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="6c49f-155">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="6c49f-155">The command contains a default list of templates.</span></span> <span data-ttu-id="6c49f-156">Use `dotnet new -all` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6c49f-156">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="6c49f-157">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="6c49f-157">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="6c49f-158">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="6c49f-158">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="6c49f-159">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="6c49f-159">Template description</span></span>  | <span data-ttu-id="6c49f-160">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="6c49f-160">Template name</span></span> | <span data-ttu-id="6c49f-161">Linguagens</span><span class="sxs-lookup"><span data-stu-id="6c49f-161">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="6c49f-162">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="6c49f-162">Console application</span></span>  | `console`     | <span data-ttu-id="6c49f-163">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c49f-163">[C#], F#</span></span>  |
| <span data-ttu-id="6c49f-164">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="6c49f-164">Class library</span></span>        | `classlib`    | <span data-ttu-id="6c49f-165">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c49f-165">[C#], F#</span></span>  |
| <span data-ttu-id="6c49f-166">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="6c49f-166">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="6c49f-167">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c49f-167">[C#], F#</span></span>  |
| <span data-ttu-id="6c49f-168">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="6c49f-168">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="6c49f-169">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c49f-169">[C#], F#</span></span>  |
| <span data-ttu-id="6c49f-170">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="6c49f-170">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="6c49f-171">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c49f-171">[C#]</span></span>      |
| <span data-ttu-id="6c49f-172">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6c49f-172">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="6c49f-173">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6c49f-173">[C#], F#</span></span>  |
| <span data-ttu-id="6c49f-174">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6c49f-174">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="6c49f-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="6c49f-175">[C#]</span></span>      |
| <span data-ttu-id="6c49f-176">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="6c49f-176">Nuget config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="6c49f-177">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="6c49f-177">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="6c49f-178">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="6c49f-178">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="6c49f-179">Opções</span><span class="sxs-lookup"><span data-stu-id="6c49f-179">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6c49f-180">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6c49f-180">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="6c49f-181">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="6c49f-181">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="6c49f-182">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-182">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="6c49f-183">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="6c49f-183">Prints out help for the command.</span></span> <span data-ttu-id="6c49f-184">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-184">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="6c49f-185">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="6c49f-185">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6c49f-186">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="6c49f-186">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="6c49f-187">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-187">Lists templates containing the specified name.</span></span> <span data-ttu-id="6c49f-188">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-188">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="6c49f-189">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-189">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="6c49f-190">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="6c49f-190">The language of the template to create.</span></span> <span data-ttu-id="6c49f-191">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="6c49f-191">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6c49f-192">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="6c49f-192">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="6c49f-193">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="6c49f-193">The name for the created output.</span></span> <span data-ttu-id="6c49f-194">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-194">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6c49f-195">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="6c49f-195">Location to place the generated output.</span></span> <span data-ttu-id="6c49f-196">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="6c49f-196">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="6c49f-197">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6c49f-197">Filters templates based on available types.</span></span> <span data-ttu-id="6c49f-198">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="6c49f-198">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="6c49f-199">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="6c49f-199">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="6c49f-200">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="6c49f-200">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="6c49f-201">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="6c49f-201">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="6c49f-202">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="6c49f-202">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6c49f-203">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6c49f-203">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="6c49f-204">Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-204">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="6c49f-205">Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força.</span><span class="sxs-lookup"><span data-stu-id="6c49f-205">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="6c49f-206">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-206">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="6c49f-207">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="6c49f-207">Prints out help for the command.</span></span> <span data-ttu-id="6c49f-208">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-208">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="6c49f-209">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-209">Lists templates containing the specified name.</span></span> <span data-ttu-id="6c49f-210">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-210">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="6c49f-211">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-211">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="6c49f-212">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="6c49f-212">The language of the template to create.</span></span> <span data-ttu-id="6c49f-213">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="6c49f-213">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6c49f-214">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="6c49f-214">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="6c49f-215">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="6c49f-215">The name for the created output.</span></span> <span data-ttu-id="6c49f-216">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-216">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6c49f-217">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="6c49f-217">Location to place the generated output.</span></span> <span data-ttu-id="6c49f-218">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="6c49f-218">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="6c49f-219">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="6c49f-219">Template options</span></span>

<span data-ttu-id="6c49f-220">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6c49f-220">Each project template may have additional options available.</span></span> <span data-ttu-id="6c49f-221">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="6c49f-221">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6c49f-222">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6c49f-222">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="6c49f-223">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="6c49f-223">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="6c49f-224">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-224">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="6c49f-225">**classlib**</span><span class="sxs-lookup"><span data-stu-id="6c49f-225">**classlib**</span></span>

<span data-ttu-id="6c49f-226">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="6c49f-226">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c49f-227">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="6c49f-227">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="6c49f-228">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-228">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="6c49f-229">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-229">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="6c49f-230">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="6c49f-230">**mstest, xunit**</span></span>

<span data-ttu-id="6c49f-231">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6c49f-231">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="6c49f-232">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-232">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="6c49f-233">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="6c49f-233">**globaljson**</span></span>

<span data-ttu-id="6c49f-234">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="6c49f-234">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="6c49f-235">**web**</span><span class="sxs-lookup"><span data-stu-id="6c49f-235">**web**</span></span>

<span data-ttu-id="6c49f-236">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-236">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="6c49f-237">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-237">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="6c49f-238">**webapi**</span><span class="sxs-lookup"><span data-stu-id="6c49f-238">**webapi**</span></span>

<span data-ttu-id="6c49f-239">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-239">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6c49f-240">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="6c49f-240">The possible values are:</span></span>

- <span data-ttu-id="6c49f-241">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="6c49f-241">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6c49f-242">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6c49f-242">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6c49f-243">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="6c49f-243">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6c49f-244">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="6c49f-244">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6c49f-245">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6c49f-245">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6c49f-246">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-246">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c49f-247">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-247">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6c49f-248">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-248">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6c49f-249">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-249">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c49f-250">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6c49f-250">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6c49f-251">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-251">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c49f-252">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-252">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6c49f-253">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-253">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6c49f-254">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-254">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="6c49f-255">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-255">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6c49f-256">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="6c49f-256">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6c49f-257">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-257">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c49f-258">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-258">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6c49f-259">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6c49f-259">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6c49f-260">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-260">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6c49f-261">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-261">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6c49f-262">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="6c49f-262">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6c49f-263">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-263">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6c49f-264">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="6c49f-265">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="6c49f-265">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6c49f-266">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-266">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c49f-267">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-267">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="6c49f-268">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="6c49f-268">**mvc, razor**</span></span>

<span data-ttu-id="6c49f-269">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-269">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6c49f-270">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="6c49f-270">The possible values are:</span></span>

- <span data-ttu-id="6c49f-271">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="6c49f-271">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6c49f-272">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="6c49f-272">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="6c49f-273">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6c49f-273">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6c49f-274">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="6c49f-274">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6c49f-275">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="6c49f-275">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="6c49f-276">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="6c49f-276">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6c49f-277">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6c49f-277">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6c49f-278">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-278">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6c49f-279">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-279">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="6c49f-280">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-280">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6c49f-281">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-281">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c49f-282">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-282">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="6c49f-283">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-283">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c49f-284">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-284">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="6c49f-285">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-285">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c49f-286">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6c49f-286">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6c49f-287">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-287">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="6c49f-288">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-288">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6c49f-289">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-289">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6c49f-290">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-290">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="6c49f-291">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-291">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6c49f-292">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="6c49f-292">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6c49f-293">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-293">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="6c49f-294">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-294">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6c49f-295">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6c49f-295">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6c49f-296">Use com a autenticação `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-296">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="6c49f-297">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-297">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6c49f-298">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="6c49f-298">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="6c49f-299">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-299">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="6c49f-300">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-300">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="6c49f-301">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="6c49f-301">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6c49f-302">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-302">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6c49f-303">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-303">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="6c49f-304">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-304">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="6c49f-305">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="6c49f-305">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6c49f-306">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-306">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6c49f-307">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6c49f-307">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="6c49f-308">**page**</span><span class="sxs-lookup"><span data-stu-id="6c49f-308">**page**</span></span>

<span data-ttu-id="6c49f-309">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-309">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="6c49f-310">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-310">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="6c49f-311">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="6c49f-311">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="6c49f-312">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="6c49f-312">**viewimports**</span></span>

<span data-ttu-id="6c49f-313">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-313">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="6c49f-314">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-314">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6c49f-315">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6c49f-315">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="6c49f-316">**console, xunit, mstest, web, webapi** </span><span class="sxs-lookup"><span data-stu-id="6c49f-316">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="6c49f-317">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="6c49f-317">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c49f-318">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-318">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="6c49f-319">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-319">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="6c49f-320">**classlib**</span><span class="sxs-lookup"><span data-stu-id="6c49f-320">**classlib**</span></span>

<span data-ttu-id="6c49f-321">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="6c49f-321">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c49f-322">Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-322">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="6c49f-323">O valor padrão é `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-323">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="6c49f-324">**mvc**</span><span class="sxs-lookup"><span data-stu-id="6c49f-324">**mvc**</span></span>

<span data-ttu-id="6c49f-325">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="6c49f-325">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6c49f-326">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-326">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="6c49f-327">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-327">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="6c49f-328">`-au|--auth` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="6c49f-328">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="6c49f-329">Valores: `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-329">Values: `None` or `Individual`.</span></span> <span data-ttu-id="6c49f-330">O valor padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-330">The default value is `None`.</span></span>

<span data-ttu-id="6c49f-331">`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="6c49f-331">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="6c49f-332">Valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-332">Values: `true` or `false`.</span></span> <span data-ttu-id="6c49f-333">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="6c49f-333">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="6c49f-334">Exemplos</span><span class="sxs-lookup"><span data-stu-id="6c49f-334">Examples</span></span>

<span data-ttu-id="6c49f-335">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="6c49f-335">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="6c49f-336">Crie um projeto de biblioteca de classes do .NET Standard no diretório especificado (disponível somente com o SDK do .NET Core 2.0 ou versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="6c49f-336">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="6c49f-337">Crie um novo projeto de aplicativo de MVC C# do ASP.NET Core no diretório atual sem autenticação direcionando o .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="6c49f-337">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="6c49f-338">Crie um novo aplicativo xUnit direcionando o .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="6c49f-338">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="6c49f-339">Lista todos os modelos disponíveis para o MVC:</span><span class="sxs-lookup"><span data-stu-id="6c49f-339">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="6c49f-340">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c49f-340">See also</span></span>

[<span data-ttu-id="6c49f-341">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="6c49f-341">Custom templates for dotnet new</span></span>](custom-templates.md)  
<span data-ttu-id="6c49f-342">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="6c49f-342">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md)</span></span>  
[<span data-ttu-id="6c49f-343">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="6c49f-343">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="6c49f-344">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="6c49f-344">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
