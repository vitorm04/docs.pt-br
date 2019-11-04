---
title: Comando dotnet new
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
ms.date: 05/06/2019
ms.openlocfilehash: c9529e135f48c80f445c91038294a3e7266486f1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420475"
---
# <a name="dotnet-new"></a><span data-ttu-id="2e882-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="2e882-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2e882-104">Name</span><span class="sxs-lookup"><span data-stu-id="2e882-104">Name</span></span>

<span data-ttu-id="2e882-105">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="2e882-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2e882-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="2e882-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="2e882-107">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="2e882-107">.NET Core 2.2</span></span>](#tab/netcore22)

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="2e882-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2e882-108">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="2e882-109">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="2e882-109">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2e882-110">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="2e882-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="2e882-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e882-111">Description</span></span>

<span data-ttu-id="2e882-112">O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido.</span><span class="sxs-lookup"><span data-stu-id="2e882-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="2e882-113">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="2e882-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="2e882-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="2e882-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="2e882-115">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="2e882-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="2e882-116">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="2e882-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="2e882-117">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="2e882-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="2e882-118">Se o valor `TEMPLATE` não for uma correspondência exata no texto na coluna **Modelos** ou **Nome Curto**, uma correspondência de substring será executada nessas duas colunas.</span><span class="sxs-lookup"><span data-stu-id="2e882-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="2e882-119">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="2e882-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="2e882-120">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="2e882-120">The command contains a default list of templates.</span></span> <span data-ttu-id="2e882-121">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2e882-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="2e882-122">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.2.100.</span><span class="sxs-lookup"><span data-stu-id="2e882-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="2e882-123">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="2e882-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="2e882-124">Modelos</span><span class="sxs-lookup"><span data-stu-id="2e882-124">Templates</span></span>                                    | <span data-ttu-id="2e882-125">Nome curto</span><span class="sxs-lookup"><span data-stu-id="2e882-125">Short Name</span></span>        | <span data-ttu-id="2e882-126">Idioma</span><span class="sxs-lookup"><span data-stu-id="2e882-126">Language</span></span>     | <span data-ttu-id="2e882-127">Marcas</span><span class="sxs-lookup"><span data-stu-id="2e882-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="2e882-128">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="2e882-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="2e882-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2e882-129">[C#], F#, VB</span></span> | <span data-ttu-id="2e882-130">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="2e882-130">Common/Console</span></span>                        |
| <span data-ttu-id="2e882-131">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="2e882-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="2e882-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2e882-132">[C#], F#, VB</span></span> | <span data-ttu-id="2e882-133">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="2e882-133">Common/Library</span></span>                        |
| <span data-ttu-id="2e882-134">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="2e882-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="2e882-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2e882-135">[C#], F#, VB</span></span> | <span data-ttu-id="2e882-136">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="2e882-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="2e882-137">Projeto de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="2e882-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="2e882-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2e882-138">[C#], F#, VB</span></span> | <span data-ttu-id="2e882-139">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="2e882-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="2e882-140">Item de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="2e882-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="2e882-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2e882-141">[C#], F#, VB</span></span> | <span data-ttu-id="2e882-142">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="2e882-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="2e882-143">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="2e882-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="2e882-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2e882-144">[C#], F#, VB</span></span> | <span data-ttu-id="2e882-145">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="2e882-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="2e882-146">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="2e882-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="2e882-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-147">[C#]</span></span>         | <span data-ttu-id="2e882-148">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2e882-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="2e882-149">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="2e882-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="2e882-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-150">[C#]</span></span>         | <span data-ttu-id="2e882-151">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2e882-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="2e882-152">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="2e882-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="2e882-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-153">[C#]</span></span>         | <span data-ttu-id="2e882-154">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2e882-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="2e882-155">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="2e882-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="2e882-156">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2e882-156">[C#], F#</span></span>     | <span data-ttu-id="2e882-157">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="2e882-157">Web/Empty</span></span>                             |
| <span data-ttu-id="2e882-158">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="2e882-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="2e882-159">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2e882-159">[C#], F#</span></span>     | <span data-ttu-id="2e882-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="2e882-160">Web/MVC</span></span>                               |
| <span data-ttu-id="2e882-161">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2e882-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="2e882-162">`webapp`, `razor`</span><span class="sxs-lookup"><span data-stu-id="2e882-162">`webapp`, `razor`</span></span> | <span data-ttu-id="2e882-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-163">[C#]</span></span>         | <span data-ttu-id="2e882-164">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="2e882-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="2e882-165">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="2e882-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="2e882-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-166">[C#]</span></span>         | <span data-ttu-id="2e882-167">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="2e882-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="2e882-168">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="2e882-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="2e882-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-169">[C#]</span></span>         | <span data-ttu-id="2e882-170">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="2e882-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="2e882-171">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="2e882-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="2e882-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-172">[C#]</span></span>         | <span data-ttu-id="2e882-173">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="2e882-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="2e882-174">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="2e882-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="2e882-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-175">[C#]</span></span>         | <span data-ttu-id="2e882-176">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="2e882-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="2e882-177">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2e882-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="2e882-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2e882-178">[C#], F#</span></span>     | <span data-ttu-id="2e882-179">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="2e882-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="2e882-180">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="2e882-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="2e882-181">Config</span><span class="sxs-lookup"><span data-stu-id="2e882-181">Config</span></span>                                |
| <span data-ttu-id="2e882-182">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="2e882-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="2e882-183">Config</span><span class="sxs-lookup"><span data-stu-id="2e882-183">Config</span></span>                                |
| <span data-ttu-id="2e882-184">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="2e882-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="2e882-185">Config</span><span class="sxs-lookup"><span data-stu-id="2e882-185">Config</span></span>                                |
| <span data-ttu-id="2e882-186">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="2e882-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="2e882-187">Solução</span><span class="sxs-lookup"><span data-stu-id="2e882-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="2e882-188">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2e882-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="2e882-189">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="2e882-189">The command contains a default list of templates.</span></span> <span data-ttu-id="2e882-190">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2e882-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="2e882-191">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="2e882-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="2e882-192">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="2e882-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="2e882-193">Modelos</span><span class="sxs-lookup"><span data-stu-id="2e882-193">Templates</span></span>                                    | <span data-ttu-id="2e882-194">Nome curto</span><span class="sxs-lookup"><span data-stu-id="2e882-194">Short Name</span></span>      | <span data-ttu-id="2e882-195">Idioma</span><span class="sxs-lookup"><span data-stu-id="2e882-195">Language</span></span>     | <span data-ttu-id="2e882-196">Marcas</span><span class="sxs-lookup"><span data-stu-id="2e882-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="2e882-197">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="2e882-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="2e882-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2e882-198">[C#], F#, VB</span></span> | <span data-ttu-id="2e882-199">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="2e882-199">Common/Console</span></span>                        |
| <span data-ttu-id="2e882-200">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="2e882-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="2e882-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2e882-201">[C#], F#, VB</span></span> | <span data-ttu-id="2e882-202">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="2e882-202">Common/Library</span></span>                        |
| <span data-ttu-id="2e882-203">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="2e882-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="2e882-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2e882-204">[C#], F#, VB</span></span> | <span data-ttu-id="2e882-205">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="2e882-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="2e882-206">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="2e882-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="2e882-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2e882-207">[C#], F#, VB</span></span> | <span data-ttu-id="2e882-208">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="2e882-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="2e882-209">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="2e882-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="2e882-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-210">[C#]</span></span>         | <span data-ttu-id="2e882-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2e882-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="2e882-212">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="2e882-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="2e882-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-213">[C#]</span></span>         | <span data-ttu-id="2e882-214">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2e882-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="2e882-215">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="2e882-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="2e882-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-216">[C#]</span></span>         | <span data-ttu-id="2e882-217">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2e882-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="2e882-218">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="2e882-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="2e882-219">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2e882-219">[C#], F#</span></span>     | <span data-ttu-id="2e882-220">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="2e882-220">Web/Empty</span></span>                             |
| <span data-ttu-id="2e882-221">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="2e882-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="2e882-222">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2e882-222">[C#], F#</span></span>     | <span data-ttu-id="2e882-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="2e882-223">Web/MVC</span></span>                               |
| <span data-ttu-id="2e882-224">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2e882-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="2e882-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-225">[C#]</span></span>         | <span data-ttu-id="2e882-226">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="2e882-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="2e882-227">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="2e882-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="2e882-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-228">[C#]</span></span>         | <span data-ttu-id="2e882-229">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="2e882-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="2e882-230">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="2e882-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="2e882-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-231">[C#]</span></span>         | <span data-ttu-id="2e882-232">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="2e882-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="2e882-233">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="2e882-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="2e882-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-234">[C#]</span></span>         | <span data-ttu-id="2e882-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="2e882-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="2e882-236">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="2e882-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="2e882-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-237">[C#]</span></span>         | <span data-ttu-id="2e882-238">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="2e882-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="2e882-239">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2e882-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="2e882-240">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2e882-240">[C#], F#</span></span>     | <span data-ttu-id="2e882-241">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="2e882-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="2e882-242">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="2e882-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="2e882-243">Config</span><span class="sxs-lookup"><span data-stu-id="2e882-243">Config</span></span>                                |
| <span data-ttu-id="2e882-244">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="2e882-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="2e882-245">Config</span><span class="sxs-lookup"><span data-stu-id="2e882-245">Config</span></span>                                |
| <span data-ttu-id="2e882-246">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="2e882-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="2e882-247">Config</span><span class="sxs-lookup"><span data-stu-id="2e882-247">Config</span></span>                                |
| <span data-ttu-id="2e882-248">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="2e882-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="2e882-249">Solução</span><span class="sxs-lookup"><span data-stu-id="2e882-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="2e882-250">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="2e882-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="2e882-251">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="2e882-251">The command contains a default list of templates.</span></span> <span data-ttu-id="2e882-252">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2e882-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="2e882-253">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="2e882-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="2e882-254">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="2e882-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="2e882-255">Modelos</span><span class="sxs-lookup"><span data-stu-id="2e882-255">Templates</span></span>                                    | <span data-ttu-id="2e882-256">Nome curto</span><span class="sxs-lookup"><span data-stu-id="2e882-256">Short Name</span></span>    | <span data-ttu-id="2e882-257">Idioma</span><span class="sxs-lookup"><span data-stu-id="2e882-257">Language</span></span>     | <span data-ttu-id="2e882-258">Marcas</span><span class="sxs-lookup"><span data-stu-id="2e882-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="2e882-259">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="2e882-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="2e882-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2e882-260">[C#], F#, VB</span></span> | <span data-ttu-id="2e882-261">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="2e882-261">Common/Console</span></span>      |
| <span data-ttu-id="2e882-262">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="2e882-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="2e882-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2e882-263">[C#], F#, VB</span></span> | <span data-ttu-id="2e882-264">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="2e882-264">Common/Library</span></span>      |
| <span data-ttu-id="2e882-265">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="2e882-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="2e882-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2e882-266">[C#], F#, VB</span></span> | <span data-ttu-id="2e882-267">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="2e882-267">Test/MSTest</span></span>         |
| <span data-ttu-id="2e882-268">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="2e882-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="2e882-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2e882-269">[C#], F#, VB</span></span> | <span data-ttu-id="2e882-270">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="2e882-270">Test/xUnit</span></span>          |
| <span data-ttu-id="2e882-271">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="2e882-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="2e882-272">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2e882-272">[C#], F#</span></span>     | <span data-ttu-id="2e882-273">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="2e882-273">Web/Empty</span></span>           |
| <span data-ttu-id="2e882-274">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="2e882-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="2e882-275">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2e882-275">[C#], F#</span></span>     | <span data-ttu-id="2e882-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="2e882-276">Web/MVC</span></span>             |
| <span data-ttu-id="2e882-277">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2e882-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="2e882-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-278">[C#]</span></span>         | <span data-ttu-id="2e882-279">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="2e882-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="2e882-280">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="2e882-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="2e882-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-281">[C#]</span></span>         | <span data-ttu-id="2e882-282">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="2e882-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="2e882-283">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="2e882-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="2e882-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-284">[C#]</span></span>         | <span data-ttu-id="2e882-285">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="2e882-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="2e882-286">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="2e882-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="2e882-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-287">[C#]</span></span>         | <span data-ttu-id="2e882-288">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="2e882-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="2e882-289">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2e882-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="2e882-290">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2e882-290">[C#], F#</span></span>     | <span data-ttu-id="2e882-291">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="2e882-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="2e882-292">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="2e882-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="2e882-293">Config</span><span class="sxs-lookup"><span data-stu-id="2e882-293">Config</span></span>              |
| <span data-ttu-id="2e882-294">Configuração do Nuget</span><span class="sxs-lookup"><span data-stu-id="2e882-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="2e882-295">Config</span><span class="sxs-lookup"><span data-stu-id="2e882-295">Config</span></span>              |
| <span data-ttu-id="2e882-296">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="2e882-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="2e882-297">Config</span><span class="sxs-lookup"><span data-stu-id="2e882-297">Config</span></span>              |
| <span data-ttu-id="2e882-298">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="2e882-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="2e882-299">Solução</span><span class="sxs-lookup"><span data-stu-id="2e882-299">Solution</span></span>            |
| <span data-ttu-id="2e882-300">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="2e882-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="2e882-301">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2e882-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="2e882-302">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="2e882-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="2e882-303">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2e882-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="2e882-304">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="2e882-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="2e882-305">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2e882-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2e882-306">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="2e882-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="2e882-307">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="2e882-307">The command contains a default list of templates.</span></span> <span data-ttu-id="2e882-308">Use `dotnet new -all` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2e882-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="2e882-309">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.0.1.</span><span class="sxs-lookup"><span data-stu-id="2e882-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="2e882-310">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="2e882-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="2e882-311">Modelos</span><span class="sxs-lookup"><span data-stu-id="2e882-311">Templates</span></span>            | <span data-ttu-id="2e882-312">Nome curto</span><span class="sxs-lookup"><span data-stu-id="2e882-312">Short Name</span></span>    | <span data-ttu-id="2e882-313">Idioma</span><span class="sxs-lookup"><span data-stu-id="2e882-313">Language</span></span> | <span data-ttu-id="2e882-314">Marcas</span><span class="sxs-lookup"><span data-stu-id="2e882-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="2e882-315">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="2e882-315">Console Application</span></span>  | `console`     | <span data-ttu-id="2e882-316">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2e882-316">[C#], F#</span></span> | <span data-ttu-id="2e882-317">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="2e882-317">Common/Console</span></span> |
| <span data-ttu-id="2e882-318">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="2e882-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="2e882-319">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2e882-319">[C#], F#</span></span> | <span data-ttu-id="2e882-320">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="2e882-320">Common/Library</span></span> |
| <span data-ttu-id="2e882-321">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="2e882-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="2e882-322">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2e882-322">[C#], F#</span></span> | <span data-ttu-id="2e882-323">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="2e882-323">Test/MSTest</span></span>    |
| <span data-ttu-id="2e882-324">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="2e882-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="2e882-325">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2e882-325">[C#], F#</span></span> | <span data-ttu-id="2e882-326">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="2e882-326">Test/xUnit</span></span>     |
| <span data-ttu-id="2e882-327">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="2e882-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="2e882-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-328">[C#]</span></span>     | <span data-ttu-id="2e882-329">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="2e882-329">Web/Empty</span></span>      |
| <span data-ttu-id="2e882-330">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2e882-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="2e882-331">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2e882-331">[C#], F#</span></span> | <span data-ttu-id="2e882-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="2e882-332">Web/MVC</span></span>        |
| <span data-ttu-id="2e882-333">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2e882-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="2e882-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="2e882-334">[C#]</span></span>     | <span data-ttu-id="2e882-335">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="2e882-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="2e882-336">Configuração do Nuget</span><span class="sxs-lookup"><span data-stu-id="2e882-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="2e882-337">Config</span><span class="sxs-lookup"><span data-stu-id="2e882-337">Config</span></span>         |
| <span data-ttu-id="2e882-338">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="2e882-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="2e882-339">Config</span><span class="sxs-lookup"><span data-stu-id="2e882-339">Config</span></span>         |
| <span data-ttu-id="2e882-340">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="2e882-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="2e882-341">Solução</span><span class="sxs-lookup"><span data-stu-id="2e882-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="2e882-342">Opções</span><span class="sxs-lookup"><span data-stu-id="2e882-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="2e882-343">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="2e882-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="2e882-344">Exibe um resumo do que ocorreria se o comando fornecido fosse executado se resultasse na criação de um modelo.</span><span class="sxs-lookup"><span data-stu-id="2e882-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="2e882-345">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="2e882-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="2e882-346">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="2e882-347">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="2e882-347">Prints out help for the command.</span></span> <span data-ttu-id="2e882-348">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="2e882-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="2e882-349">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="2e882-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="2e882-350">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="2e882-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="2e882-351">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="2e882-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="2e882-352">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="2e882-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="2e882-353">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="2e882-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="2e882-354">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="2e882-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="2e882-355">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="2e882-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="2e882-356">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="2e882-357">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="2e882-357">The language of the template to create.</span></span> <span data-ttu-id="2e882-358">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="2e882-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="2e882-359">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="2e882-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="2e882-360">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="2e882-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="2e882-361">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="2e882-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="2e882-362">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="2e882-362">The name for the created output.</span></span> <span data-ttu-id="2e882-363">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="2e882-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="2e882-364">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="2e882-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="2e882-365">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="2e882-365">Location to place the generated output.</span></span> <span data-ttu-id="2e882-366">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="2e882-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="2e882-367">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2e882-367">Filters templates based on available types.</span></span> <span data-ttu-id="2e882-368">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="2e882-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="2e882-369">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="2e882-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="2e882-370">Ao excluir o valor `<PATH|NUGET_ID>`, todos os pacotes de modelo atualmente instalados e seus modelos associados são exibidos.</span><span class="sxs-lookup"><span data-stu-id="2e882-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="2e882-371">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="2e882-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="2e882-372">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="2e882-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="2e882-373">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="2e882-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="2e882-374">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2e882-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="2e882-375">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="2e882-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="2e882-376">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="2e882-377">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="2e882-377">Prints out help for the command.</span></span> <span data-ttu-id="2e882-378">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="2e882-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="2e882-379">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="2e882-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="2e882-380">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="2e882-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="2e882-381">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="2e882-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="2e882-382">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="2e882-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="2e882-383">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="2e882-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="2e882-384">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="2e882-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="2e882-385">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="2e882-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="2e882-386">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="2e882-387">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="2e882-387">The language of the template to create.</span></span> <span data-ttu-id="2e882-388">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="2e882-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="2e882-389">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="2e882-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="2e882-390">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="2e882-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="2e882-391">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="2e882-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="2e882-392">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="2e882-392">The name for the created output.</span></span> <span data-ttu-id="2e882-393">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="2e882-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="2e882-394">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="2e882-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="2e882-395">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="2e882-395">Location to place the generated output.</span></span> <span data-ttu-id="2e882-396">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="2e882-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="2e882-397">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2e882-397">Filters templates based on available types.</span></span> <span data-ttu-id="2e882-398">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="2e882-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="2e882-399">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="2e882-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="2e882-400">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="2e882-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="2e882-401">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="2e882-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="2e882-402">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="2e882-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="2e882-403">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="2e882-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="2e882-404">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="2e882-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="2e882-405">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="2e882-406">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="2e882-406">Prints out help for the command.</span></span> <span data-ttu-id="2e882-407">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="2e882-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="2e882-408">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="2e882-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="2e882-409">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="2e882-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="2e882-410">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="2e882-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="2e882-411">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="2e882-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="2e882-412">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="2e882-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="2e882-413">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="2e882-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="2e882-414">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="2e882-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="2e882-415">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="2e882-416">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="2e882-416">The language of the template to create.</span></span> <span data-ttu-id="2e882-417">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="2e882-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="2e882-418">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="2e882-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="2e882-419">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="2e882-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="2e882-420">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="2e882-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="2e882-421">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="2e882-421">The name for the created output.</span></span> <span data-ttu-id="2e882-422">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="2e882-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="2e882-423">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="2e882-423">Location to place the generated output.</span></span> <span data-ttu-id="2e882-424">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="2e882-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="2e882-425">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2e882-425">Filters templates based on available types.</span></span> <span data-ttu-id="2e882-426">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="2e882-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="2e882-427">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="2e882-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="2e882-428">Para desinstalar um modelo usando uma origem `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="2e882-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="2e882-429">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="2e882-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="2e882-430">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="2e882-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="2e882-431">Se não for possível determinar o argumento `PATH` ou `NUGET_ID` necessário para desinstalar um modelo, executar `dotnet new --uninstall` sem um argumento listará todos os modelos instalados e o argumento necessário desinstalá-los.</span><span class="sxs-lookup"><span data-stu-id="2e882-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2e882-432">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="2e882-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="2e882-433">Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado.</span><span class="sxs-lookup"><span data-stu-id="2e882-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="2e882-434">Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força.</span><span class="sxs-lookup"><span data-stu-id="2e882-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="2e882-435">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="2e882-436">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="2e882-436">Prints out help for the command.</span></span> <span data-ttu-id="2e882-437">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="2e882-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="2e882-438">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="2e882-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="2e882-439">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="2e882-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="2e882-440">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="2e882-441">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="2e882-441">The language of the template to create.</span></span> <span data-ttu-id="2e882-442">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="2e882-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="2e882-443">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="2e882-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="2e882-444">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="2e882-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="2e882-445">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="2e882-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="2e882-446">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="2e882-446">The name for the created output.</span></span> <span data-ttu-id="2e882-447">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="2e882-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="2e882-448">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="2e882-448">Location to place the generated output.</span></span> <span data-ttu-id="2e882-449">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="2e882-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="2e882-450">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="2e882-450">Template options</span></span>

<span data-ttu-id="2e882-451">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2e882-451">Each project template may have additional options available.</span></span> <span data-ttu-id="2e882-452">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="2e882-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="2e882-453">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="2e882-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="2e882-454">**console**</span><span class="sxs-lookup"><span data-stu-id="2e882-454">**console**</span></span>

<span data-ttu-id="2e882-455">`--langVersion <VERSION_NUMBER>` – Define a propriedade `LangVersion` no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="2e882-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="2e882-456">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="2e882-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="2e882-457">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="2e882-457">Not supported for F#.</span></span>

<span data-ttu-id="2e882-458">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-459">**angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="2e882-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="2e882-460">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2e882-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="2e882-461">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-462">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2e882-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="2e882-463">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="2e882-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="2e882-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="2e882-464">**razorclasslib**</span></span>

<span data-ttu-id="2e882-465">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-466">**classlib**</span><span class="sxs-lookup"><span data-stu-id="2e882-466">**classlib**</span></span>

<span data-ttu-id="2e882-467">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="2e882-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2e882-468">Valores: `netcoreapp2.2` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2e882-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="2e882-469">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="2e882-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="2e882-470">`--langVersion <VERSION_NUMBER>` – Define a propriedade `LangVersion` no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="2e882-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="2e882-471">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="2e882-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="2e882-472">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="2e882-472">Not supported for F#.</span></span>

<span data-ttu-id="2e882-473">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-474">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="2e882-474">**mstest, xunit**</span></span>

<span data-ttu-id="2e882-475">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="2e882-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="2e882-476">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-477">**nunit**</span><span class="sxs-lookup"><span data-stu-id="2e882-477">**nunit**</span></span>

<span data-ttu-id="2e882-478">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="2e882-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2e882-479">O valor padrão é `netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="2e882-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="2e882-480">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="2e882-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="2e882-481">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-482">**page**</span><span class="sxs-lookup"><span data-stu-id="2e882-482">**page**</span></span>

<span data-ttu-id="2e882-483">`-na|--namespace <NAMESPACE_NAME>` – namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="2e882-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="2e882-484">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="2e882-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="2e882-485">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="2e882-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="2e882-486">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="2e882-486">**viewimports**</span></span>

<span data-ttu-id="2e882-487">`-na|--namespace <NAMESPACE_NAME>` – namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="2e882-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="2e882-488">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="2e882-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="2e882-489">**web**</span><span class="sxs-lookup"><span data-stu-id="2e882-489">**web**</span></span>

<span data-ttu-id="2e882-490">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2e882-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="2e882-491">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-492">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2e882-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="2e882-493">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="2e882-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="2e882-494">**mvc, webapp**</span><span class="sxs-lookup"><span data-stu-id="2e882-494">**mvc, webapp**</span></span>

<span data-ttu-id="2e882-495">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="2e882-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="2e882-496">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="2e882-496">The possible values are:</span></span>

- <span data-ttu-id="2e882-497">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="2e882-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="2e882-498">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="2e882-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="2e882-499">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="2e882-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="2e882-500">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="2e882-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="2e882-501">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="2e882-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="2e882-502">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="2e882-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="2e882-503">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="2e882-504">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="2e882-505">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="2e882-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="2e882-506">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="2e882-507">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-508">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="2e882-509">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-510">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="2e882-511">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-512">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="2e882-513">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="2e882-514">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="2e882-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="2e882-515">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="2e882-516">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="2e882-517">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="2e882-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="2e882-518">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="2e882-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="2e882-519">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2e882-520">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="2e882-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="2e882-521">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="2e882-522">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2e882-523">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="2e882-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="2e882-524">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="2e882-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="2e882-525">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2e882-526">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="2e882-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="2e882-527">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="2e882-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="2e882-528">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="2e882-529">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2e882-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="2e882-530">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2e882-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="2e882-531">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="2e882-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="2e882-532">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="2e882-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="2e882-533">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="2e882-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2e882-534">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-535">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-536">**webapi**</span><span class="sxs-lookup"><span data-stu-id="2e882-536">**webapi**</span></span>

<span data-ttu-id="2e882-537">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="2e882-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="2e882-538">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="2e882-538">The possible values are:</span></span>

- <span data-ttu-id="2e882-539">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="2e882-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="2e882-540">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="2e882-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="2e882-541">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="2e882-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="2e882-542">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="2e882-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="2e882-543">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="2e882-544">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="2e882-545">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="2e882-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="2e882-546">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="2e882-547">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-548">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="2e882-549">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2e882-550">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="2e882-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="2e882-551">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="2e882-552">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="2e882-553">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="2e882-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="2e882-554">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="2e882-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="2e882-555">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2e882-556">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="2e882-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="2e882-557">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="2e882-558">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2e882-559">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="2e882-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="2e882-560">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="2e882-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="2e882-561">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="2e882-562">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2e882-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="2e882-563">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2e882-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="2e882-564">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="2e882-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="2e882-565">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="2e882-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="2e882-566">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="2e882-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2e882-567">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-568">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="2e882-569">**globaljson**</span></span>

<span data-ttu-id="2e882-570">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="2e882-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="2e882-571">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2e882-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="2e882-572">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="2e882-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="2e882-573">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-574">**classlib**</span><span class="sxs-lookup"><span data-stu-id="2e882-574">**classlib**</span></span>

<span data-ttu-id="2e882-575">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="2e882-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2e882-576">Valores: `netcoreapp2.1` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2e882-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="2e882-577">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="2e882-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="2e882-578">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-579">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="2e882-579">**mstest, xunit**</span></span>

<span data-ttu-id="2e882-580">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="2e882-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="2e882-581">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="2e882-582">**globaljson**</span></span>

<span data-ttu-id="2e882-583">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="2e882-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="2e882-584">**web**</span><span class="sxs-lookup"><span data-stu-id="2e882-584">**web**</span></span>

<span data-ttu-id="2e882-585">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2e882-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="2e882-586">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-587">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2e882-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="2e882-588">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="2e882-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="2e882-589">**webapi**</span><span class="sxs-lookup"><span data-stu-id="2e882-589">**webapi**</span></span>

<span data-ttu-id="2e882-590">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="2e882-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="2e882-591">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="2e882-591">The possible values are:</span></span>

- <span data-ttu-id="2e882-592">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="2e882-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="2e882-593">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="2e882-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="2e882-594">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="2e882-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="2e882-595">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="2e882-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="2e882-596">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="2e882-597">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="2e882-598">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="2e882-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="2e882-599">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="2e882-600">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-601">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="2e882-602">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2e882-603">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="2e882-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="2e882-604">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="2e882-605">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="2e882-606">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="2e882-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="2e882-607">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="2e882-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="2e882-608">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2e882-609">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="2e882-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="2e882-610">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="2e882-611">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2e882-612">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="2e882-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="2e882-613">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="2e882-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="2e882-614">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="2e882-615">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2e882-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="2e882-616">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="2e882-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2e882-617">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-618">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-619">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2e882-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="2e882-620">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="2e882-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="2e882-621">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="2e882-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="2e882-622">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="2e882-622">**mvc, razor**</span></span>

<span data-ttu-id="2e882-623">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="2e882-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="2e882-624">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="2e882-624">The possible values are:</span></span>

- <span data-ttu-id="2e882-625">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="2e882-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="2e882-626">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="2e882-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="2e882-627">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="2e882-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="2e882-628">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="2e882-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="2e882-629">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="2e882-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="2e882-630">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="2e882-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="2e882-631">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="2e882-632">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="2e882-633">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="2e882-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="2e882-634">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="2e882-635">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-636">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="2e882-637">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-638">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="2e882-639">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-640">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="2e882-641">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="2e882-642">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="2e882-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="2e882-643">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="2e882-644">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="2e882-645">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="2e882-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="2e882-646">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="2e882-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="2e882-647">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2e882-648">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="2e882-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="2e882-649">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="2e882-650">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2e882-651">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="2e882-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="2e882-652">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="2e882-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="2e882-653">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2e882-654">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="2e882-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="2e882-655">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="2e882-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="2e882-656">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="2e882-657">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2e882-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="2e882-658">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="2e882-659">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="2e882-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2e882-660">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-661">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-662">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2e882-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="2e882-663">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="2e882-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="2e882-664">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="2e882-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="2e882-665">**page**</span><span class="sxs-lookup"><span data-stu-id="2e882-665">**page**</span></span>

<span data-ttu-id="2e882-666">`-na|--namespace <NAMESPACE_NAME>` – namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="2e882-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="2e882-667">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="2e882-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="2e882-668">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="2e882-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="2e882-669">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="2e882-669">**viewimports**</span></span>

<span data-ttu-id="2e882-670">`-na|--namespace <NAMESPACE_NAME>` – namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="2e882-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="2e882-671">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="2e882-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="2e882-672">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="2e882-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="2e882-673">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="2e882-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="2e882-674">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-675">**classlib**</span><span class="sxs-lookup"><span data-stu-id="2e882-675">**classlib**</span></span>

<span data-ttu-id="2e882-676">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="2e882-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2e882-677">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2e882-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="2e882-678">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="2e882-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="2e882-679">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-680">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="2e882-680">**mstest, xunit**</span></span>

<span data-ttu-id="2e882-681">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="2e882-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="2e882-682">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="2e882-683">**globaljson**</span></span>

<span data-ttu-id="2e882-684">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="2e882-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="2e882-685">**web**</span><span class="sxs-lookup"><span data-stu-id="2e882-685">**web**</span></span>

<span data-ttu-id="2e882-686">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2e882-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="2e882-687">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-688">**webapi**</span><span class="sxs-lookup"><span data-stu-id="2e882-688">**webapi**</span></span>

<span data-ttu-id="2e882-689">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="2e882-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="2e882-690">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="2e882-690">The possible values are:</span></span>

- <span data-ttu-id="2e882-691">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="2e882-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="2e882-692">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="2e882-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="2e882-693">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="2e882-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="2e882-694">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="2e882-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="2e882-695">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="2e882-696">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="2e882-697">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="2e882-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="2e882-698">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="2e882-699">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-700">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="2e882-701">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2e882-702">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="2e882-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="2e882-703">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="2e882-704">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="2e882-705">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="2e882-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="2e882-706">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="2e882-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="2e882-707">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2e882-708">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="2e882-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="2e882-709">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="2e882-710">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2e882-711">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="2e882-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="2e882-712">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="2e882-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="2e882-713">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="2e882-714">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2e882-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="2e882-715">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="2e882-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2e882-716">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-717">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-718">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="2e882-718">**mvc, razor**</span></span>

<span data-ttu-id="2e882-719">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="2e882-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="2e882-720">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="2e882-720">The possible values are:</span></span>

- <span data-ttu-id="2e882-721">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="2e882-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="2e882-722">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="2e882-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="2e882-723">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="2e882-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="2e882-724">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="2e882-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="2e882-725">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="2e882-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="2e882-726">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="2e882-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="2e882-727">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="2e882-728">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="2e882-729">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="2e882-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="2e882-730">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="2e882-731">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-732">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="2e882-733">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-734">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="2e882-735">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-736">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="2e882-737">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="2e882-738">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="2e882-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="2e882-739">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="2e882-740">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="2e882-741">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="2e882-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="2e882-742">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="2e882-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="2e882-743">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2e882-744">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="2e882-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="2e882-745">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2e882-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="2e882-746">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2e882-747">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="2e882-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="2e882-748">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="2e882-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="2e882-749">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2e882-750">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="2e882-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="2e882-751">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="2e882-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="2e882-752">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2e882-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="2e882-753">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2e882-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="2e882-754">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="2e882-755">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="2e882-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2e882-756">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2e882-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="2e882-757">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2e882-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2e882-758">**page**</span><span class="sxs-lookup"><span data-stu-id="2e882-758">**page**</span></span>

<span data-ttu-id="2e882-759">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="2e882-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="2e882-760">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="2e882-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="2e882-761">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="2e882-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="2e882-762">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="2e882-762">**viewimports**</span></span>

<span data-ttu-id="2e882-763">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="2e882-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="2e882-764">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="2e882-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2e882-765">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="2e882-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="2e882-766">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="2e882-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="2e882-767">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="2e882-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2e882-768">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="2e882-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="2e882-769">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="2e882-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="2e882-770">**classlib**</span><span class="sxs-lookup"><span data-stu-id="2e882-770">**classlib**</span></span>

<span data-ttu-id="2e882-771">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="2e882-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2e882-772">Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="2e882-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="2e882-773">O valor padrão é `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="2e882-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="2e882-774">**mvc**</span><span class="sxs-lookup"><span data-stu-id="2e882-774">**mvc**</span></span>

<span data-ttu-id="2e882-775">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="2e882-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2e882-776">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="2e882-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="2e882-777">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="2e882-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="2e882-778">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="2e882-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="2e882-779">Valores: `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="2e882-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="2e882-780">O valor padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="2e882-780">The default value is `None`.</span></span>

<span data-ttu-id="2e882-781">`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="2e882-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="2e882-782">Valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="2e882-782">Values: `true` or `false`.</span></span> <span data-ttu-id="2e882-783">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="2e882-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="2e882-784">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2e882-784">Examples</span></span>

<span data-ttu-id="2e882-785">Crie um projeto de aplicativo de console em C# especificando o nome do modelo:</span><span class="sxs-lookup"><span data-stu-id="2e882-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="2e882-786">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="2e882-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="2e882-787">Crie um projeto de biblioteca de classes .NET Standard no diretório especificado (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="2e882-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="2e882-788">Crie um projeto de MVC em C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="2e882-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="2e882-789">Crie um projeto de xUnit:</span><span class="sxs-lookup"><span data-stu-id="2e882-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="2e882-790">Lista todos os modelos disponíveis para o MVC:</span><span class="sxs-lookup"><span data-stu-id="2e882-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="2e882-791">Liste todos os modelos que correspondem à substring *we*.</span><span class="sxs-lookup"><span data-stu-id="2e882-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="2e882-792">Nenhuma correspondência exata é encontrada, portanto, a correspondência de substring é executada em relação tanto ao nome curto quanto às colunas de nome.</span><span class="sxs-lookup"><span data-stu-id="2e882-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="2e882-793">Tentativa de invocar o modelo correspondente a *ng*.</span><span class="sxs-lookup"><span data-stu-id="2e882-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="2e882-794">Se não for possível determinar uma única correspondência, liste os modelos que são correspondências parciais.</span><span class="sxs-lookup"><span data-stu-id="2e882-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="2e882-795">Instale a versão 2.0 dos modelos de aplicativo de página única do ASP.NET Core (opção de comando disponível somente para o SDK do .NET Core 1.1 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="2e882-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="2e882-796">Crie um *global.json* no diretório atual definindo a versão do SDK como 2.0.0 (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="2e882-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="2e882-797">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e882-797">See also</span></span>

- [<span data-ttu-id="2e882-798">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="2e882-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- <span data-ttu-id="2e882-799">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="2e882-799">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md)</span></span>
- [<span data-ttu-id="2e882-800">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="2e882-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="2e882-801">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="2e882-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
