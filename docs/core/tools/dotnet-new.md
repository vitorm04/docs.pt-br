---
title: Comando dotnet new
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
ms.date: 10/24/2018
ms.openlocfilehash: 3a10aaa93af57e7beb86771e7d3b00b06fca14b2
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169672"
---
# <a name="dotnet-new"></a><span data-ttu-id="22a58-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="22a58-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="22a58-104">Nome</span><span class="sxs-lookup"><span data-stu-id="22a58-104">Name</span></span>

<span data-ttu-id="22a58-105">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="22a58-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="22a58-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="22a58-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="22a58-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="22a58-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="22a58-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="22a58-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="22a58-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="22a58-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="22a58-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="22a58-110">Description</span></span>

<span data-ttu-id="22a58-111">O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido.</span><span class="sxs-lookup"><span data-stu-id="22a58-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="22a58-112">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="22a58-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="22a58-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="22a58-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="22a58-114">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="22a58-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="22a58-115">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="22a58-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="22a58-116">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="22a58-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="22a58-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="22a58-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="22a58-118">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="22a58-118">The command contains a default list of templates.</span></span> <span data-ttu-id="22a58-119">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="22a58-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="22a58-120">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="22a58-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="22a58-121">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="22a58-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="22a58-122">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="22a58-122">Template description</span></span>                          | <span data-ttu-id="22a58-123">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="22a58-123">Template name</span></span>    | <span data-ttu-id="22a58-124">Linguagens</span><span class="sxs-lookup"><span data-stu-id="22a58-124">Languages</span></span>     |
|----------------------------------------------|------------------|---------------|
| <span data-ttu-id="22a58-125">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="22a58-125">Console application</span></span>                          | `console`        | <span data-ttu-id="22a58-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="22a58-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="22a58-127">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="22a58-127">Class library</span></span>                                | `classlib`       | <span data-ttu-id="22a58-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="22a58-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="22a58-129">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="22a58-129">Unit test project</span></span>                            | `mstest`         | <span data-ttu-id="22a58-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="22a58-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="22a58-131">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="22a58-131">xUnit test project</span></span>                           | `xunit`          | <span data-ttu-id="22a58-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="22a58-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="22a58-133">Projeto de teste da NUnit</span><span class="sxs-lookup"><span data-stu-id="22a58-133">NUnit test project</span></span>                           | `nunit`          | <span data-ttu-id="22a58-134">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="22a58-134">[C#], F#, VB</span></span>  |
| <span data-ttu-id="22a58-135">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="22a58-135">Razor page</span></span>                                   | `page`           | <span data-ttu-id="22a58-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="22a58-136">[C#]</span></span>          |
| <span data-ttu-id="22a58-137">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="22a58-137">MVC ViewImports</span></span>                              | `viewimports`    | <span data-ttu-id="22a58-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="22a58-138">[C#]</span></span>          |
| <span data-ttu-id="22a58-139">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="22a58-139">MVC ViewStart</span></span>                                | `viewstart`      | <span data-ttu-id="22a58-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="22a58-140">[C#]</span></span>          |
| <span data-ttu-id="22a58-141">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="22a58-141">ASP.NET Core empty</span></span>                           | `web`            | <span data-ttu-id="22a58-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="22a58-142">[C#], F#</span></span>      |
| <span data-ttu-id="22a58-143">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="22a58-143">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`            | <span data-ttu-id="22a58-144">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="22a58-144">[C#], F#</span></span>      |
| <span data-ttu-id="22a58-145">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="22a58-145">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="22a58-146">`razor`, `webapp`</span><span class="sxs-lookup"><span data-stu-id="22a58-146">`razor`, `webapp`</span></span>| <span data-ttu-id="22a58-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="22a58-147">[C#]</span></span>          |
| <span data-ttu-id="22a58-148">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="22a58-148">ASP.NET Core with Angular</span></span>                    | `angular`        | <span data-ttu-id="22a58-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="22a58-149">[C#]</span></span>          |
| <span data-ttu-id="22a58-150">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="22a58-150">ASP.NET Core with React.js</span></span>                   | `react`          | <span data-ttu-id="22a58-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="22a58-151">[C#]</span></span>          |
| <span data-ttu-id="22a58-152">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="22a58-152">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`     | <span data-ttu-id="22a58-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="22a58-153">[C#]</span></span>          |
| <span data-ttu-id="22a58-154">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="22a58-154">ASP.NET Core Web API</span></span>                         | `webapi`         | <span data-ttu-id="22a58-155">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="22a58-155">[C#], F#</span></span>      |
| <span data-ttu-id="22a58-156">Biblioteca de classes Razor</span><span class="sxs-lookup"><span data-stu-id="22a58-156">Razor class library</span></span>                          | `razorclasslib`  | <span data-ttu-id="22a58-157">[C#]</span><span class="sxs-lookup"><span data-stu-id="22a58-157">[C#]</span></span>          |
| <span data-ttu-id="22a58-158">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="22a58-158">global.json file</span></span>                             | `globaljson`     |               |
| <span data-ttu-id="22a58-159">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="22a58-159">NuGet config</span></span>                                 | `nugetconfig`    |               |
| <span data-ttu-id="22a58-160">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="22a58-160">Web config</span></span>                                   | `webconfig`      |               |
| <span data-ttu-id="22a58-161">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="22a58-161">Solution file</span></span>                                | `sln`            |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="22a58-162">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="22a58-162">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="22a58-163">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="22a58-163">The command contains a default list of templates.</span></span> <span data-ttu-id="22a58-164">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="22a58-164">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="22a58-165">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="22a58-165">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="22a58-166">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="22a58-166">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="22a58-167">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="22a58-167">Template description</span></span>                          | <span data-ttu-id="22a58-168">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="22a58-168">Template name</span></span> | <span data-ttu-id="22a58-169">Linguagens</span><span class="sxs-lookup"><span data-stu-id="22a58-169">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="22a58-170">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="22a58-170">Console application</span></span>                          | `console`     | <span data-ttu-id="22a58-171">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="22a58-171">[C#], F#, VB</span></span>  |
| <span data-ttu-id="22a58-172">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="22a58-172">Class library</span></span>                                | `classlib`    | <span data-ttu-id="22a58-173">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="22a58-173">[C#], F#, VB</span></span>  |
| <span data-ttu-id="22a58-174">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="22a58-174">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="22a58-175">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="22a58-175">[C#], F#, VB</span></span>  |
| <span data-ttu-id="22a58-176">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="22a58-176">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="22a58-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="22a58-177">[C#], F#, VB</span></span>  |
| <span data-ttu-id="22a58-178">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="22a58-178">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="22a58-179">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="22a58-179">[C#], F#</span></span>      |
| <span data-ttu-id="22a58-180">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="22a58-180">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="22a58-181">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="22a58-181">[C#], F#</span></span>      |
| <span data-ttu-id="22a58-182">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="22a58-182">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="22a58-183">[C#]</span><span class="sxs-lookup"><span data-stu-id="22a58-183">[C#]</span></span>          |
| <span data-ttu-id="22a58-184">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="22a58-184">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="22a58-185">[C#]</span><span class="sxs-lookup"><span data-stu-id="22a58-185">[C#]</span></span>          |
| <span data-ttu-id="22a58-186">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="22a58-186">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="22a58-187">[C#]</span><span class="sxs-lookup"><span data-stu-id="22a58-187">[C#]</span></span>          |
| <span data-ttu-id="22a58-188">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="22a58-188">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="22a58-189">[C#]</span><span class="sxs-lookup"><span data-stu-id="22a58-189">[C#]</span></span>          |
| <span data-ttu-id="22a58-190">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="22a58-190">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="22a58-191">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="22a58-191">[C#], F#</span></span>      |
| <span data-ttu-id="22a58-192">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="22a58-192">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="22a58-193">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="22a58-193">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="22a58-194">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="22a58-194">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="22a58-195">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="22a58-195">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="22a58-196">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="22a58-196">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="22a58-197">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="22a58-197">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="22a58-198">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="22a58-198">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="22a58-199">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="22a58-199">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="22a58-200">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="22a58-200">The command contains a default list of templates.</span></span> <span data-ttu-id="22a58-201">Use `dotnet new -all` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="22a58-201">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="22a58-202">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="22a58-202">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="22a58-203">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="22a58-203">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="22a58-204">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="22a58-204">Template description</span></span>  | <span data-ttu-id="22a58-205">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="22a58-205">Template name</span></span> | <span data-ttu-id="22a58-206">Linguagens</span><span class="sxs-lookup"><span data-stu-id="22a58-206">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="22a58-207">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="22a58-207">Console application</span></span>  | `console`     | <span data-ttu-id="22a58-208">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="22a58-208">[C#], F#</span></span>  |
| <span data-ttu-id="22a58-209">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="22a58-209">Class library</span></span>        | `classlib`    | <span data-ttu-id="22a58-210">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="22a58-210">[C#], F#</span></span>  |
| <span data-ttu-id="22a58-211">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="22a58-211">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="22a58-212">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="22a58-212">[C#], F#</span></span>  |
| <span data-ttu-id="22a58-213">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="22a58-213">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="22a58-214">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="22a58-214">[C#], F#</span></span>  |
| <span data-ttu-id="22a58-215">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="22a58-215">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="22a58-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="22a58-216">[C#]</span></span>      |
| <span data-ttu-id="22a58-217">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="22a58-217">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="22a58-218">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="22a58-218">[C#], F#</span></span>  |
| <span data-ttu-id="22a58-219">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="22a58-219">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="22a58-220">[C#]</span><span class="sxs-lookup"><span data-stu-id="22a58-220">[C#]</span></span>      |
| <span data-ttu-id="22a58-221">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="22a58-221">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="22a58-222">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="22a58-222">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="22a58-223">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="22a58-223">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="22a58-224">Opções</span><span class="sxs-lookup"><span data-stu-id="22a58-224">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="22a58-225">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="22a58-225">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="22a58-226">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="22a58-226">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="22a58-227">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-227">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="22a58-228">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="22a58-228">Prints out help for the command.</span></span> <span data-ttu-id="22a58-229">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="22a58-229">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="22a58-230">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="22a58-230">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="22a58-231">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="22a58-231">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="22a58-232">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="22a58-232">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="22a58-233">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="22a58-233">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="22a58-234">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="22a58-234">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="22a58-235">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="22a58-235">Lists templates containing the specified name.</span></span> <span data-ttu-id="22a58-236">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="22a58-236">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="22a58-237">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-237">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="22a58-238">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="22a58-238">The language of the template to create.</span></span> <span data-ttu-id="22a58-239">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="22a58-239">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="22a58-240">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="22a58-240">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="22a58-241">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="22a58-241">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="22a58-242">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="22a58-242">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="22a58-243">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="22a58-243">The name for the created output.</span></span> <span data-ttu-id="22a58-244">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="22a58-244">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="22a58-245">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="22a58-245">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="22a58-246">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="22a58-246">Location to place the generated output.</span></span> <span data-ttu-id="22a58-247">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="22a58-247">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="22a58-248">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="22a58-248">Filters templates based on available types.</span></span> <span data-ttu-id="22a58-249">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="22a58-249">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="22a58-250">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="22a58-250">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="22a58-251">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="22a58-251">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="22a58-252">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="22a58-252">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="22a58-253">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="22a58-253">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="22a58-254">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="22a58-254">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="22a58-255">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="22a58-255">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="22a58-256">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-256">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="22a58-257">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="22a58-257">Prints out help for the command.</span></span> <span data-ttu-id="22a58-258">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="22a58-258">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="22a58-259">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="22a58-259">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="22a58-260">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="22a58-260">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="22a58-261">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="22a58-261">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="22a58-262">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="22a58-262">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="22a58-263">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="22a58-263">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="22a58-264">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="22a58-264">Lists templates containing the specified name.</span></span> <span data-ttu-id="22a58-265">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="22a58-265">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="22a58-266">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-266">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="22a58-267">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="22a58-267">The language of the template to create.</span></span> <span data-ttu-id="22a58-268">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="22a58-268">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="22a58-269">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="22a58-269">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="22a58-270">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="22a58-270">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="22a58-271">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="22a58-271">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="22a58-272">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="22a58-272">The name for the created output.</span></span> <span data-ttu-id="22a58-273">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="22a58-273">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="22a58-274">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="22a58-274">Location to place the generated output.</span></span> <span data-ttu-id="22a58-275">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="22a58-275">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="22a58-276">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="22a58-276">Filters templates based on available types.</span></span> <span data-ttu-id="22a58-277">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="22a58-277">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="22a58-278">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="22a58-278">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="22a58-279">Para desinstalar um modelo usando uma origem `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="22a58-279">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="22a58-280">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="22a58-280">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="22a58-281">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="22a58-281">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="22a58-282">Se não for possível determinar o argumento `PATH` ou `NUGET_ID` necessário para desinstalar um modelo, executar `dotnet new --uninstall` sem um argumento listará todos os modelos instalados e o argumento necessário desinstalá-los.</span><span class="sxs-lookup"><span data-stu-id="22a58-282">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="22a58-283">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="22a58-283">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="22a58-284">Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado.</span><span class="sxs-lookup"><span data-stu-id="22a58-284">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="22a58-285">Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força.</span><span class="sxs-lookup"><span data-stu-id="22a58-285">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="22a58-286">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-286">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="22a58-287">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="22a58-287">Prints out help for the command.</span></span> <span data-ttu-id="22a58-288">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="22a58-288">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="22a58-289">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="22a58-289">Lists templates containing the specified name.</span></span> <span data-ttu-id="22a58-290">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="22a58-290">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="22a58-291">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-291">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="22a58-292">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="22a58-292">The language of the template to create.</span></span> <span data-ttu-id="22a58-293">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="22a58-293">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="22a58-294">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="22a58-294">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="22a58-295">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="22a58-295">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="22a58-296">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="22a58-296">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="22a58-297">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="22a58-297">The name for the created output.</span></span> <span data-ttu-id="22a58-298">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="22a58-298">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="22a58-299">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="22a58-299">Location to place the generated output.</span></span> <span data-ttu-id="22a58-300">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="22a58-300">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="22a58-301">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="22a58-301">Template options</span></span>

<span data-ttu-id="22a58-302">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="22a58-302">Each project template may have additional options available.</span></span> <span data-ttu-id="22a58-303">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="22a58-303">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="22a58-304">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="22a58-304">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="22a58-305">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="22a58-305">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="22a58-306">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-306">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="22a58-307">**classlib**</span><span class="sxs-lookup"><span data-stu-id="22a58-307">**classlib**</span></span>

<span data-ttu-id="22a58-308">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="22a58-308">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="22a58-309">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="22a58-309">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="22a58-310">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="22a58-310">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="22a58-311">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-311">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="22a58-312">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="22a58-312">**mstest, xunit**</span></span>

<span data-ttu-id="22a58-313">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="22a58-313">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="22a58-314">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-314">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="22a58-315">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="22a58-315">**globaljson**</span></span>

<span data-ttu-id="22a58-316">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="22a58-316">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="22a58-317">**web**</span><span class="sxs-lookup"><span data-stu-id="22a58-317">**web**</span></span>

<span data-ttu-id="22a58-318">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="22a58-318">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="22a58-319">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-319">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="22a58-320">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="22a58-320">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="22a58-321">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="22a58-321">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="22a58-322">**webapi**</span><span class="sxs-lookup"><span data-stu-id="22a58-322">**webapi**</span></span>

<span data-ttu-id="22a58-323">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="22a58-323">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="22a58-324">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="22a58-324">The possible values are:</span></span>

- <span data-ttu-id="22a58-325">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="22a58-325">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="22a58-326">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="22a58-326">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="22a58-327">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="22a58-327">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="22a58-328">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="22a58-328">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="22a58-329">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="22a58-329">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="22a58-330">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-330">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="22a58-331">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="22a58-331">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="22a58-332">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-332">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="22a58-333">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-333">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="22a58-334">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="22a58-334">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="22a58-335">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="22a58-335">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="22a58-336">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="22a58-336">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="22a58-337">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-337">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="22a58-338">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="22a58-338">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="22a58-339">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="22a58-339">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="22a58-340">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="22a58-340">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="22a58-341">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-341">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="22a58-342">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="22a58-342">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="22a58-343">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="22a58-343">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="22a58-344">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="22a58-344">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="22a58-345">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="22a58-345">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="22a58-346">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="22a58-346">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="22a58-347">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="22a58-347">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="22a58-348">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="22a58-348">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="22a58-349">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="22a58-349">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="22a58-350">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-350">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="22a58-351">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-351">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="22a58-352">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="22a58-352">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="22a58-353">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="22a58-353">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="22a58-354">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="22a58-354">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="22a58-355">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="22a58-355">**mvc, razor**</span></span>

<span data-ttu-id="22a58-356">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="22a58-356">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="22a58-357">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="22a58-357">The possible values are:</span></span>

- <span data-ttu-id="22a58-358">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="22a58-358">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="22a58-359">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="22a58-359">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="22a58-360">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="22a58-360">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="22a58-361">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="22a58-361">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="22a58-362">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="22a58-362">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="22a58-363">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="22a58-363">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="22a58-364">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="22a58-364">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="22a58-365">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-365">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="22a58-366">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="22a58-366">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="22a58-367">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-367">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="22a58-368">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-368">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="22a58-369">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-369">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="22a58-370">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-370">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="22a58-371">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-371">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="22a58-372">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-372">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="22a58-373">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="22a58-373">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="22a58-374">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="22a58-374">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="22a58-375">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="22a58-375">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="22a58-376">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-376">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="22a58-377">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="22a58-377">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="22a58-378">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="22a58-378">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="22a58-379">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="22a58-379">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="22a58-380">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-380">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="22a58-381">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="22a58-381">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="22a58-382">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="22a58-382">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="22a58-383">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="22a58-383">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="22a58-384">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="22a58-384">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="22a58-385">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="22a58-385">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="22a58-386">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-386">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="22a58-387">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="22a58-387">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="22a58-388">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="22a58-388">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="22a58-389">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="22a58-389">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="22a58-390">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="22a58-390">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="22a58-391">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-391">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="22a58-392">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="22a58-392">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="22a58-393">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-393">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="22a58-394">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-394">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="22a58-395">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="22a58-395">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="22a58-396">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="22a58-396">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="22a58-397">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="22a58-397">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="22a58-398">**page**</span><span class="sxs-lookup"><span data-stu-id="22a58-398">**page**</span></span>

<span data-ttu-id="22a58-399">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="22a58-399">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="22a58-400">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="22a58-400">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="22a58-401">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="22a58-401">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="22a58-402">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="22a58-402">**viewimports**</span></span>

<span data-ttu-id="22a58-403">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="22a58-403">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="22a58-404">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="22a58-404">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="22a58-405">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="22a58-405">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="22a58-406">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="22a58-406">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="22a58-407">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-407">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="22a58-408">**classlib**</span><span class="sxs-lookup"><span data-stu-id="22a58-408">**classlib**</span></span>

<span data-ttu-id="22a58-409">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="22a58-409">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="22a58-410">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="22a58-410">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="22a58-411">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="22a58-411">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="22a58-412">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-412">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="22a58-413">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="22a58-413">**mstest, xunit**</span></span>

<span data-ttu-id="22a58-414">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="22a58-414">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="22a58-415">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-415">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="22a58-416">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="22a58-416">**globaljson**</span></span>

<span data-ttu-id="22a58-417">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="22a58-417">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="22a58-418">**web**</span><span class="sxs-lookup"><span data-stu-id="22a58-418">**web**</span></span>

<span data-ttu-id="22a58-419">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="22a58-419">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="22a58-420">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-420">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="22a58-421">**webapi**</span><span class="sxs-lookup"><span data-stu-id="22a58-421">**webapi**</span></span>

<span data-ttu-id="22a58-422">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="22a58-422">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="22a58-423">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="22a58-423">The possible values are:</span></span>

- <span data-ttu-id="22a58-424">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="22a58-424">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="22a58-425">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="22a58-425">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="22a58-426">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="22a58-426">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="22a58-427">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="22a58-427">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="22a58-428">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="22a58-428">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="22a58-429">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-429">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="22a58-430">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="22a58-430">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="22a58-431">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-431">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="22a58-432">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-432">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="22a58-433">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="22a58-433">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="22a58-434">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="22a58-434">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="22a58-435">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="22a58-435">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="22a58-436">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-436">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="22a58-437">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="22a58-437">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="22a58-438">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="22a58-438">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="22a58-439">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="22a58-439">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="22a58-440">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-440">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="22a58-441">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="22a58-441">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="22a58-442">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="22a58-442">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="22a58-443">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="22a58-443">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="22a58-444">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="22a58-444">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="22a58-445">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="22a58-445">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="22a58-446">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="22a58-446">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="22a58-447">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="22a58-447">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="22a58-448">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="22a58-448">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="22a58-449">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-449">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="22a58-450">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-450">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="22a58-451">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="22a58-451">**mvc, razor**</span></span>

<span data-ttu-id="22a58-452">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="22a58-452">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="22a58-453">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="22a58-453">The possible values are:</span></span>

- <span data-ttu-id="22a58-454">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="22a58-454">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="22a58-455">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="22a58-455">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="22a58-456">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="22a58-456">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="22a58-457">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="22a58-457">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="22a58-458">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="22a58-458">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="22a58-459">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="22a58-459">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="22a58-460">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="22a58-460">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="22a58-461">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-461">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="22a58-462">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="22a58-462">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="22a58-463">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-463">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="22a58-464">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-464">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="22a58-465">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-465">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="22a58-466">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-466">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="22a58-467">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-467">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="22a58-468">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-468">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="22a58-469">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="22a58-469">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="22a58-470">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="22a58-470">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="22a58-471">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="22a58-471">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="22a58-472">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-472">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="22a58-473">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="22a58-473">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="22a58-474">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="22a58-474">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="22a58-475">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="22a58-475">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="22a58-476">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-476">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="22a58-477">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="22a58-477">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="22a58-478">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="22a58-478">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="22a58-479">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="22a58-479">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="22a58-480">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="22a58-480">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="22a58-481">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="22a58-481">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="22a58-482">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-482">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="22a58-483">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="22a58-483">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="22a58-484">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="22a58-484">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="22a58-485">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="22a58-485">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="22a58-486">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="22a58-486">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="22a58-487">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-487">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="22a58-488">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="22a58-488">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="22a58-489">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="22a58-489">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="22a58-490">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="22a58-490">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="22a58-491">**page**</span><span class="sxs-lookup"><span data-stu-id="22a58-491">**page**</span></span>

<span data-ttu-id="22a58-492">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="22a58-492">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="22a58-493">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="22a58-493">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="22a58-494">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="22a58-494">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="22a58-495">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="22a58-495">**viewimports**</span></span>

<span data-ttu-id="22a58-496">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="22a58-496">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="22a58-497">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="22a58-497">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="22a58-498">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="22a58-498">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="22a58-499">**console, xunit, mstest, web, webapi** </span><span class="sxs-lookup"><span data-stu-id="22a58-499">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="22a58-500">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="22a58-500">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="22a58-501">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="22a58-501">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="22a58-502">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="22a58-502">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="22a58-503">**classlib**</span><span class="sxs-lookup"><span data-stu-id="22a58-503">**classlib**</span></span>

<span data-ttu-id="22a58-504">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="22a58-504">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="22a58-505">Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="22a58-505">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="22a58-506">O valor padrão é `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="22a58-506">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="22a58-507">**mvc**</span><span class="sxs-lookup"><span data-stu-id="22a58-507">**mvc**</span></span>

<span data-ttu-id="22a58-508">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="22a58-508">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="22a58-509">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="22a58-509">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="22a58-510">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="22a58-510">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="22a58-511">`-au|--auth` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="22a58-511">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="22a58-512">Valores: `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="22a58-512">Values: `None` or `Individual`.</span></span> <span data-ttu-id="22a58-513">O valor padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="22a58-513">The default value is `None`.</span></span>

<span data-ttu-id="22a58-514">`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="22a58-514">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="22a58-515">Valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="22a58-515">Values: `true` or `false`.</span></span> <span data-ttu-id="22a58-516">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="22a58-516">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="22a58-517">Exemplos</span><span class="sxs-lookup"><span data-stu-id="22a58-517">Examples</span></span>

<span data-ttu-id="22a58-518">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="22a58-518">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="22a58-519">Crie um projeto de biblioteca de classes .NET Standard no diretório especificado (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="22a58-519">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="22a58-520">Crie um novo projeto de aplicativo de MVC C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="22a58-520">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="22a58-521">Crie um novo aplicativo xUnit:</span><span class="sxs-lookup"><span data-stu-id="22a58-521">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="22a58-522">Lista todos os modelos disponíveis para o MVC:</span><span class="sxs-lookup"><span data-stu-id="22a58-522">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="22a58-523">Instale a versão 2.0 dos modelos de aplicativo de página única do ASP.NET Core (opção de comando disponível somente para o SDK do .NET Core 1.1 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="22a58-523">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="22a58-524">Crie um *global.json* no diretório atual definindo a versão do SDK como 2.0.0 (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="22a58-524">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="22a58-525">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22a58-525">See also</span></span>

* [<span data-ttu-id="22a58-526">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="22a58-526">Custom templates for dotnet new</span></span>](custom-templates.md)  
* <span data-ttu-id="22a58-527">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="22a58-527">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md)</span></span>  
* [<span data-ttu-id="22a58-528">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="22a58-528">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
* [<span data-ttu-id="22a58-529">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="22a58-529">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
