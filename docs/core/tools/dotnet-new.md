---
title: Comando dotnet new – CLI do .NET Core
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
author: mairaw
ms.author: mairaw
ms.date: 10/24/2018
ms.openlocfilehash: 56d76f1dd54097f9cf20129d74057235290c273c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188190"
---
# <a name="dotnet-new"></a><span data-ttu-id="8db41-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="8db41-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="8db41-104">Nome</span><span class="sxs-lookup"><span data-stu-id="8db41-104">Name</span></span>

<span data-ttu-id="8db41-105">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="8db41-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8db41-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="8db41-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8db41-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8db41-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8db41-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8db41-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8db41-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8db41-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="8db41-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="8db41-110">Description</span></span>

<span data-ttu-id="8db41-111">O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido.</span><span class="sxs-lookup"><span data-stu-id="8db41-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="8db41-112">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="8db41-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="8db41-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="8db41-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="8db41-114">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="8db41-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="8db41-115">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="8db41-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="8db41-116">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="8db41-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8db41-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8db41-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="8db41-118">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="8db41-118">The command contains a default list of templates.</span></span> <span data-ttu-id="8db41-119">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8db41-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="8db41-120">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="8db41-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="8db41-121">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="8db41-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="8db41-122">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="8db41-122">Template description</span></span>                          | <span data-ttu-id="8db41-123">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="8db41-123">Template name</span></span>    | <span data-ttu-id="8db41-124">Linguagens</span><span class="sxs-lookup"><span data-stu-id="8db41-124">Languages</span></span>     |
|----------------------------------------------|------------------|---------------|
| <span data-ttu-id="8db41-125">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="8db41-125">Console application</span></span>                          | `console`        | <span data-ttu-id="8db41-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8db41-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8db41-127">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="8db41-127">Class library</span></span>                                | `classlib`       | <span data-ttu-id="8db41-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8db41-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8db41-129">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="8db41-129">Unit test project</span></span>                            | `mstest`         | <span data-ttu-id="8db41-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8db41-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8db41-131">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="8db41-131">xUnit test project</span></span>                           | `xunit`          | <span data-ttu-id="8db41-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8db41-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8db41-133">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="8db41-133">Razor page</span></span>                                   | `page`           | <span data-ttu-id="8db41-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="8db41-134">[C#]</span></span>          |
| <span data-ttu-id="8db41-135">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="8db41-135">MVC ViewImports</span></span>                              | `viewimports`    | <span data-ttu-id="8db41-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="8db41-136">[C#]</span></span>          |
| <span data-ttu-id="8db41-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="8db41-137">MVC ViewStart</span></span>                                | `viewstart`      | <span data-ttu-id="8db41-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="8db41-138">[C#]</span></span>          |
| <span data-ttu-id="8db41-139">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="8db41-139">ASP.NET Core empty</span></span>                           | `web`            | <span data-ttu-id="8db41-140">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8db41-140">[C#], F#</span></span>      |
| <span data-ttu-id="8db41-141">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="8db41-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`            | <span data-ttu-id="8db41-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8db41-142">[C#], F#</span></span>      |
| <span data-ttu-id="8db41-143">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8db41-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="8db41-144">`razor`, `webapp`</span><span class="sxs-lookup"><span data-stu-id="8db41-144">`razor`, `webapp`</span></span>| <span data-ttu-id="8db41-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="8db41-145">[C#]</span></span>          |
| <span data-ttu-id="8db41-146">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="8db41-146">ASP.NET Core with Angular</span></span>                    | `angular`        | <span data-ttu-id="8db41-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="8db41-147">[C#]</span></span>          |
| <span data-ttu-id="8db41-148">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="8db41-148">ASP.NET Core with React.js</span></span>                   | `react`          | <span data-ttu-id="8db41-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="8db41-149">[C#]</span></span>          |
| <span data-ttu-id="8db41-150">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="8db41-150">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`     | <span data-ttu-id="8db41-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="8db41-151">[C#]</span></span>          |
| <span data-ttu-id="8db41-152">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8db41-152">ASP.NET Core Web API</span></span>                         | `webapi`         | <span data-ttu-id="8db41-153">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8db41-153">[C#], F#</span></span>      |
| <span data-ttu-id="8db41-154">Biblioteca de classes Razor</span><span class="sxs-lookup"><span data-stu-id="8db41-154">Razor class library</span></span>                          | `razorclasslib`  | <span data-ttu-id="8db41-155">[C#]</span><span class="sxs-lookup"><span data-stu-id="8db41-155">[C#]</span></span>          |
| <span data-ttu-id="8db41-156">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="8db41-156">global.json file</span></span>                             | `globaljson`     |               |
| <span data-ttu-id="8db41-157">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="8db41-157">NuGet config</span></span>                                 | `nugetconfig`    |               |
| <span data-ttu-id="8db41-158">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="8db41-158">Web config</span></span>                                   | `webconfig`      |               |
| <span data-ttu-id="8db41-159">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="8db41-159">Solution file</span></span>                                | `sln`            |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8db41-160">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8db41-160">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="8db41-161">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="8db41-161">The command contains a default list of templates.</span></span> <span data-ttu-id="8db41-162">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8db41-162">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="8db41-163">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="8db41-163">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="8db41-164">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="8db41-164">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="8db41-165">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="8db41-165">Template description</span></span>                          | <span data-ttu-id="8db41-166">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="8db41-166">Template name</span></span> | <span data-ttu-id="8db41-167">Linguagens</span><span class="sxs-lookup"><span data-stu-id="8db41-167">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="8db41-168">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="8db41-168">Console application</span></span>                          | `console`     | <span data-ttu-id="8db41-169">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8db41-169">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8db41-170">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="8db41-170">Class library</span></span>                                | `classlib`    | <span data-ttu-id="8db41-171">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8db41-171">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8db41-172">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="8db41-172">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="8db41-173">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8db41-173">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8db41-174">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="8db41-174">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="8db41-175">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8db41-175">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8db41-176">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="8db41-176">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="8db41-177">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8db41-177">[C#], F#</span></span>      |
| <span data-ttu-id="8db41-178">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="8db41-178">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="8db41-179">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8db41-179">[C#], F#</span></span>      |
| <span data-ttu-id="8db41-180">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8db41-180">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="8db41-181">[C#]</span><span class="sxs-lookup"><span data-stu-id="8db41-181">[C#]</span></span>          |
| <span data-ttu-id="8db41-182">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="8db41-182">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="8db41-183">[C#]</span><span class="sxs-lookup"><span data-stu-id="8db41-183">[C#]</span></span>          |
| <span data-ttu-id="8db41-184">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="8db41-184">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="8db41-185">[C#]</span><span class="sxs-lookup"><span data-stu-id="8db41-185">[C#]</span></span>          |
| <span data-ttu-id="8db41-186">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="8db41-186">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="8db41-187">[C#]</span><span class="sxs-lookup"><span data-stu-id="8db41-187">[C#]</span></span>          |
| <span data-ttu-id="8db41-188">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8db41-188">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="8db41-189">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8db41-189">[C#], F#</span></span>      |
| <span data-ttu-id="8db41-190">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="8db41-190">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="8db41-191">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="8db41-191">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="8db41-192">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="8db41-192">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="8db41-193">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="8db41-193">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="8db41-194">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="8db41-194">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="8db41-195">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="8db41-195">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="8db41-196">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="8db41-196">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8db41-197">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8db41-197">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="8db41-198">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="8db41-198">The command contains a default list of templates.</span></span> <span data-ttu-id="8db41-199">Use `dotnet new -all` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8db41-199">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="8db41-200">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="8db41-200">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="8db41-201">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="8db41-201">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="8db41-202">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="8db41-202">Template description</span></span>  | <span data-ttu-id="8db41-203">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="8db41-203">Template name</span></span> | <span data-ttu-id="8db41-204">Linguagens</span><span class="sxs-lookup"><span data-stu-id="8db41-204">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="8db41-205">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="8db41-205">Console application</span></span>  | `console`     | <span data-ttu-id="8db41-206">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8db41-206">[C#], F#</span></span>  |
| <span data-ttu-id="8db41-207">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="8db41-207">Class library</span></span>        | `classlib`    | <span data-ttu-id="8db41-208">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8db41-208">[C#], F#</span></span>  |
| <span data-ttu-id="8db41-209">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="8db41-209">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="8db41-210">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8db41-210">[C#], F#</span></span>  |
| <span data-ttu-id="8db41-211">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="8db41-211">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="8db41-212">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8db41-212">[C#], F#</span></span>  |
| <span data-ttu-id="8db41-213">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="8db41-213">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="8db41-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="8db41-214">[C#]</span></span>      |
| <span data-ttu-id="8db41-215">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8db41-215">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="8db41-216">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8db41-216">[C#], F#</span></span>  |
| <span data-ttu-id="8db41-217">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8db41-217">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="8db41-218">[C#]</span><span class="sxs-lookup"><span data-stu-id="8db41-218">[C#]</span></span>      |
| <span data-ttu-id="8db41-219">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="8db41-219">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="8db41-220">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="8db41-220">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="8db41-221">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="8db41-221">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="8db41-222">Opções</span><span class="sxs-lookup"><span data-stu-id="8db41-222">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8db41-223">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8db41-223">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="8db41-224">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="8db41-224">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="8db41-225">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-225">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="8db41-226">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="8db41-226">Prints out help for the command.</span></span> <span data-ttu-id="8db41-227">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="8db41-227">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="8db41-228">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="8db41-228">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="8db41-229">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="8db41-229">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="8db41-230">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="8db41-230">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="8db41-231">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="8db41-231">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="8db41-232">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="8db41-232">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="8db41-233">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="8db41-233">Lists templates containing the specified name.</span></span> <span data-ttu-id="8db41-234">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="8db41-234">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="8db41-235">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-235">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="8db41-236">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="8db41-236">The language of the template to create.</span></span> <span data-ttu-id="8db41-237">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="8db41-237">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="8db41-238">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="8db41-238">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="8db41-239">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="8db41-239">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="8db41-240">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="8db41-240">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="8db41-241">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="8db41-241">The name for the created output.</span></span> <span data-ttu-id="8db41-242">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="8db41-242">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="8db41-243">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="8db41-243">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="8db41-244">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="8db41-244">Location to place the generated output.</span></span> <span data-ttu-id="8db41-245">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="8db41-245">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="8db41-246">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8db41-246">Filters templates based on available types.</span></span> <span data-ttu-id="8db41-247">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="8db41-247">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="8db41-248">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="8db41-248">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="8db41-249">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="8db41-249">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="8db41-250">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="8db41-250">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="8db41-251">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="8db41-251">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8db41-252">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8db41-252">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="8db41-253">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="8db41-253">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="8db41-254">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-254">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="8db41-255">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="8db41-255">Prints out help for the command.</span></span> <span data-ttu-id="8db41-256">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="8db41-256">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="8db41-257">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="8db41-257">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="8db41-258">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="8db41-258">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="8db41-259">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="8db41-259">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="8db41-260">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="8db41-260">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="8db41-261">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="8db41-261">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="8db41-262">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="8db41-262">Lists templates containing the specified name.</span></span> <span data-ttu-id="8db41-263">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="8db41-263">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="8db41-264">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-264">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="8db41-265">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="8db41-265">The language of the template to create.</span></span> <span data-ttu-id="8db41-266">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="8db41-266">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="8db41-267">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="8db41-267">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="8db41-268">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="8db41-268">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="8db41-269">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="8db41-269">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="8db41-270">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="8db41-270">The name for the created output.</span></span> <span data-ttu-id="8db41-271">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="8db41-271">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="8db41-272">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="8db41-272">Location to place the generated output.</span></span> <span data-ttu-id="8db41-273">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="8db41-273">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="8db41-274">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8db41-274">Filters templates based on available types.</span></span> <span data-ttu-id="8db41-275">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="8db41-275">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="8db41-276">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="8db41-276">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="8db41-277">Para desinstalar um modelo usando uma origem `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="8db41-277">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="8db41-278">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="8db41-278">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="8db41-279">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="8db41-279">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="8db41-280">Se não for possível determinar o argumento `PATH` ou `NUGET_ID` necessário para desinstalar um modelo, executar `dotnet new --uninstall` sem um argumento listará todos os modelos instalados e o argumento necessário desinstalá-los.</span><span class="sxs-lookup"><span data-stu-id="8db41-280">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8db41-281">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8db41-281">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="8db41-282">Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado.</span><span class="sxs-lookup"><span data-stu-id="8db41-282">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="8db41-283">Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força.</span><span class="sxs-lookup"><span data-stu-id="8db41-283">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="8db41-284">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-284">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="8db41-285">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="8db41-285">Prints out help for the command.</span></span> <span data-ttu-id="8db41-286">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="8db41-286">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="8db41-287">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="8db41-287">Lists templates containing the specified name.</span></span> <span data-ttu-id="8db41-288">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="8db41-288">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="8db41-289">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-289">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="8db41-290">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="8db41-290">The language of the template to create.</span></span> <span data-ttu-id="8db41-291">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="8db41-291">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="8db41-292">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="8db41-292">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="8db41-293">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="8db41-293">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="8db41-294">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="8db41-294">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="8db41-295">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="8db41-295">The name for the created output.</span></span> <span data-ttu-id="8db41-296">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="8db41-296">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="8db41-297">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="8db41-297">Location to place the generated output.</span></span> <span data-ttu-id="8db41-298">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="8db41-298">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="8db41-299">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="8db41-299">Template options</span></span>

<span data-ttu-id="8db41-300">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8db41-300">Each project template may have additional options available.</span></span> <span data-ttu-id="8db41-301">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="8db41-301">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8db41-302">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8db41-302">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="8db41-303">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="8db41-303">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="8db41-304">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-304">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8db41-305">**classlib**</span><span class="sxs-lookup"><span data-stu-id="8db41-305">**classlib**</span></span>

<span data-ttu-id="8db41-306">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="8db41-306">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8db41-307">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="8db41-307">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="8db41-308">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="8db41-308">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="8db41-309">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-309">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8db41-310">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="8db41-310">**mstest, xunit**</span></span>

<span data-ttu-id="8db41-311">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="8db41-311">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="8db41-312">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-312">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8db41-313">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="8db41-313">**globaljson**</span></span>

<span data-ttu-id="8db41-314">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="8db41-314">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="8db41-315">**web**</span><span class="sxs-lookup"><span data-stu-id="8db41-315">**web**</span></span>

<span data-ttu-id="8db41-316">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="8db41-316">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="8db41-317">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-317">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8db41-318">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8db41-318">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="8db41-319">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="8db41-319">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="8db41-320">**webapi**</span><span class="sxs-lookup"><span data-stu-id="8db41-320">**webapi**</span></span>

<span data-ttu-id="8db41-321">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="8db41-321">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="8db41-322">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="8db41-322">The possible values are:</span></span>

- <span data-ttu-id="8db41-323">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="8db41-323">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="8db41-324">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="8db41-324">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="8db41-325">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="8db41-325">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="8db41-326">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="8db41-326">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="8db41-327">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8db41-327">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8db41-328">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-328">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8db41-329">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="8db41-329">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="8db41-330">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-330">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8db41-331">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-331">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8db41-332">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8db41-332">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8db41-333">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8db41-333">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8db41-334">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="8db41-334">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="8db41-335">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-335">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="8db41-336">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8db41-336">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="8db41-337">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="8db41-337">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="8db41-338">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="8db41-338">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="8db41-339">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-339">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8db41-340">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="8db41-340">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="8db41-341">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8db41-341">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8db41-342">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8db41-342">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8db41-343">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="8db41-343">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="8db41-344">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="8db41-344">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="8db41-345">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8db41-345">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="8db41-346">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="8db41-346">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="8db41-347">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="8db41-347">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8db41-348">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-348">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8db41-349">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-349">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8db41-350">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8db41-350">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="8db41-351">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="8db41-351">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="8db41-352">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="8db41-352">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="8db41-353">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="8db41-353">**mvc, razor**</span></span>

<span data-ttu-id="8db41-354">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="8db41-354">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="8db41-355">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="8db41-355">The possible values are:</span></span>

- <span data-ttu-id="8db41-356">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="8db41-356">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="8db41-357">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="8db41-357">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="8db41-358">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="8db41-358">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="8db41-359">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="8db41-359">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="8db41-360">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="8db41-360">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="8db41-361">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="8db41-361">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="8db41-362">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8db41-362">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8db41-363">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-363">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8db41-364">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="8db41-364">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="8db41-365">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-365">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8db41-366">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-366">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8db41-367">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-367">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="8db41-368">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-368">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8db41-369">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-369">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="8db41-370">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-370">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8db41-371">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8db41-371">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8db41-372">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8db41-372">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="8db41-373">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="8db41-373">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="8db41-374">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-374">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="8db41-375">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8db41-375">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="8db41-376">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="8db41-376">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="8db41-377">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="8db41-377">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="8db41-378">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-378">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8db41-379">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="8db41-379">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="8db41-380">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8db41-380">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8db41-381">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8db41-381">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8db41-382">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="8db41-382">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="8db41-383">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="8db41-383">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="8db41-384">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-384">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8db41-385">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="8db41-385">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="8db41-386">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="8db41-386">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="8db41-387">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8db41-387">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="8db41-388">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="8db41-388">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="8db41-389">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-389">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="8db41-390">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="8db41-390">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8db41-391">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-391">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8db41-392">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-392">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8db41-393">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8db41-393">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="8db41-394">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="8db41-394">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="8db41-395">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="8db41-395">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="8db41-396">**page**</span><span class="sxs-lookup"><span data-stu-id="8db41-396">**page**</span></span>

<span data-ttu-id="8db41-397">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="8db41-397">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="8db41-398">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="8db41-398">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="8db41-399">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="8db41-399">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="8db41-400">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="8db41-400">**viewimports**</span></span>

<span data-ttu-id="8db41-401">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="8db41-401">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="8db41-402">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="8db41-402">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="8db41-403">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8db41-403">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="8db41-404">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="8db41-404">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="8db41-405">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-405">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8db41-406">**classlib**</span><span class="sxs-lookup"><span data-stu-id="8db41-406">**classlib**</span></span>

<span data-ttu-id="8db41-407">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="8db41-407">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8db41-408">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="8db41-408">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="8db41-409">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="8db41-409">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="8db41-410">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-410">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8db41-411">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="8db41-411">**mstest, xunit**</span></span>

<span data-ttu-id="8db41-412">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="8db41-412">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="8db41-413">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-413">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8db41-414">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="8db41-414">**globaljson**</span></span>

<span data-ttu-id="8db41-415">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="8db41-415">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="8db41-416">**web**</span><span class="sxs-lookup"><span data-stu-id="8db41-416">**web**</span></span>

<span data-ttu-id="8db41-417">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="8db41-417">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8db41-418">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-418">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8db41-419">**webapi**</span><span class="sxs-lookup"><span data-stu-id="8db41-419">**webapi**</span></span>

<span data-ttu-id="8db41-420">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="8db41-420">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="8db41-421">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="8db41-421">The possible values are:</span></span>

- <span data-ttu-id="8db41-422">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="8db41-422">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="8db41-423">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="8db41-423">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="8db41-424">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="8db41-424">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="8db41-425">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="8db41-425">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="8db41-426">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8db41-426">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8db41-427">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-427">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8db41-428">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="8db41-428">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="8db41-429">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-429">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8db41-430">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-430">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8db41-431">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8db41-431">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8db41-432">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8db41-432">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8db41-433">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="8db41-433">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="8db41-434">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-434">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="8db41-435">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8db41-435">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="8db41-436">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="8db41-436">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="8db41-437">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="8db41-437">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="8db41-438">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-438">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8db41-439">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="8db41-439">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="8db41-440">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8db41-440">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8db41-441">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8db41-441">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8db41-442">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="8db41-442">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="8db41-443">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="8db41-443">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="8db41-444">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8db41-444">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="8db41-445">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="8db41-445">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8db41-446">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="8db41-446">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8db41-447">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-447">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8db41-448">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-448">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8db41-449">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="8db41-449">**mvc, razor**</span></span>

<span data-ttu-id="8db41-450">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="8db41-450">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="8db41-451">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="8db41-451">The possible values are:</span></span>

- <span data-ttu-id="8db41-452">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="8db41-452">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="8db41-453">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="8db41-453">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="8db41-454">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="8db41-454">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="8db41-455">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="8db41-455">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="8db41-456">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="8db41-456">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="8db41-457">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="8db41-457">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="8db41-458">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8db41-458">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8db41-459">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-459">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8db41-460">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="8db41-460">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="8db41-461">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-461">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8db41-462">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-462">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8db41-463">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-463">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="8db41-464">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-464">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8db41-465">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-465">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="8db41-466">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-466">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8db41-467">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8db41-467">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8db41-468">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8db41-468">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="8db41-469">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="8db41-469">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="8db41-470">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-470">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="8db41-471">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8db41-471">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="8db41-472">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="8db41-472">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="8db41-473">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="8db41-473">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="8db41-474">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-474">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8db41-475">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="8db41-475">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="8db41-476">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="8db41-476">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8db41-477">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="8db41-477">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8db41-478">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="8db41-478">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="8db41-479">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="8db41-479">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="8db41-480">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8db41-481">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="8db41-481">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="8db41-482">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="8db41-482">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="8db41-483">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="8db41-483">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="8db41-484">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="8db41-484">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8db41-485">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-485">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="8db41-486">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="8db41-486">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8db41-487">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="8db41-487">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8db41-488">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="8db41-488">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="8db41-489">**page**</span><span class="sxs-lookup"><span data-stu-id="8db41-489">**page**</span></span>

<span data-ttu-id="8db41-490">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="8db41-490">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="8db41-491">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="8db41-491">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="8db41-492">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="8db41-492">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="8db41-493">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="8db41-493">**viewimports**</span></span>

<span data-ttu-id="8db41-494">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="8db41-494">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="8db41-495">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="8db41-495">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8db41-496">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8db41-496">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="8db41-497">**console, xunit, mstest, web, webapi** </span><span class="sxs-lookup"><span data-stu-id="8db41-497">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="8db41-498">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="8db41-498">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8db41-499">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="8db41-499">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="8db41-500">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="8db41-500">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="8db41-501">**classlib**</span><span class="sxs-lookup"><span data-stu-id="8db41-501">**classlib**</span></span>

<span data-ttu-id="8db41-502">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="8db41-502">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8db41-503">Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="8db41-503">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="8db41-504">O valor padrão é `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="8db41-504">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="8db41-505">**mvc**</span><span class="sxs-lookup"><span data-stu-id="8db41-505">**mvc**</span></span>

<span data-ttu-id="8db41-506">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="8db41-506">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8db41-507">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="8db41-507">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="8db41-508">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="8db41-508">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="8db41-509">`-au|--auth` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="8db41-509">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="8db41-510">Valores: `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="8db41-510">Values: `None` or `Individual`.</span></span> <span data-ttu-id="8db41-511">O valor padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="8db41-511">The default value is `None`.</span></span>

<span data-ttu-id="8db41-512">`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="8db41-512">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="8db41-513">Valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="8db41-513">Values: `true` or `false`.</span></span> <span data-ttu-id="8db41-514">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="8db41-514">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="8db41-515">Exemplos</span><span class="sxs-lookup"><span data-stu-id="8db41-515">Examples</span></span>

<span data-ttu-id="8db41-516">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="8db41-516">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="8db41-517">Crie um projeto de biblioteca de classes .NET Standard no diretório especificado (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="8db41-517">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="8db41-518">Crie um novo projeto de aplicativo de MVC C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="8db41-518">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="8db41-519">Crie um novo aplicativo xUnit:</span><span class="sxs-lookup"><span data-stu-id="8db41-519">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="8db41-520">Lista todos os modelos disponíveis para o MVC:</span><span class="sxs-lookup"><span data-stu-id="8db41-520">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="8db41-521">Instale a versão 2.0 dos modelos de aplicativo de página única do ASP.NET Core (opção de comando disponível somente para o SDK do .NET Core 1.1 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="8db41-521">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="8db41-522">Crie um *global.json* no diretório atual definindo a versão do SDK como 2.0.0 (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="8db41-522">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="8db41-523">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8db41-523">See also</span></span>

* [<span data-ttu-id="8db41-524">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="8db41-524">Custom templates for dotnet new</span></span>](custom-templates.md)  
* <span data-ttu-id="8db41-525">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="8db41-525">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md)</span></span>  
* [<span data-ttu-id="8db41-526">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="8db41-526">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
* [<span data-ttu-id="8db41-527">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="8db41-527">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
