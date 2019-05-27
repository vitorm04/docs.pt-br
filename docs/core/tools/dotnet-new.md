---
title: Comando dotnet new
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
ms.date: 05/06/2019
ms.openlocfilehash: f8bc8cb59ae6e421f4e9bd05925376399939056d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878310"
---
# <a name="dotnet-new"></a><span data-ttu-id="cd8c5-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="cd8c5-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="cd8c5-104">Nome</span><span class="sxs-lookup"><span data-stu-id="cd8c5-104">Name</span></span>

<span data-ttu-id="cd8c5-105">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cd8c5-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="cd8c5-106">Synopsis</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="cd8c5-107">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="cd8c5-107">.NET Core 2.2</span></span>](#tab/netcore22)

```console
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="cd8c5-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cd8c5-108">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="cd8c5-109">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="cd8c5-109">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cd8c5-110">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="cd8c5-110">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="cd8c5-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd8c5-111">Description</span></span>

<span data-ttu-id="cd8c5-112">O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-112">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="cd8c5-113">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-113">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="cd8c5-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="cd8c5-114">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="cd8c5-115">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-115">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="cd8c5-116">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-116">Each template might have specific options you can pass.</span></span> <span data-ttu-id="cd8c5-117">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-117">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="cd8c5-118">Se o valor `TEMPLATE` não for uma correspondência exata no texto na coluna **Modelos** ou **Nome Curto**, uma correspondência de substring será executada nessas duas colunas.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-118">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column, a substring match is performed on those two columns.</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="cd8c5-119">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="cd8c5-119">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="cd8c5-120">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-120">The command contains a default list of templates.</span></span> <span data-ttu-id="cd8c5-121">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-121">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="cd8c5-122">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.2.100.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-122">The following table shows the templates that come pre-installed with the .NET Core SDK 2.2.100.</span></span> <span data-ttu-id="cd8c5-123">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-123">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="cd8c5-124">Modelos</span><span class="sxs-lookup"><span data-stu-id="cd8c5-124">Templates</span></span>                                    | <span data-ttu-id="cd8c5-125">Nome curto</span><span class="sxs-lookup"><span data-stu-id="cd8c5-125">Short Name</span></span>        | <span data-ttu-id="cd8c5-126">Idioma</span><span class="sxs-lookup"><span data-stu-id="cd8c5-126">Language</span></span>     | <span data-ttu-id="cd8c5-127">Marcas</span><span class="sxs-lookup"><span data-stu-id="cd8c5-127">Tags</span></span>                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| <span data-ttu-id="cd8c5-128">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="cd8c5-128">Console Application</span></span>                          | `console`         | <span data-ttu-id="cd8c5-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cd8c5-129">[C#], F#, VB</span></span> | <span data-ttu-id="cd8c5-130">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="cd8c5-130">Common/Console</span></span>                        |
| <span data-ttu-id="cd8c5-131">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="cd8c5-131">Class library</span></span>                                | `classlib`        | <span data-ttu-id="cd8c5-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cd8c5-132">[C#], F#, VB</span></span> | <span data-ttu-id="cd8c5-133">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="cd8c5-133">Common/Library</span></span>                        |
| <span data-ttu-id="cd8c5-134">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="cd8c5-134">Unit Test Project</span></span>                            | `mstest`          | <span data-ttu-id="cd8c5-135">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cd8c5-135">[C#], F#, VB</span></span> | <span data-ttu-id="cd8c5-136">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="cd8c5-136">Test/MSTest</span></span>                           |
| <span data-ttu-id="cd8c5-137">Projeto de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="cd8c5-137">NUnit 3 Test Project</span></span>                         | `nunit`           | <span data-ttu-id="cd8c5-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cd8c5-138">[C#], F#, VB</span></span> | <span data-ttu-id="cd8c5-139">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="cd8c5-139">Test/NUnit</span></span>                            |
| <span data-ttu-id="cd8c5-140">Item de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="cd8c5-140">NUnit 3 Test Item</span></span>                            | `nunit-test`      | <span data-ttu-id="cd8c5-141">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cd8c5-141">[C#], F#, VB</span></span> | <span data-ttu-id="cd8c5-142">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="cd8c5-142">Test/NUnit</span></span>                            |
| <span data-ttu-id="cd8c5-143">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="cd8c5-143">xUnit Test Project</span></span>                           | `xunit`           | <span data-ttu-id="cd8c5-144">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cd8c5-144">[C#], F#, VB</span></span> | <span data-ttu-id="cd8c5-145">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="cd8c5-145">Test/xUnit</span></span>                            |
| <span data-ttu-id="cd8c5-146">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="cd8c5-146">Razor Page</span></span>                                   | `page`            | <span data-ttu-id="cd8c5-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-147">[C#]</span></span>         | <span data-ttu-id="cd8c5-148">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cd8c5-148">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="cd8c5-149">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="cd8c5-149">MVC ViewImports</span></span>                              | `viewimports`     | <span data-ttu-id="cd8c5-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-150">[C#]</span></span>         | <span data-ttu-id="cd8c5-151">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cd8c5-151">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="cd8c5-152">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="cd8c5-152">MVC ViewStart</span></span>                                | `viewstart`       | <span data-ttu-id="cd8c5-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-153">[C#]</span></span>         | <span data-ttu-id="cd8c5-154">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cd8c5-154">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="cd8c5-155">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="cd8c5-155">ASP.NET Core Empty</span></span>                           | `web`             | <span data-ttu-id="cd8c5-156">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="cd8c5-156">[C#], F#</span></span>     | <span data-ttu-id="cd8c5-157">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="cd8c5-157">Web/Empty</span></span>                             |
| <span data-ttu-id="cd8c5-158">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="cd8c5-158">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`             | <span data-ttu-id="cd8c5-159">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="cd8c5-159">[C#], F#</span></span>     | <span data-ttu-id="cd8c5-160">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="cd8c5-160">Web/MVC</span></span>                               |
| <span data-ttu-id="cd8c5-161">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cd8c5-161">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="cd8c5-162">`webapp`, `razor`</span><span class="sxs-lookup"><span data-stu-id="cd8c5-162">`webapp`, `razor`</span></span> | <span data-ttu-id="cd8c5-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-163">[C#]</span></span>         | <span data-ttu-id="cd8c5-164">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="cd8c5-164">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="cd8c5-165">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="cd8c5-165">ASP.NET Core with Angular</span></span>                    | `angular`         | <span data-ttu-id="cd8c5-166">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-166">[C#]</span></span>         | <span data-ttu-id="cd8c5-167">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="cd8c5-167">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="cd8c5-168">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="cd8c5-168">ASP.NET Core with React.js</span></span>                   | `react`           | <span data-ttu-id="cd8c5-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-169">[C#]</span></span>         | <span data-ttu-id="cd8c5-170">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="cd8c5-170">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="cd8c5-171">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="cd8c5-171">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`      | <span data-ttu-id="cd8c5-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-172">[C#]</span></span>         | <span data-ttu-id="cd8c5-173">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="cd8c5-173">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="cd8c5-174">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="cd8c5-174">Razor Class Library</span></span>                          | `razorclasslib`   | <span data-ttu-id="cd8c5-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-175">[C#]</span></span>         | <span data-ttu-id="cd8c5-176">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="cd8c5-176">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="cd8c5-177">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cd8c5-177">ASP.NET Core Web API</span></span>                         | `webapi`          | <span data-ttu-id="cd8c5-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="cd8c5-178">[C#], F#</span></span>     | <span data-ttu-id="cd8c5-179">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="cd8c5-179">Web/WebAPI</span></span>                            |
| <span data-ttu-id="cd8c5-180">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="cd8c5-180">global.json file</span></span>                             | `globaljson`      |              | <span data-ttu-id="cd8c5-181">Config</span><span class="sxs-lookup"><span data-stu-id="cd8c5-181">Config</span></span>                                |
| <span data-ttu-id="cd8c5-182">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="cd8c5-182">NuGet Config</span></span>                                 | `nugetconfig`     |              | <span data-ttu-id="cd8c5-183">Config</span><span class="sxs-lookup"><span data-stu-id="cd8c5-183">Config</span></span>                                |
| <span data-ttu-id="cd8c5-184">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="cd8c5-184">Web Config</span></span>                                   | `webconfig`       |              | <span data-ttu-id="cd8c5-185">Config</span><span class="sxs-lookup"><span data-stu-id="cd8c5-185">Config</span></span>                                |
| <span data-ttu-id="cd8c5-186">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="cd8c5-186">Solution File</span></span>                                | `sln`             |              | <span data-ttu-id="cd8c5-187">Solução</span><span class="sxs-lookup"><span data-stu-id="cd8c5-187">Solution</span></span>                              |

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="cd8c5-188">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cd8c5-188">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="cd8c5-189">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-189">The command contains a default list of templates.</span></span> <span data-ttu-id="cd8c5-190">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-190">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="cd8c5-191">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-191">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="cd8c5-192">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-192">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="cd8c5-193">Modelos</span><span class="sxs-lookup"><span data-stu-id="cd8c5-193">Templates</span></span>                                    | <span data-ttu-id="cd8c5-194">Nome curto</span><span class="sxs-lookup"><span data-stu-id="cd8c5-194">Short Name</span></span>      | <span data-ttu-id="cd8c5-195">Idioma</span><span class="sxs-lookup"><span data-stu-id="cd8c5-195">Language</span></span>     | <span data-ttu-id="cd8c5-196">Marcas</span><span class="sxs-lookup"><span data-stu-id="cd8c5-196">Tags</span></span>                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| <span data-ttu-id="cd8c5-197">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="cd8c5-197">Console Application</span></span>                          | `console`       | <span data-ttu-id="cd8c5-198">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cd8c5-198">[C#], F#, VB</span></span> | <span data-ttu-id="cd8c5-199">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="cd8c5-199">Common/Console</span></span>                        |
| <span data-ttu-id="cd8c5-200">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="cd8c5-200">Class library</span></span>                                | `classlib`      | <span data-ttu-id="cd8c5-201">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cd8c5-201">[C#], F#, VB</span></span> | <span data-ttu-id="cd8c5-202">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="cd8c5-202">Common/Library</span></span>                        |
| <span data-ttu-id="cd8c5-203">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="cd8c5-203">Unit Test Project</span></span>                            | `mstest`        | <span data-ttu-id="cd8c5-204">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cd8c5-204">[C#], F#, VB</span></span> | <span data-ttu-id="cd8c5-205">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="cd8c5-205">Test/MSTest</span></span>                           |
| <span data-ttu-id="cd8c5-206">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="cd8c5-206">xUnit Test Project</span></span>                           | `xunit`         | <span data-ttu-id="cd8c5-207">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cd8c5-207">[C#], F#, VB</span></span> | <span data-ttu-id="cd8c5-208">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="cd8c5-208">Test/xUnit</span></span>                            |
| <span data-ttu-id="cd8c5-209">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="cd8c5-209">Razor Page</span></span>                                   | `page`          | <span data-ttu-id="cd8c5-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-210">[C#]</span></span>         | <span data-ttu-id="cd8c5-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cd8c5-211">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="cd8c5-212">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="cd8c5-212">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="cd8c5-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-213">[C#]</span></span>         | <span data-ttu-id="cd8c5-214">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cd8c5-214">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="cd8c5-215">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="cd8c5-215">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="cd8c5-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-216">[C#]</span></span>         | <span data-ttu-id="cd8c5-217">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cd8c5-217">Web/ASP.NET</span></span>                           |
| <span data-ttu-id="cd8c5-218">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="cd8c5-218">ASP.NET Core Empty</span></span>                           | `web`           | <span data-ttu-id="cd8c5-219">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="cd8c5-219">[C#], F#</span></span>     | <span data-ttu-id="cd8c5-220">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="cd8c5-220">Web/Empty</span></span>                             |
| <span data-ttu-id="cd8c5-221">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="cd8c5-221">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="cd8c5-222">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="cd8c5-222">[C#], F#</span></span>     | <span data-ttu-id="cd8c5-223">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="cd8c5-223">Web/MVC</span></span>                               |
| <span data-ttu-id="cd8c5-224">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cd8c5-224">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="cd8c5-225">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-225">[C#]</span></span>         | <span data-ttu-id="cd8c5-226">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="cd8c5-226">Web/MVC/Razor Pages</span></span>                   |
| <span data-ttu-id="cd8c5-227">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="cd8c5-227">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="cd8c5-228">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-228">[C#]</span></span>         | <span data-ttu-id="cd8c5-229">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="cd8c5-229">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="cd8c5-230">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="cd8c5-230">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="cd8c5-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-231">[C#]</span></span>         | <span data-ttu-id="cd8c5-232">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="cd8c5-232">Web/MVC/SPA</span></span>                           |
| <span data-ttu-id="cd8c5-233">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="cd8c5-233">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="cd8c5-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-234">[C#]</span></span>         | <span data-ttu-id="cd8c5-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="cd8c5-235">Web/MVC/SPA</span></span>                           | 
| <span data-ttu-id="cd8c5-236">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="cd8c5-236">Razor Class Library</span></span>                          | `razorclasslib` | <span data-ttu-id="cd8c5-237">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-237">[C#]</span></span>         | <span data-ttu-id="cd8c5-238">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="cd8c5-238">Web/Razor/Library/Razor Class Library</span></span> |
| <span data-ttu-id="cd8c5-239">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cd8c5-239">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="cd8c5-240">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="cd8c5-240">[C#], F#</span></span>     | <span data-ttu-id="cd8c5-241">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="cd8c5-241">Web/WebAPI</span></span>                            |
| <span data-ttu-id="cd8c5-242">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="cd8c5-242">global.json file</span></span>                             | `globaljson`    |              | <span data-ttu-id="cd8c5-243">Config</span><span class="sxs-lookup"><span data-stu-id="cd8c5-243">Config</span></span>                                |
| <span data-ttu-id="cd8c5-244">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="cd8c5-244">NuGet Config</span></span>                                 | `nugetconfig`   |              | <span data-ttu-id="cd8c5-245">Config</span><span class="sxs-lookup"><span data-stu-id="cd8c5-245">Config</span></span>                                |
| <span data-ttu-id="cd8c5-246">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="cd8c5-246">Web Config</span></span>                                   | `webconfig`     |              | <span data-ttu-id="cd8c5-247">Config</span><span class="sxs-lookup"><span data-stu-id="cd8c5-247">Config</span></span>                                |
| <span data-ttu-id="cd8c5-248">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="cd8c5-248">Solution File</span></span>                                | `sln`           |              | <span data-ttu-id="cd8c5-249">Solução</span><span class="sxs-lookup"><span data-stu-id="cd8c5-249">Solution</span></span>                              |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="cd8c5-250">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="cd8c5-250">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="cd8c5-251">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-251">The command contains a default list of templates.</span></span> <span data-ttu-id="cd8c5-252">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-252">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="cd8c5-253">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-253">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.0.</span></span> <span data-ttu-id="cd8c5-254">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-254">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="cd8c5-255">Modelos</span><span class="sxs-lookup"><span data-stu-id="cd8c5-255">Templates</span></span>                                    | <span data-ttu-id="cd8c5-256">Nome curto</span><span class="sxs-lookup"><span data-stu-id="cd8c5-256">Short Name</span></span>    | <span data-ttu-id="cd8c5-257">Idioma</span><span class="sxs-lookup"><span data-stu-id="cd8c5-257">Language</span></span>     | <span data-ttu-id="cd8c5-258">Marcas</span><span class="sxs-lookup"><span data-stu-id="cd8c5-258">Tags</span></span>                |
|----------------------------------------------|---------------|--------------|---------------------|
| <span data-ttu-id="cd8c5-259">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="cd8c5-259">Console Application</span></span>                          | `console`     | <span data-ttu-id="cd8c5-260">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cd8c5-260">[C#], F#, VB</span></span> | <span data-ttu-id="cd8c5-261">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="cd8c5-261">Common/Console</span></span>      |
| <span data-ttu-id="cd8c5-262">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="cd8c5-262">Class library</span></span>                                | `classlib`    | <span data-ttu-id="cd8c5-263">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cd8c5-263">[C#], F#, VB</span></span> | <span data-ttu-id="cd8c5-264">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="cd8c5-264">Common/Library</span></span>      |
| <span data-ttu-id="cd8c5-265">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="cd8c5-265">Unit Test Project</span></span>                            | `mstest`      | <span data-ttu-id="cd8c5-266">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cd8c5-266">[C#], F#, VB</span></span> | <span data-ttu-id="cd8c5-267">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="cd8c5-267">Test/MSTest</span></span>         |
| <span data-ttu-id="cd8c5-268">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="cd8c5-268">xUnit Test Project</span></span>                           | `xunit`       | <span data-ttu-id="cd8c5-269">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="cd8c5-269">[C#], F#, VB</span></span> | <span data-ttu-id="cd8c5-270">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="cd8c5-270">Test/xUnit</span></span>          |
| <span data-ttu-id="cd8c5-271">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="cd8c5-271">ASP.NET Core Empty</span></span>                           | `web`         | <span data-ttu-id="cd8c5-272">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="cd8c5-272">[C#], F#</span></span>     | <span data-ttu-id="cd8c5-273">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="cd8c5-273">Web/Empty</span></span>           |
| <span data-ttu-id="cd8c5-274">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="cd8c5-274">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="cd8c5-275">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="cd8c5-275">[C#], F#</span></span>     | <span data-ttu-id="cd8c5-276">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="cd8c5-276">Web/MVC</span></span>             |
| <span data-ttu-id="cd8c5-277">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cd8c5-277">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="cd8c5-278">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-278">[C#]</span></span>         | <span data-ttu-id="cd8c5-279">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="cd8c5-279">Web/MVC/Razor Pages</span></span> |
| <span data-ttu-id="cd8c5-280">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="cd8c5-280">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="cd8c5-281">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-281">[C#]</span></span>         | <span data-ttu-id="cd8c5-282">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="cd8c5-282">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="cd8c5-283">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="cd8c5-283">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="cd8c5-284">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-284">[C#]</span></span>         | <span data-ttu-id="cd8c5-285">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="cd8c5-285">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="cd8c5-286">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="cd8c5-286">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="cd8c5-287">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-287">[C#]</span></span>         | <span data-ttu-id="cd8c5-288">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="cd8c5-288">Web/MVC/SPA</span></span>         |
| <span data-ttu-id="cd8c5-289">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cd8c5-289">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="cd8c5-290">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="cd8c5-290">[C#], F#</span></span>     | <span data-ttu-id="cd8c5-291">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="cd8c5-291">Web/WebAPI</span></span>          |
| <span data-ttu-id="cd8c5-292">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="cd8c5-292">global.json file</span></span>                             | `globaljson`  |              | <span data-ttu-id="cd8c5-293">Config</span><span class="sxs-lookup"><span data-stu-id="cd8c5-293">Config</span></span>              |
| <span data-ttu-id="cd8c5-294">Configuração do Nuget</span><span class="sxs-lookup"><span data-stu-id="cd8c5-294">Nuget Config</span></span>                                 | `nugetconfig` |              | <span data-ttu-id="cd8c5-295">Config</span><span class="sxs-lookup"><span data-stu-id="cd8c5-295">Config</span></span>              |
| <span data-ttu-id="cd8c5-296">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="cd8c5-296">Web Config</span></span>                                   | `webconfig`   |              | <span data-ttu-id="cd8c5-297">Config</span><span class="sxs-lookup"><span data-stu-id="cd8c5-297">Config</span></span>              |
| <span data-ttu-id="cd8c5-298">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="cd8c5-298">Solution File</span></span>                                | `sln`         |              | <span data-ttu-id="cd8c5-299">Solução</span><span class="sxs-lookup"><span data-stu-id="cd8c5-299">Solution</span></span>            |
| <span data-ttu-id="cd8c5-300">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="cd8c5-300">Razor Page</span></span>                                   | `page`        |              | <span data-ttu-id="cd8c5-301">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cd8c5-301">Web/ASP.NET</span></span>         |
| <span data-ttu-id="cd8c5-302">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="cd8c5-302">MVC ViewImports</span></span>                              | `viewimports` |              | <span data-ttu-id="cd8c5-303">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cd8c5-303">Web/ASP.NET</span></span>         |
| <span data-ttu-id="cd8c5-304">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="cd8c5-304">MVC ViewStart</span></span>                                | `viewstart`   |              | <span data-ttu-id="cd8c5-305">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cd8c5-305">Web/ASP.NET</span></span>         |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cd8c5-306">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="cd8c5-306">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="cd8c5-307">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-307">The command contains a default list of templates.</span></span> <span data-ttu-id="cd8c5-308">Use `dotnet new -all` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-308">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="cd8c5-309">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.0.1.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-309">The following table shows the templates that come pre-installed with the .NET Core SDK 1.0.1.</span></span> <span data-ttu-id="cd8c5-310">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-310">The default language for the template is shown inside the brackets.</span></span>

| <span data-ttu-id="cd8c5-311">Modelos</span><span class="sxs-lookup"><span data-stu-id="cd8c5-311">Templates</span></span>            | <span data-ttu-id="cd8c5-312">Nome curto</span><span class="sxs-lookup"><span data-stu-id="cd8c5-312">Short Name</span></span>    | <span data-ttu-id="cd8c5-313">Idioma</span><span class="sxs-lookup"><span data-stu-id="cd8c5-313">Language</span></span> | <span data-ttu-id="cd8c5-314">Marcas</span><span class="sxs-lookup"><span data-stu-id="cd8c5-314">Tags</span></span>           |
|----------------------|---------------|----------|----------------|
| <span data-ttu-id="cd8c5-315">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="cd8c5-315">Console Application</span></span>  | `console`     | <span data-ttu-id="cd8c5-316">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="cd8c5-316">[C#], F#</span></span> | <span data-ttu-id="cd8c5-317">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="cd8c5-317">Common/Console</span></span> |
| <span data-ttu-id="cd8c5-318">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="cd8c5-318">Class library</span></span>        | `classlib`    | <span data-ttu-id="cd8c5-319">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="cd8c5-319">[C#], F#</span></span> | <span data-ttu-id="cd8c5-320">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="cd8c5-320">Common/Library</span></span> |
| <span data-ttu-id="cd8c5-321">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="cd8c5-321">Unit Test Project</span></span>    | `mstest`      | <span data-ttu-id="cd8c5-322">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="cd8c5-322">[C#], F#</span></span> | <span data-ttu-id="cd8c5-323">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="cd8c5-323">Test/MSTest</span></span>    |
| <span data-ttu-id="cd8c5-324">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="cd8c5-324">xUnit Test Project</span></span>   | `xunit`       | <span data-ttu-id="cd8c5-325">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="cd8c5-325">[C#], F#</span></span> | <span data-ttu-id="cd8c5-326">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="cd8c5-326">Test/xUnit</span></span>     |
| <span data-ttu-id="cd8c5-327">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="cd8c5-327">ASP.NET Core Empty</span></span>   | `web`         | <span data-ttu-id="cd8c5-328">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-328">[C#]</span></span>     | <span data-ttu-id="cd8c5-329">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="cd8c5-329">Web/Empty</span></span>      |
| <span data-ttu-id="cd8c5-330">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cd8c5-330">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="cd8c5-331">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="cd8c5-331">[C#], F#</span></span> | <span data-ttu-id="cd8c5-332">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="cd8c5-332">Web/MVC</span></span>        |
| <span data-ttu-id="cd8c5-333">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cd8c5-333">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="cd8c5-334">[C#]</span><span class="sxs-lookup"><span data-stu-id="cd8c5-334">[C#]</span></span>     | <span data-ttu-id="cd8c5-335">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="cd8c5-335">Web/WebAPI</span></span>     |
| <span data-ttu-id="cd8c5-336">Configuração do Nuget</span><span class="sxs-lookup"><span data-stu-id="cd8c5-336">Nuget Config</span></span>         | `nugetconfig` |          | <span data-ttu-id="cd8c5-337">Config</span><span class="sxs-lookup"><span data-stu-id="cd8c5-337">Config</span></span>         |
| <span data-ttu-id="cd8c5-338">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="cd8c5-338">Web Config</span></span>           | `webconfig`   |          | <span data-ttu-id="cd8c5-339">Config</span><span class="sxs-lookup"><span data-stu-id="cd8c5-339">Config</span></span>         |
| <span data-ttu-id="cd8c5-340">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="cd8c5-340">Solution File</span></span>        | `sln`         |          | <span data-ttu-id="cd8c5-341">Solução</span><span class="sxs-lookup"><span data-stu-id="cd8c5-341">Solution</span></span>       |

---

## <a name="options"></a><span data-ttu-id="cd8c5-342">Opções</span><span class="sxs-lookup"><span data-stu-id="cd8c5-342">Options</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="cd8c5-343">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="cd8c5-343">.NET Core 2.2</span></span>](#tab/netcore22)

`--dry-run`

<span data-ttu-id="cd8c5-344">Exibe um resumo do que ocorreria se o comando fornecido fosse executado se resultasse na criação de um modelo.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-344">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span>

`--force`

<span data-ttu-id="cd8c5-345">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-345">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="cd8c5-346">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-346">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="cd8c5-347">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-347">Prints out help for the command.</span></span> <span data-ttu-id="cd8c5-348">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-348">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="cd8c5-349">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-349">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="cd8c5-350">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-350">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="cd8c5-351">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-351">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="cd8c5-352">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-352">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="cd8c5-353">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-353">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="cd8c5-354">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-354">Lists templates containing the specified name.</span></span> <span data-ttu-id="cd8c5-355">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-355">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="cd8c5-356">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-356">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="cd8c5-357">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-357">The language of the template to create.</span></span> <span data-ttu-id="cd8c5-358">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-358">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="cd8c5-359">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-359">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="cd8c5-360">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-360">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="cd8c5-361">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-361">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="cd8c5-362">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-362">The name for the created output.</span></span> <span data-ttu-id="cd8c5-363">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-363">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="cd8c5-364">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-364">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="cd8c5-365">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-365">Location to place the generated output.</span></span> <span data-ttu-id="cd8c5-366">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-366">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="cd8c5-367">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-367">Filters templates based on available types.</span></span> <span data-ttu-id="cd8c5-368">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="cd8c5-368">Predefined values are "project", "item", or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="cd8c5-369">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-369">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="cd8c5-370">Ao excluir o valor `<PATH|NUGET_ID>`, todos os pacotes de modelo atualmente instalados e seus modelos associados são exibidos.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-370">When excluding the `<PATH|NUGET_ID>` value, all currently installed template packs and their associated templates are displayed.</span></span>

> [!NOTE]
> <span data-ttu-id="cd8c5-371">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-371">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="cd8c5-372">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-372">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="cd8c5-373">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-373">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="cd8c5-374">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cd8c5-374">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="cd8c5-375">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-375">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="cd8c5-376">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-376">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="cd8c5-377">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-377">Prints out help for the command.</span></span> <span data-ttu-id="cd8c5-378">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-378">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="cd8c5-379">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-379">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="cd8c5-380">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-380">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="cd8c5-381">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-381">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="cd8c5-382">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-382">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="cd8c5-383">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-383">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="cd8c5-384">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-384">Lists templates containing the specified name.</span></span> <span data-ttu-id="cd8c5-385">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-385">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="cd8c5-386">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-386">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="cd8c5-387">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-387">The language of the template to create.</span></span> <span data-ttu-id="cd8c5-388">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-388">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="cd8c5-389">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-389">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="cd8c5-390">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-390">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="cd8c5-391">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-391">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="cd8c5-392">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-392">The name for the created output.</span></span> <span data-ttu-id="cd8c5-393">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-393">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="cd8c5-394">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-394">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="cd8c5-395">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-395">Location to place the generated output.</span></span> <span data-ttu-id="cd8c5-396">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-396">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="cd8c5-397">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-397">Filters templates based on available types.</span></span> <span data-ttu-id="cd8c5-398">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="cd8c5-398">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="cd8c5-399">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-399">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="cd8c5-400">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-400">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="cd8c5-401">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-401">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="cd8c5-402">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-402">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="cd8c5-403">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="cd8c5-403">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="cd8c5-404">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-404">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="cd8c5-405">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-405">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="cd8c5-406">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-406">Prints out help for the command.</span></span> <span data-ttu-id="cd8c5-407">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-407">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="cd8c5-408">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-408">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="cd8c5-409">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-409">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="cd8c5-410">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-410">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="cd8c5-411">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-411">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="cd8c5-412">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-412">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="cd8c5-413">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-413">Lists templates containing the specified name.</span></span> <span data-ttu-id="cd8c5-414">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-414">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="cd8c5-415">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-415">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="cd8c5-416">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-416">The language of the template to create.</span></span> <span data-ttu-id="cd8c5-417">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-417">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="cd8c5-418">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-418">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="cd8c5-419">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-419">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="cd8c5-420">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-420">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="cd8c5-421">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-421">The name for the created output.</span></span> <span data-ttu-id="cd8c5-422">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-422">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="cd8c5-423">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-423">Location to place the generated output.</span></span> <span data-ttu-id="cd8c5-424">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-424">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="cd8c5-425">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-425">Filters templates based on available types.</span></span> <span data-ttu-id="cd8c5-426">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="cd8c5-426">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="cd8c5-427">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-427">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="cd8c5-428">Para desinstalar um modelo usando uma origem `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-428">To uninstall a template using a source `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="cd8c5-429">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-429">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span> <span data-ttu-id="cd8c5-430">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-430">Additionally, do not include a final terminating directory slash on your template path.</span></span>
> 
> <span data-ttu-id="cd8c5-431">Se não for possível determinar o argumento `PATH` ou `NUGET_ID` necessário para desinstalar um modelo, executar `dotnet new --uninstall` sem um argumento listará todos os modelos instalados e o argumento necessário desinstalá-los.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-431">If you are unable to determine the `PATH` or `NUGET_ID` argument needed to uninstall a template, running `dotnet new --uninstall` without an argument will list all installed templates and the argument required to uninstall them.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cd8c5-432">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="cd8c5-432">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="cd8c5-433">Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-433">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="cd8c5-434">Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-434">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="cd8c5-435">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-435">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="cd8c5-436">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-436">Prints out help for the command.</span></span> <span data-ttu-id="cd8c5-437">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-437">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="cd8c5-438">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-438">Lists templates containing the specified name.</span></span> <span data-ttu-id="cd8c5-439">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-439">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="cd8c5-440">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-440">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="cd8c5-441">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-441">The language of the template to create.</span></span> <span data-ttu-id="cd8c5-442">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-442">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="cd8c5-443">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-443">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="cd8c5-444">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-444">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="cd8c5-445">Nesses casos, você precisa acrescentar o valor do parâmetro de idioma, como `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-445">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="cd8c5-446">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-446">The name for the created output.</span></span> <span data-ttu-id="cd8c5-447">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-447">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="cd8c5-448">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-448">Location to place the generated output.</span></span> <span data-ttu-id="cd8c5-449">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-449">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="cd8c5-450">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="cd8c5-450">Template options</span></span>

<span data-ttu-id="cd8c5-451">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-451">Each project template may have additional options available.</span></span> <span data-ttu-id="cd8c5-452">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="cd8c5-452">The core templates have the following additional options:</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="cd8c5-453">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="cd8c5-453">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="cd8c5-454">**console**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-454">**console**</span></span>

<span data-ttu-id="cd8c5-455">`--langVersion <VERSION_NUMBER>` – Define a propriedade `LangVersion` no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-455">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="cd8c5-456">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-456">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="cd8c5-457">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-457">Not supported for F#.</span></span>

<span data-ttu-id="cd8c5-458">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-458">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-459">**angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-459">**angular, react, reactredux**</span></span>

<span data-ttu-id="cd8c5-460">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-460">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="cd8c5-461">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-461">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-462">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-462">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="cd8c5-463">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-463">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="cd8c5-464">**razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-464">**razorclasslib**</span></span>

<span data-ttu-id="cd8c5-465">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-465">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-466">**classlib**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-466">**classlib**</span></span>

<span data-ttu-id="cd8c5-467">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-467">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="cd8c5-468">Valores: `netcoreapp2.2` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-468">Values: `netcoreapp2.2` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="cd8c5-469">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-469">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="cd8c5-470">`--langVersion <VERSION_NUMBER>` – Define a propriedade `LangVersion` no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-470">`--langVersion <VERSION_NUMBER>` - Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="cd8c5-471">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-471">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="cd8c5-472">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-472">Not supported for F#.</span></span>

<span data-ttu-id="cd8c5-473">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-473">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-474">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-474">**mstest, xunit**</span></span>

<span data-ttu-id="cd8c5-475">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-475">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="cd8c5-476">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-476">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-477">**nunit**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-477">**nunit**</span></span>

<span data-ttu-id="cd8c5-478">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-478">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="cd8c5-479">O valor padrão é `netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-479">The default value is `netcoreapp2.1`.</span></span>

<span data-ttu-id="cd8c5-480">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-480">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="cd8c5-481">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-481">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-482">**page**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-482">**page**</span></span>

<span data-ttu-id="cd8c5-483">`-na|--namespace <NAMESPACE_NAME>` – namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-483">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="cd8c5-484">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-484">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="cd8c5-485">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-485">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="cd8c5-486">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-486">**viewimports**</span></span>

<span data-ttu-id="cd8c5-487">`-na|--namespace <NAMESPACE_NAME>` – namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-487">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="cd8c5-488">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-488">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="cd8c5-489">**web**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-489">**web**</span></span>

<span data-ttu-id="cd8c5-490">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-490">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="cd8c5-491">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-491">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-492">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-492">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="cd8c5-493">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-493">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="cd8c5-494">**mvc, webapp**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-494">**mvc, webapp**</span></span>

<span data-ttu-id="cd8c5-495">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-495">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="cd8c5-496">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="cd8c5-496">The possible values are:</span></span>

- <span data-ttu-id="cd8c5-497">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-497">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="cd8c5-498">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-498">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="cd8c5-499">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-499">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="cd8c5-500">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-500">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="cd8c5-501">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-501">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="cd8c5-502">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-502">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="cd8c5-503">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-503">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="cd8c5-504">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-504">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="cd8c5-505">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-505">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="cd8c5-506">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-506">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="cd8c5-507">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-507">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-508">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-508">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="cd8c5-509">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-509">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-510">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-510">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="cd8c5-511">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-511">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-512">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-512">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="cd8c5-513">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-513">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="cd8c5-514">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-514">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="cd8c5-515">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-515">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="cd8c5-516">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-516">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="cd8c5-517">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-517">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="cd8c5-518">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-518">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="cd8c5-519">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-519">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="cd8c5-520">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-520">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="cd8c5-521">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-521">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="cd8c5-522">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-522">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="cd8c5-523">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-523">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="cd8c5-524">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-524">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="cd8c5-525">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-525">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="cd8c5-526">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-526">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="cd8c5-527">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-527">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="cd8c5-528">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-528">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="cd8c5-529">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-529">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="cd8c5-530">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-530">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="cd8c5-531">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-531">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="cd8c5-532">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-532">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="cd8c5-533">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-533">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="cd8c5-534">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-534">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-535">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-535">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-536">**webapi**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-536">**webapi**</span></span>

<span data-ttu-id="cd8c5-537">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-537">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="cd8c5-538">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="cd8c5-538">The possible values are:</span></span>

- <span data-ttu-id="cd8c5-539">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-539">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="cd8c5-540">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-540">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="cd8c5-541">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-541">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="cd8c5-542">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-542">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="cd8c5-543">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-543">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="cd8c5-544">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-544">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="cd8c5-545">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-545">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="cd8c5-546">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-546">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="cd8c5-547">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-547">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-548">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-548">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="cd8c5-549">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-549">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="cd8c5-550">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-550">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="cd8c5-551">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-551">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="cd8c5-552">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-552">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="cd8c5-553">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-553">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="cd8c5-554">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-554">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="cd8c5-555">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-555">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="cd8c5-556">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-556">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="cd8c5-557">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-557">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="cd8c5-558">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="cd8c5-559">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-559">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="cd8c5-560">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-560">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="cd8c5-561">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-561">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="cd8c5-562">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-562">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="cd8c5-563">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-563">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="cd8c5-564">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-564">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="cd8c5-565">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-565">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="cd8c5-566">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-566">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="cd8c5-567">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-567">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-568">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-568">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-569">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-569">**globaljson**</span></span>

<span data-ttu-id="cd8c5-570">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-570">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="cd8c5-571">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cd8c5-571">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="cd8c5-572">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-572">**console, angular, react, reactredux, razorclasslib**</span></span>

<span data-ttu-id="cd8c5-573">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-573">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-574">**classlib**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-574">**classlib**</span></span>

<span data-ttu-id="cd8c5-575">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-575">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="cd8c5-576">Valores: `netcoreapp2.1` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-576">Values: `netcoreapp2.1` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="cd8c5-577">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-577">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="cd8c5-578">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-578">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-579">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-579">**mstest, xunit**</span></span>

<span data-ttu-id="cd8c5-580">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-580">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="cd8c5-581">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-581">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-582">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-582">**globaljson**</span></span>

<span data-ttu-id="cd8c5-583">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-583">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="cd8c5-584">**web**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-584">**web**</span></span>

<span data-ttu-id="cd8c5-585">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-585">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="cd8c5-586">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-586">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-587">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-587">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="cd8c5-588">Essa opção é aplicável somente se `IndividualAuth` ou `OrganizationalAuth` não está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-588">This option only applies if `IndividualAuth` or `OrganizationalAuth` are not being used.</span></span>

<span data-ttu-id="cd8c5-589">**webapi**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-589">**webapi**</span></span>

<span data-ttu-id="cd8c5-590">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-590">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="cd8c5-591">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="cd8c5-591">The possible values are:</span></span>

- <span data-ttu-id="cd8c5-592">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-592">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="cd8c5-593">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-593">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="cd8c5-594">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-594">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="cd8c5-595">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-595">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="cd8c5-596">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-596">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="cd8c5-597">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-597">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="cd8c5-598">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-598">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="cd8c5-599">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-599">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="cd8c5-600">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-600">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-601">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-601">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="cd8c5-602">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-602">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="cd8c5-603">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-603">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="cd8c5-604">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-604">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="cd8c5-605">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-605">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="cd8c5-606">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-606">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="cd8c5-607">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-607">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="cd8c5-608">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-608">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="cd8c5-609">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-609">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="cd8c5-610">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-610">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="cd8c5-611">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-611">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="cd8c5-612">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-612">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="cd8c5-613">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-613">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="cd8c5-614">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-614">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="cd8c5-615">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-615">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="cd8c5-616">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-616">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="cd8c5-617">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-617">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-618">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-618">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-619">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-619">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="cd8c5-620">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-620">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="cd8c5-621">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-621">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="cd8c5-622">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-622">**mvc, razor**</span></span>

<span data-ttu-id="cd8c5-623">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-623">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="cd8c5-624">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="cd8c5-624">The possible values are:</span></span>

- <span data-ttu-id="cd8c5-625">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-625">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="cd8c5-626">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-626">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="cd8c5-627">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-627">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="cd8c5-628">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-628">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="cd8c5-629">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-629">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="cd8c5-630">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-630">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="cd8c5-631">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-631">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="cd8c5-632">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-632">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="cd8c5-633">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-633">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="cd8c5-634">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-634">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="cd8c5-635">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-635">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-636">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-636">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="cd8c5-637">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-637">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-638">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-638">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="cd8c5-639">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-639">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-640">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-640">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="cd8c5-641">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-641">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="cd8c5-642">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-642">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="cd8c5-643">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-643">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="cd8c5-644">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-644">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="cd8c5-645">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-645">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="cd8c5-646">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-646">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="cd8c5-647">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-647">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="cd8c5-648">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-648">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="cd8c5-649">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-649">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="cd8c5-650">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-650">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="cd8c5-651">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-651">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="cd8c5-652">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-652">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="cd8c5-653">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-653">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="cd8c5-654">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-654">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="cd8c5-655">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-655">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="cd8c5-656">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-656">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="cd8c5-657">`--exclude-launch-settings` – Excluir *launchSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-657">`--exclude-launch-settings` - Exclude *launchSettings.json* from the generated template.</span></span>

<span data-ttu-id="cd8c5-658">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-658">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="cd8c5-659">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-659">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="cd8c5-660">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-660">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-661">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-661">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-662">`--no-https` – O projeto não requer HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-662">`--no-https` - Project doesn't require HTTPS.</span></span> <span data-ttu-id="cd8c5-663">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-663">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="cd8c5-664">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-664">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

<span data-ttu-id="cd8c5-665">**page**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-665">**page**</span></span>

<span data-ttu-id="cd8c5-666">`-na|--namespace <NAMESPACE_NAME>` – namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-666">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="cd8c5-667">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-667">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="cd8c5-668">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-668">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="cd8c5-669">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-669">**viewimports**</span></span>

<span data-ttu-id="cd8c5-670">`-na|--namespace <NAMESPACE_NAME>` – namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-670">`-na|--namespace <NAMESPACE_NAME>` - Namespace for the generated code.</span></span> <span data-ttu-id="cd8c5-671">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-671">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="cd8c5-672">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="cd8c5-672">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="cd8c5-673">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-673">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="cd8c5-674">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-674">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-675">**classlib**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-675">**classlib**</span></span>

<span data-ttu-id="cd8c5-676">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-676">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="cd8c5-677">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-677">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="cd8c5-678">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-678">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="cd8c5-679">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-679">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-680">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-680">**mstest, xunit**</span></span>

<span data-ttu-id="cd8c5-681">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-681">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="cd8c5-682">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-682">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-683">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-683">**globaljson**</span></span>

<span data-ttu-id="cd8c5-684">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-684">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="cd8c5-685">**web**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-685">**web**</span></span>

<span data-ttu-id="cd8c5-686">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-686">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="cd8c5-687">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-687">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-688">**webapi**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-688">**webapi**</span></span>

<span data-ttu-id="cd8c5-689">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-689">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="cd8c5-690">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="cd8c5-690">The possible values are:</span></span>

- <span data-ttu-id="cd8c5-691">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-691">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="cd8c5-692">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-692">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="cd8c5-693">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-693">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="cd8c5-694">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-694">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="cd8c5-695">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-695">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="cd8c5-696">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-696">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="cd8c5-697">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-697">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="cd8c5-698">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-698">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="cd8c5-699">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-699">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-700">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-700">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="cd8c5-701">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-701">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="cd8c5-702">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-702">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="cd8c5-703">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-703">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="cd8c5-704">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-704">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="cd8c5-705">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-705">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="cd8c5-706">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-706">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="cd8c5-707">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-707">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="cd8c5-708">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-708">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="cd8c5-709">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-709">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="cd8c5-710">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-710">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="cd8c5-711">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-711">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="cd8c5-712">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-712">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="cd8c5-713">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-713">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="cd8c5-714">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-714">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="cd8c5-715">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-715">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="cd8c5-716">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-716">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-717">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-717">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-718">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-718">**mvc, razor**</span></span>

<span data-ttu-id="cd8c5-719">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-719">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="cd8c5-720">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="cd8c5-720">The possible values are:</span></span>

- <span data-ttu-id="cd8c5-721">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="cd8c5-721">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="cd8c5-722">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-722">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="cd8c5-723">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-723">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="cd8c5-724">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-724">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="cd8c5-725">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-725">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="cd8c5-726">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-726">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="cd8c5-727">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-727">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="cd8c5-728">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-728">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="cd8c5-729">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-729">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="cd8c5-730">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-730">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="cd8c5-731">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-731">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-732">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-732">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="cd8c5-733">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-733">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-734">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-734">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="cd8c5-735">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-735">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-736">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-736">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="cd8c5-737">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-737">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="cd8c5-738">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-738">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="cd8c5-739">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-739">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="cd8c5-740">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-740">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="cd8c5-741">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-741">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="cd8c5-742">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-742">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="cd8c5-743">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-743">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="cd8c5-744">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-744">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="cd8c5-745">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-745">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="cd8c5-746">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-746">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="cd8c5-747">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-747">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="cd8c5-748">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-748">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="cd8c5-749">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-749">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="cd8c5-750">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-750">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="cd8c5-751">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-751">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="cd8c5-752">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-752">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="cd8c5-753">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-753">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="cd8c5-754">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-754">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="cd8c5-755">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-755">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="cd8c5-756">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-756">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="cd8c5-757">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-757">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="cd8c5-758">**page**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-758">**page**</span></span>

<span data-ttu-id="cd8c5-759">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-759">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="cd8c5-760">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-760">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="cd8c5-761">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-761">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="cd8c5-762">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-762">**viewimports**</span></span>

<span data-ttu-id="cd8c5-763">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-763">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="cd8c5-764">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-764">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cd8c5-765">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="cd8c5-765">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="cd8c5-766">**console, xunit, mstest, web, webapi** </span><span class="sxs-lookup"><span data-stu-id="cd8c5-766">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="cd8c5-767">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-767">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="cd8c5-768">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-768">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="cd8c5-769">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-769">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="cd8c5-770">**classlib**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-770">**classlib**</span></span>

<span data-ttu-id="cd8c5-771">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-771">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="cd8c5-772">Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-772">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="cd8c5-773">O valor padrão é `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-773">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="cd8c5-774">**mvc**</span><span class="sxs-lookup"><span data-stu-id="cd8c5-774">**mvc**</span></span>

<span data-ttu-id="cd8c5-775">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-775">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="cd8c5-776">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-776">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="cd8c5-777">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-777">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="cd8c5-778">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-778">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="cd8c5-779">Valores: `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-779">Values: `None` or `Individual`.</span></span> <span data-ttu-id="cd8c5-780">O valor padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-780">The default value is `None`.</span></span>

<span data-ttu-id="cd8c5-781">`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-781">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="cd8c5-782">Valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-782">Values: `true` or `false`.</span></span> <span data-ttu-id="cd8c5-783">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-783">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="cd8c5-784">Exemplos</span><span class="sxs-lookup"><span data-stu-id="cd8c5-784">Examples</span></span>

<span data-ttu-id="cd8c5-785">Crie um projeto de aplicativo de console em C# especificando o nome do modelo:</span><span class="sxs-lookup"><span data-stu-id="cd8c5-785">Create a C# console application project by specifying the template name:</span></span>

`dotnet new "Console Application"`

<span data-ttu-id="cd8c5-786">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="cd8c5-786">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="cd8c5-787">Crie um projeto de biblioteca de classes .NET Standard no diretório especificado (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="cd8c5-787">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="cd8c5-788">Crie um projeto de MVC em C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="cd8c5-788">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="cd8c5-789">Crie um projeto de xUnit:</span><span class="sxs-lookup"><span data-stu-id="cd8c5-789">Create a new xUnit project:</span></span>

`dotnet new xunit`

<span data-ttu-id="cd8c5-790">Lista todos os modelos disponíveis para o MVC:</span><span class="sxs-lookup"><span data-stu-id="cd8c5-790">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="cd8c5-791">Liste todos os modelos que correspondem à substring *we*.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-791">List all templates matching the *we* substring.</span></span> <span data-ttu-id="cd8c5-792">Nenhuma correspondência exata é encontrada, portanto, a correspondência de substring é executada em relação tanto ao nome curto quanto às colunas de nome.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-792">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

`dotnet new we -l`

<span data-ttu-id="cd8c5-793">Tentativa de invocar o modelo correspondente a *ng*.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-793">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="cd8c5-794">Se não for possível determinar uma única correspondência, liste os modelos que são correspondências parciais.</span><span class="sxs-lookup"><span data-stu-id="cd8c5-794">If a single match can't be determined, list the templates that are partial matches.</span></span>

`dotnet new ng`

<span data-ttu-id="cd8c5-795">Instale a versão 2.0 dos modelos de aplicativo de página única do ASP.NET Core (opção de comando disponível somente para o SDK do .NET Core 1.1 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="cd8c5-795">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="cd8c5-796">Crie um *global.json* no diretório atual definindo a versão do SDK como 2.0.0 (disponível somente no SDK do .NET Core 2.0 ou em versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="cd8c5-796">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="cd8c5-797">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd8c5-797">See also</span></span>

- [<span data-ttu-id="cd8c5-798">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="cd8c5-798">Custom templates for dotnet new</span></span>](custom-templates.md)
- <span data-ttu-id="cd8c5-799">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="cd8c5-799">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md)</span></span>
- [<span data-ttu-id="cd8c5-800">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="cd8c5-800">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="cd8c5-801">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="cd8c5-801">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
