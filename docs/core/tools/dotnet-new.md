---
title: Comando dotnet new
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
ms.date: 02/13/2020
ms.openlocfilehash: d3c609419596b123f5bfb3ca85cf292a61154a70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399122"
---
# <a name="dotnet-new"></a><span data-ttu-id="59748-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="59748-103">dotnet new</span></span>

<span data-ttu-id="59748-104">**Este artigo se aplica a:** ✔️ .NET Core 2.0 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="59748-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="59748-105">Nome</span><span class="sxs-lookup"><span data-stu-id="59748-105">Name</span></span>

<span data-ttu-id="59748-106">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="59748-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="59748-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="59748-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name]
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a><span data-ttu-id="59748-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="59748-108">Description</span></span>

<span data-ttu-id="59748-109">O `dotnet new` comando cria um projeto .NET Core ou outros artefatos baseados em um modelo.</span><span class="sxs-lookup"><span data-stu-id="59748-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="59748-110">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="59748-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="59748-111">Argumentos</span><span class="sxs-lookup"><span data-stu-id="59748-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="59748-112">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="59748-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="59748-113">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="59748-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="59748-114">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="59748-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="59748-115">Você pode `dotnet new --list` correr para ver uma lista de todos os modelos instalados.</span><span class="sxs-lookup"><span data-stu-id="59748-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="59748-116">Se `TEMPLATE` o valor não for uma correspondência exata no texto na coluna **Modelos** ou **Nome Curto** da tabela retornada, uma correspondência de substring será realizada nessas duas colunas.</span><span class="sxs-lookup"><span data-stu-id="59748-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="59748-117">Começando com o .NET Core 3.0 SDK, a CLI `dotnet new` procura modelos em NuGet.org quando você invoca o comando nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="59748-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="59748-118">Se a CLI não conseguir encontrar uma `dotnet new`correspondência de modelo ao invocar, nem mesmo parcial.</span><span class="sxs-lookup"><span data-stu-id="59748-118">If the CLI can’t find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="59748-119">Se houver uma versão mais recente do modelo disponível.</span><span class="sxs-lookup"><span data-stu-id="59748-119">If there’s a newer version of the template available.</span></span> <span data-ttu-id="59748-120">Neste caso, o projeto ou artefato é criado, mas a CLI avisa sobre uma versão atualizada do modelo.</span><span class="sxs-lookup"><span data-stu-id="59748-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="59748-121">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="59748-121">The command contains a default list of templates.</span></span> <span data-ttu-id="59748-122">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="59748-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="59748-123">A tabela a seguir mostra os modelos que vêm pré-instalados com o .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="59748-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="59748-124">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="59748-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="59748-125">Clique no link nome curto para ver as opções específicas de modelo.</span><span class="sxs-lookup"><span data-stu-id="59748-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="59748-126">Modelos</span><span class="sxs-lookup"><span data-stu-id="59748-126">Templates</span></span>                                    | <span data-ttu-id="59748-127">Nome curto</span><span class="sxs-lookup"><span data-stu-id="59748-127">Short name</span></span>                      | <span data-ttu-id="59748-128">Linguagem</span><span class="sxs-lookup"><span data-stu-id="59748-128">Language</span></span>     | <span data-ttu-id="59748-129">Marcas</span><span class="sxs-lookup"><span data-stu-id="59748-129">Tags</span></span>                                  | <span data-ttu-id="59748-130">Introduzido</span><span class="sxs-lookup"><span data-stu-id="59748-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="59748-131">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="59748-131">Console Application</span></span>                          | [<span data-ttu-id="59748-132">Console</span><span class="sxs-lookup"><span data-stu-id="59748-132">console</span></span>](#console)             | <span data-ttu-id="59748-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="59748-133">[C#], F#, VB</span></span> | <span data-ttu-id="59748-134">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="59748-134">Common/Console</span></span>                        | <span data-ttu-id="59748-135">1.0</span><span class="sxs-lookup"><span data-stu-id="59748-135">1.0</span></span>        |
| <span data-ttu-id="59748-136">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="59748-136">Class library</span></span>                                | [<span data-ttu-id="59748-137">classlib</span><span class="sxs-lookup"><span data-stu-id="59748-137">classlib</span></span>](#classlib)           | <span data-ttu-id="59748-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="59748-138">[C#], F#, VB</span></span> | <span data-ttu-id="59748-139">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="59748-139">Common/Library</span></span>                        | <span data-ttu-id="59748-140">1.0</span><span class="sxs-lookup"><span data-stu-id="59748-140">1.0</span></span>        |
| <span data-ttu-id="59748-141">Aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="59748-141">WPF Application</span></span>                              | [<span data-ttu-id="59748-142">Wpf</span><span class="sxs-lookup"><span data-stu-id="59748-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="59748-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-143">[C#]</span></span>         | <span data-ttu-id="59748-144">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="59748-144">Common/WPF</span></span>                            | <span data-ttu-id="59748-145">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-145">3.0</span></span>        |
| <span data-ttu-id="59748-146">Biblioteca de classe WPF</span><span class="sxs-lookup"><span data-stu-id="59748-146">WPF Class library</span></span>                            | [<span data-ttu-id="59748-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="59748-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="59748-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-148">[C#]</span></span>         | <span data-ttu-id="59748-149">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="59748-149">Common/WPF</span></span>                            | <span data-ttu-id="59748-150">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-150">3.0</span></span>        |
| <span data-ttu-id="59748-151">Biblioteca de Controles Personalizados do WPF</span><span class="sxs-lookup"><span data-stu-id="59748-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="59748-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="59748-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="59748-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-153">[C#]</span></span>         | <span data-ttu-id="59748-154">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="59748-154">Common/WPF</span></span>                            | <span data-ttu-id="59748-155">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-155">3.0</span></span>        |
| <span data-ttu-id="59748-156">Biblioteca de controle de usuário WPF</span><span class="sxs-lookup"><span data-stu-id="59748-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="59748-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="59748-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="59748-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-158">[C#]</span></span>         | <span data-ttu-id="59748-159">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="59748-159">Common/WPF</span></span>                            | <span data-ttu-id="59748-160">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-160">3.0</span></span>        |
| <span data-ttu-id="59748-161">Aplicativo Formulários do Windows (WinForms)</span><span class="sxs-lookup"><span data-stu-id="59748-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="59748-162">Winforms</span><span class="sxs-lookup"><span data-stu-id="59748-162">winforms</span></span>](#winforms)           | <span data-ttu-id="59748-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-163">[C#]</span></span>         | <span data-ttu-id="59748-164">Formas comuns/winforms</span><span class="sxs-lookup"><span data-stu-id="59748-164">Common/WinForms</span></span>                       | <span data-ttu-id="59748-165">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-165">3.0</span></span>        |
| <span data-ttu-id="59748-166">Biblioteca de classes de Formulários do Windows (WinForms)</span><span class="sxs-lookup"><span data-stu-id="59748-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="59748-167">winformslib</span><span class="sxs-lookup"><span data-stu-id="59748-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="59748-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-168">[C#]</span></span>         | <span data-ttu-id="59748-169">Formas comuns/winforms</span><span class="sxs-lookup"><span data-stu-id="59748-169">Common/WinForms</span></span>                       | <span data-ttu-id="59748-170">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-170">3.0</span></span>        |
| <span data-ttu-id="59748-171">Serviço ao Trabalhador</span><span class="sxs-lookup"><span data-stu-id="59748-171">Worker Service</span></span>                               | [<span data-ttu-id="59748-172">Trabalhador</span><span class="sxs-lookup"><span data-stu-id="59748-172">worker</span></span>](#web-others)           | <span data-ttu-id="59748-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-173">[C#]</span></span>         | <span data-ttu-id="59748-174">Comum/Trabalhador/Web</span><span class="sxs-lookup"><span data-stu-id="59748-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="59748-175">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-175">3.0</span></span>        |
| <span data-ttu-id="59748-176">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="59748-176">Unit Test Project</span></span>                            | [<span data-ttu-id="59748-177">Mstest</span><span class="sxs-lookup"><span data-stu-id="59748-177">mstest</span></span>](#test)                 | <span data-ttu-id="59748-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="59748-178">[C#], F#, VB</span></span> | <span data-ttu-id="59748-179">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="59748-179">Test/MSTest</span></span>                           | <span data-ttu-id="59748-180">1.0</span><span class="sxs-lookup"><span data-stu-id="59748-180">1.0</span></span>        |
| <span data-ttu-id="59748-181">Projeto de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="59748-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="59748-182">Nunit</span><span class="sxs-lookup"><span data-stu-id="59748-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="59748-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="59748-183">[C#], F#, VB</span></span> | <span data-ttu-id="59748-184">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="59748-184">Test/NUnit</span></span>                            | <span data-ttu-id="59748-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="59748-185">2.1.400</span></span>    |
| <span data-ttu-id="59748-186">Item de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="59748-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="59748-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="59748-187">[C#], F#, VB</span></span> | <span data-ttu-id="59748-188">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="59748-188">Test/NUnit</span></span>                            | <span data-ttu-id="59748-189">2.2</span><span class="sxs-lookup"><span data-stu-id="59748-189">2.2</span></span>        |
| <span data-ttu-id="59748-190">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="59748-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="59748-191">Xunit</span><span class="sxs-lookup"><span data-stu-id="59748-191">xunit</span></span>](#test)                  | <span data-ttu-id="59748-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="59748-192">[C#], F#, VB</span></span> | <span data-ttu-id="59748-193">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="59748-193">Test/xUnit</span></span>                            | <span data-ttu-id="59748-194">1.0</span><span class="sxs-lookup"><span data-stu-id="59748-194">1.0</span></span>        |
| <span data-ttu-id="59748-195">Componente da navalha</span><span class="sxs-lookup"><span data-stu-id="59748-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="59748-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-196">[C#]</span></span>         | <span data-ttu-id="59748-197">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="59748-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="59748-198">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-198">3.0</span></span>        |
| <span data-ttu-id="59748-199">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="59748-199">Razor Page</span></span>                                   | [<span data-ttu-id="59748-200">Página</span><span class="sxs-lookup"><span data-stu-id="59748-200">page</span></span>](#page)                   | <span data-ttu-id="59748-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-201">[C#]</span></span>         | <span data-ttu-id="59748-202">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="59748-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="59748-203">2,0</span><span class="sxs-lookup"><span data-stu-id="59748-203">2.0</span></span>        |
| <span data-ttu-id="59748-204">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="59748-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="59748-205">verimportações</span><span class="sxs-lookup"><span data-stu-id="59748-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="59748-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-206">[C#]</span></span>         | <span data-ttu-id="59748-207">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="59748-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="59748-208">2,0</span><span class="sxs-lookup"><span data-stu-id="59748-208">2.0</span></span>        |
| <span data-ttu-id="59748-209">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="59748-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="59748-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-210">[C#]</span></span>         | <span data-ttu-id="59748-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="59748-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="59748-212">2,0</span><span class="sxs-lookup"><span data-stu-id="59748-212">2.0</span></span>        |
| <span data-ttu-id="59748-213">Aplicativo Blazor Server</span><span class="sxs-lookup"><span data-stu-id="59748-213">Blazor Server App</span></span>                            | [<span data-ttu-id="59748-214">blazorserver</span><span class="sxs-lookup"><span data-stu-id="59748-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="59748-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-215">[C#]</span></span>         | <span data-ttu-id="59748-216">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="59748-216">Web/Blazor</span></span>                            | <span data-ttu-id="59748-217">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-217">3.0</span></span>        |
| <span data-ttu-id="59748-218">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="59748-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="59748-219">web</span><span class="sxs-lookup"><span data-stu-id="59748-219">web</span></span>](#web)                     | <span data-ttu-id="59748-220">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="59748-220">[C#], F#</span></span>     | <span data-ttu-id="59748-221">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="59748-221">Web/Empty</span></span>                             | <span data-ttu-id="59748-222">1.0</span><span class="sxs-lookup"><span data-stu-id="59748-222">1.0</span></span>        |
| <span data-ttu-id="59748-223">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="59748-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="59748-224">Mvc</span><span class="sxs-lookup"><span data-stu-id="59748-224">mvc</span></span>](#web-options)             | <span data-ttu-id="59748-225">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="59748-225">[C#], F#</span></span>     | <span data-ttu-id="59748-226">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="59748-226">Web/MVC</span></span>                               | <span data-ttu-id="59748-227">1.0</span><span class="sxs-lookup"><span data-stu-id="59748-227">1.0</span></span>        |
| <span data-ttu-id="59748-228">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="59748-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="59748-229">webapp, navalha</span><span class="sxs-lookup"><span data-stu-id="59748-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="59748-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-230">[C#]</span></span>         | <span data-ttu-id="59748-231">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="59748-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="59748-232">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="59748-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="59748-233">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="59748-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="59748-234">angular</span><span class="sxs-lookup"><span data-stu-id="59748-234">angular</span></span>](#spa)                 | <span data-ttu-id="59748-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-235">[C#]</span></span>         | <span data-ttu-id="59748-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="59748-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="59748-237">2,0</span><span class="sxs-lookup"><span data-stu-id="59748-237">2.0</span></span>        |
| <span data-ttu-id="59748-238">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="59748-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="59748-239">Reagir</span><span class="sxs-lookup"><span data-stu-id="59748-239">react</span></span>](#spa)                   | <span data-ttu-id="59748-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-240">[C#]</span></span>         | <span data-ttu-id="59748-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="59748-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="59748-242">2,0</span><span class="sxs-lookup"><span data-stu-id="59748-242">2.0</span></span>        |
| <span data-ttu-id="59748-243">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="59748-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="59748-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="59748-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="59748-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-245">[C#]</span></span>         | <span data-ttu-id="59748-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="59748-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="59748-247">2,0</span><span class="sxs-lookup"><span data-stu-id="59748-247">2.0</span></span>        |
| <span data-ttu-id="59748-248">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="59748-248">Razor Class Library</span></span>                          | [<span data-ttu-id="59748-249">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="59748-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="59748-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-250">[C#]</span></span>         | <span data-ttu-id="59748-251">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="59748-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="59748-252">2.1</span><span class="sxs-lookup"><span data-stu-id="59748-252">2.1</span></span>        |
| <span data-ttu-id="59748-253">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="59748-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="59748-254">webapi</span><span class="sxs-lookup"><span data-stu-id="59748-254">webapi</span></span>](#webapi)               | <span data-ttu-id="59748-255">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="59748-255">[C#], F#</span></span>     | <span data-ttu-id="59748-256">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="59748-256">Web/WebAPI</span></span>                            | <span data-ttu-id="59748-257">1.0</span><span class="sxs-lookup"><span data-stu-id="59748-257">1.0</span></span>        |
| <span data-ttu-id="59748-258">ASP.NET Core gRPC Service</span><span class="sxs-lookup"><span data-stu-id="59748-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="59748-259">grpc</span><span class="sxs-lookup"><span data-stu-id="59748-259">grpc</span></span>](#web-others)             | <span data-ttu-id="59748-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="59748-260">[C#]</span></span>         | <span data-ttu-id="59748-261">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="59748-261">Web/gRPC</span></span>                              | <span data-ttu-id="59748-262">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-262">3.0</span></span>        |
| <span data-ttu-id="59748-263">Arquivo de buffer de protocolo</span><span class="sxs-lookup"><span data-stu-id="59748-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="59748-264">Proto</span><span class="sxs-lookup"><span data-stu-id="59748-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="59748-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="59748-265">Web/gRPC</span></span>                              | <span data-ttu-id="59748-266">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-266">3.0</span></span>        |
| <span data-ttu-id="59748-267">dotnet arquivo gitignore</span><span class="sxs-lookup"><span data-stu-id="59748-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="59748-268">Config</span><span class="sxs-lookup"><span data-stu-id="59748-268">Config</span></span>                                | <span data-ttu-id="59748-269">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-269">3.0</span></span>        |
| <span data-ttu-id="59748-270">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="59748-270">global.json file</span></span>                             | [<span data-ttu-id="59748-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="59748-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="59748-272">Config</span><span class="sxs-lookup"><span data-stu-id="59748-272">Config</span></span>                                | <span data-ttu-id="59748-273">2,0</span><span class="sxs-lookup"><span data-stu-id="59748-273">2.0</span></span>        |
| <span data-ttu-id="59748-274">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="59748-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="59748-275">Config</span><span class="sxs-lookup"><span data-stu-id="59748-275">Config</span></span>                                | <span data-ttu-id="59748-276">1.0</span><span class="sxs-lookup"><span data-stu-id="59748-276">1.0</span></span>        |
| <span data-ttu-id="59748-277">dotnet arquivo manifesto ferramenta local</span><span class="sxs-lookup"><span data-stu-id="59748-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="59748-278">Config</span><span class="sxs-lookup"><span data-stu-id="59748-278">Config</span></span>                                | <span data-ttu-id="59748-279">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-279">3.0</span></span>        |
| <span data-ttu-id="59748-280">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="59748-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="59748-281">Config</span><span class="sxs-lookup"><span data-stu-id="59748-281">Config</span></span>                                | <span data-ttu-id="59748-282">1.0</span><span class="sxs-lookup"><span data-stu-id="59748-282">1.0</span></span>        |
| <span data-ttu-id="59748-283">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="59748-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="59748-284">Solução</span><span class="sxs-lookup"><span data-stu-id="59748-284">Solution</span></span>                              | <span data-ttu-id="59748-285">1.0</span><span class="sxs-lookup"><span data-stu-id="59748-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="59748-286">Opções</span><span class="sxs-lookup"><span data-stu-id="59748-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="59748-287">Exibe um resumo do que aconteceria se o comando dado fosse executado.</span><span class="sxs-lookup"><span data-stu-id="59748-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="59748-288">Disponível desde .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="59748-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="59748-289">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="59748-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="59748-290">Isso é necessário quando o modelo escolhido substituiria os arquivos existentes no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="59748-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="59748-291">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="59748-291">Prints out help for the command.</span></span> <span data-ttu-id="59748-292">Ele pode ser invocado para o `dotnet new` comando em si ou para qualquer modelo.</span><span class="sxs-lookup"><span data-stu-id="59748-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="59748-293">Por exemplo, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="59748-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="59748-294">Instala um pacote de `PATH` `NUGET_ID` modelo si mesmo ou fornecido.</span><span class="sxs-lookup"><span data-stu-id="59748-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="59748-295">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="59748-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="59748-296">Por `dotnet new` padrão, \* passa para a versão, que representa a versão mais recente do pacote estável.</span><span class="sxs-lookup"><span data-stu-id="59748-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="59748-297">Veja um exemplo na seção [Exemplos.](#examples)</span><span class="sxs-lookup"><span data-stu-id="59748-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="59748-298">Se uma versão do modelo já estiver instalada quando você executar este comando, o modelo será atualizado para a versão especificada ou para a versão estável mais recente se nenhuma versão foi especificada.</span><span class="sxs-lookup"><span data-stu-id="59748-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="59748-299">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="59748-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="59748-300">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="59748-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="59748-301">Se nenhum nome for especificado, lista todos os modelos.</span><span class="sxs-lookup"><span data-stu-id="59748-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="59748-302">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="59748-302">The language of the template to create.</span></span> <span data-ttu-id="59748-303">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="59748-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="59748-304">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="59748-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="59748-305">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="59748-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="59748-306">Nesses casos, inclui o valor do parâmetro de idioma entre aspas.</span><span class="sxs-lookup"><span data-stu-id="59748-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="59748-307">Por exemplo, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="59748-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="59748-308">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="59748-308">The name for the created output.</span></span> <span data-ttu-id="59748-309">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="59748-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source`**

  <span data-ttu-id="59748-310">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="59748-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="59748-311">Disponível desde .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="59748-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="59748-312">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="59748-312">Location to place the generated output.</span></span> <span data-ttu-id="59748-313">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="59748-313">The default is the current directory.</span></span>

- **`--type`**

  <span data-ttu-id="59748-314">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="59748-314">Filters templates based on available types.</span></span> <span data-ttu-id="59748-315">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="59748-315">Predefined values are "project", "item", or "other".</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="59748-316">Desinstala um pacote `PATH` de `NUGET_ID` modelo no ou fornecido.</span><span class="sxs-lookup"><span data-stu-id="59748-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="59748-317">Quando `<PATH|NUGET_ID>` o valor não é especificado, todos os pacotes de modelos instalados no momento e seus modelos associados são exibidos.</span><span class="sxs-lookup"><span data-stu-id="59748-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="59748-318">Ao `NUGET_ID`especificar, não inclua o número da versão.</span><span class="sxs-lookup"><span data-stu-id="59748-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="59748-319">Se você não especificar um parâmetro para essa opção, o comando listaos os modelos e detalhes instalados sobre eles.</span><span class="sxs-lookup"><span data-stu-id="59748-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="59748-320">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="59748-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="59748-321">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="59748-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="59748-322">Não inclua uma barra final de diretório de terminação no seu caminho de modelo.</span><span class="sxs-lookup"><span data-stu-id="59748-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="59748-323">Verifica se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento e os instala.</span><span class="sxs-lookup"><span data-stu-id="59748-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="59748-324">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="59748-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="59748-325">Verifique se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento.</span><span class="sxs-lookup"><span data-stu-id="59748-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="59748-326">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="59748-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="59748-327">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="59748-327">Template options</span></span>

<span data-ttu-id="59748-328">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="59748-328">Each project template may have additional options available.</span></span> <span data-ttu-id="59748-329">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="59748-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="59748-330">console</span><span class="sxs-lookup"><span data-stu-id="59748-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="59748-331">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="59748-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="59748-332">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="59748-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="59748-333">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="59748-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="59748-334">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="59748-334">SDK version</span></span> | <span data-ttu-id="59748-335">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="59748-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="59748-336">3.1</span><span class="sxs-lookup"><span data-stu-id="59748-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="59748-337">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="59748-338">Define `LangVersion` a propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="59748-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="59748-339">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="59748-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="59748-340">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="59748-340">Not supported for F#.</span></span> <span data-ttu-id="59748-341">Disponível desde .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="59748-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="59748-342">Para obter uma lista de [versões](../../csharp/language-reference/configure-language-version.md#defaults)C# padrão, consulte Padrões .</span><span class="sxs-lookup"><span data-stu-id="59748-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="59748-343">Se especificado, não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="59748-344">Disponível desde .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="59748-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="59748-345">classlib</span><span class="sxs-lookup"><span data-stu-id="59748-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="59748-346">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="59748-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="59748-347">Valores: `netcoreapp<version>` para criar uma Biblioteca de classes do .NET Core ou `netstandard<version>` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="59748-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="59748-348">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="59748-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="59748-349">Define `LangVersion` a propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="59748-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="59748-350">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="59748-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="59748-351">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="59748-351">Not supported for F#.</span></span> <span data-ttu-id="59748-352">Disponível desde .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="59748-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="59748-353">Para obter uma lista de [versões](../../csharp/language-reference/configure-language-version.md#defaults)C# padrão, consulte Padrões .</span><span class="sxs-lookup"><span data-stu-id="59748-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="59748-354">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf"></a><span data-ttu-id="59748-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="59748-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="59748-356">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="59748-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="59748-357">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="59748-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="59748-358">Disponível desde .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="59748-358">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="59748-359">Define `LangVersion` a propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="59748-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="59748-360">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="59748-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="59748-361">Para obter uma lista de [versões](../../csharp/language-reference/configure-language-version.md#defaults)C# padrão, consulte Padrões .</span><span class="sxs-lookup"><span data-stu-id="59748-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="59748-362">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms"></a><span data-ttu-id="59748-363">winforms, winformslib</span><span class="sxs-lookup"><span data-stu-id="59748-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="59748-364">Define `LangVersion` a propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="59748-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="59748-365">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="59748-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="59748-366">Para obter uma lista de [versões](../../csharp/language-reference/configure-language-version.md#defaults)C# padrão, consulte Padrões .</span><span class="sxs-lookup"><span data-stu-id="59748-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="59748-367">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web-others"></a><span data-ttu-id="59748-368">trabalhador, grpc</span><span class="sxs-lookup"><span data-stu-id="59748-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="59748-369">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="59748-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="59748-370">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="59748-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="59748-371">Disponível desde .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="59748-371">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="59748-372">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="59748-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="59748-373">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="test"></a><span data-ttu-id="59748-374">mstest, xunit</span><span class="sxs-lookup"><span data-stu-id="59748-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="59748-375">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="59748-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="59748-376">Opção disponível desde .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="59748-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="59748-377">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="59748-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="59748-378">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="59748-378">SDK version</span></span> | <span data-ttu-id="59748-379">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="59748-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="59748-380">3.1</span><span class="sxs-lookup"><span data-stu-id="59748-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="59748-381">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="59748-382">Permite a embalagem para o projeto usando [o pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="59748-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="59748-383">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="59748-384">Nunit</span><span class="sxs-lookup"><span data-stu-id="59748-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="59748-385">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="59748-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="59748-386">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="59748-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="59748-387">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="59748-387">SDK version</span></span> | <span data-ttu-id="59748-388">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="59748-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="59748-389">3.1</span><span class="sxs-lookup"><span data-stu-id="59748-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="59748-390">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="59748-391">2.2</span><span class="sxs-lookup"><span data-stu-id="59748-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="59748-392">2.1</span><span class="sxs-lookup"><span data-stu-id="59748-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="59748-393">Permite a embalagem para o projeto usando [o pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="59748-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="59748-394">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="59748-395">página</span><span class="sxs-lookup"><span data-stu-id="59748-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="59748-396">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="59748-396">Namespace for the generated code.</span></span> <span data-ttu-id="59748-397">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="59748-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="59748-398">Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="59748-398">Creates the page without a PageModel.</span></span>

***

### <a name="namespace"></a><span data-ttu-id="59748-399">verimportações, proto</span><span class="sxs-lookup"><span data-stu-id="59748-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="59748-400">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="59748-400">Namespace for the generated code.</span></span> <span data-ttu-id="59748-401">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="59748-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="59748-402">blazorserver</span><span class="sxs-lookup"><span data-stu-id="59748-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="59748-403">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="59748-403">The type of authentication to use.</span></span> <span data-ttu-id="59748-404">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="59748-404">The possible values are:</span></span>

  - <span data-ttu-id="59748-405">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="59748-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="59748-406">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="59748-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="59748-407">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="59748-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="59748-408">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="59748-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="59748-409">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="59748-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="59748-410">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="59748-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="59748-411">A ocorrência B2C do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="59748-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="59748-412">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="59748-413">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="59748-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="59748-414">O id da política de inscrição e login para este projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="59748-415">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="59748-416">O iD da política de senha redefinida para este projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="59748-417">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="59748-418">O ID de política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="59748-419">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="59748-420">A instância do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="59748-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="59748-421">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="59748-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="59748-422">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="59748-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="59748-423">O ID do Cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-423">The Client ID for this project.</span></span> <span data-ttu-id="59748-424">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="59748-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="59748-425">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="59748-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="59748-426">O domínio para o inquilino do diretório.</span><span class="sxs-lookup"><span data-stu-id="59748-426">The domain for the directory tenant.</span></span> <span data-ttu-id="59748-427">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="59748-428">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="59748-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="59748-429">O ID TenantId do diretório para se conectar.</span><span class="sxs-lookup"><span data-stu-id="59748-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="59748-430">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="59748-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="59748-431">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="59748-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="59748-432">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="59748-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="59748-433">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="59748-434">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="59748-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="59748-435">Permite que este aplicativo leia acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="59748-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="59748-436">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="59748-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="59748-437">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="59748-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="59748-438">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="59748-438">Turns off HTTPS.</span></span> <span data-ttu-id="59748-439">Esta opção só `Individual`se `IndividualB2C` `SingleOrg`aplica `MultiOrg` se , , `--auth`ou não estiver sendo usado para .</span><span class="sxs-lookup"><span data-stu-id="59748-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="59748-440">Especifica o LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="59748-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="59748-441">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="59748-442">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="59748-443">web</span><span class="sxs-lookup"><span data-stu-id="59748-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="59748-444">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="59748-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="59748-445">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="59748-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="59748-446">Opção não disponível no .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="59748-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="59748-447">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="59748-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="59748-448">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="59748-448">SDK version</span></span> | <span data-ttu-id="59748-449">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="59748-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="59748-450">3.1</span><span class="sxs-lookup"><span data-stu-id="59748-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="59748-451">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="59748-452">2.1</span><span class="sxs-lookup"><span data-stu-id="59748-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="59748-453">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="59748-454">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="59748-454">Turns off HTTPS.</span></span>

***

### <a name="web-options"></a><span data-ttu-id="59748-455">mvc, webapp</span><span class="sxs-lookup"><span data-stu-id="59748-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="59748-456">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="59748-456">The type of authentication to use.</span></span> <span data-ttu-id="59748-457">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="59748-457">The possible values are:</span></span>

  - <span data-ttu-id="59748-458">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="59748-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="59748-459">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="59748-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="59748-460">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="59748-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="59748-461">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="59748-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="59748-462">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="59748-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="59748-463">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="59748-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="59748-464">A ocorrência B2C do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="59748-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="59748-465">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="59748-466">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="59748-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="59748-467">O id da política de inscrição e login para este projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="59748-468">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="59748-469">O iD da política de senha redefinida para este projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="59748-470">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="59748-471">O ID de política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="59748-472">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="59748-473">A instância do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="59748-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="59748-474">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="59748-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="59748-475">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="59748-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="59748-476">O ID do Cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-476">The Client ID for this project.</span></span> <span data-ttu-id="59748-477">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="59748-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="59748-478">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="59748-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="59748-479">O domínio para o inquilino do diretório.</span><span class="sxs-lookup"><span data-stu-id="59748-479">The domain for the directory tenant.</span></span> <span data-ttu-id="59748-480">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="59748-481">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="59748-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="59748-482">O ID TenantId do diretório para se conectar.</span><span class="sxs-lookup"><span data-stu-id="59748-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="59748-483">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="59748-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="59748-484">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="59748-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="59748-485">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="59748-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="59748-486">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="59748-487">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="59748-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="59748-488">Permite que este aplicativo leia acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="59748-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="59748-489">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="59748-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="59748-490">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="59748-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="59748-491">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="59748-491">Turns off HTTPS.</span></span> <span data-ttu-id="59748-492">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="59748-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="59748-493">Especifica o LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="59748-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="59748-494">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="59748-495">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="59748-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="59748-496">Opção disponível desde .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="59748-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="59748-497">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="59748-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="59748-498">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="59748-498">SDK version</span></span> | <span data-ttu-id="59748-499">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="59748-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="59748-500">3.1</span><span class="sxs-lookup"><span data-stu-id="59748-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="59748-501">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="59748-502">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="59748-503">Inclui o BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="59748-504">Opção não disponível em .NET Core 2.2 e 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="59748-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

***

### <a name="spa"></a><span data-ttu-id="59748-505">angular, reagir</span><span class="sxs-lookup"><span data-stu-id="59748-505">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="59748-506">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="59748-506">The type of authentication to use.</span></span> <span data-ttu-id="59748-507">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="59748-507">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="59748-508">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="59748-508">The possible values are:</span></span>

  - <span data-ttu-id="59748-509">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="59748-509">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="59748-510">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="59748-510">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="59748-511">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="59748-511">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="59748-512">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-512">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="59748-513">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="59748-513">Turns off HTTPS.</span></span> <span data-ttu-id="59748-514">Essa opção só se aplica `None`se a autenticação for .</span><span class="sxs-lookup"><span data-stu-id="59748-514">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="59748-515">Especifica o LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="59748-515">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="59748-516">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-516">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="59748-517">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="59748-517">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="59748-518">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="59748-518">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="59748-519">Opção não disponível no .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="59748-519">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="59748-520">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="59748-520">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="59748-521">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="59748-521">SDK version</span></span> | <span data-ttu-id="59748-522">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="59748-522">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="59748-523">3.1</span><span class="sxs-lookup"><span data-stu-id="59748-523">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="59748-524">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-524">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="59748-525">2.1</span><span class="sxs-lookup"><span data-stu-id="59748-525">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="59748-526">reactredux</span><span class="sxs-lookup"><span data-stu-id="59748-526">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="59748-527">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="59748-527">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="59748-528">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="59748-528">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="59748-529">Opção não disponível no .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="59748-529">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="59748-530">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="59748-530">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="59748-531">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="59748-531">SDK version</span></span> | <span data-ttu-id="59748-532">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="59748-532">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="59748-533">3.1</span><span class="sxs-lookup"><span data-stu-id="59748-533">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="59748-534">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-534">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="59748-535">2.1</span><span class="sxs-lookup"><span data-stu-id="59748-535">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="59748-536">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-536">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="59748-537">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="59748-537">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="59748-538">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="59748-538">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="59748-539">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="59748-540">Suporta a adição de páginas e visualizações tradicionais de navalha, além de componentes para esta biblioteca.</span><span class="sxs-lookup"><span data-stu-id="59748-540">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="59748-541">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="59748-541">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="59748-542">webapi</span><span class="sxs-lookup"><span data-stu-id="59748-542">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="59748-543">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="59748-543">The type of authentication to use.</span></span> <span data-ttu-id="59748-544">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="59748-544">The possible values are:</span></span>

  - <span data-ttu-id="59748-545">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="59748-545">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="59748-546">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="59748-546">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="59748-547">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="59748-547">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="59748-548">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="59748-548">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="59748-549">A ocorrência B2C do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="59748-549">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="59748-550">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-550">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="59748-551">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="59748-551">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="59748-552">O id da política de inscrição e login para este projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-552">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="59748-553">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="59748-553">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="59748-554">A instância do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="59748-554">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="59748-555">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="59748-555">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="59748-556">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="59748-556">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="59748-557">O ID do Cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-557">The Client ID for this project.</span></span> <span data-ttu-id="59748-558">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="59748-558">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="59748-559">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="59748-559">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="59748-560">O domínio para o inquilino do diretório.</span><span class="sxs-lookup"><span data-stu-id="59748-560">The domain for the directory tenant.</span></span> <span data-ttu-id="59748-561">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="59748-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="59748-562">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="59748-562">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="59748-563">O ID TenantId do diretório para se conectar.</span><span class="sxs-lookup"><span data-stu-id="59748-563">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="59748-564">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="59748-564">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="59748-565">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="59748-565">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="59748-566">Permite que este aplicativo leia acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="59748-566">Allows this application read-access to the directory.</span></span> <span data-ttu-id="59748-567">Só se `SingleOrg` aplica à autenticação.</span><span class="sxs-lookup"><span data-stu-id="59748-567">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="59748-568">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="59748-568">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="59748-569">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="59748-569">Turns off HTTPS.</span></span> <span data-ttu-id="59748-570">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="59748-570">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="59748-571">Essa opção só `IndividualB2C` se `SingleOrg` aplica se ou não estiver sendo usada para autenticação.</span><span class="sxs-lookup"><span data-stu-id="59748-571">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="59748-572">Especifica o LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="59748-572">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="59748-573">Só se `IndividualB2C` aplica à autenticação.</span><span class="sxs-lookup"><span data-stu-id="59748-573">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="59748-574">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="59748-574">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="59748-575">Opção não disponível no .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="59748-575">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="59748-576">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="59748-576">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="59748-577">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="59748-577">SDK version</span></span> | <span data-ttu-id="59748-578">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="59748-578">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="59748-579">3.1</span><span class="sxs-lookup"><span data-stu-id="59748-579">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="59748-580">3.0</span><span class="sxs-lookup"><span data-stu-id="59748-580">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="59748-581">2.1</span><span class="sxs-lookup"><span data-stu-id="59748-581">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="59748-582">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="59748-582">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="59748-583">globaljson</span><span class="sxs-lookup"><span data-stu-id="59748-583">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="59748-584">Especifica a versão do .NET Core SDK para usar no arquivo *global.json.*</span><span class="sxs-lookup"><span data-stu-id="59748-584">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="59748-585">Exemplos</span><span class="sxs-lookup"><span data-stu-id="59748-585">Examples</span></span>

- <span data-ttu-id="59748-586">Crie um projeto de aplicativo de console em C# especificando o nome do modelo:</span><span class="sxs-lookup"><span data-stu-id="59748-586">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="59748-587">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="59748-587">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="59748-588">Criar um projeto de biblioteca de classe .NET padrão no diretório especificado:</span><span class="sxs-lookup"><span data-stu-id="59748-588">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="59748-589">Crie um projeto de MVC em C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="59748-589">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="59748-590">Crie um projeto de xUnit:</span><span class="sxs-lookup"><span data-stu-id="59748-590">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="59748-591">Liste todos os modelos disponíveis para os modelos spa (Single Page Application, aplicativo de página única):</span><span class="sxs-lookup"><span data-stu-id="59748-591">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="59748-592">Liste todos os modelos que correspondem à substring *we*.</span><span class="sxs-lookup"><span data-stu-id="59748-592">List all templates matching the *we* substring.</span></span> <span data-ttu-id="59748-593">Nenhuma correspondência exata é encontrada, portanto, a correspondência de substring é executada em relação tanto ao nome curto quanto às colunas de nome.</span><span class="sxs-lookup"><span data-stu-id="59748-593">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="59748-594">Tentativa de invocar o modelo correspondente a *ng*.</span><span class="sxs-lookup"><span data-stu-id="59748-594">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="59748-595">Se não for possível determinar uma única correspondência, liste os modelos que são correspondências parciais.</span><span class="sxs-lookup"><span data-stu-id="59748-595">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="59748-596">Instale a versão 2.0 dos modelos SPA para ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="59748-596">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="59748-597">Liste os modelos e detalhes instalados sobre eles, incluindo como desinstalá-los:</span><span class="sxs-lookup"><span data-stu-id="59748-597">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="59748-598">Crie um *global.json* no diretório atual definindo a versão SDK para 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="59748-598">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="59748-599">Confira também</span><span class="sxs-lookup"><span data-stu-id="59748-599">See also</span></span>

- [<span data-ttu-id="59748-600">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="59748-600">Custom templates for dotnet new</span></span>](custom-templates.md)
- <span data-ttu-id="59748-601">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="59748-601">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md)</span></span>
- [<span data-ttu-id="59748-602">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="59748-602">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="59748-603">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="59748-603">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
