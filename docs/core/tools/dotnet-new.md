---
title: Comando dotnet new
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
ms.date: 05/06/2019
ms.openlocfilehash: c9e960bab0e28e88b0cc8d431dad3b9f3f00c9c0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660549"
---
# <a name="dotnet-new"></a><span data-ttu-id="ba865-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="ba865-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ba865-104">Nome</span><span class="sxs-lookup"><span data-stu-id="ba865-104">Name</span></span>

<span data-ttu-id="ba865-105">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="ba865-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ba865-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="ba865-106">Synopsis</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="ba865-107">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ba865-107">.NET Core 2.2</span></span>](#tab/netcore22)

```console
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ba865-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ba865-108">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ba865-109">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ba865-109">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ba865-110">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ba865-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="ba865-111">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="ba865-111">Description</span></span>

<span data-ttu-id="ba865-112">O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido.</span><span class="sxs-lookup"><span data-stu-id="ba865-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="ba865-113">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="ba865-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="ba865-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="ba865-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="ba865-115">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="ba865-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="ba865-116">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="ba865-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="ba865-117">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="ba865-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="ba865-118">Se o valor `TEMPLATE` não for uma correspondência exata no texto na coluna **Modelos** ou **Nome Curto**, uma correspondência de substring será executada nessas duas colunas.</span><span class="sxs-lookup"><span data-stu-id="ba865-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="ba865-119">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ba865-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="ba865-120">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="ba865-120">The command contains a default list of templates.</span></span> <span data-ttu-id="ba865-121">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ba865-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="ba865-122">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.2.100.</span><span class="sxs-lookup"><span data-stu-id="ba865-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="ba865-123">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="ba865-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="ba865-124">Modelos</span><span class="sxs-lookup"><span data-stu-id="ba865-124">Templates</span></span>                                    | <span data-ttu-id="ba865-125">Nome curto</span><span class="sxs-lookup"><span data-stu-id="ba865-125">Short Name</span></span>        | <span data-ttu-id="ba865-126">Idioma</span><span class="sxs-lookup"><span data-stu-id="ba865-126">Language</span></span>     | <span data-ttu-id="ba865-127">Marcas</span><span class="sxs-lookup"><span data-stu-id="ba865-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="ba865-128">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="ba865-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="ba865-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ba865-129">[C#], F#, VB</span></span> | <span data-ttu-id="ba865-130">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="ba865-130">Common/Console</span></span>                        |
| <span data-ttu-id="ba865-131">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="ba865-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="ba865-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ba865-132">[C#], F#, VB</span></span> | <span data-ttu-id="ba865-133">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="ba865-133">Common/Library</span></span>                        |
| <span data-ttu-id="ba865-134">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="ba865-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="ba865-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ba865-135">[C#], F#, VB</span></span> | <span data-ttu-id="ba865-136">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="ba865-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="ba865-137">Projeto de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="ba865-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="ba865-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ba865-138">[C#], F#, VB</span></span> | <span data-ttu-id="ba865-139">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="ba865-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="ba865-140">Item de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="ba865-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="ba865-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ba865-141">[C#], F#, VB</span></span> | <span data-ttu-id="ba865-142">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="ba865-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="ba865-143">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="ba865-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="ba865-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ba865-144">[C#], F#, VB</span></span> | <span data-ttu-id="ba865-145">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="ba865-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="ba865-146">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="ba865-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="ba865-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-147">[C#]</span></span>         | <span data-ttu-id="ba865-148">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ba865-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="ba865-149">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="ba865-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="ba865-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-150">[C#]</span></span>         | <span data-ttu-id="ba865-151">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ba865-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="ba865-152">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="ba865-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="ba865-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-153">[C#]</span></span>         | <span data-ttu-id="ba865-154">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ba865-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="ba865-155">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="ba865-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="ba865-156">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ba865-156">[C#], F#</span></span>     | <span data-ttu-id="ba865-157">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="ba865-157">Web/Empty</span></span>                             |
| <span data-ttu-id="ba865-158">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="ba865-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="ba865-159">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ba865-159">[C#], F#</span></span>     | <span data-ttu-id="ba865-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="ba865-160">Web/MVC</span></span>                               |
| <span data-ttu-id="ba865-161">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ba865-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="ba865-162">`webapp`, `razor`</span><span class="sxs-lookup"><span data-stu-id="ba865-162">`webapp`, `razor`</span></span> | <span data-ttu-id="ba865-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-163">[C#]</span></span>         | <span data-ttu-id="ba865-164">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="ba865-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="ba865-165">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="ba865-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="ba865-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-166">[C#]</span></span>         | <span data-ttu-id="ba865-167">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ba865-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="ba865-168">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="ba865-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="ba865-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-169">[C#]</span></span>         | <span data-ttu-id="ba865-170">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ba865-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="ba865-171">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="ba865-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="ba865-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-172">[C#]</span></span>         | <span data-ttu-id="ba865-173">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ba865-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="ba865-174">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="ba865-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="ba865-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-175">[C#]</span></span>         | <span data-ttu-id="ba865-176">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="ba865-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="ba865-177">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ba865-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="ba865-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ba865-178">[C#], F#</span></span>     | <span data-ttu-id="ba865-179">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="ba865-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="ba865-180">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="ba865-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="ba865-181">Config</span><span class="sxs-lookup"><span data-stu-id="ba865-181">Config</span></span>                                |
| <span data-ttu-id="ba865-182">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="ba865-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="ba865-183">Config</span><span class="sxs-lookup"><span data-stu-id="ba865-183">Config</span></span>                                |
| <span data-ttu-id="ba865-184">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="ba865-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="ba865-185">Config</span><span class="sxs-lookup"><span data-stu-id="ba865-185">Config</span></span>                                |
| <span data-ttu-id="ba865-186">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="ba865-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="ba865-187">Solução</span><span class="sxs-lookup"><span data-stu-id="ba865-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ba865-188">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ba865-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="ba865-189">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="ba865-189">The command contains a default list of templates.</span></span> <span data-ttu-id="ba865-190">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ba865-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="ba865-191">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="ba865-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="ba865-192">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="ba865-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="ba865-193">Modelos</span><span class="sxs-lookup"><span data-stu-id="ba865-193">Templates</span></span>                                    | <span data-ttu-id="ba865-194">Nome curto</span><span class="sxs-lookup"><span data-stu-id="ba865-194">Short Name</span></span>      | <span data-ttu-id="ba865-195">Idioma</span><span class="sxs-lookup"><span data-stu-id="ba865-195">Language</span></span>     | <span data-ttu-id="ba865-196">Marcas</span><span class="sxs-lookup"><span data-stu-id="ba865-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="ba865-197">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="ba865-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="ba865-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ba865-198">[C#], F#, VB</span></span> | <span data-ttu-id="ba865-199">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="ba865-199">Common/Console</span></span>                        |
| <span data-ttu-id="ba865-200">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="ba865-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="ba865-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ba865-201">[C#], F#, VB</span></span> | <span data-ttu-id="ba865-202">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="ba865-202">Common/Library</span></span>                        |
| <span data-ttu-id="ba865-203">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="ba865-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="ba865-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ba865-204">[C#], F#, VB</span></span> | <span data-ttu-id="ba865-205">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="ba865-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="ba865-206">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="ba865-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="ba865-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ba865-207">[C#], F#, VB</span></span> | <span data-ttu-id="ba865-208">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="ba865-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="ba865-209">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="ba865-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="ba865-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-210">[C#]</span></span>         | <span data-ttu-id="ba865-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ba865-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="ba865-212">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="ba865-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="ba865-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-213">[C#]</span></span>         | <span data-ttu-id="ba865-214">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ba865-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="ba865-215">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="ba865-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="ba865-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-216">[C#]</span></span>         | <span data-ttu-id="ba865-217">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ba865-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="ba865-218">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="ba865-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="ba865-219">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ba865-219">[C#], F#</span></span>     | <span data-ttu-id="ba865-220">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="ba865-220">Web/Empty</span></span>                             |
| <span data-ttu-id="ba865-221">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="ba865-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="ba865-222">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ba865-222">[C#], F#</span></span>     | <span data-ttu-id="ba865-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="ba865-223">Web/MVC</span></span>                               |
| <span data-ttu-id="ba865-224">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ba865-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="ba865-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-225">[C#]</span></span>         | <span data-ttu-id="ba865-226">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="ba865-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="ba865-227">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="ba865-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="ba865-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-228">[C#]</span></span>         | <span data-ttu-id="ba865-229">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ba865-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="ba865-230">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="ba865-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="ba865-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-231">[C#]</span></span>         | <span data-ttu-id="ba865-232">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ba865-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="ba865-233">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="ba865-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="ba865-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-234">[C#]</span></span>         | <span data-ttu-id="ba865-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ba865-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="ba865-236">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="ba865-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="ba865-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-237">[C#]</span></span>         | <span data-ttu-id="ba865-238">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="ba865-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="ba865-239">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ba865-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="ba865-240">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ba865-240">[C#], F#</span></span>     | <span data-ttu-id="ba865-241">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="ba865-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="ba865-242">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="ba865-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="ba865-243">Config</span><span class="sxs-lookup"><span data-stu-id="ba865-243">Config</span></span>                                |
| <span data-ttu-id="ba865-244">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="ba865-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="ba865-245">Config</span><span class="sxs-lookup"><span data-stu-id="ba865-245">Config</span></span>                                |
| <span data-ttu-id="ba865-246">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="ba865-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="ba865-247">Config</span><span class="sxs-lookup"><span data-stu-id="ba865-247">Config</span></span>                                |
| <span data-ttu-id="ba865-248">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="ba865-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="ba865-249">Solução</span><span class="sxs-lookup"><span data-stu-id="ba865-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ba865-250">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ba865-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="ba865-251">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="ba865-251">The command contains a default list of templates.</span></span> <span data-ttu-id="ba865-252">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ba865-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="ba865-253">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="ba865-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="ba865-254">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="ba865-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="ba865-255">Modelos</span><span class="sxs-lookup"><span data-stu-id="ba865-255">Templates</span></span>                                    | <span data-ttu-id="ba865-256">Nome curto</span><span class="sxs-lookup"><span data-stu-id="ba865-256">Short Name</span></span>    | <span data-ttu-id="ba865-257">Idioma</span><span class="sxs-lookup"><span data-stu-id="ba865-257">Language</span></span>     | <span data-ttu-id="ba865-258">Marcas</span><span class="sxs-lookup"><span data-stu-id="ba865-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="ba865-259">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="ba865-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="ba865-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ba865-260">[C#], F#, VB</span></span> | <span data-ttu-id="ba865-261">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="ba865-261">Common/Console</span></span>      |
| <span data-ttu-id="ba865-262">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="ba865-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="ba865-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ba865-263">[C#], F#, VB</span></span> | <span data-ttu-id="ba865-264">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="ba865-264">Common/Library</span></span>      |
| <span data-ttu-id="ba865-265">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="ba865-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="ba865-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ba865-266">[C#], F#, VB</span></span> | <span data-ttu-id="ba865-267">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="ba865-267">Test/MSTest</span></span>         |
| <span data-ttu-id="ba865-268">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="ba865-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="ba865-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="ba865-269">[C#], F#, VB</span></span> | <span data-ttu-id="ba865-270">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="ba865-270">Test/xUnit</span></span>          |
| <span data-ttu-id="ba865-271">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="ba865-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="ba865-272">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ba865-272">[C#], F#</span></span>     | <span data-ttu-id="ba865-273">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="ba865-273">Web/Empty</span></span>           |
| <span data-ttu-id="ba865-274">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="ba865-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="ba865-275">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ba865-275">[C#], F#</span></span>     | <span data-ttu-id="ba865-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="ba865-276">Web/MVC</span></span>             |
| <span data-ttu-id="ba865-277">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ba865-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="ba865-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-278">[C#]</span></span>         | <span data-ttu-id="ba865-279">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="ba865-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="ba865-280">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="ba865-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="ba865-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-281">[C#]</span></span>         | <span data-ttu-id="ba865-282">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ba865-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="ba865-283">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="ba865-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="ba865-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-284">[C#]</span></span>         | <span data-ttu-id="ba865-285">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ba865-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="ba865-286">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="ba865-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="ba865-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-287">[C#]</span></span>         | <span data-ttu-id="ba865-288">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="ba865-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="ba865-289">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ba865-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="ba865-290">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ba865-290">[C#], F#</span></span>     | <span data-ttu-id="ba865-291">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="ba865-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="ba865-292">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="ba865-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="ba865-293">Config</span><span class="sxs-lookup"><span data-stu-id="ba865-293">Config</span></span>              |
| <span data-ttu-id="ba865-294">Configuração do Nuget</span><span class="sxs-lookup"><span data-stu-id="ba865-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="ba865-295">Config</span><span class="sxs-lookup"><span data-stu-id="ba865-295">Config</span></span>              |
| <span data-ttu-id="ba865-296">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="ba865-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="ba865-297">Config</span><span class="sxs-lookup"><span data-stu-id="ba865-297">Config</span></span>              |
| <span data-ttu-id="ba865-298">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="ba865-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="ba865-299">Solução</span><span class="sxs-lookup"><span data-stu-id="ba865-299">Solution</span></span>            |
| <span data-ttu-id="ba865-300">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="ba865-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="ba865-301">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ba865-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="ba865-302">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="ba865-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="ba865-303">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ba865-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="ba865-304">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="ba865-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="ba865-305">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ba865-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ba865-306">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ba865-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ba865-307">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="ba865-307">The command contains a default list of templates.</span></span> <span data-ttu-id="ba865-308">Use `dotnet new -all` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ba865-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="ba865-309">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.0.1.</span><span class="sxs-lookup"><span data-stu-id="ba865-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="ba865-310">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="ba865-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="ba865-311">Modelos</span><span class="sxs-lookup"><span data-stu-id="ba865-311">Templates</span></span>            | <span data-ttu-id="ba865-312">Nome curto</span><span class="sxs-lookup"><span data-stu-id="ba865-312">Short Name</span></span>    | <span data-ttu-id="ba865-313">Idioma</span><span class="sxs-lookup"><span data-stu-id="ba865-313">Language</span></span> | <span data-ttu-id="ba865-314">Marcas</span><span class="sxs-lookup"><span data-stu-id="ba865-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="ba865-315">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="ba865-315">Console Application</span></span>  | `console`     | <span data-ttu-id="ba865-316">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ba865-316">[C#], F#</span></span> | <span data-ttu-id="ba865-317">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="ba865-317">Common/Console</span></span> |
| <span data-ttu-id="ba865-318">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="ba865-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="ba865-319">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ba865-319">[C#], F#</span></span> | <span data-ttu-id="ba865-320">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="ba865-320">Common/Library</span></span> |
| <span data-ttu-id="ba865-321">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="ba865-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="ba865-322">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ba865-322">[C#], F#</span></span> | <span data-ttu-id="ba865-323">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="ba865-323">Test/MSTest</span></span>    |
| <span data-ttu-id="ba865-324">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="ba865-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="ba865-325">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ba865-325">[C#], F#</span></span> | <span data-ttu-id="ba865-326">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="ba865-326">Test/xUnit</span></span>     |
| <span data-ttu-id="ba865-327">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="ba865-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="ba865-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-328">[C#]</span></span>     | <span data-ttu-id="ba865-329">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="ba865-329">Web/Empty</span></span>      |
| <span data-ttu-id="ba865-330">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ba865-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="ba865-331">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="ba865-331">[C#], F#</span></span> | <span data-ttu-id="ba865-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="ba865-332">Web/MVC</span></span>        |
| <span data-ttu-id="ba865-333">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ba865-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="ba865-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="ba865-334">[C#]</span></span>     | <span data-ttu-id="ba865-335">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="ba865-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="ba865-336">Configuração do Nuget</span><span class="sxs-lookup"><span data-stu-id="ba865-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="ba865-337">Config</span><span class="sxs-lookup"><span data-stu-id="ba865-337">Config</span></span>         |
| <span data-ttu-id="ba865-338">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="ba865-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="ba865-339">Config</span><span class="sxs-lookup"><span data-stu-id="ba865-339">Config</span></span>         |
| <span data-ttu-id="ba865-340">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="ba865-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="ba865-341">Solução</span><span class="sxs-lookup"><span data-stu-id="ba865-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="ba865-342">Opções</span><span class="sxs-lookup"><span data-stu-id="ba865-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="ba865-343">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ba865-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="ba865-344">Exibe um resumo do que ocorreria se o comando fornecido fosse executado se resultasse na criação de um modelo.</span><span class="sxs-lookup"><span data-stu-id="ba865-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="ba865-345">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="ba865-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ba865-346">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ba865-347">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="ba865-347">Prints out help for the command.</span></span> <span data-ttu-id="ba865-348">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ba865-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="ba865-349">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="ba865-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ba865-350">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="ba865-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="ba865-351">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="ba865-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="ba865-352">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="ba865-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="ba865-353">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="ba865-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="ba865-354">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="ba865-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="ba865-355">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="ba865-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ba865-356">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="ba865-357">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="ba865-357">The language of the template to create.</span></span> <span data-ttu-id="ba865-358">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="ba865-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ba865-359">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="ba865-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="ba865-360">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="ba865-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ba865-361">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ba865-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ba865-362">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="ba865-362">The name for the created output.</span></span> <span data-ttu-id="ba865-363">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="ba865-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="ba865-364">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="ba865-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ba865-365">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="ba865-365">Location to place the generated output.</span></span> <span data-ttu-id="ba865-366">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="ba865-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="ba865-367">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ba865-367">Filters templates based on available types.</span></span> <span data-ttu-id="ba865-368">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="ba865-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="ba865-369">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="ba865-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ba865-370">Ao excluir o valor `<PATH|NUGET_ID>`, todos os pacotes de modelo atualmente instalados e seus modelos associados são exibidos.</span><span class="sxs-lookup"><span data-stu-id="ba865-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="ba865-371">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="ba865-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ba865-372">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="ba865-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="ba865-373">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="ba865-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ba865-374">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ba865-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="ba865-375">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="ba865-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ba865-376">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ba865-377">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="ba865-377">Prints out help for the command.</span></span> <span data-ttu-id="ba865-378">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ba865-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="ba865-379">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="ba865-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ba865-380">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="ba865-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="ba865-381">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="ba865-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="ba865-382">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="ba865-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="ba865-383">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="ba865-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="ba865-384">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="ba865-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="ba865-385">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="ba865-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ba865-386">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="ba865-387">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="ba865-387">The language of the template to create.</span></span> <span data-ttu-id="ba865-388">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="ba865-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ba865-389">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="ba865-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="ba865-390">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="ba865-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ba865-391">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ba865-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ba865-392">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="ba865-392">The name for the created output.</span></span> <span data-ttu-id="ba865-393">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="ba865-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="ba865-394">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="ba865-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ba865-395">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="ba865-395">Location to place the generated output.</span></span> <span data-ttu-id="ba865-396">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="ba865-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="ba865-397">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ba865-397">Filters templates based on available types.</span></span> <span data-ttu-id="ba865-398">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="ba865-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="ba865-399">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="ba865-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="ba865-400">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="ba865-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ba865-401">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="ba865-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="ba865-402">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="ba865-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ba865-403">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ba865-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="ba865-404">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="ba865-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="ba865-405">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ba865-406">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="ba865-406">Prints out help for the command.</span></span> <span data-ttu-id="ba865-407">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ba865-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="ba865-408">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="ba865-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="ba865-409">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="ba865-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="ba865-410">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="ba865-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="ba865-411">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="ba865-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="ba865-412">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="ba865-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="ba865-413">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="ba865-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="ba865-414">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="ba865-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ba865-415">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="ba865-416">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="ba865-416">The language of the template to create.</span></span> <span data-ttu-id="ba865-417">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="ba865-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ba865-418">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="ba865-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="ba865-419">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="ba865-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ba865-420">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ba865-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ba865-421">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="ba865-421">The name for the created output.</span></span> <span data-ttu-id="ba865-422">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="ba865-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ba865-423">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="ba865-423">Location to place the generated output.</span></span> <span data-ttu-id="ba865-424">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="ba865-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="ba865-425">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ba865-425">Filters templates based on available types.</span></span> <span data-ttu-id="ba865-426">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="ba865-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="ba865-427">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="ba865-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="ba865-428">Para desinstalar um modelo usando uma origem `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="ba865-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="ba865-429">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="ba865-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="ba865-430">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="ba865-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="ba865-431">Se não for possível determinar o argumento `PATH` ou `NUGET_ID` necessário para desinstalar um modelo, executar `dotnet new --uninstall` sem um argumento listará todos os modelos instalados e o argumento necessário desinstalá-los.</span><span class="sxs-lookup"><span data-stu-id="ba865-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ba865-432">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ba865-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="ba865-433">Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado.</span><span class="sxs-lookup"><span data-stu-id="ba865-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="ba865-434">Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força.</span><span class="sxs-lookup"><span data-stu-id="ba865-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="ba865-435">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="ba865-436">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="ba865-436">Prints out help for the command.</span></span> <span data-ttu-id="ba865-437">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="ba865-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="ba865-438">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="ba865-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="ba865-439">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="ba865-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="ba865-440">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="ba865-441">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="ba865-441">The language of the template to create.</span></span> <span data-ttu-id="ba865-442">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="ba865-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="ba865-443">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="ba865-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="ba865-444">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="ba865-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="ba865-445">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="ba865-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="ba865-446">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="ba865-446">The name for the created output.</span></span> <span data-ttu-id="ba865-447">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="ba865-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ba865-448">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="ba865-448">Location to place the generated output.</span></span> <span data-ttu-id="ba865-449">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="ba865-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="ba865-450">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="ba865-450">Template options</span></span>

<span data-ttu-id="ba865-451">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ba865-451">Each project template may have additional options available.</span></span> <span data-ttu-id="ba865-452">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="ba865-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="ba865-453">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ba865-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="ba865-454">**console**</span><span class="sxs-lookup"><span data-stu-id="ba865-454">**console**</span></span>

<span data-ttu-id="ba865-455">`--langVersion <VERSION_NUMBER>` – Define a propriedade `LangVersion` no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="ba865-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ba865-456">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="ba865-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="ba865-457">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="ba865-457">Not supported for F#.</span></span>

<span data-ttu-id="ba865-458">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-459">**angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="ba865-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="ba865-460">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ba865-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ba865-461">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-462">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ba865-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ba865-463">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="ba865-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="ba865-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="ba865-464">**razorclasslib**</span></span>

<span data-ttu-id="ba865-465">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-466">**classlib**</span><span class="sxs-lookup"><span data-stu-id="ba865-466">**classlib**</span></span>

<span data-ttu-id="ba865-467">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="ba865-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ba865-468">Valores: `netcoreapp2.2` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ba865-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ba865-469">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ba865-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="ba865-470">`--langVersion <VERSION_NUMBER>` – Define a propriedade `LangVersion` no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="ba865-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="ba865-471">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="ba865-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="ba865-472">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="ba865-472">Not supported for F#.</span></span>

<span data-ttu-id="ba865-473">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-474">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="ba865-474">**mstest, xunit**</span></span>

<span data-ttu-id="ba865-475">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ba865-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="ba865-476">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-477">**nunit**</span><span class="sxs-lookup"><span data-stu-id="ba865-477">**nunit**</span></span>

<span data-ttu-id="ba865-478">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="ba865-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ba865-479">O valor padrão é `netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="ba865-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="ba865-480">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ba865-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="ba865-481">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-482">**page**</span><span class="sxs-lookup"><span data-stu-id="ba865-482">**page**</span></span>

<span data-ttu-id="ba865-483">`-na|--namespace <NAMESPACE_NAME>` – namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="ba865-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="ba865-484">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ba865-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="ba865-485">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="ba865-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="ba865-486">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="ba865-486">**viewimports**</span></span>

<span data-ttu-id="ba865-487">`-na|--namespace <NAMESPACE_NAME>` – namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="ba865-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="ba865-488">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ba865-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="ba865-489">**web**</span><span class="sxs-lookup"><span data-stu-id="ba865-489">**web**</span></span>

<span data-ttu-id="ba865-490">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ba865-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ba865-491">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-492">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ba865-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ba865-493">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="ba865-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="ba865-494">**mvc, webapp**</span><span class="sxs-lookup"><span data-stu-id="ba865-494">**mvc, webapp**</span></span>

<span data-ttu-id="ba865-495">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="ba865-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ba865-496">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="ba865-496">The possible values are:</span></span>

- <span data-ttu-id="ba865-497">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="ba865-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ba865-498">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="ba865-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="ba865-499">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ba865-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ba865-500">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="ba865-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ba865-501">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="ba865-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="ba865-502">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="ba865-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ba865-503">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ba865-504">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ba865-505">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ba865-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ba865-506">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ba865-507">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-508">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="ba865-509">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-510">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="ba865-511">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-512">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ba865-513">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ba865-514">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ba865-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ba865-515">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ba865-516">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ba865-517">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ba865-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ba865-518">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="ba865-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ba865-519">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ba865-520">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ba865-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ba865-521">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ba865-522">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ba865-523">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ba865-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ba865-524">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="ba865-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ba865-525">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ba865-526">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ba865-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="ba865-527">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="ba865-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ba865-528">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ba865-529">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ba865-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ba865-530">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ba865-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ba865-531">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="ba865-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ba865-532">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="ba865-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="ba865-533">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="ba865-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ba865-534">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-535">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-536">**webapi**</span><span class="sxs-lookup"><span data-stu-id="ba865-536">**webapi**</span></span>

<span data-ttu-id="ba865-537">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="ba865-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ba865-538">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="ba865-538">The possible values are:</span></span>

- <span data-ttu-id="ba865-539">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="ba865-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ba865-540">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ba865-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ba865-541">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="ba865-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ba865-542">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="ba865-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ba865-543">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ba865-544">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ba865-545">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ba865-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ba865-546">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ba865-547">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-548">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ba865-549">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ba865-550">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ba865-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ba865-551">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ba865-552">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ba865-553">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ba865-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ba865-554">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="ba865-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ba865-555">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ba865-556">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ba865-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ba865-557">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ba865-558">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ba865-559">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ba865-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ba865-560">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="ba865-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ba865-561">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ba865-562">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ba865-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ba865-563">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ba865-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ba865-564">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="ba865-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ba865-565">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="ba865-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="ba865-566">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="ba865-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ba865-567">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-568">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="ba865-569">**globaljson**</span></span>

<span data-ttu-id="ba865-570">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="ba865-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="ba865-571">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ba865-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="ba865-572">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="ba865-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="ba865-573">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-574">**classlib**</span><span class="sxs-lookup"><span data-stu-id="ba865-574">**classlib**</span></span>

<span data-ttu-id="ba865-575">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="ba865-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ba865-576">Valores: `netcoreapp2.1` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ba865-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ba865-577">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ba865-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="ba865-578">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-579">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="ba865-579">**mstest, xunit**</span></span>

<span data-ttu-id="ba865-580">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ba865-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="ba865-581">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="ba865-582">**globaljson**</span></span>

<span data-ttu-id="ba865-583">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="ba865-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="ba865-584">**web**</span><span class="sxs-lookup"><span data-stu-id="ba865-584">**web**</span></span>

<span data-ttu-id="ba865-585">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ba865-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ba865-586">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-587">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ba865-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ba865-588">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="ba865-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="ba865-589">**webapi**</span><span class="sxs-lookup"><span data-stu-id="ba865-589">**webapi**</span></span>

<span data-ttu-id="ba865-590">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="ba865-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ba865-591">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="ba865-591">The possible values are:</span></span>

- <span data-ttu-id="ba865-592">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="ba865-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ba865-593">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ba865-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ba865-594">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="ba865-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ba865-595">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="ba865-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ba865-596">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ba865-597">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ba865-598">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ba865-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ba865-599">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ba865-600">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-601">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ba865-602">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ba865-603">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ba865-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ba865-604">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ba865-605">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ba865-606">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ba865-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ba865-607">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="ba865-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ba865-608">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ba865-609">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ba865-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ba865-610">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ba865-611">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ba865-612">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ba865-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ba865-613">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="ba865-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ba865-614">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ba865-615">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ba865-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ba865-616">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="ba865-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ba865-617">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-618">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-619">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ba865-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ba865-620">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="ba865-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ba865-621">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="ba865-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="ba865-622">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="ba865-622">**mvc, razor**</span></span>

<span data-ttu-id="ba865-623">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="ba865-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ba865-624">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="ba865-624">The possible values are:</span></span>

- <span data-ttu-id="ba865-625">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="ba865-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ba865-626">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="ba865-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="ba865-627">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ba865-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ba865-628">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="ba865-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ba865-629">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="ba865-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="ba865-630">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="ba865-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ba865-631">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ba865-632">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ba865-633">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ba865-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ba865-634">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ba865-635">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-636">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="ba865-637">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-638">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="ba865-639">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-640">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ba865-641">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ba865-642">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ba865-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ba865-643">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ba865-644">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ba865-645">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ba865-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ba865-646">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="ba865-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ba865-647">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ba865-648">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ba865-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ba865-649">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ba865-650">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ba865-651">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ba865-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ba865-652">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="ba865-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ba865-653">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ba865-654">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ba865-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="ba865-655">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="ba865-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ba865-656">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ba865-657">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ba865-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="ba865-658">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="ba865-659">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="ba865-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ba865-660">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-661">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-662">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ba865-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="ba865-663">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="ba865-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="ba865-664">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="ba865-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="ba865-665">**page**</span><span class="sxs-lookup"><span data-stu-id="ba865-665">**page**</span></span>

<span data-ttu-id="ba865-666">`-na|--namespace <NAMESPACE_NAME>` – namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="ba865-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="ba865-667">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ba865-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="ba865-668">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="ba865-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="ba865-669">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="ba865-669">**viewimports**</span></span>

<span data-ttu-id="ba865-670">`-na|--namespace <NAMESPACE_NAME>` – namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="ba865-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="ba865-671">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ba865-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="ba865-672">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ba865-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="ba865-673">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="ba865-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="ba865-674">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-675">**classlib**</span><span class="sxs-lookup"><span data-stu-id="ba865-675">**classlib**</span></span>

<span data-ttu-id="ba865-676">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="ba865-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ba865-677">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ba865-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="ba865-678">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ba865-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="ba865-679">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-680">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="ba865-680">**mstest, xunit**</span></span>

<span data-ttu-id="ba865-681">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="ba865-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="ba865-682">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="ba865-683">**globaljson**</span></span>

<span data-ttu-id="ba865-684">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="ba865-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="ba865-685">**web**</span><span class="sxs-lookup"><span data-stu-id="ba865-685">**web**</span></span>

<span data-ttu-id="ba865-686">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ba865-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ba865-687">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-688">**webapi**</span><span class="sxs-lookup"><span data-stu-id="ba865-688">**webapi**</span></span>

<span data-ttu-id="ba865-689">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="ba865-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ba865-690">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="ba865-690">The possible values are:</span></span>

- <span data-ttu-id="ba865-691">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="ba865-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ba865-692">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ba865-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ba865-693">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="ba865-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ba865-694">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="ba865-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ba865-695">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ba865-696">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ba865-697">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ba865-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ba865-698">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ba865-699">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-700">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ba865-701">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ba865-702">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ba865-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ba865-703">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ba865-704">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="ba865-705">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ba865-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ba865-706">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="ba865-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ba865-707">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ba865-708">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ba865-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ba865-709">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ba865-710">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ba865-711">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ba865-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ba865-712">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="ba865-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ba865-713">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ba865-714">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ba865-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ba865-715">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="ba865-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ba865-716">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-717">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-718">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="ba865-718">**mvc, razor**</span></span>

<span data-ttu-id="ba865-719">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="ba865-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ba865-720">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="ba865-720">The possible values are:</span></span>

- <span data-ttu-id="ba865-721">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="ba865-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="ba865-722">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="ba865-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="ba865-723">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="ba865-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="ba865-724">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="ba865-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="ba865-725">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="ba865-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="ba865-726">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="ba865-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="ba865-727">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="ba865-728">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="ba865-729">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="ba865-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="ba865-730">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="ba865-731">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-732">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="ba865-733">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-734">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="ba865-735">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-736">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="ba865-737">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="ba865-738">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="ba865-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="ba865-739">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="ba865-740">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="ba865-741">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="ba865-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="ba865-742">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="ba865-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="ba865-743">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ba865-744">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="ba865-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="ba865-745">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="ba865-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="ba865-746">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="ba865-747">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="ba865-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="ba865-748">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="ba865-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="ba865-749">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="ba865-750">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="ba865-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="ba865-751">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="ba865-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="ba865-752">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="ba865-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="ba865-753">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="ba865-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="ba865-754">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="ba865-755">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="ba865-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="ba865-756">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="ba865-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="ba865-757">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ba865-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="ba865-758">**page**</span><span class="sxs-lookup"><span data-stu-id="ba865-758">**page**</span></span>

<span data-ttu-id="ba865-759">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="ba865-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="ba865-760">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ba865-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="ba865-761">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="ba865-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="ba865-762">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="ba865-762">**viewimports**</span></span>

<span data-ttu-id="ba865-763">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="ba865-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="ba865-764">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="ba865-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ba865-765">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ba865-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="ba865-766">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="ba865-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="ba865-767">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="ba865-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ba865-768">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="ba865-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="ba865-769">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="ba865-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="ba865-770">**classlib**</span><span class="sxs-lookup"><span data-stu-id="ba865-770">**classlib**</span></span>

<span data-ttu-id="ba865-771">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="ba865-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ba865-772">Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="ba865-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="ba865-773">O valor padrão é `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="ba865-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="ba865-774">**mvc**</span><span class="sxs-lookup"><span data-stu-id="ba865-774">**mvc**</span></span>

<span data-ttu-id="ba865-775">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="ba865-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="ba865-776">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="ba865-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="ba865-777">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="ba865-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="ba865-778">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="ba865-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="ba865-779">Valores: `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="ba865-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="ba865-780">O valor padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="ba865-780">The default value is `None`.</span></span>

<span data-ttu-id="ba865-781">`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="ba865-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="ba865-782">Valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="ba865-782">Values: `true` or `false`.</span></span> <span data-ttu-id="ba865-783">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="ba865-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="ba865-784">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ba865-784">Examples</span></span>

<span data-ttu-id="ba865-785">Crie um projeto de aplicativo de console em C# especificando o nome do modelo:</span><span class="sxs-lookup"><span data-stu-id="ba865-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="ba865-786">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="ba865-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="ba865-787">Crie um projeto de biblioteca de classes .NET Standard no diretório especificado (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="ba865-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="ba865-788">Crie um projeto de MVC em C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="ba865-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="ba865-789">Crie um projeto de xUnit:</span><span class="sxs-lookup"><span data-stu-id="ba865-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="ba865-790">Lista todos os modelos disponíveis para o MVC:</span><span class="sxs-lookup"><span data-stu-id="ba865-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="ba865-791">Liste todos os modelos que correspondem à substring *we*.</span><span class="sxs-lookup"><span data-stu-id="ba865-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="ba865-792">Nenhuma correspondência exata é encontrada, portanto, a correspondência de substring é executada em relação tanto ao nome curto quanto às colunas de nome.</span><span class="sxs-lookup"><span data-stu-id="ba865-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="ba865-793">Tentativa de invocar o modelo correspondente a *ng*.</span><span class="sxs-lookup"><span data-stu-id="ba865-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="ba865-794">Se não for possível determinar uma única correspondência, liste os modelos que são correspondências parciais.</span><span class="sxs-lookup"><span data-stu-id="ba865-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="ba865-795">Instale a versão 2.0 dos modelos de aplicativo de página única do ASP.NET Core (opção de comando disponível somente para o SDK do .NET Core 1.1 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="ba865-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="ba865-796">Crie um *global.json* no diretório atual definindo a versão do SDK como 2.0.0 (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="ba865-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="ba865-797">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba865-797">See also</span></span>

- [<span data-ttu-id="ba865-798">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="ba865-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- <span data-ttu-id="ba865-799">[Create a custom template for dotnet new](../tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="ba865-799">[Create a custom template for dotnet new](../tutorials/create-custom-template.md)</span></span>
- [<span data-ttu-id="ba865-800">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="ba865-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="ba865-801">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="ba865-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
