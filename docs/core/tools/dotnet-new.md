---
title: Comando dotnet new – CLI do .NET Core
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: ae24c4145cc67ca863c07e4d22af8a1c2c2dd732
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34570457"
---
# <a name="dotnet-new"></a><span data-ttu-id="8a3cc-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="8a3cc-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="8a3cc-104">Nome</span><span class="sxs-lookup"><span data-stu-id="8a3cc-104">Name</span></span>

<span data-ttu-id="8a3cc-105">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8a3cc-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="8a3cc-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8a3cc-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8a3cc-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8a3cc-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8a3cc-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8a3cc-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8a3cc-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="8a3cc-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a3cc-110">Description</span></span>

<span data-ttu-id="8a3cc-111">O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="8a3cc-112">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="8a3cc-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="8a3cc-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="8a3cc-114">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="8a3cc-115">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="8a3cc-116">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="8a3cc-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8a3cc-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8a3cc-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="8a3cc-118">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-118">The command contains a default list of templates.</span></span> <span data-ttu-id="8a3cc-119">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="8a3cc-120">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="8a3cc-121">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="8a3cc-122">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="8a3cc-122">Template description</span></span>                          | <span data-ttu-id="8a3cc-123">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="8a3cc-123">Template name</span></span>   | <span data-ttu-id="8a3cc-124">Linguagens</span><span class="sxs-lookup"><span data-stu-id="8a3cc-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="8a3cc-125">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="8a3cc-125">Console application</span></span>                          | `console`       | <span data-ttu-id="8a3cc-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8a3cc-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8a3cc-127">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="8a3cc-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="8a3cc-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8a3cc-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8a3cc-129">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="8a3cc-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="8a3cc-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8a3cc-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8a3cc-131">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="8a3cc-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="8a3cc-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8a3cc-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8a3cc-133">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="8a3cc-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="8a3cc-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="8a3cc-134">[C#]</span></span>          |
| <span data-ttu-id="8a3cc-135">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="8a3cc-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="8a3cc-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="8a3cc-136">[C#]</span></span>          |
| <span data-ttu-id="8a3cc-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="8a3cc-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="8a3cc-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="8a3cc-138">[C#]</span></span>          |
| <span data-ttu-id="8a3cc-139">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="8a3cc-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="8a3cc-140">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8a3cc-140">[C#], F#</span></span>      |
| <span data-ttu-id="8a3cc-141">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="8a3cc-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="8a3cc-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8a3cc-142">[C#], F#</span></span>      |
| <span data-ttu-id="8a3cc-143">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8a3cc-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="8a3cc-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="8a3cc-144">[C#]</span></span>          |
| <span data-ttu-id="8a3cc-145">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="8a3cc-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="8a3cc-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="8a3cc-146">[C#]</span></span>          |
| <span data-ttu-id="8a3cc-147">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="8a3cc-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="8a3cc-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="8a3cc-148">[C#]</span></span>          |
| <span data-ttu-id="8a3cc-149">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="8a3cc-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="8a3cc-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="8a3cc-150">[C#]</span></span>          |
| <span data-ttu-id="8a3cc-151">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8a3cc-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="8a3cc-152">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8a3cc-152">[C#], F#</span></span>      |
| <span data-ttu-id="8a3cc-153">Biblioteca de classes Razor</span><span class="sxs-lookup"><span data-stu-id="8a3cc-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="8a3cc-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="8a3cc-154">[C#]</span></span>          |
| <span data-ttu-id="8a3cc-155">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="8a3cc-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="8a3cc-156">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="8a3cc-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="8a3cc-157">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="8a3cc-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="8a3cc-158">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="8a3cc-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8a3cc-159">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8a3cc-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="8a3cc-160">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-160">The command contains a default list of templates.</span></span> <span data-ttu-id="8a3cc-161">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="8a3cc-162">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="8a3cc-163">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="8a3cc-164">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="8a3cc-164">Template description</span></span>                          | <span data-ttu-id="8a3cc-165">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="8a3cc-165">Template name</span></span> | <span data-ttu-id="8a3cc-166">Linguagens</span><span class="sxs-lookup"><span data-stu-id="8a3cc-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="8a3cc-167">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="8a3cc-167">Console application</span></span>                          | `console`     | <span data-ttu-id="8a3cc-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8a3cc-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8a3cc-169">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="8a3cc-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="8a3cc-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8a3cc-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8a3cc-171">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="8a3cc-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="8a3cc-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8a3cc-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8a3cc-173">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="8a3cc-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="8a3cc-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8a3cc-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8a3cc-175">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="8a3cc-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="8a3cc-176">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8a3cc-176">[C#], F#</span></span>      |
| <span data-ttu-id="8a3cc-177">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="8a3cc-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="8a3cc-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8a3cc-178">[C#], F#</span></span>      |
| <span data-ttu-id="8a3cc-179">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8a3cc-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="8a3cc-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="8a3cc-180">[C#]</span></span>          |
| <span data-ttu-id="8a3cc-181">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="8a3cc-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="8a3cc-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="8a3cc-182">[C#]</span></span>          |
| <span data-ttu-id="8a3cc-183">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="8a3cc-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="8a3cc-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="8a3cc-184">[C#]</span></span>          |
| <span data-ttu-id="8a3cc-185">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="8a3cc-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="8a3cc-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="8a3cc-186">[C#]</span></span>          |
| <span data-ttu-id="8a3cc-187">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8a3cc-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="8a3cc-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8a3cc-188">[C#], F#</span></span>      |
| <span data-ttu-id="8a3cc-189">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="8a3cc-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="8a3cc-190">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="8a3cc-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="8a3cc-191">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="8a3cc-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="8a3cc-192">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="8a3cc-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="8a3cc-193">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="8a3cc-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="8a3cc-194">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="8a3cc-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="8a3cc-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="8a3cc-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8a3cc-196">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8a3cc-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="8a3cc-197">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-197">The command contains a default list of templates.</span></span> <span data-ttu-id="8a3cc-198">Use `dotnet new -all` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="8a3cc-199">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="8a3cc-200">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="8a3cc-201">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="8a3cc-201">Template description</span></span>  | <span data-ttu-id="8a3cc-202">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="8a3cc-202">Template name</span></span> | <span data-ttu-id="8a3cc-203">Linguagens</span><span class="sxs-lookup"><span data-stu-id="8a3cc-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="8a3cc-204">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="8a3cc-204">Console application</span></span>  | `console`     | <span data-ttu-id="8a3cc-205">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8a3cc-205">[C#], F#</span></span>  |
| <span data-ttu-id="8a3cc-206">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="8a3cc-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="8a3cc-207">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8a3cc-207">[C#], F#</span></span>  |
| <span data-ttu-id="8a3cc-208">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="8a3cc-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="8a3cc-209">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8a3cc-209">[C#], F#</span></span>  |
| <span data-ttu-id="8a3cc-210">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="8a3cc-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="8a3cc-211">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8a3cc-211">[C#], F#</span></span>  |
| <span data-ttu-id="8a3cc-212">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="8a3cc-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="8a3cc-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="8a3cc-213">[C#]</span></span>      |
| <span data-ttu-id="8a3cc-214">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8a3cc-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="8a3cc-215">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8a3cc-215">[C#], F#</span></span>  |
| <span data-ttu-id="8a3cc-216">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8a3cc-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="8a3cc-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="8a3cc-217">[C#]</span></span>      |
| <span data-ttu-id="8a3cc-218">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="8a3cc-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="8a3cc-219">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="8a3cc-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="8a3cc-220">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="8a3cc-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="8a3cc-221">Opções</span><span class="sxs-lookup"><span data-stu-id="8a3cc-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8a3cc-222">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8a3cc-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="8a3cc-223">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="8a3cc-224">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="8a3cc-225">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-225">Prints out help for the command.</span></span> <span data-ttu-id="8a3cc-226">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="8a3cc-227">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="8a3cc-228">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="8a3cc-229">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="8a3cc-230">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="8a3cc-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="8a3cc-231">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="8a3cc-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="8a3cc-232">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="8a3cc-233">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="8a3cc-234">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="8a3cc-235">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-235">The language of the template to create.</span></span> <span data-ttu-id="8a3cc-236">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="8a3cc-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="8a3cc-237">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-237">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="8a3cc-238">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-238">The name for the created output.</span></span> <span data-ttu-id="8a3cc-239">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-239">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="8a3cc-240">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-240">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="8a3cc-241">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-241">Location to place the generated output.</span></span> <span data-ttu-id="8a3cc-242">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-242">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="8a3cc-243">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-243">Filters templates based on available types.</span></span> <span data-ttu-id="8a3cc-244">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="8a3cc-244">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="8a3cc-245">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-245">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="8a3cc-246">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-246">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="8a3cc-247">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-247">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="8a3cc-248">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-248">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8a3cc-249">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8a3cc-249">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="8a3cc-250">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-250">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="8a3cc-251">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-251">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="8a3cc-252">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-252">Prints out help for the command.</span></span> <span data-ttu-id="8a3cc-253">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-253">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="8a3cc-254">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-254">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="8a3cc-255">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-255">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="8a3cc-256">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-256">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="8a3cc-257">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="8a3cc-257">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="8a3cc-258">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="8a3cc-258">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="8a3cc-259">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-259">Lists templates containing the specified name.</span></span> <span data-ttu-id="8a3cc-260">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-260">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="8a3cc-261">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-261">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="8a3cc-262">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-262">The language of the template to create.</span></span> <span data-ttu-id="8a3cc-263">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="8a3cc-263">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="8a3cc-264">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-264">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="8a3cc-265">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-265">The name for the created output.</span></span> <span data-ttu-id="8a3cc-266">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-266">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="8a3cc-267">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-267">Location to place the generated output.</span></span> <span data-ttu-id="8a3cc-268">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-268">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="8a3cc-269">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-269">Filters templates based on available types.</span></span> <span data-ttu-id="8a3cc-270">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="8a3cc-270">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="8a3cc-271">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-271">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="8a3cc-272">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-272">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="8a3cc-273">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-273">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="8a3cc-274">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-274">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8a3cc-275">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8a3cc-275">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="8a3cc-276">Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-276">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="8a3cc-277">Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-277">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="8a3cc-278">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-278">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="8a3cc-279">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-279">Prints out help for the command.</span></span> <span data-ttu-id="8a3cc-280">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-280">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="8a3cc-281">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-281">Lists templates containing the specified name.</span></span> <span data-ttu-id="8a3cc-282">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-282">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="8a3cc-283">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-283">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="8a3cc-284">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-284">The language of the template to create.</span></span> <span data-ttu-id="8a3cc-285">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="8a3cc-285">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="8a3cc-286">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-286">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="8a3cc-287">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-287">The name for the created output.</span></span> <span data-ttu-id="8a3cc-288">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-288">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="8a3cc-289">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-289">Location to place the generated output.</span></span> <span data-ttu-id="8a3cc-290">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-290">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="8a3cc-291">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="8a3cc-291">Template options</span></span>

<span data-ttu-id="8a3cc-292">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-292">Each project template may have additional options available.</span></span> <span data-ttu-id="8a3cc-293">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="8a3cc-293">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8a3cc-294">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8a3cc-294">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="8a3cc-295">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-295">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="8a3cc-296">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-296">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8a3cc-297">**classlib**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-297">**classlib**</span></span>

<span data-ttu-id="8a3cc-298">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-298">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8a3cc-299">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-299">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="8a3cc-300">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-300">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="8a3cc-301">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-301">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8a3cc-302">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-302">**mstest, xunit**</span></span>

<span data-ttu-id="8a3cc-303">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="8a3cc-303">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="8a3cc-304">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-304">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8a3cc-305">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-305">**globaljson**</span></span>

<span data-ttu-id="8a3cc-306">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-306">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="8a3cc-307">**web**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-307">**web**</span></span>

<span data-ttu-id="8a3cc-308">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-308">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8a3cc-309">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-309">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8a3cc-310">**webapi**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-310">**webapi**</span></span>

<span data-ttu-id="8a3cc-311">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-311">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="8a3cc-312">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="8a3cc-312">The possible values are:</span></span>

- <span data-ttu-id="8a3cc-313">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="8a3cc-313">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="8a3cc-314">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-314">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="8a3cc-315">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-315">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="8a3cc-316">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-316">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="8a3cc-317">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-317">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8a3cc-318">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-318">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8a3cc-319">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-319">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="8a3cc-320">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-320">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8a3cc-321">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-321">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8a3cc-322">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-322">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8a3cc-323">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-323">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8a3cc-324">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-324">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="8a3cc-325">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-325">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="8a3cc-326">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-326">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="8a3cc-327">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-327">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="8a3cc-328">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-328">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="8a3cc-329">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-329">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8a3cc-330">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-330">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="8a3cc-331">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-331">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8a3cc-332">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-332">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8a3cc-333">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-333">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="8a3cc-334">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-334">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="8a3cc-335">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-335">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="8a3cc-336">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-336">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8a3cc-337">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-337">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8a3cc-338">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-338">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8a3cc-339">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-339">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8a3cc-340">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-340">**mvc, razor**</span></span>

<span data-ttu-id="8a3cc-341">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-341">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="8a3cc-342">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="8a3cc-342">The possible values are:</span></span>

- <span data-ttu-id="8a3cc-343">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="8a3cc-343">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="8a3cc-344">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-344">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="8a3cc-345">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-345">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="8a3cc-346">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-346">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="8a3cc-347">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-347">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="8a3cc-348">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-348">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="8a3cc-349">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-349">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8a3cc-350">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-350">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8a3cc-351">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-351">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="8a3cc-352">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-352">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8a3cc-353">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-353">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8a3cc-354">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-354">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="8a3cc-355">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-355">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8a3cc-356">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-356">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="8a3cc-357">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-357">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8a3cc-358">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-358">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8a3cc-359">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-359">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="8a3cc-360">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-360">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="8a3cc-361">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-361">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="8a3cc-362">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-362">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="8a3cc-363">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-363">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="8a3cc-364">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-364">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="8a3cc-365">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-365">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8a3cc-366">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-366">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="8a3cc-367">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-367">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8a3cc-368">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-368">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8a3cc-369">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-369">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="8a3cc-370">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-370">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="8a3cc-371">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-371">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8a3cc-372">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-372">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="8a3cc-373">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-373">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="8a3cc-374">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-374">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="8a3cc-375">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-375">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8a3cc-376">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-376">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="8a3cc-377">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-377">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8a3cc-378">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-378">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8a3cc-379">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-379">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8a3cc-380">**page**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-380">**page**</span></span>

<span data-ttu-id="8a3cc-381">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-381">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="8a3cc-382">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-382">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="8a3cc-383">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-383">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="8a3cc-384">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-384">**viewimports**</span></span>

<span data-ttu-id="8a3cc-385">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-385">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="8a3cc-386">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-386">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8a3cc-387">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8a3cc-387">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="8a3cc-388">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-388">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="8a3cc-389">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-389">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8a3cc-390">**classlib**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-390">**classlib**</span></span>

<span data-ttu-id="8a3cc-391">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-391">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8a3cc-392">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-392">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="8a3cc-393">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-393">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="8a3cc-394">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-394">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8a3cc-395">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-395">**mstest, xunit**</span></span>

<span data-ttu-id="8a3cc-396">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="8a3cc-396">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="8a3cc-397">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-397">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8a3cc-398">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-398">**globaljson**</span></span>

<span data-ttu-id="8a3cc-399">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-399">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="8a3cc-400">**web**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-400">**web**</span></span>

<span data-ttu-id="8a3cc-401">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-401">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8a3cc-402">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-402">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8a3cc-403">**webapi**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-403">**webapi**</span></span>

<span data-ttu-id="8a3cc-404">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-404">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="8a3cc-405">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="8a3cc-405">The possible values are:</span></span>

- <span data-ttu-id="8a3cc-406">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="8a3cc-406">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="8a3cc-407">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="8a3cc-408">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="8a3cc-409">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-409">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="8a3cc-410">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-410">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8a3cc-411">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-411">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8a3cc-412">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-412">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="8a3cc-413">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-413">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8a3cc-414">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-414">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8a3cc-415">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-415">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8a3cc-416">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-416">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8a3cc-417">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-417">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="8a3cc-418">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-418">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="8a3cc-419">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-419">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="8a3cc-420">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-420">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="8a3cc-421">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-421">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="8a3cc-422">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-422">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8a3cc-423">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-423">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="8a3cc-424">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-424">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8a3cc-425">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-425">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8a3cc-426">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-426">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="8a3cc-427">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-427">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="8a3cc-428">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-428">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="8a3cc-429">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-429">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8a3cc-430">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-430">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8a3cc-431">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-431">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8a3cc-432">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-432">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8a3cc-433">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-433">**mvc, razor**</span></span>

<span data-ttu-id="8a3cc-434">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-434">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="8a3cc-435">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="8a3cc-435">The possible values are:</span></span>

- <span data-ttu-id="8a3cc-436">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="8a3cc-436">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="8a3cc-437">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-437">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="8a3cc-438">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-438">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="8a3cc-439">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-439">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="8a3cc-440">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-440">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="8a3cc-441">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-441">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="8a3cc-442">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-442">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8a3cc-443">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-443">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8a3cc-444">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-444">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="8a3cc-445">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-445">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8a3cc-446">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-446">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8a3cc-447">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-447">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="8a3cc-448">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-448">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8a3cc-449">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-449">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="8a3cc-450">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-450">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8a3cc-451">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-451">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8a3cc-452">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-452">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="8a3cc-453">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-453">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="8a3cc-454">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-454">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="8a3cc-455">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-455">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="8a3cc-456">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-456">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="8a3cc-457">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-457">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="8a3cc-458">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-458">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8a3cc-459">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-459">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="8a3cc-460">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-460">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8a3cc-461">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-461">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8a3cc-462">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-462">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="8a3cc-463">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-463">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="8a3cc-464">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-464">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8a3cc-465">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-465">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="8a3cc-466">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-466">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="8a3cc-467">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-467">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="8a3cc-468">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-468">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8a3cc-469">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-469">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="8a3cc-470">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-470">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8a3cc-471">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-471">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8a3cc-472">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-472">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8a3cc-473">**page**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-473">**page**</span></span>

<span data-ttu-id="8a3cc-474">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-474">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="8a3cc-475">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-475">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="8a3cc-476">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-476">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="8a3cc-477">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-477">**viewimports**</span></span>

<span data-ttu-id="8a3cc-478">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-478">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="8a3cc-479">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-479">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8a3cc-480">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8a3cc-480">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="8a3cc-481">**console, xunit, mstest, web, webapi** </span><span class="sxs-lookup"><span data-stu-id="8a3cc-481">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="8a3cc-482">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-482">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8a3cc-483">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-483">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="8a3cc-484">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-484">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="8a3cc-485">**classlib**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-485">**classlib**</span></span>

<span data-ttu-id="8a3cc-486">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-486">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8a3cc-487">Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-487">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="8a3cc-488">O valor padrão é `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-488">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="8a3cc-489">**mvc**</span><span class="sxs-lookup"><span data-stu-id="8a3cc-489">**mvc**</span></span>

<span data-ttu-id="8a3cc-490">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-490">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8a3cc-491">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-491">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="8a3cc-492">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-492">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="8a3cc-493">`-au|--auth` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-493">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="8a3cc-494">Valores: `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-494">Values: `None` or `Individual`.</span></span> <span data-ttu-id="8a3cc-495">O valor padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-495">The default value is `None`.</span></span>

<span data-ttu-id="8a3cc-496">`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-496">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="8a3cc-497">Valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-497">Values: `true` or `false`.</span></span> <span data-ttu-id="8a3cc-498">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="8a3cc-498">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="8a3cc-499">Exemplos</span><span class="sxs-lookup"><span data-stu-id="8a3cc-499">Examples</span></span>

<span data-ttu-id="8a3cc-500">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="8a3cc-500">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="8a3cc-501">Crie um projeto de biblioteca de classes .NET Standard no diretório especificado (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="8a3cc-501">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="8a3cc-502">Crie um novo projeto de aplicativo de MVC C# do ASP.NET Core no diretório atual sem autenticação direcionando o .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="8a3cc-502">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="8a3cc-503">Crie um novo aplicativo xUnit direcionando o .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="8a3cc-503">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="8a3cc-504">Lista todos os modelos disponíveis para o MVC:</span><span class="sxs-lookup"><span data-stu-id="8a3cc-504">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="8a3cc-505">Instale a versão 2.0 dos modelos de aplicativo de página única do ASP.NET Core (opção de comando disponível somente para o SDK do .NET Core 1.1 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="8a3cc-505">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="8a3cc-506">Crie um *global.json* no diretório atual definindo a versão do SDK como 2.0.0 (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="8a3cc-506">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="8a3cc-507">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a3cc-507">See also</span></span>

[<span data-ttu-id="8a3cc-508">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="8a3cc-508">Custom templates for dotnet new</span></span>](custom-templates.md)  
<span data-ttu-id="8a3cc-509">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="8a3cc-509">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md)</span></span>  
[<span data-ttu-id="8a3cc-510">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="8a3cc-510">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="8a3cc-511">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="8a3cc-511">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)