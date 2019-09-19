---
title: Comando dotnet new
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
ms.date: 05/06/2019
ms.openlocfilehash: b61b5fd53f470c30b636026fa19ebfad834d6354
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117665"
---
# <a name="dotnet-new"></a><span data-ttu-id="c02e8-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="c02e8-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c02e8-104">Nome</span><span class="sxs-lookup"><span data-stu-id="c02e8-104">Name</span></span>

<span data-ttu-id="c02e8-105">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c02e8-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="c02e8-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="c02e8-107">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="c02e8-107">.NET Core 2.2</span></span>](#tab/netcore22)

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c02e8-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c02e8-108">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c02e8-109">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="c02e8-109">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c02e8-110">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c02e8-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="c02e8-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="c02e8-111">Description</span></span>

<span data-ttu-id="c02e8-112">O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido.</span><span class="sxs-lookup"><span data-stu-id="c02e8-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="c02e8-113">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="c02e8-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="c02e8-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="c02e8-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="c02e8-115">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="c02e8-116">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="c02e8-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="c02e8-117">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="c02e8-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="c02e8-118">Se o valor `TEMPLATE` não for uma correspondência exata no texto na coluna **Modelos** ou **Nome Curto**, uma correspondência de substring será executada nessas duas colunas.</span><span class="sxs-lookup"><span data-stu-id="c02e8-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="c02e8-119">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="c02e8-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="c02e8-120">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="c02e8-120">The command contains a default list of templates.</span></span> <span data-ttu-id="c02e8-121">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c02e8-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="c02e8-122">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.2.100.</span><span class="sxs-lookup"><span data-stu-id="c02e8-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="c02e8-123">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="c02e8-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="c02e8-124">Modelos</span><span class="sxs-lookup"><span data-stu-id="c02e8-124">Templates</span></span>                                    | <span data-ttu-id="c02e8-125">Nome curto</span><span class="sxs-lookup"><span data-stu-id="c02e8-125">Short Name</span></span>        | <span data-ttu-id="c02e8-126">Idioma</span><span class="sxs-lookup"><span data-stu-id="c02e8-126">Language</span></span>     | <span data-ttu-id="c02e8-127">Marcas</span><span class="sxs-lookup"><span data-stu-id="c02e8-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="c02e8-128">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="c02e8-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="c02e8-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c02e8-129">[C#], F#, VB</span></span> | <span data-ttu-id="c02e8-130">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="c02e8-130">Common/Console</span></span>                        |
| <span data-ttu-id="c02e8-131">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="c02e8-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="c02e8-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c02e8-132">[C#], F#, VB</span></span> | <span data-ttu-id="c02e8-133">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="c02e8-133">Common/Library</span></span>                        |
| <span data-ttu-id="c02e8-134">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="c02e8-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="c02e8-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c02e8-135">[C#], F#, VB</span></span> | <span data-ttu-id="c02e8-136">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="c02e8-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="c02e8-137">Projeto de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="c02e8-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="c02e8-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c02e8-138">[C#], F#, VB</span></span> | <span data-ttu-id="c02e8-139">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="c02e8-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="c02e8-140">Item de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="c02e8-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="c02e8-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c02e8-141">[C#], F#, VB</span></span> | <span data-ttu-id="c02e8-142">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="c02e8-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="c02e8-143">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="c02e8-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="c02e8-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c02e8-144">[C#], F#, VB</span></span> | <span data-ttu-id="c02e8-145">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="c02e8-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="c02e8-146">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="c02e8-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="c02e8-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-147">[C#]</span></span>         | <span data-ttu-id="c02e8-148">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c02e8-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="c02e8-149">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="c02e8-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="c02e8-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-150">[C#]</span></span>         | <span data-ttu-id="c02e8-151">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c02e8-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="c02e8-152">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="c02e8-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="c02e8-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-153">[C#]</span></span>         | <span data-ttu-id="c02e8-154">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c02e8-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="c02e8-155">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="c02e8-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="c02e8-156">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c02e8-156">[C#], F#</span></span>     | <span data-ttu-id="c02e8-157">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="c02e8-157">Web/Empty</span></span>                             |
| <span data-ttu-id="c02e8-158">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="c02e8-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="c02e8-159">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c02e8-159">[C#], F#</span></span>     | <span data-ttu-id="c02e8-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="c02e8-160">Web/MVC</span></span>                               |
| <span data-ttu-id="c02e8-161">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c02e8-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="c02e8-162">`webapp`, `razor`</span><span class="sxs-lookup"><span data-stu-id="c02e8-162">`webapp`, `razor`</span></span> | <span data-ttu-id="c02e8-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-163">[C#]</span></span>         | <span data-ttu-id="c02e8-164">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="c02e8-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="c02e8-165">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="c02e8-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="c02e8-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-166">[C#]</span></span>         | <span data-ttu-id="c02e8-167">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c02e8-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="c02e8-168">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="c02e8-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="c02e8-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-169">[C#]</span></span>         | <span data-ttu-id="c02e8-170">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c02e8-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="c02e8-171">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="c02e8-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="c02e8-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-172">[C#]</span></span>         | <span data-ttu-id="c02e8-173">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c02e8-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="c02e8-174">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="c02e8-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="c02e8-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-175">[C#]</span></span>         | <span data-ttu-id="c02e8-176">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="c02e8-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="c02e8-177">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c02e8-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="c02e8-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c02e8-178">[C#], F#</span></span>     | <span data-ttu-id="c02e8-179">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="c02e8-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="c02e8-180">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="c02e8-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="c02e8-181">Config</span><span class="sxs-lookup"><span data-stu-id="c02e8-181">Config</span></span>                                |
| <span data-ttu-id="c02e8-182">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="c02e8-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="c02e8-183">Config</span><span class="sxs-lookup"><span data-stu-id="c02e8-183">Config</span></span>                                |
| <span data-ttu-id="c02e8-184">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="c02e8-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="c02e8-185">Config</span><span class="sxs-lookup"><span data-stu-id="c02e8-185">Config</span></span>                                |
| <span data-ttu-id="c02e8-186">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="c02e8-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="c02e8-187">Solução</span><span class="sxs-lookup"><span data-stu-id="c02e8-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c02e8-188">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c02e8-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="c02e8-189">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="c02e8-189">The command contains a default list of templates.</span></span> <span data-ttu-id="c02e8-190">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c02e8-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="c02e8-191">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="c02e8-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="c02e8-192">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="c02e8-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="c02e8-193">Modelos</span><span class="sxs-lookup"><span data-stu-id="c02e8-193">Templates</span></span>                                    | <span data-ttu-id="c02e8-194">Nome curto</span><span class="sxs-lookup"><span data-stu-id="c02e8-194">Short Name</span></span>      | <span data-ttu-id="c02e8-195">Idioma</span><span class="sxs-lookup"><span data-stu-id="c02e8-195">Language</span></span>     | <span data-ttu-id="c02e8-196">Marcas</span><span class="sxs-lookup"><span data-stu-id="c02e8-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="c02e8-197">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="c02e8-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="c02e8-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c02e8-198">[C#], F#, VB</span></span> | <span data-ttu-id="c02e8-199">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="c02e8-199">Common/Console</span></span>                        |
| <span data-ttu-id="c02e8-200">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="c02e8-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="c02e8-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c02e8-201">[C#], F#, VB</span></span> | <span data-ttu-id="c02e8-202">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="c02e8-202">Common/Library</span></span>                        |
| <span data-ttu-id="c02e8-203">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="c02e8-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="c02e8-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c02e8-204">[C#], F#, VB</span></span> | <span data-ttu-id="c02e8-205">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="c02e8-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="c02e8-206">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="c02e8-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="c02e8-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c02e8-207">[C#], F#, VB</span></span> | <span data-ttu-id="c02e8-208">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="c02e8-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="c02e8-209">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="c02e8-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="c02e8-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-210">[C#]</span></span>         | <span data-ttu-id="c02e8-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c02e8-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="c02e8-212">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="c02e8-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="c02e8-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-213">[C#]</span></span>         | <span data-ttu-id="c02e8-214">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c02e8-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="c02e8-215">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="c02e8-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="c02e8-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-216">[C#]</span></span>         | <span data-ttu-id="c02e8-217">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c02e8-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="c02e8-218">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="c02e8-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="c02e8-219">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c02e8-219">[C#], F#</span></span>     | <span data-ttu-id="c02e8-220">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="c02e8-220">Web/Empty</span></span>                             |
| <span data-ttu-id="c02e8-221">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="c02e8-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="c02e8-222">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c02e8-222">[C#], F#</span></span>     | <span data-ttu-id="c02e8-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="c02e8-223">Web/MVC</span></span>                               |
| <span data-ttu-id="c02e8-224">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c02e8-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="c02e8-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-225">[C#]</span></span>         | <span data-ttu-id="c02e8-226">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="c02e8-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="c02e8-227">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="c02e8-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="c02e8-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-228">[C#]</span></span>         | <span data-ttu-id="c02e8-229">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c02e8-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="c02e8-230">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="c02e8-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="c02e8-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-231">[C#]</span></span>         | <span data-ttu-id="c02e8-232">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c02e8-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="c02e8-233">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="c02e8-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="c02e8-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-234">[C#]</span></span>         | <span data-ttu-id="c02e8-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c02e8-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="c02e8-236">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="c02e8-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="c02e8-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-237">[C#]</span></span>         | <span data-ttu-id="c02e8-238">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="c02e8-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="c02e8-239">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c02e8-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="c02e8-240">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c02e8-240">[C#], F#</span></span>     | <span data-ttu-id="c02e8-241">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="c02e8-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="c02e8-242">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="c02e8-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="c02e8-243">Config</span><span class="sxs-lookup"><span data-stu-id="c02e8-243">Config</span></span>                                |
| <span data-ttu-id="c02e8-244">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="c02e8-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="c02e8-245">Config</span><span class="sxs-lookup"><span data-stu-id="c02e8-245">Config</span></span>                                |
| <span data-ttu-id="c02e8-246">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="c02e8-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="c02e8-247">Config</span><span class="sxs-lookup"><span data-stu-id="c02e8-247">Config</span></span>                                |
| <span data-ttu-id="c02e8-248">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="c02e8-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="c02e8-249">Solução</span><span class="sxs-lookup"><span data-stu-id="c02e8-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c02e8-250">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="c02e8-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="c02e8-251">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="c02e8-251">The command contains a default list of templates.</span></span> <span data-ttu-id="c02e8-252">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c02e8-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="c02e8-253">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="c02e8-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="c02e8-254">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="c02e8-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="c02e8-255">Modelos</span><span class="sxs-lookup"><span data-stu-id="c02e8-255">Templates</span></span>                                    | <span data-ttu-id="c02e8-256">Nome curto</span><span class="sxs-lookup"><span data-stu-id="c02e8-256">Short Name</span></span>    | <span data-ttu-id="c02e8-257">Idioma</span><span class="sxs-lookup"><span data-stu-id="c02e8-257">Language</span></span>     | <span data-ttu-id="c02e8-258">Marcas</span><span class="sxs-lookup"><span data-stu-id="c02e8-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="c02e8-259">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="c02e8-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="c02e8-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c02e8-260">[C#], F#, VB</span></span> | <span data-ttu-id="c02e8-261">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="c02e8-261">Common/Console</span></span>      |
| <span data-ttu-id="c02e8-262">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="c02e8-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="c02e8-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c02e8-263">[C#], F#, VB</span></span> | <span data-ttu-id="c02e8-264">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="c02e8-264">Common/Library</span></span>      |
| <span data-ttu-id="c02e8-265">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="c02e8-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="c02e8-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c02e8-266">[C#], F#, VB</span></span> | <span data-ttu-id="c02e8-267">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="c02e8-267">Test/MSTest</span></span>         |
| <span data-ttu-id="c02e8-268">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="c02e8-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="c02e8-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c02e8-269">[C#], F#, VB</span></span> | <span data-ttu-id="c02e8-270">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="c02e8-270">Test/xUnit</span></span>          |
| <span data-ttu-id="c02e8-271">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="c02e8-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="c02e8-272">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c02e8-272">[C#], F#</span></span>     | <span data-ttu-id="c02e8-273">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="c02e8-273">Web/Empty</span></span>           |
| <span data-ttu-id="c02e8-274">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="c02e8-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="c02e8-275">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c02e8-275">[C#], F#</span></span>     | <span data-ttu-id="c02e8-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="c02e8-276">Web/MVC</span></span>             |
| <span data-ttu-id="c02e8-277">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c02e8-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="c02e8-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-278">[C#]</span></span>         | <span data-ttu-id="c02e8-279">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="c02e8-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="c02e8-280">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="c02e8-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="c02e8-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-281">[C#]</span></span>         | <span data-ttu-id="c02e8-282">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c02e8-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="c02e8-283">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="c02e8-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="c02e8-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-284">[C#]</span></span>         | <span data-ttu-id="c02e8-285">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c02e8-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="c02e8-286">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="c02e8-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="c02e8-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-287">[C#]</span></span>         | <span data-ttu-id="c02e8-288">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c02e8-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="c02e8-289">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c02e8-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="c02e8-290">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c02e8-290">[C#], F#</span></span>     | <span data-ttu-id="c02e8-291">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="c02e8-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="c02e8-292">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="c02e8-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="c02e8-293">Config</span><span class="sxs-lookup"><span data-stu-id="c02e8-293">Config</span></span>              |
| <span data-ttu-id="c02e8-294">Configuração do Nuget</span><span class="sxs-lookup"><span data-stu-id="c02e8-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="c02e8-295">Config</span><span class="sxs-lookup"><span data-stu-id="c02e8-295">Config</span></span>              |
| <span data-ttu-id="c02e8-296">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="c02e8-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="c02e8-297">Config</span><span class="sxs-lookup"><span data-stu-id="c02e8-297">Config</span></span>              |
| <span data-ttu-id="c02e8-298">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="c02e8-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="c02e8-299">Solução</span><span class="sxs-lookup"><span data-stu-id="c02e8-299">Solution</span></span>            |
| <span data-ttu-id="c02e8-300">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="c02e8-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="c02e8-301">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c02e8-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="c02e8-302">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="c02e8-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="c02e8-303">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c02e8-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="c02e8-304">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="c02e8-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="c02e8-305">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c02e8-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c02e8-306">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c02e8-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="c02e8-307">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="c02e8-307">The command contains a default list of templates.</span></span> <span data-ttu-id="c02e8-308">Use `dotnet new -all` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c02e8-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="c02e8-309">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.0.1.</span><span class="sxs-lookup"><span data-stu-id="c02e8-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="c02e8-310">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="c02e8-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="c02e8-311">Modelos</span><span class="sxs-lookup"><span data-stu-id="c02e8-311">Templates</span></span>            | <span data-ttu-id="c02e8-312">Nome curto</span><span class="sxs-lookup"><span data-stu-id="c02e8-312">Short Name</span></span>    | <span data-ttu-id="c02e8-313">Idioma</span><span class="sxs-lookup"><span data-stu-id="c02e8-313">Language</span></span> | <span data-ttu-id="c02e8-314">Marcas</span><span class="sxs-lookup"><span data-stu-id="c02e8-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="c02e8-315">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="c02e8-315">Console Application</span></span>  | `console`     | <span data-ttu-id="c02e8-316">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c02e8-316">[C#], F#</span></span> | <span data-ttu-id="c02e8-317">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="c02e8-317">Common/Console</span></span> |
| <span data-ttu-id="c02e8-318">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="c02e8-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="c02e8-319">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c02e8-319">[C#], F#</span></span> | <span data-ttu-id="c02e8-320">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="c02e8-320">Common/Library</span></span> |
| <span data-ttu-id="c02e8-321">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="c02e8-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="c02e8-322">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c02e8-322">[C#], F#</span></span> | <span data-ttu-id="c02e8-323">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="c02e8-323">Test/MSTest</span></span>    |
| <span data-ttu-id="c02e8-324">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="c02e8-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="c02e8-325">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c02e8-325">[C#], F#</span></span> | <span data-ttu-id="c02e8-326">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="c02e8-326">Test/xUnit</span></span>     |
| <span data-ttu-id="c02e8-327">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="c02e8-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="c02e8-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-328">[C#]</span></span>     | <span data-ttu-id="c02e8-329">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="c02e8-329">Web/Empty</span></span>      |
| <span data-ttu-id="c02e8-330">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c02e8-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="c02e8-331">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c02e8-331">[C#], F#</span></span> | <span data-ttu-id="c02e8-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="c02e8-332">Web/MVC</span></span>        |
| <span data-ttu-id="c02e8-333">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c02e8-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="c02e8-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="c02e8-334">[C#]</span></span>     | <span data-ttu-id="c02e8-335">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="c02e8-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="c02e8-336">Configuração do Nuget</span><span class="sxs-lookup"><span data-stu-id="c02e8-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="c02e8-337">Config</span><span class="sxs-lookup"><span data-stu-id="c02e8-337">Config</span></span>         |
| <span data-ttu-id="c02e8-338">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="c02e8-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="c02e8-339">Config</span><span class="sxs-lookup"><span data-stu-id="c02e8-339">Config</span></span>         |
| <span data-ttu-id="c02e8-340">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="c02e8-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="c02e8-341">Solução</span><span class="sxs-lookup"><span data-stu-id="c02e8-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="c02e8-342">Opções</span><span class="sxs-lookup"><span data-stu-id="c02e8-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="c02e8-343">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="c02e8-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="c02e8-344">Exibe um resumo do que ocorreria se o comando fornecido fosse executado se resultasse na criação de um modelo.</span><span class="sxs-lookup"><span data-stu-id="c02e8-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="c02e8-345">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="c02e8-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="c02e8-346">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="c02e8-347">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="c02e8-347">Prints out help for the command.</span></span> <span data-ttu-id="c02e8-348">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="c02e8-349">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="c02e8-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c02e8-350">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="c02e8-351">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="c02e8-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="c02e8-352">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="c02e8-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="c02e8-353">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="c02e8-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="c02e8-354">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="c02e8-355">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="c02e8-356">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="c02e8-357">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="c02e8-357">The language of the template to create.</span></span> <span data-ttu-id="c02e8-358">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="c02e8-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c02e8-359">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="c02e8-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="c02e8-360">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="c02e8-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c02e8-361">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="c02e8-362">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="c02e8-362">The name for the created output.</span></span> <span data-ttu-id="c02e8-363">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="c02e8-364">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="c02e8-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c02e8-365">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="c02e8-365">Location to place the generated output.</span></span> <span data-ttu-id="c02e8-366">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="c02e8-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="c02e8-367">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c02e8-367">Filters templates based on available types.</span></span> <span data-ttu-id="c02e8-368">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="c02e8-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="c02e8-369">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="c02e8-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c02e8-370">Ao excluir o valor `<PATH|NUGET_ID>`, todos os pacotes de modelo atualmente instalados e seus modelos associados são exibidos.</span><span class="sxs-lookup"><span data-stu-id="c02e8-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="c02e8-371">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="c02e8-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="c02e8-372">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="c02e8-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="c02e8-373">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="c02e8-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c02e8-374">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c02e8-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="c02e8-375">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="c02e8-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="c02e8-376">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="c02e8-377">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="c02e8-377">Prints out help for the command.</span></span> <span data-ttu-id="c02e8-378">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="c02e8-379">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="c02e8-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c02e8-380">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="c02e8-381">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="c02e8-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="c02e8-382">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="c02e8-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="c02e8-383">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="c02e8-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="c02e8-384">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="c02e8-385">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="c02e8-386">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="c02e8-387">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="c02e8-387">The language of the template to create.</span></span> <span data-ttu-id="c02e8-388">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="c02e8-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c02e8-389">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="c02e8-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="c02e8-390">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="c02e8-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c02e8-391">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="c02e8-392">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="c02e8-392">The name for the created output.</span></span> <span data-ttu-id="c02e8-393">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="c02e8-394">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="c02e8-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c02e8-395">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="c02e8-395">Location to place the generated output.</span></span> <span data-ttu-id="c02e8-396">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="c02e8-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="c02e8-397">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c02e8-397">Filters templates based on available types.</span></span> <span data-ttu-id="c02e8-398">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="c02e8-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="c02e8-399">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="c02e8-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="c02e8-400">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="c02e8-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="c02e8-401">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="c02e8-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="c02e8-402">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="c02e8-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c02e8-403">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="c02e8-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="c02e8-404">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="c02e8-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="c02e8-405">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="c02e8-406">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="c02e8-406">Prints out help for the command.</span></span> <span data-ttu-id="c02e8-407">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="c02e8-408">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="c02e8-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c02e8-409">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="c02e8-410">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="c02e8-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="c02e8-411">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="c02e8-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="c02e8-412">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="c02e8-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="c02e8-413">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="c02e8-414">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="c02e8-415">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="c02e8-416">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="c02e8-416">The language of the template to create.</span></span> <span data-ttu-id="c02e8-417">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="c02e8-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c02e8-418">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="c02e8-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="c02e8-419">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="c02e8-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c02e8-420">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="c02e8-421">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="c02e8-421">The name for the created output.</span></span> <span data-ttu-id="c02e8-422">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c02e8-423">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="c02e8-423">Location to place the generated output.</span></span> <span data-ttu-id="c02e8-424">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="c02e8-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="c02e8-425">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c02e8-425">Filters templates based on available types.</span></span> <span data-ttu-id="c02e8-426">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="c02e8-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="c02e8-427">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="c02e8-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="c02e8-428">Para desinstalar um modelo usando uma origem `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="c02e8-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="c02e8-429">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="c02e8-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="c02e8-430">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="c02e8-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="c02e8-431">Se não for possível determinar o argumento `PATH` ou `NUGET_ID` necessário para desinstalar um modelo, executar `dotnet new --uninstall` sem um argumento listará todos os modelos instalados e o argumento necessário desinstalá-los.</span><span class="sxs-lookup"><span data-stu-id="c02e8-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c02e8-432">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c02e8-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="c02e8-433">Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="c02e8-434">Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força.</span><span class="sxs-lookup"><span data-stu-id="c02e8-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="c02e8-435">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="c02e8-436">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="c02e8-436">Prints out help for the command.</span></span> <span data-ttu-id="c02e8-437">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="c02e8-438">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="c02e8-439">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="c02e8-440">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="c02e8-441">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="c02e8-441">The language of the template to create.</span></span> <span data-ttu-id="c02e8-442">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="c02e8-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c02e8-443">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="c02e8-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="c02e8-444">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="c02e8-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c02e8-445">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="c02e8-446">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="c02e8-446">The name for the created output.</span></span> <span data-ttu-id="c02e8-447">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c02e8-448">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="c02e8-448">Location to place the generated output.</span></span> <span data-ttu-id="c02e8-449">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="c02e8-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="c02e8-450">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="c02e8-450">Template options</span></span>

<span data-ttu-id="c02e8-451">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c02e8-451">Each project template may have additional options available.</span></span> <span data-ttu-id="c02e8-452">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="c02e8-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="c02e8-453">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="c02e8-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="c02e8-454">**console**</span><span class="sxs-lookup"><span data-stu-id="c02e8-454">**console**</span></span>

<span data-ttu-id="c02e8-455">`--langVersion <VERSION_NUMBER>` – Define a propriedade `LangVersion` no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c02e8-456">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c02e8-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="c02e8-457">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="c02e8-457">Not supported for F#.</span></span>

<span data-ttu-id="c02e8-458">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-459">**angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="c02e8-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="c02e8-460">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c02e8-461">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-462">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c02e8-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c02e8-463">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="c02e8-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="c02e8-464">**razorclasslib**</span></span>

<span data-ttu-id="c02e8-465">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-466">**classlib**</span><span class="sxs-lookup"><span data-stu-id="c02e8-466">**classlib**</span></span>

<span data-ttu-id="c02e8-467">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="c02e8-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c02e8-468">Valores: `netcoreapp2.2` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c02e8-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="c02e8-469">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="c02e8-470">`--langVersion <VERSION_NUMBER>` – Define a propriedade `LangVersion` no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c02e8-471">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c02e8-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="c02e8-472">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="c02e8-472">Not supported for F#.</span></span>

<span data-ttu-id="c02e8-473">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-474">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="c02e8-474">**mstest, xunit**</span></span>

<span data-ttu-id="c02e8-475">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c02e8-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="c02e8-476">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-477">**nunit**</span><span class="sxs-lookup"><span data-stu-id="c02e8-477">**nunit**</span></span>

<span data-ttu-id="c02e8-478">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="c02e8-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c02e8-479">O valor padrão é `netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="c02e8-480">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c02e8-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="c02e8-481">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-482">**page**</span><span class="sxs-lookup"><span data-stu-id="c02e8-482">**page**</span></span>

<span data-ttu-id="c02e8-483">`-na|--namespace <NAMESPACE_NAME>` – namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="c02e8-484">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="c02e8-485">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="c02e8-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="c02e8-486">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="c02e8-486">**viewimports**</span></span>

<span data-ttu-id="c02e8-487">`-na|--namespace <NAMESPACE_NAME>` – namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="c02e8-488">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="c02e8-489">**web**</span><span class="sxs-lookup"><span data-stu-id="c02e8-489">**web**</span></span>

<span data-ttu-id="c02e8-490">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c02e8-491">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-492">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c02e8-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c02e8-493">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="c02e8-494">**mvc, webapp**</span><span class="sxs-lookup"><span data-stu-id="c02e8-494">**mvc, webapp**</span></span>

<span data-ttu-id="c02e8-495">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c02e8-496">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="c02e8-496">The possible values are:</span></span>

- <span data-ttu-id="c02e8-497">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="c02e8-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c02e8-498">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="c02e8-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="c02e8-499">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c02e8-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c02e8-500">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="c02e8-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c02e8-501">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="c02e8-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="c02e8-502">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="c02e8-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c02e8-503">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c02e8-504">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c02e8-505">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c02e8-506">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c02e8-507">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-508">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="c02e8-509">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-510">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="c02e8-511">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-512">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c02e8-513">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c02e8-514">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c02e8-515">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c02e8-516">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c02e8-517">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c02e8-518">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="c02e8-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c02e8-519">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c02e8-520">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c02e8-521">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c02e8-522">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c02e8-523">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c02e8-524">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="c02e8-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c02e8-525">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c02e8-526">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="c02e8-527">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="c02e8-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c02e8-528">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c02e8-529">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c02e8-530">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c02e8-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c02e8-531">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c02e8-532">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="c02e8-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="c02e8-533">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="c02e8-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c02e8-534">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-535">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-536">**webapi**</span><span class="sxs-lookup"><span data-stu-id="c02e8-536">**webapi**</span></span>

<span data-ttu-id="c02e8-537">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c02e8-538">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="c02e8-538">The possible values are:</span></span>

- <span data-ttu-id="c02e8-539">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="c02e8-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c02e8-540">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c02e8-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c02e8-541">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="c02e8-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c02e8-542">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="c02e8-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c02e8-543">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c02e8-544">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c02e8-545">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c02e8-546">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c02e8-547">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-548">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c02e8-549">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c02e8-550">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c02e8-551">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c02e8-552">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c02e8-553">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c02e8-554">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="c02e8-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c02e8-555">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c02e8-556">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c02e8-557">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c02e8-558">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c02e8-559">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c02e8-560">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="c02e8-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c02e8-561">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c02e8-562">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c02e8-563">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c02e8-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c02e8-564">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c02e8-565">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="c02e8-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="c02e8-566">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="c02e8-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c02e8-567">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-568">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="c02e8-569">**globaljson**</span></span>

<span data-ttu-id="c02e8-570">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="c02e8-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="c02e8-571">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c02e8-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="c02e8-572">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="c02e8-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="c02e8-573">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-574">**classlib**</span><span class="sxs-lookup"><span data-stu-id="c02e8-574">**classlib**</span></span>

<span data-ttu-id="c02e8-575">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="c02e8-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c02e8-576">Valores: `netcoreapp2.1` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c02e8-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="c02e8-577">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="c02e8-578">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-579">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="c02e8-579">**mstest, xunit**</span></span>

<span data-ttu-id="c02e8-580">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c02e8-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="c02e8-581">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="c02e8-582">**globaljson**</span></span>

<span data-ttu-id="c02e8-583">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="c02e8-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="c02e8-584">**web**</span><span class="sxs-lookup"><span data-stu-id="c02e8-584">**web**</span></span>

<span data-ttu-id="c02e8-585">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c02e8-586">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-587">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c02e8-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c02e8-588">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="c02e8-589">**webapi**</span><span class="sxs-lookup"><span data-stu-id="c02e8-589">**webapi**</span></span>

<span data-ttu-id="c02e8-590">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c02e8-591">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="c02e8-591">The possible values are:</span></span>

- <span data-ttu-id="c02e8-592">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="c02e8-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c02e8-593">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c02e8-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c02e8-594">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="c02e8-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c02e8-595">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="c02e8-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c02e8-596">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c02e8-597">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c02e8-598">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c02e8-599">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c02e8-600">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-601">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c02e8-602">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c02e8-603">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c02e8-604">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c02e8-605">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c02e8-606">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c02e8-607">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="c02e8-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c02e8-608">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c02e8-609">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c02e8-610">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c02e8-611">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c02e8-612">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c02e8-613">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="c02e8-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c02e8-614">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c02e8-615">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c02e8-616">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="c02e8-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c02e8-617">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-618">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-619">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c02e8-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c02e8-620">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c02e8-621">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="c02e8-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="c02e8-622">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="c02e8-622">**mvc, razor**</span></span>

<span data-ttu-id="c02e8-623">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c02e8-624">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="c02e8-624">The possible values are:</span></span>

- <span data-ttu-id="c02e8-625">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="c02e8-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c02e8-626">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="c02e8-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="c02e8-627">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c02e8-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c02e8-628">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="c02e8-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c02e8-629">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="c02e8-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="c02e8-630">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="c02e8-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c02e8-631">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c02e8-632">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c02e8-633">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c02e8-634">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c02e8-635">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-636">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="c02e8-637">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-638">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="c02e8-639">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-640">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c02e8-641">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c02e8-642">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c02e8-643">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c02e8-644">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c02e8-645">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c02e8-646">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="c02e8-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c02e8-647">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c02e8-648">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c02e8-649">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c02e8-650">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c02e8-651">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c02e8-652">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="c02e8-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c02e8-653">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c02e8-654">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="c02e8-655">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="c02e8-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c02e8-656">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c02e8-657">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="c02e8-658">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="c02e8-659">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="c02e8-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c02e8-660">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-661">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-662">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c02e8-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="c02e8-663">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c02e8-664">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="c02e8-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="c02e8-665">**page**</span><span class="sxs-lookup"><span data-stu-id="c02e8-665">**page**</span></span>

<span data-ttu-id="c02e8-666">`-na|--namespace <NAMESPACE_NAME>` – namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="c02e8-667">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="c02e8-668">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="c02e8-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="c02e8-669">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="c02e8-669">**viewimports**</span></span>

<span data-ttu-id="c02e8-670">`-na|--namespace <NAMESPACE_NAME>` – namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="c02e8-671">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="c02e8-672">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="c02e8-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="c02e8-673">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="c02e8-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="c02e8-674">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-675">**classlib**</span><span class="sxs-lookup"><span data-stu-id="c02e8-675">**classlib**</span></span>

<span data-ttu-id="c02e8-676">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="c02e8-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c02e8-677">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c02e8-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="c02e8-678">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="c02e8-679">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-680">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="c02e8-680">**mstest, xunit**</span></span>

<span data-ttu-id="c02e8-681">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c02e8-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="c02e8-682">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="c02e8-683">**globaljson**</span></span>

<span data-ttu-id="c02e8-684">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="c02e8-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="c02e8-685">**web**</span><span class="sxs-lookup"><span data-stu-id="c02e8-685">**web**</span></span>

<span data-ttu-id="c02e8-686">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="c02e8-687">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-688">**webapi**</span><span class="sxs-lookup"><span data-stu-id="c02e8-688">**webapi**</span></span>

<span data-ttu-id="c02e8-689">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c02e8-690">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="c02e8-690">The possible values are:</span></span>

- <span data-ttu-id="c02e8-691">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="c02e8-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c02e8-692">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c02e8-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c02e8-693">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="c02e8-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c02e8-694">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="c02e8-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c02e8-695">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c02e8-696">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c02e8-697">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c02e8-698">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c02e8-699">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-700">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c02e8-701">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c02e8-702">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c02e8-703">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c02e8-704">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c02e8-705">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c02e8-706">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="c02e8-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c02e8-707">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c02e8-708">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c02e8-709">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c02e8-710">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c02e8-711">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c02e8-712">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="c02e8-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c02e8-713">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c02e8-714">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="c02e8-715">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="c02e8-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c02e8-716">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-717">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-718">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="c02e8-718">**mvc, razor**</span></span>

<span data-ttu-id="c02e8-719">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c02e8-720">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="c02e8-720">The possible values are:</span></span>

- <span data-ttu-id="c02e8-721">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="c02e8-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="c02e8-722">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="c02e8-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="c02e8-723">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c02e8-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="c02e8-724">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="c02e8-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="c02e8-725">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="c02e8-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="c02e8-726">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="c02e8-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="c02e8-727">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c02e8-728">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c02e8-729">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="c02e8-730">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c02e8-731">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-732">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="c02e8-733">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-734">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="c02e8-735">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-736">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c02e8-737">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c02e8-738">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="c02e8-739">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="c02e8-740">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c02e8-741">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="c02e8-742">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="c02e8-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="c02e8-743">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c02e8-744">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="c02e8-745">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c02e8-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c02e8-746">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c02e8-747">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="c02e8-748">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="c02e8-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c02e8-749">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c02e8-750">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="c02e8-751">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="c02e8-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="c02e8-752">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="c02e8-753">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="c02e8-754">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="c02e8-755">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="c02e8-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c02e8-756">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="c02e8-757">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c02e8-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="c02e8-758">**page**</span><span class="sxs-lookup"><span data-stu-id="c02e8-758">**page**</span></span>

<span data-ttu-id="c02e8-759">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="c02e8-760">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="c02e8-761">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="c02e8-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="c02e8-762">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="c02e8-762">**viewimports**</span></span>

<span data-ttu-id="c02e8-763">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="c02e8-764">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c02e8-765">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c02e8-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="c02e8-766">**console, xunit, mstest, web, webapi**</span><span class="sxs-lookup"><span data-stu-id="c02e8-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="c02e8-767">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="c02e8-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c02e8-768">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="c02e8-769">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="c02e8-770">**classlib**</span><span class="sxs-lookup"><span data-stu-id="c02e8-770">**classlib**</span></span>

<span data-ttu-id="c02e8-771">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="c02e8-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c02e8-772">Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="c02e8-773">O valor padrão é `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="c02e8-774">**mvc**</span><span class="sxs-lookup"><span data-stu-id="c02e8-774">**mvc**</span></span>

<span data-ttu-id="c02e8-775">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="c02e8-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c02e8-776">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="c02e8-777">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="c02e8-778">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="c02e8-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="c02e8-779">Valores: `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="c02e8-780">O valor padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-780">The default value is `None`.</span></span>

<span data-ttu-id="c02e8-781">`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="c02e8-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="c02e8-782">Valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-782">Values: `true` or `false`.</span></span> <span data-ttu-id="c02e8-783">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="c02e8-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="c02e8-784">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c02e8-784">Examples</span></span>

<span data-ttu-id="c02e8-785">Crie um projeto de aplicativo de console em C# especificando o nome do modelo:</span><span class="sxs-lookup"><span data-stu-id="c02e8-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="c02e8-786">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="c02e8-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="c02e8-787">Crie um projeto de biblioteca de classes .NET Standard no diretório especificado (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="c02e8-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="c02e8-788">Crie um projeto de MVC em C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="c02e8-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="c02e8-789">Crie um projeto de xUnit:</span><span class="sxs-lookup"><span data-stu-id="c02e8-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="c02e8-790">Lista todos os modelos disponíveis para o MVC:</span><span class="sxs-lookup"><span data-stu-id="c02e8-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="c02e8-791">Liste todos os modelos que correspondem à substring *we*.</span><span class="sxs-lookup"><span data-stu-id="c02e8-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="c02e8-792">Nenhuma correspondência exata é encontrada, portanto, a correspondência de substring é executada em relação tanto ao nome curto quanto às colunas de nome.</span><span class="sxs-lookup"><span data-stu-id="c02e8-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="c02e8-793">Tentativa de invocar o modelo correspondente a *ng*.</span><span class="sxs-lookup"><span data-stu-id="c02e8-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="c02e8-794">Se não for possível determinar uma única correspondência, liste os modelos que são correspondências parciais.</span><span class="sxs-lookup"><span data-stu-id="c02e8-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="c02e8-795">Instale a versão 2.0 dos modelos de aplicativo de página única do ASP.NET Core (opção de comando disponível somente para o SDK do .NET Core 1.1 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="c02e8-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="c02e8-796">Crie um *global.json* no diretório atual definindo a versão do SDK como 2.0.0 (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="c02e8-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="c02e8-797">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c02e8-797">See also</span></span>

- [<span data-ttu-id="c02e8-798">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="c02e8-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- <span data-ttu-id="c02e8-799">[Create a custom template for dotnet new](../tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="c02e8-799">[Create a custom template for dotnet new](../tutorials/create-custom-template.md)</span></span>
- [<span data-ttu-id="c02e8-800">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="c02e8-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="c02e8-801">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="c02e8-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
