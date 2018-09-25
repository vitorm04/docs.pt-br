---
title: Comando dotnet new – CLI do .NET Core
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
author: mairaw
ms.author: mairaw
ms.date: 07/31/2018
ms.openlocfilehash: 2c82dda2d93225edb360316637e22964135cd5e4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512549"
---
# <a name="dotnet-new"></a><span data-ttu-id="ea538-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="ea538-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ea538-104">Nome</span><span class="sxs-lookup"><span data-stu-id="ea538-104">Name</span></span>

<span data-ttu-id="ea538-105">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="ea538-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ea538-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="ea538-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ea538-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ea538-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ea538-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ea538-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ea538-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ea538-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="ea538-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea538-110">Description</span></span>

<span data-ttu-id="ea538-111">O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido.</span><span class="sxs-lookup"><span data-stu-id="ea538-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="ea538-112">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="ea538-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="ea538-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="ea538-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="ea538-114">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="ea538-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="ea538-115">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="ea538-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="ea538-116">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="ea538-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ea538-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ea538-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="ea538-118">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="ea538-118">The command contains a default list of templates.</span></span> <span data-ttu-id="ea538-119">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ea538-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="ea538-120">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="ea538-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="ea538-121">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="ea538-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="ea538-122">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="ea538-122">Template description</span></span>                          | <span data-ttu-id="ea538-123">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="ea538-123">Template name</span></span>   | <span data-ttu-id="ea538-124">Linguagens</span><span class="sxs-lookup"><span data-stu-id="ea538-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="ea538-125">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="ea538-125">Console application</span></span>                          | `console`       | <span data-ttu-id="ea538-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ea538-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ea538-127">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="ea538-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="ea538-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ea538-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ea538-129">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="ea538-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="ea538-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ea538-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ea538-131">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="ea538-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="ea538-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ea538-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ea538-133">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="ea538-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="ea538-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="ea538-134">[C#]</span></span>          |
| <span data-ttu-id="ea538-135">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="ea538-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="ea538-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="ea538-136">[C#]</span></span>          |
| <span data-ttu-id="ea538-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="ea538-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="ea538-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="ea538-138">[C#]</span></span>          |
| <span data-ttu-id="ea538-139">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="ea538-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="ea538-140">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ea538-140">[C#], F#</span></span>      |
| <span data-ttu-id="ea538-141">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="ea538-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="ea538-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ea538-142">[C#], F#</span></span>      |
| <span data-ttu-id="ea538-143">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ea538-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="ea538-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="ea538-144">[C#]</span></span>          |
| <span data-ttu-id="ea538-145">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="ea538-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="ea538-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="ea538-146">[C#]</span></span>          |
| <span data-ttu-id="ea538-147">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="ea538-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="ea538-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="ea538-148">[C#]</span></span>          |
| <span data-ttu-id="ea538-149">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="ea538-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="ea538-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="ea538-150">[C#]</span></span>          |
| <span data-ttu-id="ea538-151">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ea538-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="ea538-152">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ea538-152">[C#], F#</span></span>      |
| <span data-ttu-id="ea538-153">Biblioteca de classes Razor</span><span class="sxs-lookup"><span data-stu-id="ea538-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="ea538-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="ea538-154">[C#]</span></span>          |
| <span data-ttu-id="ea538-155">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="ea538-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="ea538-156">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="ea538-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="ea538-157">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="ea538-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="ea538-158">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="ea538-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ea538-159">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ea538-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="ea538-160">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="ea538-160">The command contains a default list of templates.</span></span> <span data-ttu-id="ea538-161">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ea538-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="ea538-162">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="ea538-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="ea538-163">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="ea538-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="ea538-164">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="ea538-164">Template description</span></span>                          | <span data-ttu-id="ea538-165">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="ea538-165">Template name</span></span> | <span data-ttu-id="ea538-166">Linguagens</span><span class="sxs-lookup"><span data-stu-id="ea538-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="ea538-167">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="ea538-167">Console application</span></span>                          | `console`     | <span data-ttu-id="ea538-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ea538-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ea538-169">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="ea538-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="ea538-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ea538-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ea538-171">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="ea538-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="ea538-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ea538-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ea538-173">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="ea538-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="ea538-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ea538-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="ea538-175">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="ea538-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="ea538-176">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ea538-176">[C#], F#</span></span>      |
| <span data-ttu-id="ea538-177">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="ea538-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="ea538-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ea538-178">[C#], F#</span></span>      |
| <span data-ttu-id="ea538-179">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ea538-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="ea538-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="ea538-180">[C#]</span></span>          |
| <span data-ttu-id="ea538-181">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="ea538-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="ea538-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="ea538-182">[C#]</span></span>          |
| <span data-ttu-id="ea538-183">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="ea538-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="ea538-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="ea538-184">[C#]</span></span>          |
| <span data-ttu-id="ea538-185">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="ea538-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="ea538-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="ea538-186">[C#]</span></span>          |
| <span data-ttu-id="ea538-187">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ea538-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="ea538-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ea538-188">[C#], F#</span></span>      |
| <span data-ttu-id="ea538-189">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="ea538-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="ea538-190">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="ea538-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="ea538-191">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="ea538-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="ea538-192">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="ea538-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="ea538-193">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="ea538-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="ea538-194">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="ea538-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="ea538-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="ea538-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ea538-196">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ea538-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ea538-197">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="ea538-197">The command contains a default list of templates.</span></span> <span data-ttu-id="ea538-198">Use `dotnet new -all` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ea538-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="ea538-199">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="ea538-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="ea538-200">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="ea538-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="ea538-201">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="ea538-201">Template description</span></span>  | <span data-ttu-id="ea538-202">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="ea538-202">Template name</span></span> | <span data-ttu-id="ea538-203">Linguagens</span><span class="sxs-lookup"><span data-stu-id="ea538-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="ea538-204">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="ea538-204">Console application</span></span>  | `console`     | <span data-ttu-id="ea538-205">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ea538-205">[C#], F#</span></span>  |
| <span data-ttu-id="ea538-206">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="ea538-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="ea538-207">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ea538-207">[C#], F#</span></span>  |
| <span data-ttu-id="ea538-208">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="ea538-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="ea538-209">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ea538-209">[C#], F#</span></span>  |
| <span data-ttu-id="ea538-210">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="ea538-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="ea538-211">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ea538-211">[C#], F#</span></span>  |
| <span data-ttu-id="ea538-212">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="ea538-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="ea538-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="ea538-213">[C#]</span></span>      |
| <span data-ttu-id="ea538-214">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ea538-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="ea538-215">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ea538-215">[C#], F#</span></span>  |
| <span data-ttu-id="ea538-216">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ea538-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="ea538-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="ea538-217">[C#]</span></span>      |
| <span data-ttu-id="ea538-218">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="ea538-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="ea538-219">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="ea538-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="ea538-220">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="ea538-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="ea538-221">Opções</span><span class="sxs-lookup"><span data-stu-id="ea538-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ea538-222">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ea538-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="ea538-223">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="ea538-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ea538-224">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ea538-225">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="ea538-225">Prints out help for the command.</span></span> <span data-ttu-id="ea538-226">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ea538-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="ea538-227">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="ea538-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ea538-228">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="ea538-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="ea538-229">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="ea538-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="ea538-230">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="ea538-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="ea538-231">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="ea538-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="ea538-232">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="ea538-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="ea538-233">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="ea538-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ea538-234">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="ea538-235">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="ea538-235">The language of the template to create.</span></span> <span data-ttu-id="ea538-236">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="ea538-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ea538-237">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="ea538-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="ea538-238">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="ea538-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ea538-239">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ea538-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ea538-240">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="ea538-240">The name for the created output.</span></span> <span data-ttu-id="ea538-241">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="ea538-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="ea538-242">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="ea538-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ea538-243">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="ea538-243">Location to place the generated output.</span></span> <span data-ttu-id="ea538-244">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="ea538-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="ea538-245">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ea538-245">Filters templates based on available types.</span></span> <span data-ttu-id="ea538-246">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="ea538-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="ea538-247">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="ea538-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="ea538-248">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="ea538-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ea538-249">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="ea538-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="ea538-250">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="ea538-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ea538-251">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ea538-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="ea538-252">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="ea538-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ea538-253">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ea538-254">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="ea538-254">Prints out help for the command.</span></span> <span data-ttu-id="ea538-255">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ea538-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="ea538-256">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="ea538-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ea538-257">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="ea538-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="ea538-258">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="ea538-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="ea538-259">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="ea538-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="ea538-260">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="ea538-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="ea538-261">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="ea538-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="ea538-262">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="ea538-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ea538-263">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="ea538-264">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="ea538-264">The language of the template to create.</span></span> <span data-ttu-id="ea538-265">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="ea538-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ea538-266">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="ea538-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="ea538-267">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="ea538-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ea538-268">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ea538-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ea538-269">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="ea538-269">The name for the created output.</span></span> <span data-ttu-id="ea538-270">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="ea538-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ea538-271">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="ea538-271">Location to place the generated output.</span></span> <span data-ttu-id="ea538-272">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="ea538-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="ea538-273">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ea538-273">Filters templates based on available types.</span></span> <span data-ttu-id="ea538-274">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="ea538-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="ea538-275">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="ea538-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="ea538-276">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="ea538-276">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ea538-277">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="ea538-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="ea538-278">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="ea538-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ea538-279">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ea538-279">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="ea538-280">Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado.</span><span class="sxs-lookup"><span data-stu-id="ea538-280">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="ea538-281">Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força.</span><span class="sxs-lookup"><span data-stu-id="ea538-281">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="ea538-282">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-282">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ea538-283">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="ea538-283">Prints out help for the command.</span></span> <span data-ttu-id="ea538-284">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ea538-284">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="ea538-285">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="ea538-285">Lists templates containing the specified name.</span></span> <span data-ttu-id="ea538-286">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="ea538-286">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ea538-287">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-287">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="ea538-288">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="ea538-288">The language of the template to create.</span></span> <span data-ttu-id="ea538-289">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="ea538-289">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ea538-290">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="ea538-290">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="ea538-291">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="ea538-291">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ea538-292">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ea538-292">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ea538-293">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="ea538-293">The name for the created output.</span></span> <span data-ttu-id="ea538-294">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="ea538-294">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ea538-295">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="ea538-295">Location to place the generated output.</span></span> <span data-ttu-id="ea538-296">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="ea538-296">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="ea538-297">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="ea538-297">Template options</span></span>

<span data-ttu-id="ea538-298">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ea538-298">Each project template may have additional options available.</span></span> <span data-ttu-id="ea538-299">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="ea538-299">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ea538-300">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ea538-300">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="ea538-301">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="ea538-301">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="ea538-302">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-302">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ea538-303">**classlib**</span><span class="sxs-lookup"><span data-stu-id="ea538-303">**classlib**</span></span>

<span data-ttu-id="ea538-304">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="ea538-304">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ea538-305">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ea538-305">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ea538-306">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ea538-306">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="ea538-307">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-307">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ea538-308">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="ea538-308">**mstest, xunit**</span></span>

<span data-ttu-id="ea538-309">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ea538-309">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="ea538-310">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-310">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ea538-311">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="ea538-311">**globaljson**</span></span>

<span data-ttu-id="ea538-312">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="ea538-312">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="ea538-313">**web**</span><span class="sxs-lookup"><span data-stu-id="ea538-313">**web**</span></span>

<span data-ttu-id="ea538-314">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ea538-314">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ea538-315">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-315">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ea538-316">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ea538-316">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ea538-317">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="ea538-317">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="ea538-318">**webapi**</span><span class="sxs-lookup"><span data-stu-id="ea538-318">**webapi**</span></span>

<span data-ttu-id="ea538-319">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="ea538-319">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ea538-320">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="ea538-320">The possible values are:</span></span>

- <span data-ttu-id="ea538-321">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="ea538-321">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ea538-322">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ea538-322">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ea538-323">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="ea538-323">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ea538-324">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="ea538-324">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ea538-325">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ea538-325">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ea538-326">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-326">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ea538-327">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ea538-327">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ea538-328">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-328">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ea538-329">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-329">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ea538-330">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ea538-330">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ea538-331">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ea538-331">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ea538-332">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ea538-332">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ea538-333">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-333">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ea538-334">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ea538-334">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ea538-335">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ea538-335">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ea538-336">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="ea538-336">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ea538-337">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-337">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ea538-338">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ea538-338">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ea538-339">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ea538-339">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ea538-340">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ea538-340">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ea538-341">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ea538-341">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ea538-342">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="ea538-342">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ea538-343">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ea538-343">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ea538-344">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ea538-344">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ea538-345">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="ea538-345">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ea538-346">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-346">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ea538-347">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-347">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ea538-348">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ea538-348">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ea538-349">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="ea538-349">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ea538-350">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="ea538-350">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="ea538-351">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="ea538-351">**mvc, razor**</span></span>

<span data-ttu-id="ea538-352">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="ea538-352">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ea538-353">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="ea538-353">The possible values are:</span></span>

- <span data-ttu-id="ea538-354">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="ea538-354">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ea538-355">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="ea538-355">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="ea538-356">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ea538-356">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ea538-357">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="ea538-357">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ea538-358">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="ea538-358">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="ea538-359">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="ea538-359">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ea538-360">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ea538-360">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ea538-361">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-361">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ea538-362">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ea538-362">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ea538-363">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-363">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ea538-364">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-364">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ea538-365">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-365">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="ea538-366">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-366">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ea538-367">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-367">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="ea538-368">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-368">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ea538-369">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ea538-369">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ea538-370">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ea538-370">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ea538-371">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ea538-371">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ea538-372">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-372">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ea538-373">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ea538-373">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ea538-374">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ea538-374">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ea538-375">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="ea538-375">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ea538-376">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-376">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ea538-377">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ea538-377">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ea538-378">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ea538-378">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ea538-379">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ea538-379">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ea538-380">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ea538-380">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ea538-381">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="ea538-381">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ea538-382">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-382">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ea538-383">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ea538-383">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="ea538-384">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="ea538-384">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ea538-385">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ea538-385">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ea538-386">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ea538-386">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ea538-387">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-387">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="ea538-388">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="ea538-388">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ea538-389">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-389">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ea538-390">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-390">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ea538-391">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ea538-391">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ea538-392">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="ea538-392">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ea538-393">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="ea538-393">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="ea538-394">**page**</span><span class="sxs-lookup"><span data-stu-id="ea538-394">**page**</span></span>

<span data-ttu-id="ea538-395">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="ea538-395">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="ea538-396">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ea538-396">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="ea538-397">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="ea538-397">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="ea538-398">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="ea538-398">**viewimports**</span></span>

<span data-ttu-id="ea538-399">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="ea538-399">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="ea538-400">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ea538-400">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ea538-401">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ea538-401">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="ea538-402">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="ea538-402">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="ea538-403">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-403">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ea538-404">**classlib**</span><span class="sxs-lookup"><span data-stu-id="ea538-404">**classlib**</span></span>

<span data-ttu-id="ea538-405">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="ea538-405">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ea538-406">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ea538-406">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ea538-407">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ea538-407">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="ea538-408">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-408">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ea538-409">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="ea538-409">**mstest, xunit**</span></span>

<span data-ttu-id="ea538-410">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ea538-410">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="ea538-411">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-411">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ea538-412">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="ea538-412">**globaljson**</span></span>

<span data-ttu-id="ea538-413">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="ea538-413">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="ea538-414">**web**</span><span class="sxs-lookup"><span data-stu-id="ea538-414">**web**</span></span>

<span data-ttu-id="ea538-415">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ea538-415">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ea538-416">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-416">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ea538-417">**webapi**</span><span class="sxs-lookup"><span data-stu-id="ea538-417">**webapi**</span></span>

<span data-ttu-id="ea538-418">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="ea538-418">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ea538-419">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="ea538-419">The possible values are:</span></span>

- <span data-ttu-id="ea538-420">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="ea538-420">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ea538-421">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ea538-421">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ea538-422">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="ea538-422">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ea538-423">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="ea538-423">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ea538-424">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ea538-424">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ea538-425">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-425">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ea538-426">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ea538-426">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ea538-427">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-427">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ea538-428">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-428">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ea538-429">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ea538-429">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ea538-430">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ea538-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ea538-431">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ea538-431">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ea538-432">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-432">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ea538-433">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ea538-433">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ea538-434">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ea538-434">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ea538-435">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="ea538-435">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ea538-436">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-436">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ea538-437">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ea538-437">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ea538-438">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ea538-438">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ea538-439">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ea538-439">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ea538-440">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ea538-440">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ea538-441">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="ea538-441">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ea538-442">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ea538-442">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ea538-443">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ea538-443">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ea538-444">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="ea538-444">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ea538-445">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-445">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ea538-446">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-446">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ea538-447">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="ea538-447">**mvc, razor**</span></span>

<span data-ttu-id="ea538-448">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="ea538-448">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ea538-449">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="ea538-449">The possible values are:</span></span>

- <span data-ttu-id="ea538-450">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="ea538-450">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ea538-451">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="ea538-451">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="ea538-452">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ea538-452">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ea538-453">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="ea538-453">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ea538-454">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="ea538-454">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="ea538-455">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="ea538-455">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ea538-456">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ea538-456">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ea538-457">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-457">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ea538-458">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ea538-458">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ea538-459">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-459">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ea538-460">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-460">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ea538-461">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-461">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="ea538-462">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-462">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ea538-463">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-463">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="ea538-464">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-464">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ea538-465">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ea538-465">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ea538-466">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ea538-466">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ea538-467">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ea538-467">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ea538-468">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-468">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ea538-469">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ea538-469">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ea538-470">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ea538-470">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ea538-471">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="ea538-471">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ea538-472">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-472">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ea538-473">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ea538-473">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ea538-474">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ea538-474">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ea538-475">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ea538-475">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ea538-476">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ea538-476">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ea538-477">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="ea538-477">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ea538-478">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-478">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ea538-479">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ea538-479">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="ea538-480">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="ea538-480">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ea538-481">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ea538-481">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ea538-482">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ea538-482">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ea538-483">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-483">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="ea538-484">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="ea538-484">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ea538-485">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ea538-485">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ea538-486">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ea538-486">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ea538-487">**page**</span><span class="sxs-lookup"><span data-stu-id="ea538-487">**page**</span></span>

<span data-ttu-id="ea538-488">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="ea538-488">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="ea538-489">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ea538-489">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="ea538-490">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="ea538-490">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="ea538-491">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="ea538-491">**viewimports**</span></span>

<span data-ttu-id="ea538-492">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="ea538-492">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="ea538-493">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ea538-493">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ea538-494">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ea538-494">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ea538-495">**console, xunit, mstest, web, webapi** </span><span class="sxs-lookup"><span data-stu-id="ea538-495">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="ea538-496">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="ea538-496">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ea538-497">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="ea538-497">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="ea538-498">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="ea538-498">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="ea538-499">**classlib**</span><span class="sxs-lookup"><span data-stu-id="ea538-499">**classlib**</span></span>

<span data-ttu-id="ea538-500">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="ea538-500">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ea538-501">Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="ea538-501">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="ea538-502">O valor padrão é `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="ea538-502">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="ea538-503">**mvc**</span><span class="sxs-lookup"><span data-stu-id="ea538-503">**mvc**</span></span>

<span data-ttu-id="ea538-504">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="ea538-504">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ea538-505">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="ea538-505">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="ea538-506">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="ea538-506">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="ea538-507">`-au|--auth` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="ea538-507">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="ea538-508">Valores: `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="ea538-508">Values: `None` or `Individual`.</span></span> <span data-ttu-id="ea538-509">O valor padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="ea538-509">The default value is `None`.</span></span>

<span data-ttu-id="ea538-510">`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="ea538-510">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="ea538-511">Valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="ea538-511">Values: `true` or `false`.</span></span> <span data-ttu-id="ea538-512">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="ea538-512">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="ea538-513">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ea538-513">Examples</span></span>

<span data-ttu-id="ea538-514">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="ea538-514">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="ea538-515">Crie um projeto de biblioteca de classes .NET Standard no diretório especificado (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="ea538-515">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="ea538-516">Crie um novo projeto de aplicativo de MVC C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="ea538-516">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="ea538-517">Crie um novo aplicativo xUnit:</span><span class="sxs-lookup"><span data-stu-id="ea538-517">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="ea538-518">Lista todos os modelos disponíveis para o MVC:</span><span class="sxs-lookup"><span data-stu-id="ea538-518">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="ea538-519">Instale a versão 2.0 dos modelos de aplicativo de página única do ASP.NET Core (opção de comando disponível somente para o SDK do .NET Core 1.1 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="ea538-519">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="ea538-520">Crie um *global.json* no diretório atual definindo a versão do SDK como 2.0.0 (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="ea538-520">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="ea538-521">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea538-521">See also</span></span>

* [<span data-ttu-id="ea538-522">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="ea538-522">Custom templates for dotnet new</span></span>](custom-templates.md)  
* <span data-ttu-id="ea538-523">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="ea538-523">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md)</span></span>  
* [<span data-ttu-id="ea538-524">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="ea538-524">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
* [<span data-ttu-id="ea538-525">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="ea538-525">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
