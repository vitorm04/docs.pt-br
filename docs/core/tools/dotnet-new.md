---
title: Comando dotnet new – CLI do .NET Core
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
author: mairaw
ms.author: mairaw
ms.date: 07/31/2018
ms.openlocfilehash: 396c4ddf09854fa4582226bdb1422f8c929e459b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47208622"
---
# <a name="dotnet-new"></a><span data-ttu-id="0b55a-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="0b55a-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0b55a-104">Nome</span><span class="sxs-lookup"><span data-stu-id="0b55a-104">Name</span></span>

<span data-ttu-id="0b55a-105">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0b55a-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="0b55a-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0b55a-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0b55a-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0b55a-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="0b55a-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0b55a-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0b55a-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="0b55a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b55a-110">Description</span></span>

<span data-ttu-id="0b55a-111">O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido.</span><span class="sxs-lookup"><span data-stu-id="0b55a-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="0b55a-112">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="0b55a-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="0b55a-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="0b55a-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="0b55a-114">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="0b55a-115">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="0b55a-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="0b55a-116">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="0b55a-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0b55a-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0b55a-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="0b55a-118">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="0b55a-118">The command contains a default list of templates.</span></span> <span data-ttu-id="0b55a-119">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0b55a-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="0b55a-120">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="0b55a-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="0b55a-121">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="0b55a-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="0b55a-122">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="0b55a-122">Template description</span></span>                          | <span data-ttu-id="0b55a-123">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="0b55a-123">Template name</span></span>   | <span data-ttu-id="0b55a-124">Linguagens</span><span class="sxs-lookup"><span data-stu-id="0b55a-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="0b55a-125">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="0b55a-125">Console application</span></span>                          | `console`       | <span data-ttu-id="0b55a-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="0b55a-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0b55a-127">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="0b55a-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="0b55a-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="0b55a-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0b55a-129">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="0b55a-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="0b55a-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="0b55a-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0b55a-131">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="0b55a-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="0b55a-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="0b55a-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0b55a-133">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="0b55a-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="0b55a-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="0b55a-134">[C#]</span></span>          |
| <span data-ttu-id="0b55a-135">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="0b55a-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="0b55a-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="0b55a-136">[C#]</span></span>          |
| <span data-ttu-id="0b55a-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="0b55a-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="0b55a-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="0b55a-138">[C#]</span></span>          |
| <span data-ttu-id="0b55a-139">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="0b55a-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="0b55a-140">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="0b55a-140">[C#], F#</span></span>      |
| <span data-ttu-id="0b55a-141">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="0b55a-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="0b55a-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="0b55a-142">[C#], F#</span></span>      |
| <span data-ttu-id="0b55a-143">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0b55a-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="0b55a-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="0b55a-144">[C#]</span></span>          |
| <span data-ttu-id="0b55a-145">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="0b55a-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="0b55a-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="0b55a-146">[C#]</span></span>          |
| <span data-ttu-id="0b55a-147">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="0b55a-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="0b55a-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="0b55a-148">[C#]</span></span>          |
| <span data-ttu-id="0b55a-149">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="0b55a-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="0b55a-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="0b55a-150">[C#]</span></span>          |
| <span data-ttu-id="0b55a-151">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0b55a-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="0b55a-152">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="0b55a-152">[C#], F#</span></span>      |
| <span data-ttu-id="0b55a-153">Biblioteca de classes Razor</span><span class="sxs-lookup"><span data-stu-id="0b55a-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="0b55a-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="0b55a-154">[C#]</span></span>          |
| <span data-ttu-id="0b55a-155">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="0b55a-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="0b55a-156">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="0b55a-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="0b55a-157">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="0b55a-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="0b55a-158">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="0b55a-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0b55a-159">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="0b55a-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="0b55a-160">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="0b55a-160">The command contains a default list of templates.</span></span> <span data-ttu-id="0b55a-161">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0b55a-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="0b55a-162">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="0b55a-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="0b55a-163">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="0b55a-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="0b55a-164">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="0b55a-164">Template description</span></span>                          | <span data-ttu-id="0b55a-165">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="0b55a-165">Template name</span></span> | <span data-ttu-id="0b55a-166">Linguagens</span><span class="sxs-lookup"><span data-stu-id="0b55a-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="0b55a-167">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="0b55a-167">Console application</span></span>                          | `console`     | <span data-ttu-id="0b55a-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="0b55a-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0b55a-169">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="0b55a-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="0b55a-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="0b55a-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0b55a-171">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="0b55a-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="0b55a-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="0b55a-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0b55a-173">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="0b55a-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="0b55a-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="0b55a-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="0b55a-175">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="0b55a-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="0b55a-176">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="0b55a-176">[C#], F#</span></span>      |
| <span data-ttu-id="0b55a-177">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="0b55a-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="0b55a-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="0b55a-178">[C#], F#</span></span>      |
| <span data-ttu-id="0b55a-179">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0b55a-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="0b55a-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="0b55a-180">[C#]</span></span>          |
| <span data-ttu-id="0b55a-181">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="0b55a-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="0b55a-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="0b55a-182">[C#]</span></span>          |
| <span data-ttu-id="0b55a-183">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="0b55a-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="0b55a-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="0b55a-184">[C#]</span></span>          |
| <span data-ttu-id="0b55a-185">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="0b55a-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="0b55a-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="0b55a-186">[C#]</span></span>          |
| <span data-ttu-id="0b55a-187">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0b55a-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="0b55a-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="0b55a-188">[C#], F#</span></span>      |
| <span data-ttu-id="0b55a-189">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="0b55a-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="0b55a-190">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="0b55a-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="0b55a-191">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="0b55a-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="0b55a-192">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="0b55a-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="0b55a-193">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="0b55a-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="0b55a-194">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="0b55a-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="0b55a-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="0b55a-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0b55a-196">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0b55a-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="0b55a-197">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="0b55a-197">The command contains a default list of templates.</span></span> <span data-ttu-id="0b55a-198">Use `dotnet new -all` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0b55a-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="0b55a-199">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="0b55a-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="0b55a-200">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="0b55a-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="0b55a-201">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="0b55a-201">Template description</span></span>  | <span data-ttu-id="0b55a-202">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="0b55a-202">Template name</span></span> | <span data-ttu-id="0b55a-203">Linguagens</span><span class="sxs-lookup"><span data-stu-id="0b55a-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="0b55a-204">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="0b55a-204">Console application</span></span>  | `console`     | <span data-ttu-id="0b55a-205">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="0b55a-205">[C#], F#</span></span>  |
| <span data-ttu-id="0b55a-206">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="0b55a-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="0b55a-207">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="0b55a-207">[C#], F#</span></span>  |
| <span data-ttu-id="0b55a-208">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="0b55a-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="0b55a-209">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="0b55a-209">[C#], F#</span></span>  |
| <span data-ttu-id="0b55a-210">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="0b55a-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="0b55a-211">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="0b55a-211">[C#], F#</span></span>  |
| <span data-ttu-id="0b55a-212">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="0b55a-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="0b55a-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="0b55a-213">[C#]</span></span>      |
| <span data-ttu-id="0b55a-214">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0b55a-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="0b55a-215">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="0b55a-215">[C#], F#</span></span>  |
| <span data-ttu-id="0b55a-216">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0b55a-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="0b55a-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="0b55a-217">[C#]</span></span>      |
| <span data-ttu-id="0b55a-218">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="0b55a-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="0b55a-219">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="0b55a-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="0b55a-220">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="0b55a-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="0b55a-221">Opções</span><span class="sxs-lookup"><span data-stu-id="0b55a-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0b55a-222">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0b55a-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="0b55a-223">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="0b55a-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="0b55a-224">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="0b55a-225">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="0b55a-225">Prints out help for the command.</span></span> <span data-ttu-id="0b55a-226">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="0b55a-227">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="0b55a-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="0b55a-228">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="0b55a-229">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="0b55a-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="0b55a-230">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="0b55a-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="0b55a-231">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="0b55a-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="0b55a-232">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="0b55a-233">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="0b55a-234">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="0b55a-235">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="0b55a-235">The language of the template to create.</span></span> <span data-ttu-id="0b55a-236">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="0b55a-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="0b55a-237">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="0b55a-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="0b55a-238">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="0b55a-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="0b55a-239">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="0b55a-240">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="0b55a-240">The name for the created output.</span></span> <span data-ttu-id="0b55a-241">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="0b55a-242">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="0b55a-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="0b55a-243">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="0b55a-243">Location to place the generated output.</span></span> <span data-ttu-id="0b55a-244">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="0b55a-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="0b55a-245">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0b55a-245">Filters templates based on available types.</span></span> <span data-ttu-id="0b55a-246">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="0b55a-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="0b55a-247">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="0b55a-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="0b55a-248">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="0b55a-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="0b55a-249">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="0b55a-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="0b55a-250">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="0b55a-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0b55a-251">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="0b55a-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="0b55a-252">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="0b55a-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="0b55a-253">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="0b55a-254">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="0b55a-254">Prints out help for the command.</span></span> <span data-ttu-id="0b55a-255">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="0b55a-256">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="0b55a-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="0b55a-257">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="0b55a-258">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="0b55a-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="0b55a-259">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="0b55a-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="0b55a-260">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="0b55a-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="0b55a-261">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="0b55a-262">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="0b55a-263">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="0b55a-264">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="0b55a-264">The language of the template to create.</span></span> <span data-ttu-id="0b55a-265">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="0b55a-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="0b55a-266">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="0b55a-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="0b55a-267">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="0b55a-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="0b55a-268">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="0b55a-269">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="0b55a-269">The name for the created output.</span></span> <span data-ttu-id="0b55a-270">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="0b55a-271">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="0b55a-271">Location to place the generated output.</span></span> <span data-ttu-id="0b55a-272">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="0b55a-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="0b55a-273">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0b55a-273">Filters templates based on available types.</span></span> <span data-ttu-id="0b55a-274">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="0b55a-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="0b55a-275">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="0b55a-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="0b55a-276">Para desinstalar um modelo usando uma origem `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="0b55a-276">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="0b55a-277">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="0b55a-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="0b55a-278">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="0b55a-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="0b55a-279">Se não for possível determinar o argumento `PATH` ou `NUGET_ID` necessário para desinstalar um modelo, executar `dotnet new --uninstall` sem um argumento listará todos os modelos instalados e o argumento necessário desinstalá-los.</span><span class="sxs-lookup"><span data-stu-id="0b55a-279">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0b55a-280">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0b55a-280">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="0b55a-281">Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-281">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="0b55a-282">Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força.</span><span class="sxs-lookup"><span data-stu-id="0b55a-282">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="0b55a-283">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-283">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="0b55a-284">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="0b55a-284">Prints out help for the command.</span></span> <span data-ttu-id="0b55a-285">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-285">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="0b55a-286">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-286">Lists templates containing the specified name.</span></span> <span data-ttu-id="0b55a-287">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-287">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="0b55a-288">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-288">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="0b55a-289">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="0b55a-289">The language of the template to create.</span></span> <span data-ttu-id="0b55a-290">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="0b55a-290">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="0b55a-291">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="0b55a-291">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="0b55a-292">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="0b55a-292">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="0b55a-293">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-293">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="0b55a-294">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="0b55a-294">The name for the created output.</span></span> <span data-ttu-id="0b55a-295">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-295">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="0b55a-296">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="0b55a-296">Location to place the generated output.</span></span> <span data-ttu-id="0b55a-297">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="0b55a-297">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="0b55a-298">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="0b55a-298">Template options</span></span>

<span data-ttu-id="0b55a-299">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0b55a-299">Each project template may have additional options available.</span></span> <span data-ttu-id="0b55a-300">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="0b55a-300">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0b55a-301">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0b55a-301">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="0b55a-302">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="0b55a-302">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="0b55a-303">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-303">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0b55a-304">**classlib**</span><span class="sxs-lookup"><span data-stu-id="0b55a-304">**classlib**</span></span>

<span data-ttu-id="0b55a-305">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="0b55a-305">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0b55a-306">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0b55a-306">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="0b55a-307">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-307">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="0b55a-308">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-308">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0b55a-309">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="0b55a-309">**mstest, xunit**</span></span>

<span data-ttu-id="0b55a-310">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="0b55a-310">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="0b55a-311">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-311">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0b55a-312">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="0b55a-312">**globaljson**</span></span>

<span data-ttu-id="0b55a-313">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="0b55a-313">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="0b55a-314">**web**</span><span class="sxs-lookup"><span data-stu-id="0b55a-314">**web**</span></span>

<span data-ttu-id="0b55a-315">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-315">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="0b55a-316">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-316">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0b55a-317">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0b55a-317">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="0b55a-318">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-318">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="0b55a-319">**webapi**</span><span class="sxs-lookup"><span data-stu-id="0b55a-319">**webapi**</span></span>

<span data-ttu-id="0b55a-320">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-320">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="0b55a-321">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="0b55a-321">The possible values are:</span></span>

- <span data-ttu-id="0b55a-322">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="0b55a-322">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="0b55a-323">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="0b55a-323">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="0b55a-324">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="0b55a-324">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="0b55a-325">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="0b55a-325">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="0b55a-326">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="0b55a-326">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="0b55a-327">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-327">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="0b55a-328">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-328">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="0b55a-329">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-329">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="0b55a-330">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-330">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0b55a-331">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="0b55a-331">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="0b55a-332">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-332">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0b55a-333">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-333">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="0b55a-334">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-334">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="0b55a-335">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-335">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="0b55a-336">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-336">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="0b55a-337">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="0b55a-337">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="0b55a-338">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-338">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0b55a-339">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-339">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="0b55a-340">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="0b55a-340">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="0b55a-341">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-341">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0b55a-342">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-342">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="0b55a-343">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="0b55a-343">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="0b55a-344">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-344">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="0b55a-345">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-345">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="0b55a-346">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="0b55a-346">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="0b55a-347">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-347">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0b55a-348">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-348">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0b55a-349">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0b55a-349">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="0b55a-350">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-350">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="0b55a-351">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="0b55a-351">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="0b55a-352">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="0b55a-352">**mvc, razor**</span></span>

<span data-ttu-id="0b55a-353">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-353">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="0b55a-354">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="0b55a-354">The possible values are:</span></span>

- <span data-ttu-id="0b55a-355">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="0b55a-355">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="0b55a-356">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="0b55a-356">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="0b55a-357">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="0b55a-357">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="0b55a-358">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="0b55a-358">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="0b55a-359">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="0b55a-359">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="0b55a-360">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="0b55a-360">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="0b55a-361">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="0b55a-361">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="0b55a-362">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-362">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="0b55a-363">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-363">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="0b55a-364">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-364">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="0b55a-365">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-365">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0b55a-366">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-366">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="0b55a-367">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-367">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0b55a-368">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-368">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="0b55a-369">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-369">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0b55a-370">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="0b55a-370">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="0b55a-371">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-371">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="0b55a-372">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-372">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="0b55a-373">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-373">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="0b55a-374">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-374">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="0b55a-375">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-375">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="0b55a-376">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="0b55a-376">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="0b55a-377">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-377">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0b55a-378">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-378">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="0b55a-379">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="0b55a-379">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="0b55a-380">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-380">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0b55a-381">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-381">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="0b55a-382">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="0b55a-382">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="0b55a-383">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-383">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0b55a-384">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-384">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="0b55a-385">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="0b55a-385">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="0b55a-386">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-386">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="0b55a-387">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-387">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="0b55a-388">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-388">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="0b55a-389">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="0b55a-389">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="0b55a-390">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-390">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0b55a-391">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-391">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0b55a-392">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0b55a-392">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="0b55a-393">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-393">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="0b55a-394">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="0b55a-394">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="0b55a-395">**page**</span><span class="sxs-lookup"><span data-stu-id="0b55a-395">**page**</span></span>

<span data-ttu-id="0b55a-396">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-396">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="0b55a-397">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-397">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="0b55a-398">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="0b55a-398">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="0b55a-399">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="0b55a-399">**viewimports**</span></span>

<span data-ttu-id="0b55a-400">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-400">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="0b55a-401">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-401">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0b55a-402">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="0b55a-402">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="0b55a-403">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="0b55a-403">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="0b55a-404">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-404">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0b55a-405">**classlib**</span><span class="sxs-lookup"><span data-stu-id="0b55a-405">**classlib**</span></span>

<span data-ttu-id="0b55a-406">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="0b55a-406">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0b55a-407">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0b55a-407">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="0b55a-408">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-408">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="0b55a-409">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-409">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0b55a-410">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="0b55a-410">**mstest, xunit**</span></span>

<span data-ttu-id="0b55a-411">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="0b55a-411">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="0b55a-412">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-412">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0b55a-413">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="0b55a-413">**globaljson**</span></span>

<span data-ttu-id="0b55a-414">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="0b55a-414">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="0b55a-415">**web**</span><span class="sxs-lookup"><span data-stu-id="0b55a-415">**web**</span></span>

<span data-ttu-id="0b55a-416">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-416">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="0b55a-417">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-417">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0b55a-418">**webapi**</span><span class="sxs-lookup"><span data-stu-id="0b55a-418">**webapi**</span></span>

<span data-ttu-id="0b55a-419">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-419">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="0b55a-420">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="0b55a-420">The possible values are:</span></span>

- <span data-ttu-id="0b55a-421">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="0b55a-421">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="0b55a-422">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="0b55a-422">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="0b55a-423">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="0b55a-423">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="0b55a-424">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="0b55a-424">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="0b55a-425">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="0b55a-425">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="0b55a-426">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-426">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="0b55a-427">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-427">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="0b55a-428">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-428">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="0b55a-429">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-429">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0b55a-430">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="0b55a-430">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="0b55a-431">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0b55a-432">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-432">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="0b55a-433">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-433">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="0b55a-434">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-434">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="0b55a-435">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-435">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="0b55a-436">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="0b55a-436">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="0b55a-437">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-437">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0b55a-438">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-438">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="0b55a-439">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="0b55a-439">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="0b55a-440">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-440">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0b55a-441">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-441">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="0b55a-442">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="0b55a-442">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="0b55a-443">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-443">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="0b55a-444">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-444">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="0b55a-445">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="0b55a-445">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="0b55a-446">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-446">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0b55a-447">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-447">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0b55a-448">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="0b55a-448">**mvc, razor**</span></span>

<span data-ttu-id="0b55a-449">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-449">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="0b55a-450">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="0b55a-450">The possible values are:</span></span>

- <span data-ttu-id="0b55a-451">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="0b55a-451">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="0b55a-452">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="0b55a-452">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="0b55a-453">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="0b55a-453">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="0b55a-454">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="0b55a-454">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="0b55a-455">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="0b55a-455">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="0b55a-456">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="0b55a-456">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="0b55a-457">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="0b55a-457">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="0b55a-458">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-458">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="0b55a-459">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-459">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="0b55a-460">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-460">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="0b55a-461">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-461">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0b55a-462">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-462">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="0b55a-463">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-463">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0b55a-464">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-464">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="0b55a-465">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-465">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0b55a-466">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="0b55a-466">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="0b55a-467">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-467">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="0b55a-468">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-468">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="0b55a-469">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-469">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="0b55a-470">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-470">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="0b55a-471">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-471">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="0b55a-472">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="0b55a-472">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="0b55a-473">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-473">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0b55a-474">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-474">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="0b55a-475">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="0b55a-475">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="0b55a-476">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-476">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="0b55a-477">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-477">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="0b55a-478">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="0b55a-478">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="0b55a-479">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-479">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="0b55a-480">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-480">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="0b55a-481">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="0b55a-481">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="0b55a-482">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-482">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="0b55a-483">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-483">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="0b55a-484">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-484">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="0b55a-485">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="0b55a-485">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="0b55a-486">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-486">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="0b55a-487">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="0b55a-487">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="0b55a-488">**page**</span><span class="sxs-lookup"><span data-stu-id="0b55a-488">**page**</span></span>

<span data-ttu-id="0b55a-489">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-489">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="0b55a-490">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-490">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="0b55a-491">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="0b55a-491">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="0b55a-492">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="0b55a-492">**viewimports**</span></span>

<span data-ttu-id="0b55a-493">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-493">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="0b55a-494">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-494">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0b55a-495">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0b55a-495">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="0b55a-496">**console, xunit, mstest, web, webapi** </span><span class="sxs-lookup"><span data-stu-id="0b55a-496">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="0b55a-497">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="0b55a-497">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0b55a-498">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-498">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="0b55a-499">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-499">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="0b55a-500">**classlib**</span><span class="sxs-lookup"><span data-stu-id="0b55a-500">**classlib**</span></span>

<span data-ttu-id="0b55a-501">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="0b55a-501">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0b55a-502">Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-502">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="0b55a-503">O valor padrão é `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-503">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="0b55a-504">**mvc**</span><span class="sxs-lookup"><span data-stu-id="0b55a-504">**mvc**</span></span>

<span data-ttu-id="0b55a-505">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="0b55a-505">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="0b55a-506">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-506">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="0b55a-507">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-507">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="0b55a-508">`-au|--auth` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="0b55a-508">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="0b55a-509">Valores: `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-509">Values: `None` or `Individual`.</span></span> <span data-ttu-id="0b55a-510">O valor padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-510">The default value is `None`.</span></span>

<span data-ttu-id="0b55a-511">`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="0b55a-511">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="0b55a-512">Valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-512">Values: `true` or `false`.</span></span> <span data-ttu-id="0b55a-513">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="0b55a-513">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="0b55a-514">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0b55a-514">Examples</span></span>

<span data-ttu-id="0b55a-515">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="0b55a-515">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="0b55a-516">Crie um projeto de biblioteca de classes .NET Standard no diretório especificado (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="0b55a-516">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="0b55a-517">Crie um novo projeto de aplicativo de MVC C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="0b55a-517">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="0b55a-518">Crie um novo aplicativo xUnit:</span><span class="sxs-lookup"><span data-stu-id="0b55a-518">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="0b55a-519">Lista todos os modelos disponíveis para o MVC:</span><span class="sxs-lookup"><span data-stu-id="0b55a-519">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="0b55a-520">Instale a versão 2.0 dos modelos de aplicativo de página única do ASP.NET Core (opção de comando disponível somente para o SDK do .NET Core 1.1 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="0b55a-520">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="0b55a-521">Crie um *global.json* no diretório atual definindo a versão do SDK como 2.0.0 (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="0b55a-521">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="0b55a-522">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b55a-522">See also</span></span>

* [<span data-ttu-id="0b55a-523">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="0b55a-523">Custom templates for dotnet new</span></span>](custom-templates.md)  
* <span data-ttu-id="0b55a-524">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="0b55a-524">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md)</span></span>  
* [<span data-ttu-id="0b55a-525">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="0b55a-525">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
* [<span data-ttu-id="0b55a-526">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="0b55a-526">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
