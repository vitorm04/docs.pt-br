---
title: Comando dotnet new – CLI do .NET Core
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
author: mairaw
ms.author: mairaw
ms.date: 06/12/2018
ms.openlocfilehash: f0ef91361dfbc2c2ba5532fbd607786289e98c69
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207751"
---
# <a name="dotnet-new"></a><span data-ttu-id="d262a-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d262a-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d262a-104">Nome</span><span class="sxs-lookup"><span data-stu-id="d262a-104">Name</span></span>

<span data-ttu-id="d262a-105">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="d262a-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d262a-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="d262a-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d262a-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d262a-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d262a-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d262a-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d262a-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d262a-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="d262a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d262a-110">Description</span></span>

<span data-ttu-id="d262a-111">O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido.</span><span class="sxs-lookup"><span data-stu-id="d262a-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="d262a-112">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="d262a-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="d262a-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="d262a-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="d262a-114">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="d262a-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="d262a-115">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="d262a-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="d262a-116">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="d262a-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d262a-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d262a-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="d262a-118">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="d262a-118">The command contains a default list of templates.</span></span> <span data-ttu-id="d262a-119">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d262a-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="d262a-120">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="d262a-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="d262a-121">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="d262a-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="d262a-122">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="d262a-122">Template description</span></span>                          | <span data-ttu-id="d262a-123">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="d262a-123">Template name</span></span>   | <span data-ttu-id="d262a-124">Linguagens</span><span class="sxs-lookup"><span data-stu-id="d262a-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="d262a-125">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="d262a-125">Console application</span></span>                          | `console`       | <span data-ttu-id="d262a-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d262a-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="d262a-127">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="d262a-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="d262a-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d262a-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="d262a-129">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="d262a-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="d262a-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d262a-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="d262a-131">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="d262a-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="d262a-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d262a-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="d262a-133">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="d262a-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="d262a-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="d262a-134">[C#]</span></span>          |
| <span data-ttu-id="d262a-135">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="d262a-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="d262a-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="d262a-136">[C#]</span></span>          |
| <span data-ttu-id="d262a-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="d262a-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="d262a-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="d262a-138">[C#]</span></span>          |
| <span data-ttu-id="d262a-139">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="d262a-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="d262a-140">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d262a-140">[C#], F#</span></span>      |
| <span data-ttu-id="d262a-141">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="d262a-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="d262a-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d262a-142">[C#], F#</span></span>      |
| <span data-ttu-id="d262a-143">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d262a-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="d262a-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="d262a-144">[C#]</span></span>          |
| <span data-ttu-id="d262a-145">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="d262a-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="d262a-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="d262a-146">[C#]</span></span>          |
| <span data-ttu-id="d262a-147">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="d262a-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="d262a-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="d262a-148">[C#]</span></span>          |
| <span data-ttu-id="d262a-149">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="d262a-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="d262a-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="d262a-150">[C#]</span></span>          |
| <span data-ttu-id="d262a-151">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d262a-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="d262a-152">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d262a-152">[C#], F#</span></span>      |
| <span data-ttu-id="d262a-153">Biblioteca de classes Razor</span><span class="sxs-lookup"><span data-stu-id="d262a-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="d262a-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="d262a-154">[C#]</span></span>          |
| <span data-ttu-id="d262a-155">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="d262a-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="d262a-156">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="d262a-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="d262a-157">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="d262a-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="d262a-158">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="d262a-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d262a-159">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d262a-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="d262a-160">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="d262a-160">The command contains a default list of templates.</span></span> <span data-ttu-id="d262a-161">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d262a-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="d262a-162">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="d262a-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="d262a-163">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="d262a-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="d262a-164">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="d262a-164">Template description</span></span>                          | <span data-ttu-id="d262a-165">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="d262a-165">Template name</span></span> | <span data-ttu-id="d262a-166">Linguagens</span><span class="sxs-lookup"><span data-stu-id="d262a-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="d262a-167">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="d262a-167">Console application</span></span>                          | `console`     | <span data-ttu-id="d262a-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d262a-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="d262a-169">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="d262a-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="d262a-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d262a-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="d262a-171">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="d262a-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="d262a-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d262a-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="d262a-173">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="d262a-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="d262a-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d262a-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="d262a-175">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="d262a-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="d262a-176">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d262a-176">[C#], F#</span></span>      |
| <span data-ttu-id="d262a-177">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="d262a-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="d262a-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d262a-178">[C#], F#</span></span>      |
| <span data-ttu-id="d262a-179">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d262a-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="d262a-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="d262a-180">[C#]</span></span>          |
| <span data-ttu-id="d262a-181">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="d262a-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="d262a-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="d262a-182">[C#]</span></span>          |
| <span data-ttu-id="d262a-183">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="d262a-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="d262a-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="d262a-184">[C#]</span></span>          |
| <span data-ttu-id="d262a-185">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="d262a-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="d262a-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="d262a-186">[C#]</span></span>          |
| <span data-ttu-id="d262a-187">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d262a-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="d262a-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d262a-188">[C#], F#</span></span>      |
| <span data-ttu-id="d262a-189">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="d262a-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="d262a-190">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="d262a-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="d262a-191">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="d262a-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="d262a-192">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="d262a-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="d262a-193">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="d262a-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="d262a-194">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="d262a-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="d262a-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="d262a-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d262a-196">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d262a-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="d262a-197">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="d262a-197">The command contains a default list of templates.</span></span> <span data-ttu-id="d262a-198">Use `dotnet new -all` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d262a-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="d262a-199">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="d262a-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="d262a-200">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="d262a-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="d262a-201">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="d262a-201">Template description</span></span>  | <span data-ttu-id="d262a-202">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="d262a-202">Template name</span></span> | <span data-ttu-id="d262a-203">Linguagens</span><span class="sxs-lookup"><span data-stu-id="d262a-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="d262a-204">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="d262a-204">Console application</span></span>  | `console`     | <span data-ttu-id="d262a-205">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d262a-205">[C#], F#</span></span>  |
| <span data-ttu-id="d262a-206">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="d262a-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="d262a-207">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d262a-207">[C#], F#</span></span>  |
| <span data-ttu-id="d262a-208">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="d262a-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="d262a-209">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d262a-209">[C#], F#</span></span>  |
| <span data-ttu-id="d262a-210">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="d262a-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="d262a-211">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d262a-211">[C#], F#</span></span>  |
| <span data-ttu-id="d262a-212">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="d262a-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="d262a-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="d262a-213">[C#]</span></span>      |
| <span data-ttu-id="d262a-214">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d262a-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="d262a-215">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d262a-215">[C#], F#</span></span>  |
| <span data-ttu-id="d262a-216">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d262a-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="d262a-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="d262a-217">[C#]</span></span>      |
| <span data-ttu-id="d262a-218">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="d262a-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="d262a-219">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="d262a-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="d262a-220">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="d262a-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="d262a-221">Opções</span><span class="sxs-lookup"><span data-stu-id="d262a-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d262a-222">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d262a-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="d262a-223">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="d262a-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="d262a-224">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="d262a-225">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="d262a-225">Prints out help for the command.</span></span> <span data-ttu-id="d262a-226">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="d262a-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="d262a-227">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="d262a-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="d262a-228">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="d262a-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="d262a-229">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="d262a-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="d262a-230">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="d262a-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="d262a-231">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="d262a-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="d262a-232">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="d262a-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="d262a-233">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="d262a-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="d262a-234">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="d262a-235">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="d262a-235">The language of the template to create.</span></span> <span data-ttu-id="d262a-236">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="d262a-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="d262a-237">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="d262a-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="d262a-238">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="d262a-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="d262a-239">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="d262a-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="d262a-240">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="d262a-240">The name for the created output.</span></span> <span data-ttu-id="d262a-241">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="d262a-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="d262a-242">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="d262a-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d262a-243">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="d262a-243">Location to place the generated output.</span></span> <span data-ttu-id="d262a-244">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="d262a-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="d262a-245">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d262a-245">Filters templates based on available types.</span></span> <span data-ttu-id="d262a-246">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="d262a-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="d262a-247">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="d262a-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="d262a-248">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="d262a-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="d262a-249">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="d262a-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="d262a-250">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="d262a-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d262a-251">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d262a-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="d262a-252">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="d262a-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="d262a-253">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="d262a-254">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="d262a-254">Prints out help for the command.</span></span> <span data-ttu-id="d262a-255">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="d262a-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="d262a-256">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="d262a-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="d262a-257">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="d262a-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="d262a-258">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="d262a-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="d262a-259">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="d262a-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="d262a-260">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="d262a-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="d262a-261">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="d262a-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="d262a-262">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="d262a-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="d262a-263">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="d262a-264">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="d262a-264">The language of the template to create.</span></span> <span data-ttu-id="d262a-265">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="d262a-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="d262a-266">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="d262a-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="d262a-267">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="d262a-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="d262a-268">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="d262a-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="d262a-269">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="d262a-269">The name for the created output.</span></span> <span data-ttu-id="d262a-270">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="d262a-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d262a-271">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="d262a-271">Location to place the generated output.</span></span> <span data-ttu-id="d262a-272">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="d262a-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="d262a-273">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d262a-273">Filters templates based on available types.</span></span> <span data-ttu-id="d262a-274">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="d262a-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="d262a-275">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="d262a-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="d262a-276">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="d262a-276">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="d262a-277">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="d262a-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="d262a-278">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="d262a-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d262a-279">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d262a-279">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="d262a-280">Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado.</span><span class="sxs-lookup"><span data-stu-id="d262a-280">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="d262a-281">Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força.</span><span class="sxs-lookup"><span data-stu-id="d262a-281">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="d262a-282">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-282">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="d262a-283">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="d262a-283">Prints out help for the command.</span></span> <span data-ttu-id="d262a-284">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="d262a-284">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="d262a-285">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="d262a-285">Lists templates containing the specified name.</span></span> <span data-ttu-id="d262a-286">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="d262a-286">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="d262a-287">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-287">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="d262a-288">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="d262a-288">The language of the template to create.</span></span> <span data-ttu-id="d262a-289">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="d262a-289">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="d262a-290">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="d262a-290">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="d262a-291">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="d262a-291">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="d262a-292">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="d262a-292">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="d262a-293">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="d262a-293">The name for the created output.</span></span> <span data-ttu-id="d262a-294">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="d262a-294">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d262a-295">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="d262a-295">Location to place the generated output.</span></span> <span data-ttu-id="d262a-296">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="d262a-296">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="d262a-297">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="d262a-297">Template options</span></span>

<span data-ttu-id="d262a-298">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d262a-298">Each project template may have additional options available.</span></span> <span data-ttu-id="d262a-299">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="d262a-299">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d262a-300">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d262a-300">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="d262a-301">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="d262a-301">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="d262a-302">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-302">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="d262a-303">**classlib**</span><span class="sxs-lookup"><span data-stu-id="d262a-303">**classlib**</span></span>

<span data-ttu-id="d262a-304">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="d262a-304">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d262a-305">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d262a-305">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="d262a-306">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="d262a-306">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="d262a-307">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-307">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="d262a-308">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="d262a-308">**mstest, xunit**</span></span>

<span data-ttu-id="d262a-309">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="d262a-309">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="d262a-310">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-310">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="d262a-311">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="d262a-311">**globaljson**</span></span>

<span data-ttu-id="d262a-312">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="d262a-312">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="d262a-313">**web**</span><span class="sxs-lookup"><span data-stu-id="d262a-313">**web**</span></span>

<span data-ttu-id="d262a-314">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d262a-314">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="d262a-315">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-315">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="d262a-316">**webapi**</span><span class="sxs-lookup"><span data-stu-id="d262a-316">**webapi**</span></span>

<span data-ttu-id="d262a-317">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="d262a-317">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="d262a-318">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="d262a-318">The possible values are:</span></span>

- <span data-ttu-id="d262a-319">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="d262a-319">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="d262a-320">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="d262a-320">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="d262a-321">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="d262a-321">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="d262a-322">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="d262a-322">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="d262a-323">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d262a-323">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d262a-324">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-324">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d262a-325">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="d262a-325">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="d262a-326">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-326">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d262a-327">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-327">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d262a-328">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d262a-328">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d262a-329">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d262a-329">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d262a-330">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="d262a-330">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="d262a-331">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-331">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="d262a-332">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d262a-332">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="d262a-333">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="d262a-333">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="d262a-334">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="d262a-334">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="d262a-335">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-335">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d262a-336">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="d262a-336">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="d262a-337">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d262a-337">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d262a-338">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d262a-338">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d262a-339">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="d262a-339">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="d262a-340">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="d262a-340">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="d262a-341">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d262a-341">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="d262a-342">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d262a-342">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="d262a-343">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="d262a-343">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d262a-344">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-344">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d262a-345">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-345">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="d262a-346">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="d262a-346">**mvc, razor**</span></span>

<span data-ttu-id="d262a-347">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="d262a-347">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="d262a-348">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="d262a-348">The possible values are:</span></span>

- <span data-ttu-id="d262a-349">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="d262a-349">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="d262a-350">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="d262a-350">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="d262a-351">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="d262a-351">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="d262a-352">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="d262a-352">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="d262a-353">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="d262a-353">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="d262a-354">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="d262a-354">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="d262a-355">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d262a-355">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d262a-356">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-356">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d262a-357">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="d262a-357">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="d262a-358">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-358">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d262a-359">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-359">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d262a-360">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-360">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="d262a-361">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-361">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d262a-362">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-362">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="d262a-363">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-363">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d262a-364">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d262a-364">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d262a-365">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d262a-365">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="d262a-366">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="d262a-366">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="d262a-367">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-367">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="d262a-368">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d262a-368">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="d262a-369">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="d262a-369">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="d262a-370">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="d262a-370">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="d262a-371">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-371">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d262a-372">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="d262a-372">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="d262a-373">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d262a-373">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d262a-374">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d262a-374">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d262a-375">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="d262a-375">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="d262a-376">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="d262a-376">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="d262a-377">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-377">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d262a-378">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="d262a-378">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="d262a-379">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="d262a-379">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="d262a-380">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d262a-380">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="d262a-381">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d262a-381">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="d262a-382">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-382">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="d262a-383">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="d262a-383">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d262a-384">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-384">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d262a-385">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-385">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="d262a-386">**page**</span><span class="sxs-lookup"><span data-stu-id="d262a-386">**page**</span></span>

<span data-ttu-id="d262a-387">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="d262a-387">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="d262a-388">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="d262a-388">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="d262a-389">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="d262a-389">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="d262a-390">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="d262a-390">**viewimports**</span></span>

<span data-ttu-id="d262a-391">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="d262a-391">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="d262a-392">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="d262a-392">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d262a-393">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d262a-393">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="d262a-394">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="d262a-394">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="d262a-395">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-395">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="d262a-396">**classlib**</span><span class="sxs-lookup"><span data-stu-id="d262a-396">**classlib**</span></span>

<span data-ttu-id="d262a-397">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="d262a-397">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d262a-398">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d262a-398">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="d262a-399">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="d262a-399">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="d262a-400">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-400">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="d262a-401">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="d262a-401">**mstest, xunit**</span></span>

<span data-ttu-id="d262a-402">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="d262a-402">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="d262a-403">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-403">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="d262a-404">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="d262a-404">**globaljson**</span></span>

<span data-ttu-id="d262a-405">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="d262a-405">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="d262a-406">**web**</span><span class="sxs-lookup"><span data-stu-id="d262a-406">**web**</span></span>

<span data-ttu-id="d262a-407">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d262a-407">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="d262a-408">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-408">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="d262a-409">**webapi**</span><span class="sxs-lookup"><span data-stu-id="d262a-409">**webapi**</span></span>

<span data-ttu-id="d262a-410">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="d262a-410">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="d262a-411">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="d262a-411">The possible values are:</span></span>

- <span data-ttu-id="d262a-412">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="d262a-412">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="d262a-413">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="d262a-413">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="d262a-414">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="d262a-414">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="d262a-415">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="d262a-415">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="d262a-416">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d262a-416">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d262a-417">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-417">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d262a-418">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="d262a-418">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="d262a-419">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-419">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d262a-420">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-420">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d262a-421">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d262a-421">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d262a-422">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d262a-422">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d262a-423">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="d262a-423">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="d262a-424">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-424">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="d262a-425">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d262a-425">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="d262a-426">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="d262a-426">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="d262a-427">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="d262a-427">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="d262a-428">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-428">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d262a-429">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="d262a-429">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="d262a-430">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d262a-430">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d262a-431">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d262a-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d262a-432">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="d262a-432">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="d262a-433">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="d262a-433">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="d262a-434">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d262a-434">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="d262a-435">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d262a-435">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="d262a-436">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="d262a-436">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d262a-437">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-437">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d262a-438">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-438">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="d262a-439">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="d262a-439">**mvc, razor**</span></span>

<span data-ttu-id="d262a-440">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="d262a-440">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="d262a-441">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="d262a-441">The possible values are:</span></span>

- <span data-ttu-id="d262a-442">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="d262a-442">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="d262a-443">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="d262a-443">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="d262a-444">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="d262a-444">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="d262a-445">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="d262a-445">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="d262a-446">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="d262a-446">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="d262a-447">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="d262a-447">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="d262a-448">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d262a-448">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d262a-449">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-449">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d262a-450">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="d262a-450">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="d262a-451">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-451">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d262a-452">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-452">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d262a-453">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-453">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="d262a-454">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-454">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d262a-455">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-455">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="d262a-456">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-456">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d262a-457">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d262a-457">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d262a-458">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d262a-458">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="d262a-459">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="d262a-459">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="d262a-460">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-460">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="d262a-461">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d262a-461">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="d262a-462">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="d262a-462">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="d262a-463">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="d262a-463">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="d262a-464">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-464">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d262a-465">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="d262a-465">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="d262a-466">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="d262a-466">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d262a-467">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d262a-467">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d262a-468">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="d262a-468">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="d262a-469">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="d262a-469">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="d262a-470">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-470">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d262a-471">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="d262a-471">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="d262a-472">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="d262a-472">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="d262a-473">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d262a-473">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="d262a-474">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d262a-474">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="d262a-475">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-475">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="d262a-476">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="d262a-476">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d262a-477">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d262a-477">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="d262a-478">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d262a-478">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="d262a-479">**page**</span><span class="sxs-lookup"><span data-stu-id="d262a-479">**page**</span></span>

<span data-ttu-id="d262a-480">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="d262a-480">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="d262a-481">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="d262a-481">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="d262a-482">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="d262a-482">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="d262a-483">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="d262a-483">**viewimports**</span></span>

<span data-ttu-id="d262a-484">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="d262a-484">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="d262a-485">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="d262a-485">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d262a-486">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d262a-486">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="d262a-487">**console, xunit, mstest, web, webapi** </span><span class="sxs-lookup"><span data-stu-id="d262a-487">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="d262a-488">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="d262a-488">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d262a-489">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="d262a-489">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="d262a-490">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="d262a-490">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="d262a-491">**classlib**</span><span class="sxs-lookup"><span data-stu-id="d262a-491">**classlib**</span></span>

<span data-ttu-id="d262a-492">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="d262a-492">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d262a-493">Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="d262a-493">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="d262a-494">O valor padrão é `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="d262a-494">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="d262a-495">**mvc**</span><span class="sxs-lookup"><span data-stu-id="d262a-495">**mvc**</span></span>

<span data-ttu-id="d262a-496">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="d262a-496">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d262a-497">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="d262a-497">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="d262a-498">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="d262a-498">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="d262a-499">`-au|--auth` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="d262a-499">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="d262a-500">Valores: `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="d262a-500">Values: `None` or `Individual`.</span></span> <span data-ttu-id="d262a-501">O valor padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="d262a-501">The default value is `None`.</span></span>

<span data-ttu-id="d262a-502">`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="d262a-502">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="d262a-503">Valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="d262a-503">Values: `true` or `false`.</span></span> <span data-ttu-id="d262a-504">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="d262a-504">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="d262a-505">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d262a-505">Examples</span></span>

<span data-ttu-id="d262a-506">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="d262a-506">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="d262a-507">Crie um projeto de biblioteca de classes .NET Standard no diretório especificado (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="d262a-507">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="d262a-508">Crie um novo projeto de aplicativo de MVC C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="d262a-508">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="d262a-509">Crie um novo aplicativo xUnit:</span><span class="sxs-lookup"><span data-stu-id="d262a-509">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="d262a-510">Lista todos os modelos disponíveis para o MVC:</span><span class="sxs-lookup"><span data-stu-id="d262a-510">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="d262a-511">Instale a versão 2.0 dos modelos de aplicativo de página única do ASP.NET Core (opção de comando disponível somente para o SDK do .NET Core 1.1 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="d262a-511">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="d262a-512">Crie um *global.json* no diretório atual definindo a versão do SDK como 2.0.0 (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="d262a-512">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="d262a-513">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d262a-513">See also</span></span>

[<span data-ttu-id="d262a-514">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="d262a-514">Custom templates for dotnet new</span></span>](custom-templates.md)  
<span data-ttu-id="d262a-515">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="d262a-515">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md)</span></span>  
[<span data-ttu-id="d262a-516">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="d262a-516">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="d262a-517">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="d262a-517">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
