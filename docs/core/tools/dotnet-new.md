---
title: Comando dotnet new
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
ms.date: 10/24/2018
ms.openlocfilehash: 5177c920fee6fa946d2bf5d96644f26309ed0a99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516142"
---
# <a name="dotnet-new"></a><span data-ttu-id="6aa78-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="6aa78-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="6aa78-104">Nome</span><span class="sxs-lookup"><span data-stu-id="6aa78-104">Name</span></span>

<span data-ttu-id="6aa78-105">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6aa78-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="6aa78-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6aa78-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6aa78-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6aa78-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="6aa78-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6aa78-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6aa78-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="6aa78-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="6aa78-110">Description</span></span>

<span data-ttu-id="6aa78-111">O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido.</span><span class="sxs-lookup"><span data-stu-id="6aa78-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="6aa78-112">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="6aa78-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="6aa78-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="6aa78-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="6aa78-114">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="6aa78-115">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="6aa78-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="6aa78-116">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="6aa78-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6aa78-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6aa78-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="6aa78-118">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="6aa78-118">The command contains a default list of templates.</span></span> <span data-ttu-id="6aa78-119">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6aa78-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="6aa78-120">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="6aa78-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="6aa78-121">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="6aa78-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="6aa78-122">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="6aa78-122">Template description</span></span>                          | <span data-ttu-id="6aa78-123">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="6aa78-123">Template name</span></span>    | <span data-ttu-id="6aa78-124">Linguagens</span><span class="sxs-lookup"><span data-stu-id="6aa78-124">Languages</span></span>     |
|----------------------------------------------|------------------|---------------|
| <span data-ttu-id="6aa78-125">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="6aa78-125">Console application</span></span>                          | `console`        | <span data-ttu-id="6aa78-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6aa78-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6aa78-127">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="6aa78-127">Class library</span></span>                                | `classlib`       | <span data-ttu-id="6aa78-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6aa78-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6aa78-129">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="6aa78-129">Unit test project</span></span>                            | `mstest`         | <span data-ttu-id="6aa78-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6aa78-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6aa78-131">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="6aa78-131">xUnit test project</span></span>                           | `xunit`          | <span data-ttu-id="6aa78-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6aa78-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6aa78-133">Projeto de teste da NUnit</span><span class="sxs-lookup"><span data-stu-id="6aa78-133">NUnit test project</span></span>                           | `nunit`          | <span data-ttu-id="6aa78-134">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6aa78-134">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6aa78-135">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="6aa78-135">Razor page</span></span>                                   | `page`           | <span data-ttu-id="6aa78-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="6aa78-136">[C#]</span></span>          |
| <span data-ttu-id="6aa78-137">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="6aa78-137">MVC ViewImports</span></span>                              | `viewimports`    | <span data-ttu-id="6aa78-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="6aa78-138">[C#]</span></span>          |
| <span data-ttu-id="6aa78-139">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="6aa78-139">MVC ViewStart</span></span>                                | `viewstart`      | <span data-ttu-id="6aa78-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="6aa78-140">[C#]</span></span>          |
| <span data-ttu-id="6aa78-141">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="6aa78-141">ASP.NET Core empty</span></span>                           | `web`            | <span data-ttu-id="6aa78-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6aa78-142">[C#], F#</span></span>      |
| <span data-ttu-id="6aa78-143">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="6aa78-143">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`            | <span data-ttu-id="6aa78-144">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6aa78-144">[C#], F#</span></span>      |
| <span data-ttu-id="6aa78-145">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6aa78-145">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="6aa78-146">`razor`, `webapp`</span><span class="sxs-lookup"><span data-stu-id="6aa78-146">`razor`, `webapp`</span></span>| <span data-ttu-id="6aa78-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="6aa78-147">[C#]</span></span>          |
| <span data-ttu-id="6aa78-148">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="6aa78-148">ASP.NET Core with Angular</span></span>                    | `angular`        | <span data-ttu-id="6aa78-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="6aa78-149">[C#]</span></span>          |
| <span data-ttu-id="6aa78-150">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="6aa78-150">ASP.NET Core with React.js</span></span>                   | `react`          | <span data-ttu-id="6aa78-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="6aa78-151">[C#]</span></span>          |
| <span data-ttu-id="6aa78-152">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="6aa78-152">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`     | <span data-ttu-id="6aa78-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="6aa78-153">[C#]</span></span>          |
| <span data-ttu-id="6aa78-154">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6aa78-154">ASP.NET Core Web API</span></span>                         | `webapi`         | <span data-ttu-id="6aa78-155">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6aa78-155">[C#], F#</span></span>      |
| <span data-ttu-id="6aa78-156">Biblioteca de classes Razor</span><span class="sxs-lookup"><span data-stu-id="6aa78-156">Razor class library</span></span>                          | `razorclasslib`  | <span data-ttu-id="6aa78-157">[C#]</span><span class="sxs-lookup"><span data-stu-id="6aa78-157">[C#]</span></span>          |
| <span data-ttu-id="6aa78-158">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="6aa78-158">global.json file</span></span>                             | `globaljson`     |               |
| <span data-ttu-id="6aa78-159">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="6aa78-159">NuGet config</span></span>                                 | `nugetconfig`    |               |
| <span data-ttu-id="6aa78-160">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="6aa78-160">Web config</span></span>                                   | `webconfig`      |               |
| <span data-ttu-id="6aa78-161">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="6aa78-161">Solution file</span></span>                                | `sln`            |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6aa78-162">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="6aa78-162">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="6aa78-163">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="6aa78-163">The command contains a default list of templates.</span></span> <span data-ttu-id="6aa78-164">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6aa78-164">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="6aa78-165">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="6aa78-165">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="6aa78-166">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="6aa78-166">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="6aa78-167">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="6aa78-167">Template description</span></span>                          | <span data-ttu-id="6aa78-168">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="6aa78-168">Template name</span></span> | <span data-ttu-id="6aa78-169">Linguagens</span><span class="sxs-lookup"><span data-stu-id="6aa78-169">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="6aa78-170">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="6aa78-170">Console application</span></span>                          | `console`     | <span data-ttu-id="6aa78-171">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6aa78-171">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6aa78-172">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="6aa78-172">Class library</span></span>                                | `classlib`    | <span data-ttu-id="6aa78-173">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6aa78-173">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6aa78-174">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="6aa78-174">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="6aa78-175">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6aa78-175">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6aa78-176">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="6aa78-176">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="6aa78-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="6aa78-177">[C#], F#, VB</span></span>  |
| <span data-ttu-id="6aa78-178">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="6aa78-178">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="6aa78-179">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6aa78-179">[C#], F#</span></span>      |
| <span data-ttu-id="6aa78-180">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="6aa78-180">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="6aa78-181">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6aa78-181">[C#], F#</span></span>      |
| <span data-ttu-id="6aa78-182">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6aa78-182">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="6aa78-183">[C#]</span><span class="sxs-lookup"><span data-stu-id="6aa78-183">[C#]</span></span>          |
| <span data-ttu-id="6aa78-184">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="6aa78-184">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="6aa78-185">[C#]</span><span class="sxs-lookup"><span data-stu-id="6aa78-185">[C#]</span></span>          |
| <span data-ttu-id="6aa78-186">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="6aa78-186">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="6aa78-187">[C#]</span><span class="sxs-lookup"><span data-stu-id="6aa78-187">[C#]</span></span>          |
| <span data-ttu-id="6aa78-188">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="6aa78-188">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="6aa78-189">[C#]</span><span class="sxs-lookup"><span data-stu-id="6aa78-189">[C#]</span></span>          |
| <span data-ttu-id="6aa78-190">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6aa78-190">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="6aa78-191">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6aa78-191">[C#], F#</span></span>      |
| <span data-ttu-id="6aa78-192">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="6aa78-192">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="6aa78-193">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="6aa78-193">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="6aa78-194">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="6aa78-194">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="6aa78-195">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="6aa78-195">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="6aa78-196">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="6aa78-196">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="6aa78-197">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="6aa78-197">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="6aa78-198">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="6aa78-198">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6aa78-199">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6aa78-199">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="6aa78-200">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="6aa78-200">The command contains a default list of templates.</span></span> <span data-ttu-id="6aa78-201">Use `dotnet new -all` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6aa78-201">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="6aa78-202">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="6aa78-202">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="6aa78-203">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="6aa78-203">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="6aa78-204">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="6aa78-204">Template description</span></span>  | <span data-ttu-id="6aa78-205">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="6aa78-205">Template name</span></span> | <span data-ttu-id="6aa78-206">Linguagens</span><span class="sxs-lookup"><span data-stu-id="6aa78-206">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="6aa78-207">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="6aa78-207">Console application</span></span>  | `console`     | <span data-ttu-id="6aa78-208">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6aa78-208">[C#], F#</span></span>  |
| <span data-ttu-id="6aa78-209">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="6aa78-209">Class library</span></span>        | `classlib`    | <span data-ttu-id="6aa78-210">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6aa78-210">[C#], F#</span></span>  |
| <span data-ttu-id="6aa78-211">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="6aa78-211">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="6aa78-212">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6aa78-212">[C#], F#</span></span>  |
| <span data-ttu-id="6aa78-213">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="6aa78-213">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="6aa78-214">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6aa78-214">[C#], F#</span></span>  |
| <span data-ttu-id="6aa78-215">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="6aa78-215">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="6aa78-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="6aa78-216">[C#]</span></span>      |
| <span data-ttu-id="6aa78-217">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6aa78-217">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="6aa78-218">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="6aa78-218">[C#], F#</span></span>  |
| <span data-ttu-id="6aa78-219">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6aa78-219">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="6aa78-220">[C#]</span><span class="sxs-lookup"><span data-stu-id="6aa78-220">[C#]</span></span>      |
| <span data-ttu-id="6aa78-221">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="6aa78-221">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="6aa78-222">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="6aa78-222">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="6aa78-223">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="6aa78-223">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="6aa78-224">Opções</span><span class="sxs-lookup"><span data-stu-id="6aa78-224">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6aa78-225">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6aa78-225">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="6aa78-226">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="6aa78-226">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="6aa78-227">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-227">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="6aa78-228">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="6aa78-228">Prints out help for the command.</span></span> <span data-ttu-id="6aa78-229">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-229">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="6aa78-230">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="6aa78-230">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6aa78-231">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-231">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="6aa78-232">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="6aa78-232">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="6aa78-233">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="6aa78-233">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="6aa78-234">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="6aa78-234">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="6aa78-235">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-235">Lists templates containing the specified name.</span></span> <span data-ttu-id="6aa78-236">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-236">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="6aa78-237">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-237">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="6aa78-238">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="6aa78-238">The language of the template to create.</span></span> <span data-ttu-id="6aa78-239">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="6aa78-239">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6aa78-240">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="6aa78-240">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="6aa78-241">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="6aa78-241">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="6aa78-242">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-242">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="6aa78-243">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="6aa78-243">The name for the created output.</span></span> <span data-ttu-id="6aa78-244">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-244">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="6aa78-245">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="6aa78-245">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6aa78-246">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="6aa78-246">Location to place the generated output.</span></span> <span data-ttu-id="6aa78-247">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="6aa78-247">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="6aa78-248">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6aa78-248">Filters templates based on available types.</span></span> <span data-ttu-id="6aa78-249">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="6aa78-249">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="6aa78-250">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="6aa78-250">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="6aa78-251">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="6aa78-251">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="6aa78-252">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="6aa78-252">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="6aa78-253">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="6aa78-253">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6aa78-254">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="6aa78-254">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="6aa78-255">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="6aa78-255">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="6aa78-256">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-256">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="6aa78-257">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="6aa78-257">Prints out help for the command.</span></span> <span data-ttu-id="6aa78-258">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-258">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="6aa78-259">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="6aa78-259">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="6aa78-260">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-260">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="6aa78-261">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="6aa78-261">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="6aa78-262">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="6aa78-262">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="6aa78-263">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="6aa78-263">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="6aa78-264">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-264">Lists templates containing the specified name.</span></span> <span data-ttu-id="6aa78-265">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-265">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="6aa78-266">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-266">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="6aa78-267">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="6aa78-267">The language of the template to create.</span></span> <span data-ttu-id="6aa78-268">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="6aa78-268">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6aa78-269">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="6aa78-269">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="6aa78-270">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="6aa78-270">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="6aa78-271">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-271">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="6aa78-272">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="6aa78-272">The name for the created output.</span></span> <span data-ttu-id="6aa78-273">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-273">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6aa78-274">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="6aa78-274">Location to place the generated output.</span></span> <span data-ttu-id="6aa78-275">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="6aa78-275">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="6aa78-276">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6aa78-276">Filters templates based on available types.</span></span> <span data-ttu-id="6aa78-277">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="6aa78-277">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="6aa78-278">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="6aa78-278">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="6aa78-279">Para desinstalar um modelo usando uma origem `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="6aa78-279">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="6aa78-280">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="6aa78-280">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="6aa78-281">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="6aa78-281">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="6aa78-282">Se não for possível determinar o argumento `PATH` ou `NUGET_ID` necessário para desinstalar um modelo, executar `dotnet new --uninstall` sem um argumento listará todos os modelos instalados e o argumento necessário desinstalá-los.</span><span class="sxs-lookup"><span data-stu-id="6aa78-282">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6aa78-283">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6aa78-283">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="6aa78-284">Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-284">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="6aa78-285">Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força.</span><span class="sxs-lookup"><span data-stu-id="6aa78-285">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="6aa78-286">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-286">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="6aa78-287">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="6aa78-287">Prints out help for the command.</span></span> <span data-ttu-id="6aa78-288">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-288">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="6aa78-289">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-289">Lists templates containing the specified name.</span></span> <span data-ttu-id="6aa78-290">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-290">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="6aa78-291">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-291">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="6aa78-292">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="6aa78-292">The language of the template to create.</span></span> <span data-ttu-id="6aa78-293">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="6aa78-293">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="6aa78-294">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="6aa78-294">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="6aa78-295">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="6aa78-295">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="6aa78-296">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-296">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="6aa78-297">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="6aa78-297">The name for the created output.</span></span> <span data-ttu-id="6aa78-298">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-298">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6aa78-299">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="6aa78-299">Location to place the generated output.</span></span> <span data-ttu-id="6aa78-300">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="6aa78-300">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="6aa78-301">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="6aa78-301">Template options</span></span>

<span data-ttu-id="6aa78-302">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6aa78-302">Each project template may have additional options available.</span></span> <span data-ttu-id="6aa78-303">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="6aa78-303">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6aa78-304">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6aa78-304">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="6aa78-305">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="6aa78-305">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="6aa78-306">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-306">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6aa78-307">**classlib**</span><span class="sxs-lookup"><span data-stu-id="6aa78-307">**classlib**</span></span>

<span data-ttu-id="6aa78-308">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="6aa78-308">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6aa78-309">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="6aa78-309">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="6aa78-310">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-310">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="6aa78-311">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-311">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6aa78-312">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="6aa78-312">**mstest, xunit**</span></span>

<span data-ttu-id="6aa78-313">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6aa78-313">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="6aa78-314">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-314">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6aa78-315">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="6aa78-315">**globaljson**</span></span>

<span data-ttu-id="6aa78-316">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="6aa78-316">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="6aa78-317">**web**</span><span class="sxs-lookup"><span data-stu-id="6aa78-317">**web**</span></span>

<span data-ttu-id="6aa78-318">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-318">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6aa78-319">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-319">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6aa78-320">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6aa78-320">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6aa78-321">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-321">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="6aa78-322">**webapi**</span><span class="sxs-lookup"><span data-stu-id="6aa78-322">**webapi**</span></span>

<span data-ttu-id="6aa78-323">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-323">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6aa78-324">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="6aa78-324">The possible values are:</span></span>

- <span data-ttu-id="6aa78-325">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="6aa78-325">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6aa78-326">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6aa78-326">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6aa78-327">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="6aa78-327">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6aa78-328">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="6aa78-328">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6aa78-329">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6aa78-329">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6aa78-330">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-330">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6aa78-331">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-331">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6aa78-332">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-332">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6aa78-333">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-333">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6aa78-334">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6aa78-334">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6aa78-335">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-335">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6aa78-336">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-336">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6aa78-337">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-337">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6aa78-338">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-338">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="6aa78-339">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-339">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6aa78-340">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="6aa78-340">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6aa78-341">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-341">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6aa78-342">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-342">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6aa78-343">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6aa78-343">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6aa78-344">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-344">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6aa78-345">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-345">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6aa78-346">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="6aa78-346">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6aa78-347">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-347">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6aa78-348">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-348">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6aa78-349">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="6aa78-349">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6aa78-350">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-350">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6aa78-351">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-351">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6aa78-352">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6aa78-352">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6aa78-353">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-353">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="6aa78-354">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="6aa78-354">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="6aa78-355">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="6aa78-355">**mvc, razor**</span></span>

<span data-ttu-id="6aa78-356">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-356">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6aa78-357">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="6aa78-357">The possible values are:</span></span>

- <span data-ttu-id="6aa78-358">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="6aa78-358">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6aa78-359">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="6aa78-359">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="6aa78-360">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6aa78-360">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6aa78-361">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="6aa78-361">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6aa78-362">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="6aa78-362">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="6aa78-363">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="6aa78-363">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6aa78-364">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6aa78-364">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6aa78-365">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-365">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6aa78-366">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-366">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6aa78-367">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-367">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6aa78-368">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-368">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6aa78-369">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-369">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="6aa78-370">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-370">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6aa78-371">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-371">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="6aa78-372">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-372">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6aa78-373">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6aa78-373">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6aa78-374">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-374">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="6aa78-375">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-375">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6aa78-376">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-376">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6aa78-377">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-377">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="6aa78-378">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-378">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6aa78-379">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="6aa78-379">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6aa78-380">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-380">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6aa78-381">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-381">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6aa78-382">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6aa78-382">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6aa78-383">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-383">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6aa78-384">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-384">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6aa78-385">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="6aa78-385">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="6aa78-386">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-386">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6aa78-387">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-387">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="6aa78-388">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="6aa78-388">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6aa78-389">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-389">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6aa78-390">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-390">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="6aa78-391">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-391">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="6aa78-392">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="6aa78-392">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6aa78-393">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-393">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6aa78-394">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-394">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6aa78-395">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6aa78-395">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="6aa78-396">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-396">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="6aa78-397">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="6aa78-397">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="6aa78-398">**page**</span><span class="sxs-lookup"><span data-stu-id="6aa78-398">**page**</span></span>

<span data-ttu-id="6aa78-399">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-399">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="6aa78-400">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-400">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="6aa78-401">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="6aa78-401">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="6aa78-402">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="6aa78-402">**viewimports**</span></span>

<span data-ttu-id="6aa78-403">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-403">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="6aa78-404">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-404">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6aa78-405">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="6aa78-405">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="6aa78-406">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="6aa78-406">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="6aa78-407">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-407">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6aa78-408">**classlib**</span><span class="sxs-lookup"><span data-stu-id="6aa78-408">**classlib**</span></span>

<span data-ttu-id="6aa78-409">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="6aa78-409">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6aa78-410">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="6aa78-410">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="6aa78-411">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-411">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="6aa78-412">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-412">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6aa78-413">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="6aa78-413">**mstest, xunit**</span></span>

<span data-ttu-id="6aa78-414">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6aa78-414">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="6aa78-415">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-415">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6aa78-416">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="6aa78-416">**globaljson**</span></span>

<span data-ttu-id="6aa78-417">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="6aa78-417">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="6aa78-418">**web**</span><span class="sxs-lookup"><span data-stu-id="6aa78-418">**web**</span></span>

<span data-ttu-id="6aa78-419">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-419">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="6aa78-420">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-420">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6aa78-421">**webapi**</span><span class="sxs-lookup"><span data-stu-id="6aa78-421">**webapi**</span></span>

<span data-ttu-id="6aa78-422">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-422">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6aa78-423">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="6aa78-423">The possible values are:</span></span>

- <span data-ttu-id="6aa78-424">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="6aa78-424">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6aa78-425">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6aa78-425">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6aa78-426">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="6aa78-426">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6aa78-427">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="6aa78-427">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6aa78-428">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6aa78-428">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6aa78-429">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-429">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6aa78-430">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-430">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6aa78-431">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-431">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6aa78-432">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-432">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6aa78-433">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6aa78-433">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6aa78-434">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-434">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6aa78-435">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-435">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6aa78-436">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-436">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6aa78-437">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-437">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="6aa78-438">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-438">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6aa78-439">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="6aa78-439">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6aa78-440">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-440">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6aa78-441">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-441">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6aa78-442">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6aa78-442">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6aa78-443">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-443">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6aa78-444">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-444">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6aa78-445">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="6aa78-445">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6aa78-446">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-446">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6aa78-447">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-447">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="6aa78-448">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="6aa78-448">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6aa78-449">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-449">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6aa78-450">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-450">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6aa78-451">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="6aa78-451">**mvc, razor**</span></span>

<span data-ttu-id="6aa78-452">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-452">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="6aa78-453">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="6aa78-453">The possible values are:</span></span>

- <span data-ttu-id="6aa78-454">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="6aa78-454">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="6aa78-455">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="6aa78-455">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="6aa78-456">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="6aa78-456">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="6aa78-457">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="6aa78-457">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="6aa78-458">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="6aa78-458">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="6aa78-459">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="6aa78-459">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="6aa78-460">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6aa78-460">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="6aa78-461">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-461">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="6aa78-462">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-462">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="6aa78-463">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-463">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="6aa78-464">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-464">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6aa78-465">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-465">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="6aa78-466">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-466">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6aa78-467">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-467">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="6aa78-468">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-468">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6aa78-469">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6aa78-469">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="6aa78-470">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-470">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="6aa78-471">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-471">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="6aa78-472">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-472">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="6aa78-473">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-473">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="6aa78-474">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-474">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="6aa78-475">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="6aa78-475">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="6aa78-476">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-476">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6aa78-477">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-477">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="6aa78-478">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="6aa78-478">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="6aa78-479">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-479">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="6aa78-480">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-480">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="6aa78-481">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="6aa78-481">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="6aa78-482">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-482">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="6aa78-483">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-483">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="6aa78-484">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="6aa78-484">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="6aa78-485">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-485">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="6aa78-486">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-486">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="6aa78-487">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-487">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="6aa78-488">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="6aa78-488">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="6aa78-489">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-489">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="6aa78-490">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6aa78-490">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="6aa78-491">**page**</span><span class="sxs-lookup"><span data-stu-id="6aa78-491">**page**</span></span>

<span data-ttu-id="6aa78-492">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-492">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="6aa78-493">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-493">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="6aa78-494">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="6aa78-494">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="6aa78-495">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="6aa78-495">**viewimports**</span></span>

<span data-ttu-id="6aa78-496">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-496">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="6aa78-497">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-497">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6aa78-498">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6aa78-498">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="6aa78-499">**console, xunit, mstest, web, webapi** </span><span class="sxs-lookup"><span data-stu-id="6aa78-499">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="6aa78-500">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="6aa78-500">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6aa78-501">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-501">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="6aa78-502">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-502">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="6aa78-503">**classlib**</span><span class="sxs-lookup"><span data-stu-id="6aa78-503">**classlib**</span></span>

<span data-ttu-id="6aa78-504">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="6aa78-504">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6aa78-505">Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-505">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="6aa78-506">O valor padrão é `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-506">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="6aa78-507">**mvc**</span><span class="sxs-lookup"><span data-stu-id="6aa78-507">**mvc**</span></span>

<span data-ttu-id="6aa78-508">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="6aa78-508">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="6aa78-509">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-509">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="6aa78-510">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-510">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="6aa78-511">`-au|--auth` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="6aa78-511">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="6aa78-512">Valores: `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-512">Values: `None` or `Individual`.</span></span> <span data-ttu-id="6aa78-513">O valor padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-513">The default value is `None`.</span></span>

<span data-ttu-id="6aa78-514">`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="6aa78-514">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="6aa78-515">Valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-515">Values: `true` or `false`.</span></span> <span data-ttu-id="6aa78-516">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="6aa78-516">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="6aa78-517">Exemplos</span><span class="sxs-lookup"><span data-stu-id="6aa78-517">Examples</span></span>

<span data-ttu-id="6aa78-518">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="6aa78-518">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="6aa78-519">Crie um projeto de biblioteca de classes .NET Standard no diretório especificado (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="6aa78-519">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="6aa78-520">Crie um novo projeto de aplicativo de MVC C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="6aa78-520">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="6aa78-521">Crie um novo aplicativo xUnit:</span><span class="sxs-lookup"><span data-stu-id="6aa78-521">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="6aa78-522">Lista todos os modelos disponíveis para o MVC:</span><span class="sxs-lookup"><span data-stu-id="6aa78-522">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="6aa78-523">Instale a versão 2.0 dos modelos de aplicativo de página única do ASP.NET Core (opção de comando disponível somente para o SDK do .NET Core 1.1 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="6aa78-523">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="6aa78-524">Crie um *global.json* no diretório atual definindo a versão do SDK como 2.0.0 (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="6aa78-524">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="6aa78-525">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6aa78-525">See also</span></span>

- [<span data-ttu-id="6aa78-526">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="6aa78-526">Custom templates for dotnet new</span></span>](custom-templates.md)
- <span data-ttu-id="6aa78-527">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="6aa78-527">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md)</span></span>
- [<span data-ttu-id="6aa78-528">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="6aa78-528">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="6aa78-529">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="6aa78-529">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
