---
title: Comando dotnet new
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
ms.date: 02/13/2020
ms.openlocfilehash: d3c609419596b123f5bfb3ca85cf292a61154a70
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157213"
---
# <a name="dotnet-new"></a><span data-ttu-id="facbd-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="facbd-103">dotnet new</span></span>

<span data-ttu-id="facbd-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="facbd-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="facbd-105">Nome</span><span class="sxs-lookup"><span data-stu-id="facbd-105">Name</span></span>

<span data-ttu-id="facbd-106">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="facbd-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="facbd-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="facbd-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name]
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a><span data-ttu-id="facbd-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="facbd-108">Description</span></span>

<span data-ttu-id="facbd-109">O comando `dotnet new` cria um projeto .NET Core ou outros artefatos com base em um modelo.</span><span class="sxs-lookup"><span data-stu-id="facbd-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="facbd-110">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="facbd-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="facbd-111">Argumentos</span><span class="sxs-lookup"><span data-stu-id="facbd-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="facbd-112">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="facbd-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="facbd-113">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="facbd-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="facbd-114">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="facbd-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="facbd-115">Você pode executar `dotnet new --list` para ver uma lista de todos os modelos instalados.</span><span class="sxs-lookup"><span data-stu-id="facbd-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="facbd-116">Se o valor de `TEMPLATE` não for uma correspondência exata no texto na coluna **modelos** ou **nome curto** da tabela retornada, uma correspondência de subcadeia de caracteres será executada nessas duas colunas.</span><span class="sxs-lookup"><span data-stu-id="facbd-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="facbd-117">A partir do SDK do .NET Core 3,0, a CLI procura modelos em NuGet.org quando você invoca o comando `dotnet new` nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="facbd-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="facbd-118">Se a CLI não encontrar uma correspondência de modelo ao invocar `dotnet new`, nem mesmo parcial.</span><span class="sxs-lookup"><span data-stu-id="facbd-118">If the CLI can’t find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="facbd-119">Se houver uma versão mais recente do modelo disponível.</span><span class="sxs-lookup"><span data-stu-id="facbd-119">If there’s a newer version of the template available.</span></span> <span data-ttu-id="facbd-120">Nesse caso, o projeto ou artefato é criado, mas a CLI avisa sobre uma versão atualizada do modelo.</span><span class="sxs-lookup"><span data-stu-id="facbd-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="facbd-121">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="facbd-121">The command contains a default list of templates.</span></span> <span data-ttu-id="facbd-122">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="facbd-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="facbd-123">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="facbd-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="facbd-124">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="facbd-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="facbd-125">Clique no link nome curto para ver as opções de modelo específicas.</span><span class="sxs-lookup"><span data-stu-id="facbd-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="facbd-126">Modelos</span><span class="sxs-lookup"><span data-stu-id="facbd-126">Templates</span></span>                                    | <span data-ttu-id="facbd-127">Nome curto</span><span class="sxs-lookup"><span data-stu-id="facbd-127">Short name</span></span>                      | <span data-ttu-id="facbd-128">Linguagem</span><span class="sxs-lookup"><span data-stu-id="facbd-128">Language</span></span>     | <span data-ttu-id="facbd-129">Marcas</span><span class="sxs-lookup"><span data-stu-id="facbd-129">Tags</span></span>                                  | <span data-ttu-id="facbd-130">Incluída</span><span class="sxs-lookup"><span data-stu-id="facbd-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="facbd-131">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="facbd-131">Console Application</span></span>                          | [<span data-ttu-id="facbd-132">console</span><span class="sxs-lookup"><span data-stu-id="facbd-132">console</span></span>](#console)             | <span data-ttu-id="facbd-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="facbd-133">[C#], F#, VB</span></span> | <span data-ttu-id="facbd-134">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="facbd-134">Common/Console</span></span>                        | <span data-ttu-id="facbd-135">1.0</span><span class="sxs-lookup"><span data-stu-id="facbd-135">1.0</span></span>        |
| <span data-ttu-id="facbd-136">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="facbd-136">Class library</span></span>                                | [<span data-ttu-id="facbd-137">classlib</span><span class="sxs-lookup"><span data-stu-id="facbd-137">classlib</span></span>](#classlib)           | <span data-ttu-id="facbd-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="facbd-138">[C#], F#, VB</span></span> | <span data-ttu-id="facbd-139">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="facbd-139">Common/Library</span></span>                        | <span data-ttu-id="facbd-140">1.0</span><span class="sxs-lookup"><span data-stu-id="facbd-140">1.0</span></span>        |
| <span data-ttu-id="facbd-141">Aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="facbd-141">WPF Application</span></span>                              | [<span data-ttu-id="facbd-142">WFP</span><span class="sxs-lookup"><span data-stu-id="facbd-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="facbd-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-143">[C#]</span></span>         | <span data-ttu-id="facbd-144">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="facbd-144">Common/WPF</span></span>                            | <span data-ttu-id="facbd-145">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-145">3.0</span></span>        |
| <span data-ttu-id="facbd-146">Biblioteca de classes do WPF</span><span class="sxs-lookup"><span data-stu-id="facbd-146">WPF Class library</span></span>                            | [<span data-ttu-id="facbd-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="facbd-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="facbd-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-148">[C#]</span></span>         | <span data-ttu-id="facbd-149">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="facbd-149">Common/WPF</span></span>                            | <span data-ttu-id="facbd-150">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-150">3.0</span></span>        |
| <span data-ttu-id="facbd-151">Biblioteca de controle personalizado WPF</span><span class="sxs-lookup"><span data-stu-id="facbd-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="facbd-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="facbd-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="facbd-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-153">[C#]</span></span>         | <span data-ttu-id="facbd-154">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="facbd-154">Common/WPF</span></span>                            | <span data-ttu-id="facbd-155">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-155">3.0</span></span>        |
| <span data-ttu-id="facbd-156">Biblioteca de Controle de Usuário do WPF</span><span class="sxs-lookup"><span data-stu-id="facbd-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="facbd-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="facbd-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="facbd-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-158">[C#]</span></span>         | <span data-ttu-id="facbd-159">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="facbd-159">Common/WPF</span></span>                            | <span data-ttu-id="facbd-160">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-160">3.0</span></span>        |
| <span data-ttu-id="facbd-161">Aplicativo Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="facbd-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="facbd-162">WinForms</span><span class="sxs-lookup"><span data-stu-id="facbd-162">winforms</span></span>](#winforms)           | <span data-ttu-id="facbd-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-163">[C#]</span></span>         | <span data-ttu-id="facbd-164">Comum/WinForms</span><span class="sxs-lookup"><span data-stu-id="facbd-164">Common/WinForms</span></span>                       | <span data-ttu-id="facbd-165">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-165">3.0</span></span>        |
| <span data-ttu-id="facbd-166">Biblioteca de classes do Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="facbd-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="facbd-167">winformslib</span><span class="sxs-lookup"><span data-stu-id="facbd-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="facbd-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-168">[C#]</span></span>         | <span data-ttu-id="facbd-169">Comum/WinForms</span><span class="sxs-lookup"><span data-stu-id="facbd-169">Common/WinForms</span></span>                       | <span data-ttu-id="facbd-170">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-170">3.0</span></span>        |
| <span data-ttu-id="facbd-171">Serviço de trabalho</span><span class="sxs-lookup"><span data-stu-id="facbd-171">Worker Service</span></span>                               | [<span data-ttu-id="facbd-172">funcionários</span><span class="sxs-lookup"><span data-stu-id="facbd-172">worker</span></span>](#web-others)           | <span data-ttu-id="facbd-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-173">[C#]</span></span>         | <span data-ttu-id="facbd-174">Comum/de trabalho/Web</span><span class="sxs-lookup"><span data-stu-id="facbd-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="facbd-175">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-175">3.0</span></span>        |
| <span data-ttu-id="facbd-176">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="facbd-176">Unit Test Project</span></span>                            | [<span data-ttu-id="facbd-177">MSTest</span><span class="sxs-lookup"><span data-stu-id="facbd-177">mstest</span></span>](#test)                 | <span data-ttu-id="facbd-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="facbd-178">[C#], F#, VB</span></span> | <span data-ttu-id="facbd-179">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="facbd-179">Test/MSTest</span></span>                           | <span data-ttu-id="facbd-180">1.0</span><span class="sxs-lookup"><span data-stu-id="facbd-180">1.0</span></span>        |
| <span data-ttu-id="facbd-181">Projeto de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="facbd-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="facbd-182">nunit</span><span class="sxs-lookup"><span data-stu-id="facbd-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="facbd-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="facbd-183">[C#], F#, VB</span></span> | <span data-ttu-id="facbd-184">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="facbd-184">Test/NUnit</span></span>                            | <span data-ttu-id="facbd-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="facbd-185">2.1.400</span></span>    |
| <span data-ttu-id="facbd-186">Item de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="facbd-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="facbd-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="facbd-187">[C#], F#, VB</span></span> | <span data-ttu-id="facbd-188">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="facbd-188">Test/NUnit</span></span>                            | <span data-ttu-id="facbd-189">2.2</span><span class="sxs-lookup"><span data-stu-id="facbd-189">2.2</span></span>        |
| <span data-ttu-id="facbd-190">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="facbd-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="facbd-191">xUnit</span><span class="sxs-lookup"><span data-stu-id="facbd-191">xunit</span></span>](#test)                  | <span data-ttu-id="facbd-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="facbd-192">[C#], F#, VB</span></span> | <span data-ttu-id="facbd-193">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="facbd-193">Test/xUnit</span></span>                            | <span data-ttu-id="facbd-194">1.0</span><span class="sxs-lookup"><span data-stu-id="facbd-194">1.0</span></span>        |
| <span data-ttu-id="facbd-195">Componente Razor</span><span class="sxs-lookup"><span data-stu-id="facbd-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="facbd-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-196">[C#]</span></span>         | <span data-ttu-id="facbd-197">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="facbd-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="facbd-198">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-198">3.0</span></span>        |
| <span data-ttu-id="facbd-199">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="facbd-199">Razor Page</span></span>                                   | [<span data-ttu-id="facbd-200">page</span><span class="sxs-lookup"><span data-stu-id="facbd-200">page</span></span>](#page)                   | <span data-ttu-id="facbd-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-201">[C#]</span></span>         | <span data-ttu-id="facbd-202">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="facbd-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="facbd-203">2,0</span><span class="sxs-lookup"><span data-stu-id="facbd-203">2.0</span></span>        |
| <span data-ttu-id="facbd-204">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="facbd-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="facbd-205">viewimports</span><span class="sxs-lookup"><span data-stu-id="facbd-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="facbd-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-206">[C#]</span></span>         | <span data-ttu-id="facbd-207">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="facbd-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="facbd-208">2,0</span><span class="sxs-lookup"><span data-stu-id="facbd-208">2.0</span></span>        |
| <span data-ttu-id="facbd-209">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="facbd-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="facbd-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-210">[C#]</span></span>         | <span data-ttu-id="facbd-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="facbd-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="facbd-212">2,0</span><span class="sxs-lookup"><span data-stu-id="facbd-212">2.0</span></span>        |
| <span data-ttu-id="facbd-213">Aplicativo de servidor mais incrivelmente</span><span class="sxs-lookup"><span data-stu-id="facbd-213">Blazor Server App</span></span>                            | [<span data-ttu-id="facbd-214">blazorserver</span><span class="sxs-lookup"><span data-stu-id="facbd-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="facbd-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-215">[C#]</span></span>         | <span data-ttu-id="facbd-216">Web/mais e mais</span><span class="sxs-lookup"><span data-stu-id="facbd-216">Web/Blazor</span></span>                            | <span data-ttu-id="facbd-217">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-217">3.0</span></span>        |
| <span data-ttu-id="facbd-218">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="facbd-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="facbd-219">web</span><span class="sxs-lookup"><span data-stu-id="facbd-219">web</span></span>](#web)                     | <span data-ttu-id="facbd-220">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="facbd-220">[C#], F#</span></span>     | <span data-ttu-id="facbd-221">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="facbd-221">Web/Empty</span></span>                             | <span data-ttu-id="facbd-222">1.0</span><span class="sxs-lookup"><span data-stu-id="facbd-222">1.0</span></span>        |
| <span data-ttu-id="facbd-223">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="facbd-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="facbd-224">mvc</span><span class="sxs-lookup"><span data-stu-id="facbd-224">mvc</span></span>](#web-options)             | <span data-ttu-id="facbd-225">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="facbd-225">[C#], F#</span></span>     | <span data-ttu-id="facbd-226">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="facbd-226">Web/MVC</span></span>                               | <span data-ttu-id="facbd-227">1.0</span><span class="sxs-lookup"><span data-stu-id="facbd-227">1.0</span></span>        |
| <span data-ttu-id="facbd-228">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="facbd-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="facbd-229">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="facbd-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="facbd-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-230">[C#]</span></span>         | <span data-ttu-id="facbd-231">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="facbd-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="facbd-232">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="facbd-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="facbd-233">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="facbd-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="facbd-234">angular</span><span class="sxs-lookup"><span data-stu-id="facbd-234">angular</span></span>](#spa)                 | <span data-ttu-id="facbd-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-235">[C#]</span></span>         | <span data-ttu-id="facbd-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="facbd-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="facbd-237">2,0</span><span class="sxs-lookup"><span data-stu-id="facbd-237">2.0</span></span>        |
| <span data-ttu-id="facbd-238">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="facbd-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="facbd-239">reagir</span><span class="sxs-lookup"><span data-stu-id="facbd-239">react</span></span>](#spa)                   | <span data-ttu-id="facbd-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-240">[C#]</span></span>         | <span data-ttu-id="facbd-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="facbd-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="facbd-242">2,0</span><span class="sxs-lookup"><span data-stu-id="facbd-242">2.0</span></span>        |
| <span data-ttu-id="facbd-243">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="facbd-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="facbd-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="facbd-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="facbd-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-245">[C#]</span></span>         | <span data-ttu-id="facbd-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="facbd-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="facbd-247">2,0</span><span class="sxs-lookup"><span data-stu-id="facbd-247">2.0</span></span>        |
| <span data-ttu-id="facbd-248">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="facbd-248">Razor Class Library</span></span>                          | [<span data-ttu-id="facbd-249">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="facbd-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="facbd-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-250">[C#]</span></span>         | <span data-ttu-id="facbd-251">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="facbd-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="facbd-252">2.1</span><span class="sxs-lookup"><span data-stu-id="facbd-252">2.1</span></span>        |
| <span data-ttu-id="facbd-253">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="facbd-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="facbd-254">webapi</span><span class="sxs-lookup"><span data-stu-id="facbd-254">webapi</span></span>](#webapi)               | <span data-ttu-id="facbd-255">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="facbd-255">[C#], F#</span></span>     | <span data-ttu-id="facbd-256">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="facbd-256">Web/WebAPI</span></span>                            | <span data-ttu-id="facbd-257">1.0</span><span class="sxs-lookup"><span data-stu-id="facbd-257">1.0</span></span>        |
| <span data-ttu-id="facbd-258">ASP.NET Core serviço gRPC</span><span class="sxs-lookup"><span data-stu-id="facbd-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="facbd-259">grpc</span><span class="sxs-lookup"><span data-stu-id="facbd-259">grpc</span></span>](#web-others)             | <span data-ttu-id="facbd-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="facbd-260">[C#]</span></span>         | <span data-ttu-id="facbd-261">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="facbd-261">Web/gRPC</span></span>                              | <span data-ttu-id="facbd-262">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-262">3.0</span></span>        |
| <span data-ttu-id="facbd-263">Arquivo de buffer de protocolo</span><span class="sxs-lookup"><span data-stu-id="facbd-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="facbd-264">proto</span><span class="sxs-lookup"><span data-stu-id="facbd-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="facbd-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="facbd-265">Web/gRPC</span></span>                              | <span data-ttu-id="facbd-266">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-266">3.0</span></span>        |
| <span data-ttu-id="facbd-267">arquivo dotnet gitignore</span><span class="sxs-lookup"><span data-stu-id="facbd-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="facbd-268">Config</span><span class="sxs-lookup"><span data-stu-id="facbd-268">Config</span></span>                                | <span data-ttu-id="facbd-269">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-269">3.0</span></span>        |
| <span data-ttu-id="facbd-270">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="facbd-270">global.json file</span></span>                             | [<span data-ttu-id="facbd-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="facbd-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="facbd-272">Config</span><span class="sxs-lookup"><span data-stu-id="facbd-272">Config</span></span>                                | <span data-ttu-id="facbd-273">2,0</span><span class="sxs-lookup"><span data-stu-id="facbd-273">2.0</span></span>        |
| <span data-ttu-id="facbd-274">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="facbd-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="facbd-275">Config</span><span class="sxs-lookup"><span data-stu-id="facbd-275">Config</span></span>                                | <span data-ttu-id="facbd-276">1.0</span><span class="sxs-lookup"><span data-stu-id="facbd-276">1.0</span></span>        |
| <span data-ttu-id="facbd-277">arquivo de manifesto da ferramenta local dotnet</span><span class="sxs-lookup"><span data-stu-id="facbd-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="facbd-278">Config</span><span class="sxs-lookup"><span data-stu-id="facbd-278">Config</span></span>                                | <span data-ttu-id="facbd-279">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-279">3.0</span></span>        |
| <span data-ttu-id="facbd-280">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="facbd-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="facbd-281">Config</span><span class="sxs-lookup"><span data-stu-id="facbd-281">Config</span></span>                                | <span data-ttu-id="facbd-282">1.0</span><span class="sxs-lookup"><span data-stu-id="facbd-282">1.0</span></span>        |
| <span data-ttu-id="facbd-283">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="facbd-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="facbd-284">Solução</span><span class="sxs-lookup"><span data-stu-id="facbd-284">Solution</span></span>                              | <span data-ttu-id="facbd-285">1.0</span><span class="sxs-lookup"><span data-stu-id="facbd-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="facbd-286">Opções</span><span class="sxs-lookup"><span data-stu-id="facbd-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="facbd-287">Exibe um resumo do que aconteceria se o comando fornecido fosse executado.</span><span class="sxs-lookup"><span data-stu-id="facbd-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="facbd-288">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="facbd-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="facbd-289">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="facbd-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="facbd-290">Isso é necessário quando o modelo escolhido substituiria os arquivos existentes no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="facbd-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="facbd-291">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="facbd-291">Prints out help for the command.</span></span> <span data-ttu-id="facbd-292">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo.</span><span class="sxs-lookup"><span data-stu-id="facbd-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="facbd-293">Por exemplo, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="facbd-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="facbd-294">Instala um pacote de modelos do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="facbd-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="facbd-295">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="facbd-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="facbd-296">Por padrão, `dotnet new` passa \* para a versão, que representa a versão de pacote estável mais recente.</span><span class="sxs-lookup"><span data-stu-id="facbd-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="facbd-297">Veja um exemplo na seção [exemplos](#examples) .</span><span class="sxs-lookup"><span data-stu-id="facbd-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="facbd-298">Se uma versão do modelo já tiver sido instalada quando você executar esse comando, o modelo será atualizado para a versão especificada ou para a versão estável mais recente se nenhuma versão tiver sido especificada.</span><span class="sxs-lookup"><span data-stu-id="facbd-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="facbd-299">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="facbd-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="facbd-300">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="facbd-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="facbd-301">Se nenhum nome for especificado, listará todos os modelos.</span><span class="sxs-lookup"><span data-stu-id="facbd-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="facbd-302">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="facbd-302">The language of the template to create.</span></span> <span data-ttu-id="facbd-303">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="facbd-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="facbd-304">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="facbd-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="facbd-305">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="facbd-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="facbd-306">Nesses casos, coloque o valor do parâmetro de idioma entre aspas.</span><span class="sxs-lookup"><span data-stu-id="facbd-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="facbd-307">Por exemplo, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="facbd-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="facbd-308">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="facbd-308">The name for the created output.</span></span> <span data-ttu-id="facbd-309">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="facbd-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source`**

  <span data-ttu-id="facbd-310">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="facbd-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="facbd-311">Disponível desde o SDK do .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="facbd-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="facbd-312">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="facbd-312">Location to place the generated output.</span></span> <span data-ttu-id="facbd-313">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="facbd-313">The default is the current directory.</span></span>

- **`--type`**

  <span data-ttu-id="facbd-314">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="facbd-314">Filters templates based on available types.</span></span> <span data-ttu-id="facbd-315">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="facbd-315">Predefined values are "project", "item", or "other".</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="facbd-316">Desinstala um pacote de modelos no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="facbd-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="facbd-317">Quando o valor de `<PATH|NUGET_ID>` não é especificado, todos os pacotes de modelos instalados atualmente e seus modelos associados são exibidos.</span><span class="sxs-lookup"><span data-stu-id="facbd-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="facbd-318">Ao especificar `NUGET_ID`, não inclua o número de versão.</span><span class="sxs-lookup"><span data-stu-id="facbd-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="facbd-319">Se você não especificar um parâmetro para essa opção, o comando listará os modelos instalados e os detalhes sobre eles.</span><span class="sxs-lookup"><span data-stu-id="facbd-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="facbd-320">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="facbd-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="facbd-321">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="facbd-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="facbd-322">Não inclua uma barra de diretório final de encerramento no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="facbd-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="facbd-323">Verifica se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento e os instala.</span><span class="sxs-lookup"><span data-stu-id="facbd-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="facbd-324">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="facbd-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="facbd-325">Verifica se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento.</span><span class="sxs-lookup"><span data-stu-id="facbd-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="facbd-326">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="facbd-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="facbd-327">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="facbd-327">Template options</span></span>

<span data-ttu-id="facbd-328">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="facbd-328">Each project template may have additional options available.</span></span> <span data-ttu-id="facbd-329">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="facbd-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="facbd-330">console</span><span class="sxs-lookup"><span data-stu-id="facbd-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="facbd-331">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="facbd-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="facbd-332">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="facbd-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="facbd-333">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="facbd-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="facbd-334">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="facbd-334">SDK version</span></span> | <span data-ttu-id="facbd-335">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="facbd-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="facbd-336">3.1</span><span class="sxs-lookup"><span data-stu-id="facbd-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="facbd-337">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="facbd-338">Define a propriedade `LangVersion` no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="facbd-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="facbd-339">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="facbd-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="facbd-340">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="facbd-340">Not supported for F#.</span></span> <span data-ttu-id="facbd-341">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="facbd-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="facbd-342">Para obter uma lista de C# versões padrão, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="facbd-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="facbd-343">Se especificado, não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="facbd-344">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="facbd-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="facbd-345">classlib</span><span class="sxs-lookup"><span data-stu-id="facbd-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="facbd-346">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="facbd-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="facbd-347">Valores: `netcoreapp<version>` para criar uma Biblioteca de classes do .NET Core ou `netstandard<version>` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="facbd-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="facbd-348">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="facbd-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="facbd-349">Define a propriedade `LangVersion` no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="facbd-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="facbd-350">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="facbd-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="facbd-351">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="facbd-351">Not supported for F#.</span></span> <span data-ttu-id="facbd-352">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="facbd-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="facbd-353">Para obter uma lista de C# versões padrão, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="facbd-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="facbd-354">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf"></a><span data-ttu-id="facbd-355">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="facbd-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="facbd-356">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="facbd-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="facbd-357">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="facbd-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="facbd-358">Disponível desde o SDK do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="facbd-358">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="facbd-359">Define a propriedade `LangVersion` no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="facbd-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="facbd-360">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="facbd-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="facbd-361">Para obter uma lista de C# versões padrão, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="facbd-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="facbd-362">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms"></a><span data-ttu-id="facbd-363">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="facbd-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="facbd-364">Define a propriedade `LangVersion` no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="facbd-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="facbd-365">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="facbd-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="facbd-366">Para obter uma lista de C# versões padrão, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="facbd-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="facbd-367">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web-others"></a><span data-ttu-id="facbd-368">trabalho, grpc</span><span class="sxs-lookup"><span data-stu-id="facbd-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="facbd-369">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="facbd-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="facbd-370">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="facbd-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="facbd-371">Disponível desde o SDK do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="facbd-371">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="facbd-372">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="facbd-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="facbd-373">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="test"></a><span data-ttu-id="facbd-374">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="facbd-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="facbd-375">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="facbd-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="facbd-376">Opção disponível desde o SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="facbd-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="facbd-377">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="facbd-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="facbd-378">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="facbd-378">SDK version</span></span> | <span data-ttu-id="facbd-379">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="facbd-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="facbd-380">3.1</span><span class="sxs-lookup"><span data-stu-id="facbd-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="facbd-381">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="facbd-382">Habilita o empacotamento para o projeto usando o [pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="facbd-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="facbd-383">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="facbd-384">NUnit</span><span class="sxs-lookup"><span data-stu-id="facbd-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="facbd-385">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="facbd-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="facbd-386">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="facbd-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="facbd-387">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="facbd-387">SDK version</span></span> | <span data-ttu-id="facbd-388">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="facbd-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="facbd-389">3.1</span><span class="sxs-lookup"><span data-stu-id="facbd-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="facbd-390">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="facbd-391">2.2</span><span class="sxs-lookup"><span data-stu-id="facbd-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="facbd-392">2.1</span><span class="sxs-lookup"><span data-stu-id="facbd-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="facbd-393">Habilita o empacotamento para o projeto usando o [pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="facbd-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="facbd-394">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="facbd-395">página</span><span class="sxs-lookup"><span data-stu-id="facbd-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="facbd-396">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="facbd-396">Namespace for the generated code.</span></span> <span data-ttu-id="facbd-397">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="facbd-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="facbd-398">Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="facbd-398">Creates the page without a PageModel.</span></span>

***

### <a name="namespace"></a><span data-ttu-id="facbd-399">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="facbd-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="facbd-400">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="facbd-400">Namespace for the generated code.</span></span> <span data-ttu-id="facbd-401">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="facbd-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="facbd-402">blazorserver</span><span class="sxs-lookup"><span data-stu-id="facbd-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="facbd-403">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="facbd-403">The type of authentication to use.</span></span> <span data-ttu-id="facbd-404">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="facbd-404">The possible values are:</span></span>

  - <span data-ttu-id="facbd-405">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="facbd-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="facbd-406">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="facbd-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="facbd-407">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="facbd-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="facbd-408">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="facbd-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="facbd-409">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="facbd-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="facbd-410">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="facbd-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="facbd-411">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="facbd-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="facbd-412">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="facbd-413">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="facbd-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="facbd-414">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="facbd-415">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="facbd-416">A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="facbd-417">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="facbd-418">A ID de política de perfil de edição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="facbd-419">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="facbd-420">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="facbd-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="facbd-421">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="facbd-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="facbd-422">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="facbd-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="facbd-423">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-423">The Client ID for this project.</span></span> <span data-ttu-id="facbd-424">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="facbd-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="facbd-425">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="facbd-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="facbd-426">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="facbd-426">The domain for the directory tenant.</span></span> <span data-ttu-id="facbd-427">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="facbd-428">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="facbd-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="facbd-429">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="facbd-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="facbd-430">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="facbd-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="facbd-431">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="facbd-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="facbd-432">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="facbd-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="facbd-433">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="facbd-434">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="facbd-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="facbd-435">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="facbd-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="facbd-436">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="facbd-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="facbd-437">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="facbd-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="facbd-438">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="facbd-438">Turns off HTTPS.</span></span> <span data-ttu-id="facbd-439">Essa opção só se aplica se `Individual`, `IndividualB2C`, `SingleOrg`ou `MultiOrg` não estiverem sendo usadas para `--auth`.</span><span class="sxs-lookup"><span data-stu-id="facbd-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="facbd-440">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="facbd-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="facbd-441">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="facbd-442">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="facbd-443">web</span><span class="sxs-lookup"><span data-stu-id="facbd-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="facbd-444">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="facbd-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="facbd-445">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="facbd-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="facbd-446">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="facbd-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="facbd-447">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="facbd-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="facbd-448">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="facbd-448">SDK version</span></span> | <span data-ttu-id="facbd-449">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="facbd-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="facbd-450">3.1</span><span class="sxs-lookup"><span data-stu-id="facbd-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="facbd-451">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="facbd-452">2.1</span><span class="sxs-lookup"><span data-stu-id="facbd-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="facbd-453">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="facbd-454">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="facbd-454">Turns off HTTPS.</span></span>

***

### <a name="web-options"></a><span data-ttu-id="facbd-455">MVC, webapp</span><span class="sxs-lookup"><span data-stu-id="facbd-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="facbd-456">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="facbd-456">The type of authentication to use.</span></span> <span data-ttu-id="facbd-457">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="facbd-457">The possible values are:</span></span>

  - <span data-ttu-id="facbd-458">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="facbd-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="facbd-459">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="facbd-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="facbd-460">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="facbd-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="facbd-461">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="facbd-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="facbd-462">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="facbd-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="facbd-463">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="facbd-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="facbd-464">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="facbd-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="facbd-465">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="facbd-466">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="facbd-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="facbd-467">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="facbd-468">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="facbd-469">A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="facbd-470">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="facbd-471">A ID de política de perfil de edição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="facbd-472">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="facbd-473">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="facbd-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="facbd-474">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="facbd-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="facbd-475">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="facbd-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="facbd-476">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-476">The Client ID for this project.</span></span> <span data-ttu-id="facbd-477">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="facbd-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="facbd-478">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="facbd-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="facbd-479">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="facbd-479">The domain for the directory tenant.</span></span> <span data-ttu-id="facbd-480">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="facbd-481">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="facbd-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="facbd-482">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="facbd-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="facbd-483">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="facbd-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="facbd-484">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="facbd-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="facbd-485">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="facbd-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="facbd-486">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="facbd-487">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="facbd-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="facbd-488">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="facbd-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="facbd-489">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="facbd-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="facbd-490">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="facbd-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="facbd-491">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="facbd-491">Turns off HTTPS.</span></span> <span data-ttu-id="facbd-492">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="facbd-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="facbd-493">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="facbd-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="facbd-494">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="facbd-495">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="facbd-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="facbd-496">Opção disponível desde o SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="facbd-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="facbd-497">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="facbd-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="facbd-498">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="facbd-498">SDK version</span></span> | <span data-ttu-id="facbd-499">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="facbd-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="facbd-500">3.1</span><span class="sxs-lookup"><span data-stu-id="facbd-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="facbd-501">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="facbd-502">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="facbd-503">Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="facbd-504">Opção não disponível no SDK do .NET Core 2,2 e 3,1.</span><span class="sxs-lookup"><span data-stu-id="facbd-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

***

### <a name="spa"></a><span data-ttu-id="facbd-505">angular, reagir</span><span class="sxs-lookup"><span data-stu-id="facbd-505">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="facbd-506">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="facbd-506">The type of authentication to use.</span></span> <span data-ttu-id="facbd-507">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="facbd-507">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="facbd-508">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="facbd-508">The possible values are:</span></span>

  - <span data-ttu-id="facbd-509">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="facbd-509">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="facbd-510">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="facbd-510">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="facbd-511">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="facbd-511">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="facbd-512">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-512">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="facbd-513">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="facbd-513">Turns off HTTPS.</span></span> <span data-ttu-id="facbd-514">Essa opção se aplica somente se a autenticação for `None`.</span><span class="sxs-lookup"><span data-stu-id="facbd-514">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="facbd-515">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="facbd-515">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="facbd-516">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-516">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="facbd-517">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="facbd-517">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="facbd-518">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="facbd-518">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="facbd-519">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="facbd-519">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="facbd-520">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="facbd-520">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="facbd-521">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="facbd-521">SDK version</span></span> | <span data-ttu-id="facbd-522">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="facbd-522">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="facbd-523">3.1</span><span class="sxs-lookup"><span data-stu-id="facbd-523">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="facbd-524">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-524">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="facbd-525">2.1</span><span class="sxs-lookup"><span data-stu-id="facbd-525">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="facbd-526">reactredux</span><span class="sxs-lookup"><span data-stu-id="facbd-526">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="facbd-527">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="facbd-527">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="facbd-528">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="facbd-528">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="facbd-529">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="facbd-529">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="facbd-530">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="facbd-530">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="facbd-531">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="facbd-531">SDK version</span></span> | <span data-ttu-id="facbd-532">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="facbd-532">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="facbd-533">3.1</span><span class="sxs-lookup"><span data-stu-id="facbd-533">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="facbd-534">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-534">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="facbd-535">2.1</span><span class="sxs-lookup"><span data-stu-id="facbd-535">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="facbd-536">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-536">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="facbd-537">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="facbd-537">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="facbd-538">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="facbd-538">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="facbd-539">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="facbd-540">Dá suporte à adição de páginas e exibições do Razor tradicionais, além dos componentes dessa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="facbd-540">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="facbd-541">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="facbd-541">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="facbd-542">webapi</span><span class="sxs-lookup"><span data-stu-id="facbd-542">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="facbd-543">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="facbd-543">The type of authentication to use.</span></span> <span data-ttu-id="facbd-544">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="facbd-544">The possible values are:</span></span>

  - <span data-ttu-id="facbd-545">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="facbd-545">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="facbd-546">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="facbd-546">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="facbd-547">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="facbd-547">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="facbd-548">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="facbd-548">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="facbd-549">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="facbd-549">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="facbd-550">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-550">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="facbd-551">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="facbd-551">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="facbd-552">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-552">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="facbd-553">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-553">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="facbd-554">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="facbd-554">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="facbd-555">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="facbd-555">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="facbd-556">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="facbd-556">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="facbd-557">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-557">The Client ID for this project.</span></span> <span data-ttu-id="facbd-558">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="facbd-558">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="facbd-559">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="facbd-559">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="facbd-560">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="facbd-560">The domain for the directory tenant.</span></span> <span data-ttu-id="facbd-561">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="facbd-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="facbd-562">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="facbd-562">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="facbd-563">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="facbd-563">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="facbd-564">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="facbd-564">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="facbd-565">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="facbd-565">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="facbd-566">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="facbd-566">Allows this application read-access to the directory.</span></span> <span data-ttu-id="facbd-567">Aplica-se somente à autenticação `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="facbd-567">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="facbd-568">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="facbd-568">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="facbd-569">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="facbd-569">Turns off HTTPS.</span></span> <span data-ttu-id="facbd-570">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="facbd-570">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="facbd-571">Esta opção se aplica somente se `IndividualB2C` ou `SingleOrg` não estiverem sendo usados para autenticação.</span><span class="sxs-lookup"><span data-stu-id="facbd-571">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="facbd-572">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="facbd-572">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="facbd-573">Aplica-se somente à autenticação `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="facbd-573">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="facbd-574">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="facbd-574">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="facbd-575">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="facbd-575">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="facbd-576">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="facbd-576">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="facbd-577">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="facbd-577">SDK version</span></span> | <span data-ttu-id="facbd-578">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="facbd-578">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="facbd-579">3.1</span><span class="sxs-lookup"><span data-stu-id="facbd-579">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="facbd-580">3.0</span><span class="sxs-lookup"><span data-stu-id="facbd-580">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="facbd-581">2.1</span><span class="sxs-lookup"><span data-stu-id="facbd-581">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="facbd-582">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="facbd-582">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="facbd-583">globaljson</span><span class="sxs-lookup"><span data-stu-id="facbd-583">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="facbd-584">Especifica a versão do SDK do .NET Core a ser usada no arquivo *global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="facbd-584">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="facbd-585">Exemplos</span><span class="sxs-lookup"><span data-stu-id="facbd-585">Examples</span></span>

- <span data-ttu-id="facbd-586">Crie um projeto de aplicativo de console em C# especificando o nome do modelo:</span><span class="sxs-lookup"><span data-stu-id="facbd-586">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="facbd-587">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="facbd-587">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="facbd-588">Crie um projeto de biblioteca de classe .NET Standard no diretório especificado:</span><span class="sxs-lookup"><span data-stu-id="facbd-588">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="facbd-589">Crie um projeto de MVC em C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="facbd-589">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="facbd-590">Crie um projeto de xUnit:</span><span class="sxs-lookup"><span data-stu-id="facbd-590">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="facbd-591">Listar todos os modelos disponíveis para modelos de aplicativo de página única (SPA):</span><span class="sxs-lookup"><span data-stu-id="facbd-591">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="facbd-592">Liste todos os modelos que correspondem à substring *we*.</span><span class="sxs-lookup"><span data-stu-id="facbd-592">List all templates matching the *we* substring.</span></span> <span data-ttu-id="facbd-593">Nenhuma correspondência exata é encontrada, portanto, a correspondência de substring é executada em relação tanto ao nome curto quanto às colunas de nome.</span><span class="sxs-lookup"><span data-stu-id="facbd-593">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="facbd-594">Tentativa de invocar o modelo correspondente a *ng*.</span><span class="sxs-lookup"><span data-stu-id="facbd-594">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="facbd-595">Se não for possível determinar uma única correspondência, liste os modelos que são correspondências parciais.</span><span class="sxs-lookup"><span data-stu-id="facbd-595">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="facbd-596">Instale a versão 2,0 dos modelos SPA para ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="facbd-596">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="facbd-597">Liste os modelos instalados e os detalhes sobre eles, incluindo como desinstalá-los:</span><span class="sxs-lookup"><span data-stu-id="facbd-597">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="facbd-598">Crie um *global. JSON* no diretório atual definindo a versão do SDK para 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="facbd-598">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="facbd-599">Confira também</span><span class="sxs-lookup"><span data-stu-id="facbd-599">See also</span></span>

- [<span data-ttu-id="facbd-600">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="facbd-600">Custom templates for dotnet new</span></span>](custom-templates.md)
- <span data-ttu-id="facbd-601">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="facbd-601">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md)</span></span>
- [<span data-ttu-id="facbd-602">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="facbd-602">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="facbd-603">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="facbd-603">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
